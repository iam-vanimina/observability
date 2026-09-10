# Roboshop Monitoring & Observability

Complete monitoring and observability stack for the **Roboshop microservices application** running on Docker Desktop Kubernetes.

The project provides:

* 📊 Metrics monitoring with Prometheus
* 📈 Visualization with Grafana
* 📝 Centralized application logs with Loki
* 🔄 Log collection with Grafana Alloy
* 🔍 Distributed application tracing with OpenTelemetry
* 🧵 Trace storage with Grafana Tempo
* 🔗 Logs ↔ Traces correlation
* ☸️ Kubernetes workload monitoring
* 🚨 Application and infrastructure troubleshooting

---

## Architecture

```text
                         ROBOSHOP APPLICATION
                                  │
              ┌───────────────────┼───────────────────┐
              │                   │                   │
              ▼                   ▼                   ▼
          Frontend              Cart              Catalogue
              │                   │                   │
              └───────────────────┼───────────────────┘
                                  │
                         ┌────────┴────────┐
                         ▼                 ▼
                     Payment           Shipping
                         │                 │
                         └────────┬────────┘
                                  ▼
                              Dispatch


                    KUBERNETES OBSERVABILITY
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
        ▼                     ▼                     ▼
   Application              Metrics              Logs
      Traces                   │                   │
        │                      ▼                   ▼
        ▼                 Prometheus             Alloy
  OpenTelemetry                                  │
        │                                         ▼
        ▼                                        Loki
      Tempo                                        │
        │                                         │
        └────────────────────┬────────────────────┘
                             ▼
                           Grafana
                             │
                  ┌──────────┼──────────┐
                  ▼          ▼          ▼
               Metrics      Logs      Traces
```

---

# Components

| Component     | Purpose                                    |
| ------------- | ------------------------------------------ |
| Kubernetes    | Runs Roboshop microservices                |
| Prometheus    | Collects metrics                           |
| Grafana       | Visualization and dashboards               |
| Loki          | Stores application logs                    |
| Grafana Alloy | Collects and forwards logs/traces          |
| OpenTelemetry | Generates and propagates traces            |
| Grafana Tempo | Stores distributed traces                  |
| Helm          | Installs and manages monitoring components |
| Argo CD       | GitOps deployment                          |

---

# Roboshop Services

The monitoring stack is designed for the following services:

```text
frontend
catalogue
cart
user
payment
shipping
dispatch
mysql
mongodb
redis
rabbitmq
```

---

# Prerequisites

Install the following tools:

```bash
kubectl
helm
docker
git
```

Verify:

```bash
kubectl version --client
helm version
docker version
```

Make sure Docker Desktop Kubernetes is enabled.

Check the cluster:

```bash
kubectl get nodes
```

Expected:

```text
NAME              STATUS   ROLES           AGE
docker-desktop    Ready    control-plane   ...
```

---

# Create Monitoring Namespace

```bash
kubectl create namespace monitoring
```

Verify:

```bash
kubectl get ns
```

---

# Add Helm Repositories

## Grafana

```bash
helm repo add grafana https://grafana.github.io/helm-charts
```

## Prometheus Community

```bash
helm repo add prometheus-community \
https://prometheus-community.github.io/helm-charts
```

Update repositories:

```bash
helm repo update
```

Verify:

```bash
helm repo list
```

---

# Prometheus Installation

Install kube-prometheus-stack:

```bash
helm upgrade --install prometheus \
prometheus-community/kube-prometheus-stack \
-n monitoring
```

Check pods:

```bash
kubectl get pods -n monitoring
```

Check services:

```bash
kubectl get svc -n monitoring
```

---

# Grafana

Grafana is installed as part of kube-prometheus-stack.

Check:

```bash
kubectl get pods -n monitoring | grep grafana
```

Access Grafana using port forwarding:

```bash
kubectl port-forward \
svc/prometheus-grafana \
-n monitoring \
3000:80
```

Open:

```text
http://localhost:3000
```

---

# Grafana NodePort

If Grafana is exposed through NodePort:

```bash
kubectl get svc -n monitoring
```

Example:

```text
prometheus-grafana   NodePort   10.x.x.x   <none>   80:30300/TCP
```

Access:

```text
http://localhost:30300
```

---

# Loki

Loki provides centralized log storage for Roboshop application logs.

Install Loki:

```bash
helm upgrade --install loki \
grafana/loki \
-n monitoring \
-f loki-values.yaml
```

Check:

```bash
kubectl get pods -n monitoring
```

Expected components may include:

```text
loki-0
loki-canary
loki-gateway
```

Verify Loki:

```bash
kubectl get svc -n monitoring | grep loki
```

---

# Loki API Test

Run a temporary curl pod:

```bash
kubectl run loki-test \
-n monitoring \
--rm -it \
--image=curlimages/curl \
--restart=Never \
-- \
curl -s \
http://loki-gateway.monitoring.svc.cluster.local/loki/api/v1/labels
```

Expected response:

```json
{
  "status": "success"
}
```

Available labels may include:

```text
app
container
instance
job
namespace
pod
project
service_name
stream
tier
```

---

# Grafana Alloy

Grafana Alloy collects Kubernetes container logs and forwards them to Loki.

Install:

```bash
helm upgrade --install alloy \
grafana/alloy \
-n monitoring \
-f alloy-values.yaml
```

Check:

```bash
kubectl get pods -n monitoring
```

Alloy should run on Kubernetes nodes as a DaemonSet.

```bash
kubectl get daemonset -n monitoring
```

---

# Alloy Log Collection

Alloy discovers Kubernetes pods:

```text
Kubernetes Pods
      │
      ▼
discovery.kubernetes
      │
      ▼
discovery.relabel
      │
      ├── namespace
      ├── pod
      ├── container
      ├── app
      ├── project
      └── tier
      │
      ▼
loki.source.kubernetes
      │
      ▼
Loki
```

Example Roboshop labels:

```yaml
labels:
  app: payment
  project: roboshop
  tier: app
```

These labels make Grafana log queries much easier.

---

# Loki Log Queries

## All Roboshop logs

```logql
{namespace="roboshop"}
```

## Payment logs

```logql
{namespace="roboshop", app="payment"}
```

## Cart logs

```logql
{namespace="roboshop", app="cart"}
```

## Catalogue logs

```logql
{namespace="roboshop", app="catalogue"}
```

## Frontend logs

```logql
{namespace="roboshop", app="frontend"}
```

## Shipping logs

```logql
{namespace="roboshop", app="shipping"}
```

## Dispatch logs

```logql
{namespace="roboshop", app="dispatch"}
```

---

# Error Logs

Search application errors:

```logql
{namespace="roboshop"} |= "error"
```

Case-insensitive regex:

```logql
{namespace="roboshop"} |~ "(?i)error|exception|failed"
```

Warnings:

```logql
{namespace="roboshop"} |~ "(?i)warn|warning"
```

HTTP 500:

```logql
{namespace="roboshop"} |= "500"
```

---

# Kubernetes Monitoring

Check all Roboshop pods:

```bash
kubectl get pods -n roboshop
```

Check services:

```bash
kubectl get svc -n roboshop
```

Check deployments:

```bash
kubectl get deployments -n roboshop
```

Check StatefulSets:

```bash
kubectl get statefulsets -n roboshop
```

Check resource usage:

```bash
kubectl top pods -n roboshop
```

```bash
kubectl top nodes
```

---

# Application Traceability

Application traceability allows a single request to be followed across multiple Roboshop microservices.

Example:

```text
User
 │
 ▼
Frontend
 │
 ▼
Cart
 │
 ▼
Catalogue
 │
 ▼
Payment
 │
 ▼
Shipping
 │
 ▼
Dispatch
```

A single request carries the same:

```text
Trace ID
```

across services.

Example:

```text
Trace ID:
4bf92f3577b34da6a3ce929d0e0e4736
```

---

# OpenTelemetry

OpenTelemetry is used to instrument Roboshop applications.

The architecture is:

```text
Roboshop Application
        │
        ▼
OpenTelemetry SDK
        │
        ▼
OTLP
        │
        ▼
Grafana Alloy
        │
        ▼
Grafana Tempo
```

Each request generates spans.

Example:

```text
Trace: 4bf92f3577b34da6a3ce929d0e0e4736

Frontend       35 ms
   │
   └── Cart     82 ms
        │
        └── Catalogue     120 ms
             │
             └── Payment     850 ms
                  │
                  └── Shipping     310 ms
                       │
                       └── Dispatch     150 ms
```

This makes it possible to identify the slow or failing service.

---

# Tempo

Grafana Tempo stores distributed traces.

Architecture:

```text
Application
     │
     ▼
OpenTelemetry
     │
     ▼
Alloy
     │
     ▼
Tempo
     │
     ▼
Grafana
```

Check Tempo:

```bash
kubectl get pods -n monitoring
```

Check services:

```bash
kubectl get svc -n monitoring | grep tempo
```

---

# Logs + Traces Correlation

One of the main objectives of this project is to connect:

```text
Trace
  │
  └── Trace ID
          │
          ▼
       Loki Log
```

Example:

```text
Trace ID: abc123
       │
       ├── frontend
       ├── cart
       ├── payment
       ├── shipping
       └── dispatch
                  │
                  ▼
              Loki Logs
```

This allows an engineer to move from a trace span directly to the related application logs.

---

# Metrics + Logs + Traces

The final observability model is:

```text
             Observability
                  │
       ┌──────────┼──────────┐
       │          │          │
       ▼          ▼          ▼
    Metrics      Logs      Traces
       │          │          │
       ▼          ▼          ▼
 Prometheus     Loki       Tempo
       │          │          │
       └──────────┼──────────┘
                  ▼
                Grafana
```

This provides:

### Metrics

Answer:

```text
Is the application healthy?
```

### Logs

Answer:

```text
What happened?
```

### Traces

Answer:

```text
Where did the request fail or become slow?
```

---

# Useful Grafana Dashboards

Recommended dashboards:

```text
Roboshop Kubernetes Overview
Roboshop Application Logs
Roboshop Application Errors
Roboshop Service Health
Roboshop Application Traces
Roboshop API Latency
Roboshop Pod Resources
Roboshop Node Resources
```

---

# Useful Prometheus Queries

## CPU Usage

```promql
sum(rate(container_cpu_usage_seconds_total{
  namespace="roboshop"
}[5m])) by (pod)
```

## Memory Usage

```promql
sum(container_memory_working_set_bytes{
  namespace="roboshop"
}) by (pod)
```

## Pod Count

```promql
count(kube_pod_info{
  namespace="roboshop"
})
```

## Running Pods

```promql
count(kube_pod_status_phase{
  namespace="roboshop",
  phase="Running"
})
```

---

# Troubleshooting

## Check monitoring pods

```bash
kubectl get pods -n monitoring
```

## Check Alloy logs

```bash
kubectl logs \
-n monitoring \
-l app.kubernetes.io/name=alloy \
--tail=100
```

## Check Loki logs

```bash
kubectl logs \
-n monitoring \
-l app.kubernetes.io/name=loki \
--tail=100
```

## Check Grafana logs

```bash
kubectl logs \
-n monitoring \
-l app.kubernetes.io/name=grafana \
--tail=100
```

## Describe failed pod

```bash
kubectl describe pod <pod-name> -n monitoring
```

## Check events

```bash
kubectl get events \
-n monitoring \
--sort-by=.lastTimestamp
```

---

# Verify End-to-End Logging

Generate traffic to Roboshop:

```bash
kubectl get svc -n roboshop
```

Then check:

```bash
kubectl logs \
-n roboshop \
deployment/payment \
--tail=50
```

Verify the same logs are available in Loki:

```logql
{namespace="roboshop", app="payment"}
```

---

# Verify Traceability

After OpenTelemetry instrumentation:

```text
1. Generate an application request
2. Find the request in Grafana
3. Open the trace
4. Identify the trace ID
5. Inspect individual service spans
6. Open the related Loki logs
7. Analyze the complete request path
```

Expected:

```text
Request
   ↓
Trace ID
   ↓
Frontend
   ↓
Cart
   ↓
Catalogue
   ↓
Payment
   ↓
Shipping
   ↓
Dispatch
   ↓
Related Loki logs
```

---

# GitOps Structure

Recommended repository structure:

```text
monitoring/
│
├── README.md
│
├── prometheus/
│   └── values.yaml
│
├── grafana/
│   ├── dashboards/
│   └── datasources/
│
├── loki/
│   └── loki-values.yaml
│
├── alloy/
│   └── alloy-values.yaml
│
├── tempo/
│   └── tempo-values.yaml
│
├── opentelemetry/
│   └── otel-config.yaml
│
└── k8s/
    ├── namespace.yaml
    └── ingress.yaml
```

---

# Technology Stack

```text
AWS / Azure
   │
   ▼
Kubernetes
   │
   ├── Roboshop Microservices
   │
   └── Monitoring
          │
          ├── Prometheus
          ├── Grafana
          ├── Loki
          ├── Alloy
          ├── OpenTelemetry
          └── Tempo
```

---

# Benefits

This project provides:

* Centralized application logging
* Kubernetes monitoring
* Application metrics
* Distributed tracing
* Request traceability
* Error investigation
* Performance analysis
* Service dependency visibility
* Logs and traces correlation
* Grafana dashboards
* GitOps-ready monitoring configuration

---

# Observability Goals

```text
                    ROBOSHOP
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
      Metrics         Logs          Traces
        │              │              │
   Prometheus         Loki           Tempo
        │              │              │
        └──────────────┼──────────────┘
                       │
                       ▼
                    Grafana
                       │
                       ▼
              Full Observability
```

The goal is to provide complete visibility into **infrastructure, Kubernetes workloads, application logs, application metrics, and distributed requests**.

---

## Author

**Venkata Ram Vanimina**

### Roboshop DevOps & Cloud Native Monitoring Project

Technologies:

- Kubernetes
- Docker
- Helm
- Prometheus
- Grafana
- Loki
- Grafana Alloy
- OpenTelemetry
- Grafana Tempo
- Argo CD
- GitHub
