```
venka@Think-VVRAM MINGW64 ~
$ kubectl exec -n roboshop mongodb-9f4d77799-9z9fp -- \
  mongosh --quiet --eval "show dbs"
admin       40.00 KiB
catalogue   80.00 KiB
config      92.00 KiB
local       72.00 KiB
users      164.00 KiB

venka@Think-VVRAM MINGW64 ~
$ kubectl exec -n roboshop mongodb-9f4d77799-9z9fp -- \
  mongosh --quiet users --eval "show collections"
orders
users

venka@Think-VVRAM MINGW64 ~
$ kubectl exec -n roboshop mongodb-9f4d77799-9z9fp -- \
  mongosh --quiet users --eval "db.getCollectionNames().forEach(c => print(c + ': ' + db[c].countDocuments()))"
users: 4
orders: 1

venka@Think-VVRAM MINGW64 ~
$ kubectl exec -n roboshop mongodb-9f4d77799-9z9fp -- \
  sh -c 'ls -lah /data/db'
total 680K
drwxr-xr-x 5 mongodb mongodb 4.0K Sep 11 05:02 .
drwxr-xr-x 4 root    root    4.0K Aug 18 01:19 ..
drwx------ 3 mongodb mongodb 4.0K Sep 11 04:13 .mongodb
-rw------- 1 mongodb mongodb   50 Sep 11 04:12 WiredTiger
-rw------- 1 mongodb mongodb   21 Sep 11 04:12 WiredTiger.lock
-rw------- 1 mongodb mongodb 1.5K Sep 11 05:02 WiredTiger.turtle
-rw------- 1 mongodb mongodb 100K Sep 11 05:02 WiredTiger.wt
-rw------- 1 mongodb mongodb 4.0K Sep 11 04:13 WiredTigerHS.wt
-rw------- 1 mongodb mongodb  36K Sep 11 04:33 _mdb_catalog.wt
-rw------- 1 mongodb mongodb  20K Sep 11 04:13 collection-0--1390267075650654356.wt
-rw------- 1 mongodb mongodb  36K Sep 11 04:34 collection-0-4315634600610952832.wt
-rw------- 1 mongodb mongodb  36K Sep 11 04:33 collection-14--1390267075650654356.wt
-rw------- 1 mongodb mongodb  36K Sep 11 04:14 collection-2--1390267075650654356.wt
-rw------- 1 mongodb mongodb  36K Sep 11 04:58 collection-4--1390267075650654356.wt
-rw------- 1 mongodb mongodb  20K Sep 11 04:25 collection-7--1390267075650654356.wt
drwx------ 2 mongodb mongodb 4.0K Sep 11 05:03 diagnostic.data
-rw------- 1 mongodb mongodb  20K Sep 11 04:13 index-1--1390267075650654356.wt
-rw------- 1 mongodb mongodb  20K Sep 11 04:33 index-1-4315634600610952832.wt
-rw------- 1 mongodb mongodb  20K Sep 11 04:32 index-11--1390267075650654356.wt
-rw------- 1 mongodb mongodb  36K Sep 11 04:33 index-15--1390267075650654356.wt
-rw------- 1 mongodb mongodb  36K Sep 11 04:33 index-16--1390267075650654356.wt
-rw------- 1 mongodb mongodb  36K Sep 11 04:14 index-3--1390267075650654356.wt
-rw------- 1 mongodb mongodb  36K Sep 11 04:58 index-5--1390267075650654356.wt
-rw------- 1 mongodb mongodb  36K Sep 11 04:58 index-6--1390267075650654356.wt
-rw------- 1 mongodb mongodb  20K Sep 11 04:13 index-8--1390267075650654356.wt
-rw------- 1 mongodb mongodb  20K Sep 11 04:13 index-9--1390267075650654356.wt
drwx------ 2 mongodb mongodb 4.0K Sep 11 04:13 journal
-rw------- 1 mongodb mongodb    2 Sep 11 04:13 mongod.lock
-rw------- 1 mongodb mongodb  36K Sep 11 04:58 sizeStorer.wt
-rw------- 1 mongodb mongodb  114 Sep 11 04:12 storage.bson

venka@Think-VVRAM MINGW64 ~
$ kubectl get pod mongodb-9f4d77799-9z9fp -n roboshop \
  -o jsonpath='{range .spec.containers[*].volumeMounts[*]}{.name}{" -> "}{.mountPath}{"\n"}{end}'
kube-api-access-mgbwq -> /var/run/secrets/kubernetes.io/serviceaccount

venka@Think-VVRAM MINGW64 ~
$ kubectl get pod mongodb-9f4d77799-9z9fp -n roboshop \
  -o jsonpath='{range .spec.volumes[*]}{.name}{" -> "}{.persistentVolumeClaim.claimName}{"\n"}{end}'
kube-api-access-mgbwq ->

venka@Think-VVRAM MINGW64 ~
$ helm install opentelemetry-collector \
  open-telemetry/opentelemetry-collector \
  -n opentelemetry
Error: INSTALLATION FAILED: execution error at (opentelemetry-collector/templates/NOTES.txt:2:3): [ERROR] 'image.repository' must be set. See https://github.com/open-telemetry/opentelemetry-helm-charts/blob/main/charts/opentelemetry-collector/UPGRADING.md for instructions.

venka@Think-VVRAM MINGW64 ~
$ helm repo add open-telemetry https://open-telemetry.github.io/opentelemetry-helm-charts
helm repo update
"open-telemetry" already exists with the same configuration, skipping
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "botkube" chart repository
...Successfully got an update from the "ollama" chart repository
...Successfully got an update from the "kiali" chart repository
...Successfully got an update from the "k8sgpt-operator" chart repository
...Successfully got an update from the "k8sgpt" chart repository
...Successfully got an update from the "istio" chart repository
...Unable to get an update from the "gitlab" chart repository (https://charts.gitlab.io):
        read tcp [2409:40f0:442f:6648:4069:9ee8:94fd:22e5]:53378->[2600:1901:0:7b8a::]:443: wsarecv: An existing connection was forcibly closed by the remote host.
...Successfully got an update from the "argo" chart repository
...Successfully got an update from the "open-telemetry" chart repository
...Successfully got an update from the "open-webui" chart repository
...Unable to get an update from the "prometheus-community" chart repository (https://prometheus-community.github.io/helm-charts):
        context deadline exceeded (Client.Timeout or context cancellation while reading body)
...Unable to get an update from the "grafana" chart repository (https://grafana.github.io/helm-charts):
        context deadline exceeded (Client.Timeout or context cancellation while reading body)
Update Complete. ⎈Happy Helming!⎈

venka@Think-VVRAM MINGW64 ~
$ kubectl create namespace opentelemetry
namespace/opentelemetry created

venka@Think-VVRAM MINGW64 ~
$ helm install opentelemetry-collector \
  open-telemetry/opentelemetry-collector \
  -n opentelemetry
Error: INSTALLATION FAILED: execution error at (opentelemetry-collector/templates/NOTES.txt:2:3): [ERROR] 'image.repository' must be set. See https://github.com/open-telemetry/opentelemetry-helm-charts/blob/main/charts/opentelemetry-collector/UPGRADING.md for instructions.

venka@Think-VVRAM MINGW64 ~
$ kubectl get pods -n opentelemetry
kubectl get svc -n opentelemetry
No resources found in opentelemetry namespace.
No resources found in opentelemetry namespace.

venka@Think-VVRAM MINGW64 ~
$ helm install opentelemetry-collector \
  open-telemetry/opentelemetry-collector \
  -n opentelemetry \
  --set mode=deployment \
  --set image.repository=ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-k8s \
  --set command.name=otelcol-k8s
NAME: opentelemetry-collector
LAST DEPLOYED: Fri Sep 11 11:06:39 2026
NAMESPACE: opentelemetry
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
[WARNING] No resource limits or requests were set. Consider setting resource requests and limits for your collector(s) via the `resources` field.

[WARNING] "useGOMEMLIMIT" is enabled but memory limits have not been supplied so the GOMEMLIMIT env var could not be added. Solve this problem by setting resources.limits.memory or disabling useGOMEMLIMIT

venka@Think-VVRAM MINGW64 ~
$ kubectl get pods -n opentelemetry
NAME                                       READY   STATUS              RESTARTS   AGE
opentelemetry-collector-5576df4994-6m44s   0/1     ContainerCreating   0          59s

venka@Think-VVRAM MINGW64 ~
$ kubectl get pods -n opentelemetry
NAME                                       READY   STATUS              RESTARTS   AGE
opentelemetry-collector-5576df4994-6m44s   0/1     ContainerCreating   0          63s

venka@Think-VVRAM MINGW64 ~
$ kubectl get pods -n opentelemetry
NAME                                       READY   STATUS              RESTARTS   AGE
opentelemetry-collector-5576df4994-6m44s   0/1     ContainerCreating   0          65s

venka@Think-VVRAM MINGW64 ~
$ kubectl get svc -n opentelemetry
NAME                      TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)                                                   AGE
opentelemetry-collector   ClusterIP   10.96.112.155   <none>        6831/UDP,14250/TCP,14268/TCP,4317/TCP,4318/TCP,9411/TCP   74s

venka@Think-VVRAM MINGW64 ~
$ kubectl get pods -n opentelemetry
NAME                                       READY   STATUS              RESTARTS   AGE
opentelemetry-collector-5576df4994-6m44s   0/1     ContainerCreating   0          83s

venka@Think-VVRAM MINGW64 ~
$ kubectl get pods -n opentelemetry
NAME                                       READY   STATUS              RESTARTS   AGE
opentelemetry-collector-5576df4994-6m44s   0/1     ContainerCreating   0          3m49s

venka@Think-VVRAM MINGW64 ~
$ kubectl get pods -n opentelemetry
NAME                                       READY   STATUS              RESTARTS   AGE
opentelemetry-collector-5576df4994-6m44s   0/1     ContainerCreating   0          3m52s

venka@Think-VVRAM MINGW64 ~
$ kubectl get pods -n opentelemetry
NAME                                       READY   STATUS              RESTARTS   AGE
opentelemetry-collector-5576df4994-6m44s   0/1     ContainerCreating   0          3m55s

venka@Think-VVRAM MINGW64 ~
$ kubectl logs opentelemetry-collector-5576df4994-6m44s -n opentelemetry
Error from server (BadRequest): container "opentelemetry-collector" in pod "opentelemetry-collector-5576df4994-6m44s" is waiting to start: ContainerCreating

venka@Think-VVRAM MINGW64 ~
$ kubectl describe pod opentelemetry-collector-5576df4994-6m44s -n opentelemetry
Name:             opentelemetry-collector-5576df4994-6m44s
Namespace:        opentelemetry
Priority:         0
Service Account:  opentelemetry-collector
Node:             desktop-worker/172.18.0.4
Start Time:       Fri, 11 Sep 2026 11:06:41 +0530
Labels:           app.kubernetes.io/instance=opentelemetry-collector
                  app.kubernetes.io/name=opentelemetry-collector
                  component=standalone-collector
                  pod-template-hash=5576df4994
Annotations:      checksum/config: 0b9ee0ec98ee41e21334c8764ce4f6d45e086e0a217e2594d07fe24515af0c6e
Status:           Pending
IP:
IPs:              <none>
Controlled By:    ReplicaSet/opentelemetry-collector-5576df4994
Containers:
  opentelemetry-collector:
    Container ID:
    Image:         ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-k8s:0.160.0
    Image ID:
    Ports:         6831/UDP (jaeger-compact), 14250/TCP (jaeger-grpc), 14268/TCP (jaeger-thrift), 4317/TCP (otlp), 4318/TCP (otlp-http), 9411/TCP (zipkin)
    Host Ports:    0/UDP (jaeger-compact), 0/TCP (jaeger-grpc), 0/TCP (jaeger-thrift), 0/TCP (otlp), 0/TCP (otlp-http), 0/TCP (zipkin)
    Command:
      /otelcol-k8s
    Args:
      --config=/conf/relay.yaml
    State:          Waiting
      Reason:       ContainerCreating
    Ready:          False
    Restart Count:  0
    Liveness:       http-get http://:13133/ delay=0s timeout=1s period=10s #success=1 #failure=3
    Readiness:      http-get http://:13133/ delay=0s timeout=1s period=10s #success=1 #failure=3
    Environment:
      MY_POD_IP:            (v1:status.podIP)
      OTEL_K8S_NODE_NAME:   (v1:spec.nodeName)
      OTEL_K8S_NODE_IP:     (v1:status.hostIP)
      OTEL_K8S_NAMESPACE:  opentelemetry (v1:metadata.namespace)
      OTEL_K8S_POD_NAME:   opentelemetry-collector-5576df4994-6m44s (v1:metadata.name)
      OTEL_K8S_POD_IP:      (v1:status.podIP)
    Mounts:
      /conf from opentelemetry-collector-configmap (rw)
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-fzjgc (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   False
  Initialized                 True
  Ready                       False
  ContainersReady             False
  PodScheduled                True
Volumes:
  opentelemetry-collector-configmap:
    Type:      ConfigMap (a volume populated by a ConfigMap)
    Name:      opentelemetry-collector
    Optional:  false
  kube-api-access-fzjgc:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    Optional:                false
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age   From               Message
  ----    ------     ----  ----               -------
  Normal  Scheduled  5m6s  default-scheduler  Successfully assigned opentelemetry/opentelemetry-collector-5576df4994-6m44s to desktop-worker
  Normal  Pulling    5m4s  kubelet            spec.containers{opentelemetry-collector}: Pulling image "ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-k8s:0.160.0"

venka@Think-VVRAM MINGW64 ~
$ docker pull ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-k8s:0.160.0
0.160.0: Pulling from open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-k8s
6e602d714375: Pull complete
0eec36b67603: Pull complete
Digest: sha256:76d7a04f2291da1d8b7ce259468d09f0f9f44f71f67a5737539f64ca82b5bdb1
Status: Downloaded newer image for ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-k8s:0.160.0
ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-k8s:0.160.0

What's next:
    View a summary of image vulnerabilities and recommendations → docker scout quickview ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-k8s:0.160.0

venka@Think-VVRAM MINGW64 ~
$

venka@Think-VVRAM MINGW64 ~
$

venka@Think-VVRAM MINGW64 ~
$

venka@Think-VVRAM MINGW64 ~
$

venka@Think-VVRAM MINGW64 ~
$

venka@Think-VVRAM MINGW64 ~
$

venka@Think-VVRAM MINGW64 ~
$

venka@Think-VVRAM MINGW64 ~
$

venka@Think-VVRAM MINGW64 ~
$

venka@Think-VVRAM MINGW64 ~
$

venka@Think-VVRAM MINGW64 ~
$

venka@Think-VVRAM MINGW64 ~
$

venka@Think-VVRAM MINGW64 ~
$

venka@Think-VVRAM MINGW64 ~
$ kubectl get pods -n opentelemetry
NAME                                       READY   STATUS    RESTARTS   AGE
opentelemetry-collector-5576df4994-6m44s   1/1     Running   0          29m

venka@Think-VVRAM MINGW64 ~
$ kubectl get svc -n opentelemetry
NAME                      TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)                                                   AGE
opentelemetry-collector   ClusterIP   10.96.112.155   <none>        6831/UDP,14250/TCP,14268/TCP,4317/TCP,4318/TCP,9411/TCP   30m

venka@Think-VVRAM MINGW64 ~
$ helm status opentelemetry-collector -n opentelemetry
NAME: opentelemetry-collector
LAST DEPLOYED: Fri Sep 11 11:06:39 2026
NAMESPACE: opentelemetry
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
[WARNING] No resource limits or requests were set. Consider setting resource requests and limits for your collector(s) via the `resources` field.

[WARNING] "useGOMEMLIMIT" is enabled but memory limits have not been supplied so the GOMEMLIMIT env var could not be added. Solve this problem by setting resources.limits.memory or disabling useGOMEMLIMIT

venka@Think-VVRAM MINGW64 ~
$ helm repo add open-telemetry https://open-telemetry.github.io/opentelemetry-helm-charts
helm repo update
"open-telemetry" already exists with the same configuration, skipping
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "k8sgpt" chart repository
...Successfully got an update from the "k8sgpt-operator" chart repository
...Successfully got an update from the "botkube" chart repository
...Successfully got an update from the "kiali" chart repository
...Unable to get an update from the "gitlab" chart repository (https://charts.gitlab.io):
        read tcp [2409:40f0:442f:6648:4069:9ee8:94fd:22e5]:52918->[2600:1901:0:7b8a::]:443: wsarecv: An existing connection was forcibly closed by the remote host.
...Successfully got an update from the "ollama" chart repository
...Successfully got an update from the "istio" chart repository
...Successfully got an update from the "open-webui" chart repository
...Successfully got an update from the "open-telemetry" chart repository
...Successfully got an update from the "argo" chart repository
...Unable to get an update from the "grafana" chart repository (https://grafana.github.io/helm-charts):
        context deadline exceeded (Client.Timeout or context cancellation while reading body)
...Unable to get an update from the "prometheus-community" chart repository (https://prometheus-community.github.io/helm-charts):
        context deadline exceeded (Client.Timeout or context cancellation while reading body)
Update Complete. ⎈Happy Helming!⎈

venka@Think-VVRAM MINGW64 ~
$      helm install opentelemetry-operator \
  open-telemetry/opentelemetry-operator \
  -n opentelemetry \
  --create-namespace
Error: INSTALLATION FAILED: unable to build kubernetes objects from release manifest: [resource mapping not found for name: "opentelemetry-operator-serving-cert" namespace: "opentelemetry" from "": no matches for kind "Certificate" in version "cert-manager.io/v1"
ensure CRDs are installed first, resource mapping not found for name: "opentelemetry-operator-selfsigned-issuer" namespace: "opentelemetry" from "": no matches for kind "Issuer" in version "cert-manager.io/v1"
ensure CRDs are installed first]

venka@Think-VVRAM MINGW64 ~
$  kubectl get ns
NAME                 STATUS   AGE
argocd               Active   7d16h
default              Active   7d17h
elastic-system       Active   4d12h
kube-node-lease      Active   7d17h
kube-public          Active   7d17h
kube-system          Active   7d17h
local-path-storage   Active   7d17h
monitoring           Active   4d
opentelemetry        Active   43m
otel-demo            Active   11h
roboshop             Active   7d16h

venka@Think-VVRAM MINGW64 ~
$ helm repo add jetstack https://charts.jetstack.io
helm repo update
"jetstack" has been added to your repositories
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "k8sgpt-operator" chart repository
...Successfully got an update from the "k8sgpt" chart repository
...Successfully got an update from the "botkube" chart repository
...Successfully got an update from the "ollama" chart repository
...Successfully got an update from the "kiali" chart repository
...Successfully got an update from the "jetstack" chart repository
...Successfully got an update from the "istio" chart repository
...Unable to get an update from the "gitlab" chart repository (https://charts.gitlab.io):
        read tcp [2409:40f0:442f:6648:4069:9ee8:94fd:22e5]:55782->[2600:1901:0:7b8a::]:443: wsarecv: An existing connection was forcibly closed by the remote host.
...Successfully got an update from the "open-webui" chart repository
...Successfully got an update from the "open-telemetry" chart repository
...Successfully got an update from the "argo" chart repository
...Successfully got an update from the "grafana" chart repository
...Successfully got an update from the "prometheus-community" chart repository
Update Complete. ⎈Happy Helming!⎈

venka@Think-VVRAM MINGW64 ~
$ helm install cert-manager jetstack/cert-manager \
  --namespace cert-manager \
  --create-namespace \
  --set crds.enabled=true
NAME: cert-manager
LAST DEPLOYED: Fri Sep 11 11:54:05 2026
NAMESPACE: cert-manager
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
cert-manager v1.21.1 has been deployed successfully!

In order to begin issuing certificates, you will need to set up a ClusterIssuer
or Issuer resource (for example, by creating a 'letsencrypt-staging' issuer).

More information on the different types of issuers and how to configure them
can be found in our documentation:

https://cert-manager.io/docs/configuration/

For information on how to configure cert-manager to automatically provision
Certificates for Ingress resources, take a look at the `ingress-shim`
documentation:

https://cert-manager.io/docs/usage/ingress/

For information on how to configure cert-manager to automatically provision
Certificates for Gateway API resources, take a look at the `gateway resource`
documentation:

https://cert-manager.io/docs/usage/gateway/

venka@Think-VVRAM MINGW64 ~
$ kubectl get pods -n cert-manager
NAME                                       READY   STATUS    RESTARTS   AGE
cert-manager-cainjector-7996d59c89-qrkqh   1/1     Running   0          4m19s
cert-manager-d55696cd6-mn8qg               1/1     Running   0          4m19s
cert-manager-webhook-6565cc777d-7gdld      1/1     Running   0          4m19s

venka@Think-VVRAM MINGW64 ~
$ kubectl get crd | grep cert-manager
certificaterequests.cert-manager.io         2026-09-11T06:24:07Z
certificates.cert-manager.io                2026-09-11T06:24:07Z
challenges.acme.cert-manager.io             2026-09-11T06:24:07Z
clusterissuers.cert-manager.io              2026-09-11T06:24:07Z
issuers.cert-manager.io                     2026-09-11T06:24:07Z
orders.acme.cert-manager.io                 2026-09-11T06:24:07Z

venka@Think-VVRAM MINGW64 ~
$ helm install opentelemetry-operator \
  open-telemetry/opentelemetry-operator \
  -n opentelemetry \
  --create-namespace
NAME: opentelemetry-operator
LAST DEPLOYED: Fri Sep 11 12:04:22 2026
NAMESPACE: opentelemetry
STATUS: deployed
REVISION: 1
NOTES:
[WARNING] No resource limits or requests were set. Consider setter resource requests and limits via the `resources` field.


opentelemetry-operator has been installed. Check its status by running:
  kubectl --namespace opentelemetry get pods -l "app.kubernetes.io/instance=opentelemetry-operator"

Visit https://github.com/open-telemetry/opentelemetry-operator for instructions on how to create & configure OpenTelemetryCollector and Instrumentation custom resources by using the Operator.

venka@Think-VVRAM MINGW64 ~
$ kubectl get pods -n opentelemetry
NAME                                       READY   STATUS              RESTARTS   AGE
opentelemetry-collector-5576df4994-6m44s   1/1     Running             0          59m
opentelemetry-operator-75684646f7-ssfvs    0/1     ContainerCreating   0          83s

venka@Think-VVRAM MINGW64 ~
$ kubectl describe pod opentelemetry-operator-75684646f7-ssfvs  -n opentelemetry
Name:             opentelemetry-operator-75684646f7-ssfvs
Namespace:        opentelemetry
Priority:         0
Service Account:  opentelemetry-operator
Node:             desktop-worker2/172.18.0.2
Start Time:       Fri, 11 Sep 2026 12:04:24 +0530
Labels:           app.kubernetes.io/component=controller-manager
                  app.kubernetes.io/instance=opentelemetry-operator
                  app.kubernetes.io/managed-by=Helm
                  app.kubernetes.io/name=opentelemetry-operator
                  app.kubernetes.io/part-of=opentelemetry-operator
                  app.kubernetes.io/version=0.158.0
                  helm.sh/chart=opentelemetry-operator-0.122.0
                  pod-template-hash=75684646f7
Annotations:      kubectl.kubernetes.io/default-container: manager
Status:           Pending
IP:
IPs:              <none>
Controlled By:    ReplicaSet/opentelemetry-operator-75684646f7
Containers:
  manager:
    Container ID:
    Image:           ghcr.io/open-telemetry/opentelemetry-operator/opentelemetry-operator:0.158.0
    Image ID:
    Ports:           8443/TCP (metrics), 9443/TCP (webhook-server)
    Host Ports:      0/TCP (metrics), 0/TCP (webhook-server)
    SeccompProfile:  RuntimeDefault
    Command:
      /manager
    Args:
      --metrics-addr=0.0.0.0:8443
      --metrics-secure=true
      --enable-leader-election
      --health-probe-addr=:8081
      --webhook-port=9443
      --collector-image=ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-k8s:0.158.0
      --feature-gates=-operator.networkpolicy
    State:          Waiting
      Reason:       ContainerCreating
    Ready:          False
    Restart Count:  0
    Liveness:       http-get http://:8081/healthz delay=15s timeout=1s period=20s #success=1 #failure=3
    Readiness:      http-get http://:8081/readyz delay=5s timeout=1s period=10s #success=1 #failure=3
    Environment:
      NAMESPACE:             opentelemetry (v1:metadata.namespace)
      SERVICE_ACCOUNT_NAME:   (v1:spec.serviceAccountName)
      ENABLE_WEBHOOKS:       true
    Mounts:
      /tmp/k8s-webhook-server/serving-certs from cert (ro)
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-cz528 (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   False
  Initialized                 True
  Ready                       False
  ContainersReady             False
  PodScheduled                True
Volumes:
  cert:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  opentelemetry-operator-controller-manager-service-cert
    Optional:    false
  kube-api-access-cz528:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    Optional:                false
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              kubernetes.io/os=linux
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type     Reason       Age    From               Message
  ----     ------       ----   ----               -------
  Normal   Scheduled    2m24s  default-scheduler  Successfully assigned opentelemetry/opentelemetry-operator-75684646f7-ssfvs to desktop-worker2
  Warning  FailedMount  2m23s  kubelet            MountVolume.SetUp failed for volume "cert" : secret "opentelemetry-operator-controller-manager-service-cert" not found
  Normal   Pulling      2m22s  kubelet            spec.containers{manager}: Pulling image "ghcr.io/open-telemetry/opentelemetry-operator/opentelemetry-operator:0.158.0"

venka@Think-VVRAM MINGW64 ~
$ docker pull ghcr.io/open-telemetry/opentelemetry-operator/opentelemetry-operator:0.158.0
0.158.0: Pulling from open-telemetry/opentelemetry-operator/opentelemetry-operator
759fca3e6557: Pull complete
370283a5e421: Pull complete
44136fa355b3: Already exists
5a1ba0df342a: Download complete
Digest: sha256:d4789a6537fdbc69929dc9227900511224b2fe8e5a0938e604cc8ca56b07336e
Status: Downloaded newer image for ghcr.io/open-telemetry/opentelemetry-operator/opentelemetry-operator:0.158.0
ghcr.io/open-telemetry/opentelemetry-operator/opentelemetry-operator:0.158.0

What's next:
    View a summary of image vulnerabilities and recommendations → docker scout quickview ghcr.io/open-telemetry/opentelemetry-operator/opentelemetry-operator:0.158.0

venka@Think-VVRAM MINGW64 ~
$ kubectl get pods -n opentelemetry
NAME                                       READY   STATUS    RESTARTS   AGE
opentelemetry-collector-5576df4994-6m44s   1/1     Running   0          145m
opentelemetry-operator-75684646f7-ssfvs    1/1     Running   0          87m

venka@Think-VVRAM MINGW64 ~
$ kubectl get crd | grep opentelemetry
instrumentations.opentelemetry.io           2026-09-11T06:34:23Z
opampbridges.opentelemetry.io               2026-09-11T06:34:23Z
opentelemetrycollectors.opentelemetry.io    2026-09-11T06:34:23Z
targetallocators.opentelemetry.io           2026-09-11T06:34:23Z

venka@Think-VVRAM MINGW64 ~
$ cd /c/azure/roboshop/

venka@Think-VVRAM MINGW64 /c/azure/roboshop
$ ls
CD/  CI/  monitoring/

venka@Think-VVRAM MINGW64 /c/azure/roboshop
$ cd monitoring/

venka@Think-VVRAM MINGW64 /c/azure/roboshop/monitoring
$ ls
alloy-values.yaml  elasticsearch.yaml  grafana-values.yaml  kibana.yaml  loki-values.yaml  observability/  otel-values.yaml

venka@Think-VVRAM MINGW64 /c/azure/roboshop/monitoring
$ cd observability/

venka@Think-VVRAM MINGW64 /c/azure/roboshop/monitoring/observability (main)
$ ls
README.md  opentelemetery-instrumentation.yaml  roboshop-grafana-dashboards/  roboshop-monitoring.md

venka@Think-VVRAM MINGW64 /c/azure/roboshop/monitoring/observability (main)
$ kubectl apply -f  opentelemetery-instrumentation.yaml
instrumentation.opentelemetry.io/roboshop-auto created

venka@Think-VVRAM MINGW64 /c/azure/roboshop/monitoring/observability (main)
$ kubectl get instrumentation -n roboshop
NAME            AGE   ENDPOINT                                                              SAMPLER                    SAMPLER ARG
roboshop-auto   16s   http://opentelemetry-collector.opentelemetry.svc.cluster.local:4318   parentbased_traceidratio   1

venka@Think-VVRAM MINGW64 /c/azure/roboshop/monitoring/observability (main)
$ kubectl apply -f  opentelemetery-instrumentation.yaml
instrumentation.opentelemetry.io/roboshop-auto configured

venka@Think-VVRAM MINGW64 /c/azure/roboshop/monitoring/observability (main)
$ ls
README.md  opentelemetery-instrumentation.yaml  otel-values-1.yaml  roboshop-grafana-dashboards/  roboshop-monitoring.md

venka@Think-VVRAM MINGW64 /c/azure/roboshop/monitoring/observability (main)
$ helm upgrade opentelemetry-collector \
  open-telemetry/opentelemetry-collector \
  -n opentelemetry \
  -f otel-values-1.yaml
Release "opentelemetry-collector" has been upgraded. Happy Helming!
NAME: opentelemetry-collector
LAST DEPLOYED: Fri Sep 11 15:00:23 2026
NAMESPACE: opentelemetry
STATUS: deployed
REVISION: 2
TEST SUITE: None
NOTES:
[WARNING] No resource limits or requests were set. Consider setting resource requests and limits for your collector(s) via the `resources` field.

[WARNING] "useGOMEMLIMIT" is enabled but memory limits have not been supplied so the GOMEMLIMIT env var could not be added. Solve this problem by setting resources.limits.memory or disabling useGOMEMLIMIT

[DEPRECATION] Exporter 'otlp' has been renamed to 'otlp_grpc'. Your config has been automatically rewritten for this release. Please update your values.yaml — auto-rewrite will be removed in a future release. See UPGRADING.md.
[DEPRECATION] Pipeline 'traces' references renamed exporter 'otlp'. It has been automatically rewritten to 'otlp_grpc' for this release. Please update your values.yaml — auto-rewrite will be removed in a future release. See UPGRADING.md.

venka@Think-VVRAM MINGW64 /c/azure/roboshop/monitoring/observability (main)
$ kubectl rollout status deployment/opentelemetry-collector -n opentelemetry
deployment "opentelemetry-collector" successfully rolled out

venka@Think-VVRAM MINGW64 /c/azure/roboshop/monitoring/observability (main)
$ kubectl run test-curl \
  --rm -it \
  --image=curlimages/curl \
  -n roboshop \
  -- sh
All commands and output from this session will be recorded in container logs, including credentials and sensitive information passed through the command prompt.
If you don't see a command prompt, try pressing enter.
~ $ for i in $(seq 1 20); do
>   curl -s http://user:8080/health
>   echo
> done
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
{"app":"OK","mongo":true}
~ $ exit
Session ended, resume using 'kubectl attach test-curl -c test-curl -n roboshop -i -t' command
pod "test-curl" deleted from roboshop namespace

venka@Think-VVRAM MINGW64 /c/azure/roboshop/monitoring/observability (main)
$ kubectl logs -n opentelemetry deployment/opentelemetry-collector --since=2m
2026-09-11T10:02:30.828Z        warn    otelconftelemetry/logger.go:143 Using legacy service.telemetry.resource inline map format; prefer service.telemetry.resource.attributes (array of maps with `name` and `value` keys)        {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "legacy_resource_attributes": ["host.name", "k8s.namespace.name", "k8s.node.ip", "k8s.node.name", "k8s.pod.ip", "k8s.pod.name"]}
2026-09-11T10:02:30.872Z        info    otelconftelemetry/tracer.go:47  Internal trace telemetry disabled       {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}}
2026-09-11T10:02:30.879Z        info    memorylimiter@v0.160.0/memorylimiter.go:185     Using percentage memory limiter {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.kind": "processor", "total_memory_mib": 7779, "limit_percentage": 80, "spike_limit_percentage": 25}
2026-09-11T10:02:30.880Z        info    memorylimiter@v0.160.0/memorylimiter.go:109     Memory limiter configured       {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.kind": "processor", "limit_mib": 6223, "spike_limit_mib": 1944, "check_interval": 5}
2026-09-11T10:02:30.886Z        info    service@v0.160.0/service.go:261 Starting otelcol-k8s... {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "Version": "0.160.0", "NumCPU": 12}
2026-09-11T10:02:30.886Z        info    extensions/extensions.go:44     Starting extensions...  {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}}
2026-09-11T10:02:30.887Z        info    extensions/extensions.go:48     Extension is starting...        {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "health_check", "otelcol.component.kind": "extension"}
2026-09-11T10:02:30.888Z        info    healthcheckextension@v0.160.0/healthcheckextension.go:32        Starting health_check extension {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "health_check", "otelcol.component.kind": "extension", "config": {"Config":{"ServerConfig":{"NetAddr":{"Endpoint":"10.244.1.39:13133","Transport":"tcp","DialerConfig":{"Timeout":0}},"TLS":{},"CORS":{},"Auth":{},"MaxRequestBodySize":0,"IncludeMetadata":false,"ResponseHeaders":null,"CompressionAlgorithms":null,"ReadTimeout":0,"ReadHeaderTimeout":0,"WriteTimeout":0,"Middlewares":null,"Keepalive":{},"IdleTimeout":0,"KeepAlivesEnabled":false},"Path":"/","ResponseBody":null,"CheckCollectorPipeline":{"Enabled":false,"Interval":"5m","ExporterFailureThreshold":5},"UseV2":false,"GRPCConfig":null,"HTTPConfig":null,"ComponentHealthConfig":null}}}
2026-09-11T10:02:30.890Z        info    extensions/extensions.go:66     Extension started.      {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "health_check", "otelcol.component.kind": "extension"}
2026-09-11T10:02:30.894Z        info    otlpreceiver@v0.160.0/otlp.go:120       Starting GRPC server    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "otlp", "otelcol.component.kind": "receiver", "endpoint": "10.244.1.39:4317"}
2026-09-11T10:02:30.896Z        info    otlpreceiver@v0.160.0/otlp.go:175       Starting HTTP server    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "otlp", "otelcol.component.kind": "receiver", "endpoint": "10.244.1.39:4318"}
2026-09-11T10:02:30.896Z        info    healthcheck/handler.go:131      Health Check state change       {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "health_check", "otelcol.component.kind": "extension", "status": "ready"}
2026-09-11T10:02:30.896Z        info    service@v0.160.0/service.go:284 Everything is ready. Begin running and processing data. {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}}
2026-09-11T10:02:33.108Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 53}
2026-09-11T10:02:33.109Z        info    ResourceMetrics #0
Resource SchemaURL:
Resource attributes:
     -> k8s.container.name: Str(user)
     -> k8s.deployment.name: Str(user)
     -> k8s.namespace.name: Str(roboshop)
     -> k8s.node.name: Str(desktop-worker)
     -> k8s.pod.name: Str(user-74bcc7d99c-jw4sg)
     -> k8s.replicaset.name: Str(user-74bcc7d99c)
     -> service.instance.id: Str(roboshop.user-74bcc7d99c-jw4sg.user)
     -> service.namespace: Str(roboshop)
     -> service.version: Str(1.0.0)
     -> service.name: Str(user)
     -> process.pid: Int(1)
     -> process.executable.name: Str(node)
     -> process.executable.path: Str(/usr/local/bin/node)
     -> process.command_args: Slice(["/usr/local/bin/node","/opt/server/server.js"])
     -> process.runtime.version: Str(18.19.1)
     -> process.runtime.name: Str(nodejs)
     -> process.runtime.description: Str(Node.js)
     -> process.command: Str(/opt/server/server.js)
     -> process.owner: Str(roboshop)
     -> os.type: Str(linux)
     -> os.version: Str(6.6.87.2-microsoft-standard-WSL2)
     -> host.name: Str(user-74bcc7d99c-jw4sg)
     -> host.arch: Str(amd64)
     -> telemetry.sdk.language: Str(nodejs)
     -> telemetry.sdk.name: Str(opentelemetry)
     -> telemetry.sdk.version: Str(2.9.0)
ScopeMetrics #0
ScopeMetrics SchemaURL:
InstrumentationScope @opentelemetry/instrumentation-http 0.220.0
Metric #0
Descriptor:
     -> Name: http.server.duration
     -> Description: Measures the duration of inbound HTTP requests.
     -> Unit: ms
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> http.scheme: Str(http)
     -> http.method: Str(GET)
     -> net.host.name: Str(user)
     -> http.flavor: Str(1.1)
     -> http.status_code: Int(200)
     -> net.host.port: Int(8080)
     -> http.route: Str(/health)
StartTimestamp: 2026-09-11 09:32:21.804 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Count: 21
Sum: 217.332755
Min: 2.716886
Max: 41.640505
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 11
Buckets #2, Count: 4
Buckets #3, Count: 3
Buckets #4, Count: 3
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
Metric #1
Descriptor:
     -> Name: http.client.duration
     -> Description: Measures the duration of outbound HTTP requests.
     -> Unit: ms
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> http.method: Str(POST)
     -> net.peer.name: Str(opentelemetry-collector.opentelemetry.svc.cluster.local)
     -> net.peer.port: Int(4318)
     -> http.status_code: Int(200)
     -> http.flavor: Str(1.1)
StartTimestamp: 2026-09-11 09:17:35.209 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Count: 44
Sum: 783.588437
Min: 1.671517
Max: 128.512492
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 15
Buckets #2, Count: 12
Buckets #3, Count: 9
Buckets #4, Count: 4
Buckets #5, Count: 2
Buckets #6, Count: 1
Buckets #7, Count: 1
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
HistogramDataPoints #1
Data point attributes:
     -> http.method: Str(POST)
     -> net.peer.name: Str(opentelemetry-collector.opentelemetry.svc.cluster.local)
StartTimestamp: 2026-09-11 09:30:28.491 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Count: 1
Sum: 60.403901
Min: 60.403901
Max: 60.403901
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 1
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
ScopeMetrics #1
ScopeMetrics SchemaURL:
InstrumentationScope @opentelemetry/instrumentation-runtime-node 0.33.0
Metric #0
Descriptor:
     -> Name: nodejs.eventloop.utilization
     -> Description: Event loop utilization
     -> Unit: 1
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.005219
Metric #1
Descriptor:
     -> Name: nodejs.eventloop.time
     -> Description: Cumulative duration of time the event loop has been in each state.
     -> Unit: s
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> nodejs.eventloop.state: Str(active)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 14.331666
NumberDataPoints #1
Data point attributes:
     -> nodejs.eventloop.state: Str(idle)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 2443.089758
Metric #2
Descriptor:
     -> Name: nodejs.eventloop.delay.min
     -> Description: Event loop minimum delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.008126
Metric #3
Descriptor:
     -> Name: nodejs.eventloop.delay.max
     -> Description: Event loop maximum delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.046006
Metric #4
Descriptor:
     -> Name: nodejs.eventloop.delay.mean
     -> Description: Event loop mean delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.010315
Metric #5
Descriptor:
     -> Name: nodejs.eventloop.delay.stddev
     -> Description: Event loop standard deviation delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.000887
Metric #6
Descriptor:
     -> Name: nodejs.eventloop.delay.p50
     -> Description: Event loop 50 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.010215
Metric #7
Descriptor:
     -> Name: nodejs.eventloop.delay.p90
     -> Description: Event loop 90 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.010387
Metric #8
Descriptor:
     -> Name: nodejs.eventloop.delay.p99
     -> Description: Event loop 99 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.012878
Metric #9
Descriptor:
     -> Name: v8js.gc.duration
     -> Description: Garbage collection duration by kind, one of major, minor, incremental or weakcb.
     -> Unit: s
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> v8js.gc.type: Str(minor)
StartTimestamp: 2026-09-11 09:17:30.275 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Count: 47
Sum: 0.473390
Min: 0.000782
Max: 0.068666
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 21
Buckets #1, Count: 11
Buckets #2, Count: 12
Buckets #3, Count: 1
Buckets #4, Count: 2
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
HistogramDataPoints #1
Data point attributes:
     -> v8js.gc.type: Str(incremental)
StartTimestamp: 2026-09-11 09:17:30.676 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Count: 5
Sum: 0.005285
Min: 0.000005
Max: 0.003731
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 5
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
HistogramDataPoints #2
Data point attributes:
     -> v8js.gc.type: Str(major)
StartTimestamp: 2026-09-11 09:18:27.143 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Count: 2
Sum: 0.197411
Min: 0.096776
Max: 0.100635
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 1
Buckets #6, Count: 1
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Metric #10
Descriptor:
     -> Name: v8js.memory.heap.limit
     -> Description: Maximum heap size allowed by the V8 engine, as set by --max-old-space-size or V8 defaults.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 2197815296.000000
Metric #11
Descriptor:
     -> Name: v8js.memory.heap.space.size
     -> Description: Total heap memory size pre-allocated for a heap space.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 31076352.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 2568192.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 1843200.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 3944448.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 1048576.000000
Metric #12
Descriptor:
     -> Name: v8js.memory.heap.used
     -> Description: Heap Memory size allocated.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 29585416.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 2386112.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 1270872.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 3861384.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 247368.000000
Metric #13
Descriptor:
     -> Name: v8js.memory.heap.space.available_size
     -> Description: Heap space available size.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 891664.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 18240.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 537128.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 1030976.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 783608.000000
Metric #14
Descriptor:
     -> Name: v8js.memory.heap.space.physical_size
     -> Description: Committed size of a heap space.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 31076352.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 2445312.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 1708032.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 3944448.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 274432.000000
Metric #15
Descriptor:
     -> Name: v8js.resource.active
     -> Description: Count of the active resources that are currently keeping the event loop alive.
     -> Unit: {resource}
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.resource.type: Str(PipeWrap)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 2.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.resource.type: Str(TCPSocketWrap)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 2.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.resource.type: Str(TCPServerWrap)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 1.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.resource.type: Str(Timeout)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:02:32.981 +0000 UTC
Value: 5.000000
        {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics"}
2026-09-11T10:02:41.139Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 2, "metrics": 42, "data points": 111}
2026-09-11T10:02:41.143Z        info    ResourceMetrics #0
Resource SchemaURL: https://opentelemetry.io/schemas/1.24.0
Resource attributes:
     -> host.arch: Str(amd64)
     -> host.name: Str(shipping-6bccb998cb-pzknx)
     -> k8s.container.name: Str(shipping)
     -> k8s.deployment.name: Str(shipping)
     -> k8s.namespace.name: Str(roboshop)
     -> k8s.node.name: Str(desktop-worker)
     -> k8s.pod.name: Str(shipping-6bccb998cb-pzknx)
     -> k8s.replicaset.name: Str(shipping-6bccb998cb)
     -> os.description: Str(Linux 6.6.87.2-microsoft-standard-WSL2)
     -> os.type: Str(linux)
     -> os.version: Str(6.6.87.2-microsoft-standard-WSL2)
     -> process.command_args: Slice(["/opt/java/openjdk/bin/java","-Xmn256m","-Xmx768m","-jar","shipping.jar"])
     -> process.executable.path: Str(/opt/java/openjdk/bin/java)
     -> process.pid: Int(1)
     -> process.runtime.description: Str(Eclipse Adoptium OpenJDK 64-Bit Server VM 21.0.12+8-LTS)
     -> process.runtime.name: Str(OpenJDK Runtime Environment)
     -> process.runtime.version: Str(21.0.12+8-LTS)
     -> service.instance.id: Str(roboshop.shipping-6bccb998cb-pzknx.shipping)
     -> service.name: Str(shipping)
     -> service.namespace: Str(roboshop)
     -> service.version: Str(1.0.0)
     -> telemetry.distro.name: Str(opentelemetry-java-instrumentation)
     -> telemetry.distro.version: Str(2.31.1)
     -> telemetry.sdk.language: Str(java)
     -> telemetry.sdk.name: Str(opentelemetry)
     -> telemetry.sdk.version: Str(1.65.0)
ScopeMetrics #0
ScopeMetrics SchemaURL:
InstrumentationScope io.opentelemetry.hikaricp-3.0 2.31.1-alpha
Metric #0
Descriptor:
     -> Name: db.client.connections.pending_requests
     -> Description: The number of pending requests for an open connection, cumulative for the entire pool.
     -> Unit: {requests}
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
StartTimestamp: 2026-09-11 09:18:35.556527023 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 0
Metric #1
Descriptor:
     -> Name: db.client.connections.wait_time
     -> Description: The time it took to obtain an open connection from the pool.
     -> Unit: ms
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
StartTimestamp: 2026-09-11 09:18:43.259791939 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Count: 3
Sum: 2.487134
Min: 0.110020
Max: 1.222083
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 3
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
Metric #2
Descriptor:
     -> Name: db.client.connections.usage
     -> Description: The number of connections that are currently in state described by the state attribute.
     -> Unit: {connections}
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
     -> state: Str(idle)
StartTimestamp: 2026-09-11 09:18:35.556527023 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 10
NumberDataPoints #1
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
     -> state: Str(used)
StartTimestamp: 2026-09-11 09:18:35.556527023 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 0
Metric #3
Descriptor:
     -> Name: db.client.connections.idle.min
     -> Description: The minimum number of idle open connections allowed.
     -> Unit: {connections}
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
StartTimestamp: 2026-09-11 09:18:35.556527023 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 10
Metric #4
Descriptor:
     -> Name: db.client.connections.create_time
     -> Description: The time it took to create a new connection.
     -> Unit: ms
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
StartTimestamp: 2026-09-11 09:18:43.452814386 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Count: 19
Sum: 1108.000000
Min: 6.000000
Max: 121.000000
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 3
Buckets #3, Count: 6
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 6
Buckets #7, Count: 4
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
Metric #5
Descriptor:
     -> Name: db.client.connections.use_time
     -> Description: The time between borrowing a connection and returning it to the pool.
     -> Unit: ms
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
StartTimestamp: 2026-09-11 09:18:43.764227505 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Count: 3
Sum: 3902.000000
Min: 0.000000
Max: 3397.000000
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 1
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 1
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 1
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
Metric #6
Descriptor:
     -> Name: db.client.connections.max
     -> Description: The maximum number of open connections allowed.
     -> Unit: {connections}
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
StartTimestamp: 2026-09-11 09:18:35.556527023 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 10
ScopeMetrics #1
ScopeMetrics SchemaURL:
InstrumentationScope io.opentelemetry.exporters.otlp-http
Metric #0
Descriptor:
     -> Name: otlp.exporter.seen
     -> Description:
     -> Unit:
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> type: Str(span)
StartTimestamp: 2026-09-11 09:19:01.652963733 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 1
NumberDataPoints #1
Data point attributes:
     -> type: Str(log)
StartTimestamp: 2026-09-11 09:18:04.767379578 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 27
NumberDataPoints #2
Data point attributes:
     -> type: Str(metric)
StartTimestamp: 2026-09-11 09:18:36.067711625 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 991
Metric #1
Descriptor:
     -> Name: otlp.exporter.exported
     -> Description:
     -> Unit:
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> success: Bool(true)
     -> type: Str(log)
StartTimestamp: 2026-09-11 09:18:07.234445712 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 27
NumberDataPoints #1
Data point attributes:
     -> success: Bool(true)
     -> type: Str(span)
StartTimestamp: 2026-09-11 09:19:01.753338727 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 1
NumberDataPoints #2
Data point attributes:
     -> success: Bool(true)
     -> type: Str(metric)
StartTimestamp: 2026-09-11 09:18:36.158788103 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 991
ScopeMetrics #2
ScopeMetrics SchemaURL:
InstrumentationScope io.opentelemetry.sdk.logs
Metric #0
Descriptor:
     -> Name: processedLogs
     -> Description: The number of logs processed by the BatchLogRecordProcessor. [dropped=true if they were dropped due to high throughput]
     -> Unit: 1
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> dropped: Bool(false)
     -> processorType: Str(BatchLogRecordProcessor)
StartTimestamp: 2026-09-11 09:18:07.235174666 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 27
Metric #1
Descriptor:
     -> Name: queueSize
     -> Description: The number of items queued
     -> Unit: 1
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> processorType: Str(BatchLogRecordProcessor)
StartTimestamp: 2026-09-11 09:18:03.883428068 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 0
ScopeMetrics #3
ScopeMetrics SchemaURL:
InstrumentationScope io.opentelemetry.sdk.trace
Metric #0
Descriptor:
     -> Name: processedSpans
     -> Description: The number of spans processed by the BatchSpanProcessor. [dropped=true if they were dropped due to high throughput]
     -> Unit: 1
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> dropped: Bool(false)
     -> processorType: Str(BatchSpanProcessor)
StartTimestamp: 2026-09-11 09:19:01.753845195 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 1
Metric #1
Descriptor:
     -> Name: queueSize
     -> Description: The number of items queued
     -> Unit: 1
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> processorType: Str(BatchSpanProcessor)
StartTimestamp: 2026-09-11 09:18:35.556527023 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 0
ScopeMetrics #4
ScopeMetrics SchemaURL:
InstrumentationScope io.opentelemetry.runtime-telemetry-java8 2.31.1-alpha
Metric #0
Descriptor:
     -> Name: jvm.class.loaded
     -> Description: Number of classes loaded since JVM start.
     -> Unit: {class}
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:17:56.084185822 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 16710
Metric #1
Descriptor:
     -> Name: jvm.cpu.recent_utilization
     -> Description: Recent CPU utilization for the process as reported by the JVM.
     -> Unit: 1
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:17:56.281542597 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 0.014634
Metric #2
Descriptor:
     -> Name: jvm.memory.limit
     -> Description: Measure of max obtainable memory.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> jvm.memory.pool.name: Str(Compressed Class Space)
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584813338 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 1073741824
NumberDataPoints #1
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'non-profiled nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584813338 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 122916864
NumberDataPoints #2
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'non-nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584813338 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 5828608
NumberDataPoints #3
Data point attributes:
     -> jvm.memory.pool.name: Str(Eden Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.584813338 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 214827008
NumberDataPoints #4
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'profiled nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584813338 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 122912768
NumberDataPoints #5
Data point attributes:
     -> jvm.memory.pool.name: Str(Tenured Gen)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.584813338 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 536870912
NumberDataPoints #6
Data point attributes:
     -> jvm.memory.pool.name: Str(Survivor Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.584813338 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 26804224
Metric #3
Descriptor:
     -> Name: jvm.thread.count
     -> Description: Number of executing platform threads.
     -> Unit: {thread}
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> jvm.thread.daemon: Bool(true)
     -> jvm.thread.state: Str(waiting)
StartTimestamp: 2026-09-11 09:17:56.588451809 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 12
NumberDataPoints #1
Data point attributes:
     -> jvm.thread.daemon: Bool(true)
     -> jvm.thread.state: Str(runnable)
StartTimestamp: 2026-09-11 09:17:56.588451809 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 7
NumberDataPoints #2
Data point attributes:
     -> jvm.thread.daemon: Bool(true)
     -> jvm.thread.state: Str(timed_waiting)
StartTimestamp: 2026-09-11 09:17:56.588451809 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 8
NumberDataPoints #3
Data point attributes:
     -> jvm.thread.daemon: Bool(false)
     -> jvm.thread.state: Str(runnable)
StartTimestamp: 2026-09-11 09:17:56.588451809 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 1
NumberDataPoints #4
Data point attributes:
     -> jvm.thread.daemon: Bool(false)
     -> jvm.thread.state: Str(waiting)
StartTimestamp: 2026-09-11 09:17:56.588451809 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 1
NumberDataPoints #5
Data point attributes:
     -> jvm.thread.daemon: Bool(false)
     -> jvm.thread.state: Str(timed_waiting)
StartTimestamp: 2026-09-11 09:17:56.588451809 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 2
Metric #4
Descriptor:
     -> Name: jvm.cpu.time
     -> Description: CPU time used by the process as reported by the JVM.
     -> Unit: s
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:17:56.278263608 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 62.940000
Metric #5
Descriptor:
     -> Name: jvm.class.count
     -> Description: Number of classes currently loaded.
     -> Unit: {class}
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:17:56.174725824 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 16710
Metric #6
Descriptor:
     -> Name: jvm.memory.used_after_last_gc
     -> Description: Measure of memory used, as measured after the most recent garbage collection event on this pool.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> jvm.memory.pool.name: Str(Eden Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.585255913 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 2134592
NumberDataPoints #1
Data point attributes:
     -> jvm.memory.pool.name: Str(Tenured Gen)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.585255913 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 37724152
NumberDataPoints #2
Data point attributes:
     -> jvm.memory.pool.name: Str(Survivor Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.585255913 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 0
Metric #7
Descriptor:
     -> Name: jvm.memory.used
     -> Description: Measure of memory used.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> jvm.memory.pool.name: Str(Compressed Class Space)
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 11004816
NumberDataPoints #1
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'non-profiled nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 5649280
NumberDataPoints #2
Data point attributes:
     -> jvm.memory.pool.name: Str(Metaspace)
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 83184904
NumberDataPoints #3
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'non-nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 1463808
NumberDataPoints #4
Data point attributes:
     -> jvm.memory.pool.name: Str(Eden Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 44769576
NumberDataPoints #5
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'profiled nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 15478912
NumberDataPoints #6
Data point attributes:
     -> jvm.memory.pool.name: Str(Tenured Gen)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 37724152
NumberDataPoints #7
Data point attributes:
     -> jvm.memory.pool.name: Str(Survivor Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 0
Metric #8
Descriptor:
     -> Name: jvm.cpu.count
     -> Description: Number of processors available to the Java virtual machine.
     -> Unit: {cpu}
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:17:56.284061517 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 1
Metric #9
Descriptor:
     -> Name: jvm.class.unloaded
     -> Description: Number of classes unloaded since JVM start.
     -> Unit: {class}
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:17:56.171743598 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 0
Metric #10
Descriptor:
     -> Name: jvm.memory.committed
     -> Description: Measure of memory committed.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> jvm.memory.pool.name: Str(Compressed Class Space)
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 11272192
NumberDataPoints #1
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'non-profiled nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 5701632
NumberDataPoints #2
Data point attributes:
     -> jvm.memory.pool.name: Str(Metaspace)
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 83820544
NumberDataPoints #3
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'non-nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 2555904
NumberDataPoints #4
Data point attributes:
     -> jvm.memory.pool.name: Str(Eden Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 214827008
NumberDataPoints #5
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'profiled nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 15532032
NumberDataPoints #6
Data point attributes:
     -> jvm.memory.pool.name: Str(Tenured Gen)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 62873600
NumberDataPoints #7
Data point attributes:
     -> jvm.memory.pool.name: Str(Survivor Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Value: 26804224
Metric #11
Descriptor:
     -> Name: jvm.gc.duration
     -> Description: Duration of JVM garbage collection actions.
     -> Unit: s
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> jvm.gc.action: Str(end of minor GC)
     -> jvm.gc.name: Str(Copy)
StartTimestamp: 2026-09-11 09:17:58.779314233 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Count: 7
Sum: 1.079000
Min: 0.106000
Max: 0.304000
ExplicitBounds #0: 0.010000
ExplicitBounds #1: 0.100000
ExplicitBounds #2: 1.000000
ExplicitBounds #3: 10.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 7
Buckets #3, Count: 0
Buckets #4, Count: 0
HistogramDataPoints #1
Data point attributes:
     -> jvm.gc.action: Str(end of major GC)
     -> jvm.gc.name: Str(MarkSweepCompact)
StartTimestamp: 2026-09-11 09:18:06.99709607 +0000 UTC
Timestamp: 2026-09-11 10:02:40.964631198 +0000 UTC
Count: 3
Sum: 0.842000
Min: 0.130000
Max: 0.403000
ExplicitBounds #0: 0.010000
ExplicitBounds #1: 0.100000
ExplicitBounds #2: 1.000000
ExplicitBounds #3: 10.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 3
Buckets #3, Count: 0
Buckets #4, Count: 0
ResourceMetrics #1
Resource SchemaURL:
Resource attributes:
     -> k8s.container.name: Str(catalogue)
     -> k8s.deployment.name: Str(catalogue)
     -> k8s.namespace.name: Str(roboshop)
     -> k8s.node.name: Str(desktop-worker2)
     -> k8s.pod.name: Str(catalogue-5bcb5b9b49-x2fxx)
     -> k8s.replicaset.name: Str(catalogue-5bcb5b9b49)
     -> service.instance.id: Str(roboshop.catalogue-5bcb5b9b49-x2fxx.catalogue)
     -> service.namespace: Str(roboshop)
     -> service.version: Str(1.0.0)
     -> service.name: Str(catalogue)
     -> process.pid: Int(1)
     -> process.executable.name: Str(node)
     -> process.executable.path: Str(/usr/local/bin/node)
     -> process.command_args: Slice(["/usr/local/bin/node","/opt/server/server.js"])
     -> process.runtime.version: Str(18.19.1)
     -> process.runtime.name: Str(nodejs)
     -> process.runtime.description: Str(Node.js)
     -> process.command: Str(/opt/server/server.js)
     -> process.owner: Str(roboshop)
     -> os.type: Str(linux)
     -> os.version: Str(6.6.87.2-microsoft-standard-WSL2)
     -> host.name: Str(catalogue-5bcb5b9b49-x2fxx)
     -> host.arch: Str(amd64)
     -> telemetry.sdk.language: Str(nodejs)
     -> telemetry.sdk.name: Str(opentelemetry)
     -> telemetry.sdk.version: Str(2.9.0)
ScopeMetrics #0
ScopeMetrics SchemaURL:
InstrumentationScope @opentelemetry/instrumentation-http 0.220.0
Metric #0
Descriptor:
     -> Name: http.client.duration
     -> Description: Measures the duration of outbound HTTP requests.
     -> Unit: ms
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> http.method: Str(GET)
     -> net.peer.name: Str(169.254.169.254)
StartTimestamp: 2026-09-11 09:21:38.135 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Count: 1
Sum: 25.668065
Min: 25.668065
Max: 25.668065
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 1
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
HistogramDataPoints #1
Data point attributes:
     -> http.method: Str(GET)
     -> net.peer.name: Str(metadata.google.internal.)
StartTimestamp: 2026-09-11 09:21:38.179 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Count: 1
Sum: 62.296378
Min: 62.296378
Max: 62.296378
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 1
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
HistogramDataPoints #2
Data point attributes:
     -> http.method: Str(POST)
     -> net.peer.name: Str(opentelemetry-collector.opentelemetry.svc.cluster.local)
     -> net.peer.port: Int(4318)
     -> http.status_code: Int(200)
     -> http.flavor: Str(1.1)
StartTimestamp: 2026-09-11 09:21:42.15 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Count: 37
Sum: 875.657237
Min: 5.871870
Max: 261.634589
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 17
Buckets #3, Count: 12
Buckets #4, Count: 5
Buckets #5, Count: 0
Buckets #6, Count: 2
Buckets #7, Count: 0
Buckets #8, Count: 1
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
ScopeMetrics #1
ScopeMetrics SchemaURL:
InstrumentationScope @opentelemetry/instrumentation-runtime-node 0.33.0
Metric #0
Descriptor:
     -> Name: nodejs.eventloop.utilization
     -> Description: Event loop utilization
     -> Unit: 1
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.006159
Metric #1
Descriptor:
     -> Name: nodejs.eventloop.time
     -> Description: Cumulative duration of time the event loop has been in each state.
     -> Unit: s
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> nodejs.eventloop.state: Str(active)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 15.444787
NumberDataPoints #1
Data point attributes:
     -> nodejs.eventloop.state: Str(idle)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 2202.906314
Metric #2
Descriptor:
     -> Name: nodejs.eventloop.delay.min
     -> Description: Event loop minimum delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.007197
Metric #3
Descriptor:
     -> Name: nodejs.eventloop.delay.max
     -> Description: Event loop maximum delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.035750
Metric #4
Descriptor:
     -> Name: nodejs.eventloop.delay.mean
     -> Description: Event loop mean delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.010316
Metric #5
Descriptor:
     -> Name: nodejs.eventloop.delay.stddev
     -> Description: Event loop standard deviation delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.000903
Metric #6
Descriptor:
     -> Name: nodejs.eventloop.delay.p50
     -> Description: Event loop 50 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.010215
Metric #7
Descriptor:
     -> Name: nodejs.eventloop.delay.p90
     -> Description: Event loop 90 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.010387
Metric #8
Descriptor:
     -> Name: nodejs.eventloop.delay.p99
     -> Description: Event loop 99 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.013238
Metric #9
Descriptor:
     -> Name: v8js.gc.duration
     -> Description: Garbage collection duration by kind, one of major, minor, incremental or weakcb.
     -> Unit: s
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> v8js.gc.type: Str(minor)
StartTimestamp: 2026-09-11 09:21:37.202 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Count: 38
Sum: 0.484784
Min: 0.001311
Max: 0.106107
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 12
Buckets #1, Count: 7
Buckets #2, Count: 17
Buckets #3, Count: 1
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 1
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
HistogramDataPoints #1
Data point attributes:
     -> v8js.gc.type: Str(incremental)
StartTimestamp: 2026-09-11 09:21:37.579 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Count: 5
Sum: 0.009636
Min: 0.000004
Max: 0.008901
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 4
Buckets #1, Count: 1
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
HistogramDataPoints #2
Data point attributes:
     -> v8js.gc.type: Str(major)
StartTimestamp: 2026-09-11 09:22:35.25 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Count: 2
Sum: 0.230786
Min: 0.099846
Max: 0.130940
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 1
Buckets #6, Count: 1
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Metric #10
Descriptor:
     -> Name: v8js.memory.heap.limit
     -> Description: Maximum heap size allowed by the V8 engine, as set by --max-old-space-size or V8 defaults.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 2197815296.000000
Metric #11
Descriptor:
     -> Name: v8js.memory.heap.space.size
     -> Description: Total heap memory size pre-allocated for a heap space.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 29241344.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 2306048.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 1843200.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 3944448.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 1048576.000000
Metric #12
Descriptor:
     -> Name: v8js.memory.heap.used
     -> Description: Heap Memory size allocated.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 27396400.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 2152192.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 1161416.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 3861384.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 342248.000000
Metric #13
Descriptor:
     -> Name: v8js.memory.heap.space.available_size
     -> Description: Heap space available size.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 1287560.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 6400.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 646584.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 1030976.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 688728.000000
Metric #14
Descriptor:
     -> Name: v8js.memory.heap.space.physical_size
     -> Description: Committed size of a heap space.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 29241344.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 2195456.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 1589248.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 3944448.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 532480.000000
Metric #15
Descriptor:
     -> Name: v8js.resource.active
     -> Description: Count of the active resources that are currently keeping the event loop alive.
     -> Unit: {resource}
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.resource.type: Str(PipeWrap)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 2.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.resource.type: Str(TCPSocketWrap)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 1.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.resource.type: Str(TCPServerWrap)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 1.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.resource.type: Str(Timeout)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:02:41.026 +0000 UTC
Value: 5.000000
        {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics"}
2026-09-11T10:03:27.718Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 52}
2026-09-11T10:03:27.719Z        info    ResourceMetrics #0
Resource SchemaURL:
Resource attributes:
     -> k8s.container.name: Str(cart)
     -> k8s.deployment.name: Str(cart)
     -> k8s.namespace.name: Str(roboshop)
     -> k8s.node.name: Str(desktop-worker)
     -> k8s.pod.name: Str(cart-74c6975b45-jjlq8)
     -> k8s.replicaset.name: Str(cart-74c6975b45)
     -> service.instance.id: Str(roboshop.cart-74c6975b45-jjlq8.cart)
     -> service.namespace: Str(roboshop)
     -> service.version: Str(1.0.0)
     -> service.name: Str(cart)
     -> process.pid: Int(1)
     -> process.executable.name: Str(node)
     -> process.executable.path: Str(/usr/local/bin/node)
     -> process.command_args: Slice(["/usr/local/bin/node","/opt/server/server.js"])
     -> process.runtime.version: Str(18.19.1)
     -> process.runtime.name: Str(nodejs)
     -> process.runtime.description: Str(Node.js)
     -> process.command: Str(/opt/server/server.js)
     -> process.owner: Str(roboshop)
     -> os.type: Str(linux)
     -> os.version: Str(6.6.87.2-microsoft-standard-WSL2)
     -> host.name: Str(cart-74c6975b45-jjlq8)
     -> host.arch: Str(amd64)
     -> telemetry.sdk.language: Str(nodejs)
     -> telemetry.sdk.name: Str(opentelemetry)
     -> telemetry.sdk.version: Str(2.9.0)
ScopeMetrics #0
ScopeMetrics SchemaURL:
InstrumentationScope @opentelemetry/instrumentation-http 0.220.0
Metric #0
Descriptor:
     -> Name: http.client.duration
     -> Description: Measures the duration of outbound HTTP requests.
     -> Unit: ms
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> http.method: Str(GET)
     -> net.peer.name: Str(kubernetes.default.svc)
     -> net.peer.port: Int(443)
     -> http.status_code: Int(403)
     -> http.flavor: Str(1.1)
StartTimestamp: 2026-09-11 09:17:26.829 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Count: 1
Sum: 506.311820
Min: 506.311820
Max: 506.311820
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 1
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
HistogramDataPoints #1
Data point attributes:
     -> http.method: Str(POST)
     -> net.peer.name: Str(opentelemetry-collector.opentelemetry.svc.cluster.local)
     -> net.peer.port: Int(4318)
     -> http.status_code: Int(200)
     -> http.flavor: Str(1.1)
StartTimestamp: 2026-09-11 09:17:31.076 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Count: 43
Sum: 1393.730308
Min: 3.232514
Max: 140.630282
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 1
Buckets #2, Count: 2
Buckets #3, Count: 20
Buckets #4, Count: 12
Buckets #5, Count: 6
Buckets #6, Count: 1
Buckets #7, Count: 1
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
ScopeMetrics #1
ScopeMetrics SchemaURL:
InstrumentationScope @opentelemetry/instrumentation-runtime-node 0.33.0
Metric #0
Descriptor:
     -> Name: nodejs.eventloop.utilization
     -> Description: Event loop utilization
     -> Unit: 1
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.004318
Metric #1
Descriptor:
     -> Name: nodejs.eventloop.time
     -> Description: Cumulative duration of time the event loop has been in each state.
     -> Unit: s
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> nodejs.eventloop.state: Str(active)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 14.371688
NumberDataPoints #1
Data point attributes:
     -> nodejs.eventloop.state: Str(idle)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 2502.070666
Metric #2
Descriptor:
     -> Name: nodejs.eventloop.delay.min
     -> Description: Event loop minimum delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.005263
Metric #3
Descriptor:
     -> Name: nodejs.eventloop.delay.max
     -> Description: Event loop maximum delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.028525
Metric #4
Descriptor:
     -> Name: nodejs.eventloop.delay.mean
     -> Description: Event loop mean delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.010241
Metric #5
Descriptor:
     -> Name: nodejs.eventloop.delay.stddev
     -> Description: Event loop standard deviation delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.000399
Metric #6
Descriptor:
     -> Name: nodejs.eventloop.delay.p50
     -> Description: Event loop 50 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.010207
Metric #7
Descriptor:
     -> Name: nodejs.eventloop.delay.p90
     -> Description: Event loop 90 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.010363
Metric #8
Descriptor:
     -> Name: nodejs.eventloop.delay.p99
     -> Description: Event loop 99 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.011084
Metric #9
Descriptor:
     -> Name: v8js.gc.duration
     -> Description: Garbage collection duration by kind, one of major, minor, incremental or weakcb.
     -> Unit: s
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> v8js.gc.type: Str(minor)
StartTimestamp: 2026-09-11 09:17:25.93 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Count: 37
Sum: 0.272816
Min: 0.000527
Max: 0.072193
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 21
Buckets #1, Count: 9
Buckets #2, Count: 6
Buckets #3, Count: 0
Buckets #4, Count: 1
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
HistogramDataPoints #1
Data point attributes:
     -> v8js.gc.type: Str(incremental)
StartTimestamp: 2026-09-11 09:18:55.009 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Count: 6
Sum: 0.007490
Min: 0.000005
Max: 0.004002
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 6
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
HistogramDataPoints #2
Data point attributes:
     -> v8js.gc.type: Str(major)
StartTimestamp: 2026-09-11 09:18:55.211 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Count: 3
Sum: 0.326538
Min: 0.008762
Max: 0.202812
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 0
Buckets #1, Count: 1
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 2
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Metric #10
Descriptor:
     -> Name: v8js.memory.heap.limit
     -> Description: Maximum heap size allowed by the V8 engine, as set by --max-old-space-size or V8 defaults.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 2197815296.000000
Metric #11
Descriptor:
     -> Name: v8js.memory.heap.space.size
     -> Description: Total heap memory size pre-allocated for a heap space.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 29503488.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 2043904.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 1843200.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 2875392.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 1048576.000000
Metric #12
Descriptor:
     -> Name: v8js.memory.heap.used
     -> Description: Heap Memory size allocated.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 28233032.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 1885760.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 1161936.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 2829656.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 997504.000000
Metric #13
Descriptor:
     -> Name: v8js.memory.heap.space.available_size
     -> Description: Heap space available size.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 713024.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 27072.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 646064.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 1030976.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 33472.000000
Metric #14
Descriptor:
     -> Name: v8js.memory.heap.space.physical_size
     -> Description: Committed size of a heap space.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 29503488.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 1945600.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 1650688.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 2875392.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 1048576.000000
Metric #15
Descriptor:
     -> Name: v8js.resource.active
     -> Description: Count of the active resources that are currently keeping the event loop alive.
     -> Unit: {resource}
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.resource.type: Str(PipeWrap)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 2.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.resource.type: Str(TCPSocketWrap)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 1.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.resource.type: Str(TCPServerWrap)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 1.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.resource.type: Str(Timeout)
StartTimestamp: 2026-09-11 09:18:22.233 +0000 UTC
Timestamp: 2026-09-11 10:03:27.623 +0000 UTC
Value: 4.000000
        {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics"}
2026-09-11T10:03:33.147Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 53}
2026-09-11T10:03:33.148Z        info    ResourceMetrics #0
Resource SchemaURL:
Resource attributes:
     -> k8s.container.name: Str(user)
     -> k8s.deployment.name: Str(user)
     -> k8s.namespace.name: Str(roboshop)
     -> k8s.node.name: Str(desktop-worker)
     -> k8s.pod.name: Str(user-74bcc7d99c-jw4sg)
     -> k8s.replicaset.name: Str(user-74bcc7d99c)
     -> service.instance.id: Str(roboshop.user-74bcc7d99c-jw4sg.user)
     -> service.namespace: Str(roboshop)
     -> service.version: Str(1.0.0)
     -> service.name: Str(user)
     -> process.pid: Int(1)
     -> process.executable.name: Str(node)
     -> process.executable.path: Str(/usr/local/bin/node)
     -> process.command_args: Slice(["/usr/local/bin/node","/opt/server/server.js"])
     -> process.runtime.version: Str(18.19.1)
     -> process.runtime.name: Str(nodejs)
     -> process.runtime.description: Str(Node.js)
     -> process.command: Str(/opt/server/server.js)
     -> process.owner: Str(roboshop)
     -> os.type: Str(linux)
     -> os.version: Str(6.6.87.2-microsoft-standard-WSL2)
     -> host.name: Str(user-74bcc7d99c-jw4sg)
     -> host.arch: Str(amd64)
     -> telemetry.sdk.language: Str(nodejs)
     -> telemetry.sdk.name: Str(opentelemetry)
     -> telemetry.sdk.version: Str(2.9.0)
ScopeMetrics #0
ScopeMetrics SchemaURL:
InstrumentationScope @opentelemetry/instrumentation-http 0.220.0
Metric #0
Descriptor:
     -> Name: http.server.duration
     -> Description: Measures the duration of inbound HTTP requests.
     -> Unit: ms
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> http.scheme: Str(http)
     -> http.method: Str(GET)
     -> net.host.name: Str(user)
     -> http.flavor: Str(1.1)
     -> http.status_code: Int(200)
     -> net.host.port: Int(8080)
     -> http.route: Str(/health)
StartTimestamp: 2026-09-11 09:32:21.804 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Count: 21
Sum: 217.332755
Min: 2.716886
Max: 41.640505
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 11
Buckets #2, Count: 4
Buckets #3, Count: 3
Buckets #4, Count: 3
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
Metric #1
Descriptor:
     -> Name: http.client.duration
     -> Description: Measures the duration of outbound HTTP requests.
     -> Unit: ms
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> http.method: Str(POST)
     -> net.peer.name: Str(opentelemetry-collector.opentelemetry.svc.cluster.local)
     -> net.peer.port: Int(4318)
     -> http.status_code: Int(200)
     -> http.flavor: Str(1.1)
StartTimestamp: 2026-09-11 09:17:35.209 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Count: 45
Sum: 814.999993
Min: 1.671517
Max: 128.512492
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 15
Buckets #2, Count: 12
Buckets #3, Count: 9
Buckets #4, Count: 5
Buckets #5, Count: 2
Buckets #6, Count: 1
Buckets #7, Count: 1
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
HistogramDataPoints #1
Data point attributes:
     -> http.method: Str(POST)
     -> net.peer.name: Str(opentelemetry-collector.opentelemetry.svc.cluster.local)
StartTimestamp: 2026-09-11 09:30:28.491 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Count: 1
Sum: 60.403901
Min: 60.403901
Max: 60.403901
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 1
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
ScopeMetrics #1
ScopeMetrics SchemaURL:
InstrumentationScope @opentelemetry/instrumentation-runtime-node 0.33.0
Metric #0
Descriptor:
     -> Name: nodejs.eventloop.utilization
     -> Description: Event loop utilization
     -> Unit: 1
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.004623
Metric #1
Descriptor:
     -> Name: nodejs.eventloop.time
     -> Description: Cumulative duration of time the event loop has been in each state.
     -> Unit: s
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> nodejs.eventloop.state: Str(active)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 14.609017
NumberDataPoints #1
Data point attributes:
     -> nodejs.eventloop.state: Str(idle)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 2502.813151
Metric #2
Descriptor:
     -> Name: nodejs.eventloop.delay.min
     -> Description: Event loop minimum delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.009101
Metric #3
Descriptor:
     -> Name: nodejs.eventloop.delay.max
     -> Description: Event loop maximum delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.020038
Metric #4
Descriptor:
     -> Name: nodejs.eventloop.delay.mean
     -> Description: Event loop mean delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.010240
Metric #5
Descriptor:
     -> Name: nodejs.eventloop.delay.stddev
     -> Description: Event loop standard deviation delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.000305
Metric #6
Descriptor:
     -> Name: nodejs.eventloop.delay.p50
     -> Description: Event loop 50 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.010207
Metric #7
Descriptor:
     -> Name: nodejs.eventloop.delay.p90
     -> Description: Event loop 90 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.010363
Metric #8
Descriptor:
     -> Name: nodejs.eventloop.delay.p99
     -> Description: Event loop 99 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.010994
Metric #9
Descriptor:
     -> Name: v8js.gc.duration
     -> Description: Garbage collection duration by kind, one of major, minor, incremental or weakcb.
     -> Unit: s
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> v8js.gc.type: Str(minor)
StartTimestamp: 2026-09-11 09:17:30.275 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Count: 48
Sum: 0.475027
Min: 0.000782
Max: 0.068666
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 22
Buckets #1, Count: 11
Buckets #2, Count: 12
Buckets #3, Count: 1
Buckets #4, Count: 2
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
HistogramDataPoints #1
Data point attributes:
     -> v8js.gc.type: Str(incremental)
StartTimestamp: 2026-09-11 09:17:30.676 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Count: 5
Sum: 0.005285
Min: 0.000005
Max: 0.003731
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 5
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
HistogramDataPoints #2
Data point attributes:
     -> v8js.gc.type: Str(major)
StartTimestamp: 2026-09-11 09:18:27.143 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Count: 2
Sum: 0.197411
Min: 0.096776
Max: 0.100635
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 1
Buckets #6, Count: 1
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Metric #10
Descriptor:
     -> Name: v8js.memory.heap.limit
     -> Description: Maximum heap size allowed by the V8 engine, as set by --max-old-space-size or V8 defaults.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 2197815296.000000
Metric #11
Descriptor:
     -> Name: v8js.memory.heap.space.size
     -> Description: Total heap memory size pre-allocated for a heap space.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 31076352.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 2568192.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 1843200.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 3944448.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 1048576.000000
Metric #12
Descriptor:
     -> Name: v8js.memory.heap.used
     -> Description: Heap Memory size allocated.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 29589744.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 2386112.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 1270872.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 3861384.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 195896.000000
Metric #13
Descriptor:
     -> Name: v8js.memory.heap.space.available_size
     -> Description: Heap space available size.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 887184.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 18240.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 537128.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 1030976.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 835080.000000
Metric #14
Descriptor:
     -> Name: v8js.memory.heap.space.physical_size
     -> Description: Committed size of a heap space.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 31076352.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 2445312.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 1708032.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 3944448.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 274432.000000
Metric #15
Descriptor:
     -> Name: v8js.resource.active
     -> Description: Count of the active resources that are currently keeping the event loop alive.
     -> Unit: {resource}
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.resource.type: Str(PipeWrap)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 2.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.resource.type: Str(TCPSocketWrap)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 2.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.resource.type: Str(TCPServerWrap)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 1.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.resource.type: Str(Timeout)
StartTimestamp: 2026-09-11 09:18:27.562 +0000 UTC
Timestamp: 2026-09-11 10:03:32.964 +0000 UTC
Value: 5.000000
        {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics"}
2026-09-11T10:03:40.979Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 25, "data points": 58}
2026-09-11T10:03:40.980Z        info    ResourceMetrics #0
Resource SchemaURL: https://opentelemetry.io/schemas/1.24.0
Resource attributes:
     -> host.arch: Str(amd64)
     -> host.name: Str(shipping-6bccb998cb-pzknx)
     -> k8s.container.name: Str(shipping)
     -> k8s.deployment.name: Str(shipping)
     -> k8s.namespace.name: Str(roboshop)
     -> k8s.node.name: Str(desktop-worker)
     -> k8s.pod.name: Str(shipping-6bccb998cb-pzknx)
     -> k8s.replicaset.name: Str(shipping-6bccb998cb)
     -> os.description: Str(Linux 6.6.87.2-microsoft-standard-WSL2)
     -> os.type: Str(linux)
     -> os.version: Str(6.6.87.2-microsoft-standard-WSL2)
     -> process.command_args: Slice(["/opt/java/openjdk/bin/java","-Xmn256m","-Xmx768m","-jar","shipping.jar"])
     -> process.executable.path: Str(/opt/java/openjdk/bin/java)
     -> process.pid: Int(1)
     -> process.runtime.description: Str(Eclipse Adoptium OpenJDK 64-Bit Server VM 21.0.12+8-LTS)
     -> process.runtime.name: Str(OpenJDK Runtime Environment)
     -> process.runtime.version: Str(21.0.12+8-LTS)
     -> service.instance.id: Str(roboshop.shipping-6bccb998cb-pzknx.shipping)
     -> service.name: Str(shipping)
     -> service.namespace: Str(roboshop)
     -> service.version: Str(1.0.0)
     -> telemetry.distro.name: Str(opentelemetry-java-instrumentation)
     -> telemetry.distro.version: Str(2.31.1)
     -> telemetry.sdk.language: Str(java)
     -> telemetry.sdk.name: Str(opentelemetry)
     -> telemetry.sdk.version: Str(1.65.0)
ScopeMetrics #0
ScopeMetrics SchemaURL:
InstrumentationScope io.opentelemetry.hikaricp-3.0 2.31.1-alpha
Metric #0
Descriptor:
     -> Name: db.client.connections.pending_requests
     -> Description: The number of pending requests for an open connection, cumulative for the entire pool.
     -> Unit: {requests}
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
StartTimestamp: 2026-09-11 09:18:35.556527023 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 0
Metric #1
Descriptor:
     -> Name: db.client.connections.wait_time
     -> Description: The time it took to obtain an open connection from the pool.
     -> Unit: ms
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
StartTimestamp: 2026-09-11 09:18:43.259791939 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Count: 3
Sum: 2.487134
Min: 0.110020
Max: 1.222083
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 3
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
Metric #2
Descriptor:
     -> Name: db.client.connections.usage
     -> Description: The number of connections that are currently in state described by the state attribute.
     -> Unit: {connections}
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
     -> state: Str(idle)
StartTimestamp: 2026-09-11 09:18:35.556527023 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 10
NumberDataPoints #1
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
     -> state: Str(used)
StartTimestamp: 2026-09-11 09:18:35.556527023 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 0
Metric #3
Descriptor:
     -> Name: db.client.connections.idle.min
     -> Description: The minimum number of idle open connections allowed.
     -> Unit: {connections}
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
StartTimestamp: 2026-09-11 09:18:35.556527023 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 10
Metric #4
Descriptor:
     -> Name: db.client.connections.create_time
     -> Description: The time it took to create a new connection.
     -> Unit: ms
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
StartTimestamp: 2026-09-11 09:18:43.452814386 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Count: 19
Sum: 1108.000000
Min: 6.000000
Max: 121.000000
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 3
Buckets #3, Count: 6
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 6
Buckets #7, Count: 4
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
Metric #5
Descriptor:
     -> Name: db.client.connections.use_time
     -> Description: The time between borrowing a connection and returning it to the pool.
     -> Unit: ms
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
StartTimestamp: 2026-09-11 09:18:43.764227505 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Count: 3
Sum: 3902.000000
Min: 0.000000
Max: 3397.000000
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 1
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 1
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 1
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
Metric #6
Descriptor:
     -> Name: db.client.connections.max
     -> Description: The maximum number of open connections allowed.
     -> Unit: {connections}
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> pool.name: Str(mysql:3306/cities)
StartTimestamp: 2026-09-11 09:18:35.556527023 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 10
ScopeMetrics #1
ScopeMetrics SchemaURL:
InstrumentationScope io.opentelemetry.exporters.otlp-http
Metric #0
Descriptor:
     -> Name: otlp.exporter.seen
     -> Description:
     -> Unit:
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> type: Str(span)
StartTimestamp: 2026-09-11 09:19:01.652963733 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 1
NumberDataPoints #1
Data point attributes:
     -> type: Str(log)
StartTimestamp: 2026-09-11 09:18:04.767379578 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 27
NumberDataPoints #2
Data point attributes:
     -> type: Str(metric)
StartTimestamp: 2026-09-11 09:18:36.067711625 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 1016
Metric #1
Descriptor:
     -> Name: otlp.exporter.exported
     -> Description:
     -> Unit:
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> success: Bool(true)
     -> type: Str(log)
StartTimestamp: 2026-09-11 09:18:07.234445712 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 27
NumberDataPoints #1
Data point attributes:
     -> success: Bool(true)
     -> type: Str(span)
StartTimestamp: 2026-09-11 09:19:01.753338727 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 1
NumberDataPoints #2
Data point attributes:
     -> success: Bool(true)
     -> type: Str(metric)
StartTimestamp: 2026-09-11 09:18:36.158788103 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 1016
ScopeMetrics #2
ScopeMetrics SchemaURL:
InstrumentationScope io.opentelemetry.sdk.logs
Metric #0
Descriptor:
     -> Name: processedLogs
     -> Description: The number of logs processed by the BatchLogRecordProcessor. [dropped=true if they were dropped due to high throughput]
     -> Unit: 1
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> dropped: Bool(false)
     -> processorType: Str(BatchLogRecordProcessor)
StartTimestamp: 2026-09-11 09:18:07.235174666 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 27
Metric #1
Descriptor:
     -> Name: queueSize
     -> Description: The number of items queued
     -> Unit: 1
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> processorType: Str(BatchLogRecordProcessor)
StartTimestamp: 2026-09-11 09:18:03.883428068 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 0
ScopeMetrics #3
ScopeMetrics SchemaURL:
InstrumentationScope io.opentelemetry.sdk.trace
Metric #0
Descriptor:
     -> Name: processedSpans
     -> Description: The number of spans processed by the BatchSpanProcessor. [dropped=true if they were dropped due to high throughput]
     -> Unit: 1
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> dropped: Bool(false)
     -> processorType: Str(BatchSpanProcessor)
StartTimestamp: 2026-09-11 09:19:01.753845195 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 1
Metric #1
Descriptor:
     -> Name: queueSize
     -> Description: The number of items queued
     -> Unit: 1
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> processorType: Str(BatchSpanProcessor)
StartTimestamp: 2026-09-11 09:18:35.556527023 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 0
ScopeMetrics #4
ScopeMetrics SchemaURL:
InstrumentationScope io.opentelemetry.runtime-telemetry-java8 2.31.1-alpha
Metric #0
Descriptor:
     -> Name: jvm.class.loaded
     -> Description: Number of classes loaded since JVM start.
     -> Unit: {class}
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:17:56.084185822 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 16710
Metric #1
Descriptor:
     -> Name: jvm.cpu.recent_utilization
     -> Description: Recent CPU utilization for the process as reported by the JVM.
     -> Unit: 1
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:17:56.281542597 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 0.015936
Metric #2
Descriptor:
     -> Name: jvm.memory.limit
     -> Description: Measure of max obtainable memory.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> jvm.memory.pool.name: Str(Compressed Class Space)
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584813338 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 1073741824
NumberDataPoints #1
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'non-profiled nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584813338 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 122916864
NumberDataPoints #2
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'non-nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584813338 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 5828608
NumberDataPoints #3
Data point attributes:
     -> jvm.memory.pool.name: Str(Eden Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.584813338 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 214827008
NumberDataPoints #4
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'profiled nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584813338 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 122912768
NumberDataPoints #5
Data point attributes:
     -> jvm.memory.pool.name: Str(Tenured Gen)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.584813338 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 536870912
NumberDataPoints #6
Data point attributes:
     -> jvm.memory.pool.name: Str(Survivor Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.584813338 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 26804224
Metric #3
Descriptor:
     -> Name: jvm.thread.count
     -> Description: Number of executing platform threads.
     -> Unit: {thread}
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> jvm.thread.daemon: Bool(true)
     -> jvm.thread.state: Str(waiting)
StartTimestamp: 2026-09-11 09:17:56.588451809 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 12
NumberDataPoints #1
Data point attributes:
     -> jvm.thread.daemon: Bool(true)
     -> jvm.thread.state: Str(runnable)
StartTimestamp: 2026-09-11 09:17:56.588451809 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 7
NumberDataPoints #2
Data point attributes:
     -> jvm.thread.daemon: Bool(true)
     -> jvm.thread.state: Str(timed_waiting)
StartTimestamp: 2026-09-11 09:17:56.588451809 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 8
NumberDataPoints #3
Data point attributes:
     -> jvm.thread.daemon: Bool(false)
     -> jvm.thread.state: Str(runnable)
StartTimestamp: 2026-09-11 09:17:56.588451809 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 1
NumberDataPoints #4
Data point attributes:
     -> jvm.thread.daemon: Bool(false)
     -> jvm.thread.state: Str(waiting)
StartTimestamp: 2026-09-11 09:17:56.588451809 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 1
NumberDataPoints #5
Data point attributes:
     -> jvm.thread.daemon: Bool(false)
     -> jvm.thread.state: Str(timed_waiting)
StartTimestamp: 2026-09-11 09:17:56.588451809 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 2
Metric #4
Descriptor:
     -> Name: jvm.cpu.time
     -> Description: CPU time used by the process as reported by the JVM.
     -> Unit: s
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:17:56.278263608 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 63.150000
Metric #5
Descriptor:
     -> Name: jvm.class.count
     -> Description: Number of classes currently loaded.
     -> Unit: {class}
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:17:56.174725824 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 16710
Metric #6
Descriptor:
     -> Name: jvm.memory.used_after_last_gc
     -> Description: Measure of memory used, as measured after the most recent garbage collection event on this pool.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> jvm.memory.pool.name: Str(Eden Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.585255913 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 2134592
NumberDataPoints #1
Data point attributes:
     -> jvm.memory.pool.name: Str(Tenured Gen)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.585255913 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 37724152
NumberDataPoints #2
Data point attributes:
     -> jvm.memory.pool.name: Str(Survivor Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.585255913 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 0
Metric #7
Descriptor:
     -> Name: jvm.memory.used
     -> Description: Measure of memory used.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> jvm.memory.pool.name: Str(Compressed Class Space)
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 11004816
NumberDataPoints #1
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'non-profiled nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 5650048
NumberDataPoints #2
Data point attributes:
     -> jvm.memory.pool.name: Str(Metaspace)
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 83184904
NumberDataPoints #3
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'non-nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 1463808
NumberDataPoints #4
Data point attributes:
     -> jvm.memory.pool.name: Str(Eden Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 45076560
NumberDataPoints #5
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'profiled nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 15479936
NumberDataPoints #6
Data point attributes:
     -> jvm.memory.pool.name: Str(Tenured Gen)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 37724152
NumberDataPoints #7
Data point attributes:
     -> jvm.memory.pool.name: Str(Survivor Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.58369219 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 0
Metric #8
Descriptor:
     -> Name: jvm.cpu.count
     -> Description: Number of processors available to the Java virtual machine.
     -> Unit: {cpu}
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:17:56.284061517 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 1
Metric #9
Descriptor:
     -> Name: jvm.class.unloaded
     -> Description: Number of classes unloaded since JVM start.
     -> Unit: {class}
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:17:56.171743598 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 0
Metric #10
Descriptor:
     -> Name: jvm.memory.committed
     -> Description: Measure of memory committed.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> jvm.memory.pool.name: Str(Compressed Class Space)
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 11272192
NumberDataPoints #1
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'non-profiled nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 5701632
NumberDataPoints #2
Data point attributes:
     -> jvm.memory.pool.name: Str(Metaspace)
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 83820544
NumberDataPoints #3
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'non-nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 2555904
NumberDataPoints #4
Data point attributes:
     -> jvm.memory.pool.name: Str(Eden Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 214827008
NumberDataPoints #5
Data point attributes:
     -> jvm.memory.pool.name: Str(CodeHeap 'profiled nmethods')
     -> jvm.memory.type: Str(non_heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 15532032
NumberDataPoints #6
Data point attributes:
     -> jvm.memory.pool.name: Str(Tenured Gen)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 62873600
NumberDataPoints #7
Data point attributes:
     -> jvm.memory.pool.name: Str(Survivor Space)
     -> jvm.memory.type: Str(heap)
StartTimestamp: 2026-09-11 09:17:56.584346752 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Value: 26804224
Metric #11
Descriptor:
     -> Name: jvm.gc.duration
     -> Description: Duration of JVM garbage collection actions.
     -> Unit: s
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> jvm.gc.action: Str(end of minor GC)
     -> jvm.gc.name: Str(Copy)
StartTimestamp: 2026-09-11 09:17:58.779314233 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Count: 7
Sum: 1.079000
Min: 0.106000
Max: 0.304000
ExplicitBounds #0: 0.010000
ExplicitBounds #1: 0.100000
ExplicitBounds #2: 1.000000
ExplicitBounds #3: 10.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 7
Buckets #3, Count: 0
Buckets #4, Count: 0
HistogramDataPoints #1
Data point attributes:
     -> jvm.gc.action: Str(end of major GC)
     -> jvm.gc.name: Str(MarkSweepCompact)
StartTimestamp: 2026-09-11 09:18:06.99709607 +0000 UTC
Timestamp: 2026-09-11 10:03:40.948866061 +0000 UTC
Count: 3
Sum: 0.842000
Min: 0.130000
Max: 0.403000
ExplicitBounds #0: 0.010000
ExplicitBounds #1: 0.100000
ExplicitBounds #2: 1.000000
ExplicitBounds #3: 10.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 3
Buckets #3, Count: 0
Buckets #4, Count: 0
        {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics"}
2026-09-11T10:03:41.181Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 53}
2026-09-11T10:03:41.182Z        info    ResourceMetrics #0
Resource SchemaURL:
Resource attributes:
     -> k8s.container.name: Str(catalogue)
     -> k8s.deployment.name: Str(catalogue)
     -> k8s.namespace.name: Str(roboshop)
     -> k8s.node.name: Str(desktop-worker2)
     -> k8s.pod.name: Str(catalogue-5bcb5b9b49-x2fxx)
     -> k8s.replicaset.name: Str(catalogue-5bcb5b9b49)
     -> service.instance.id: Str(roboshop.catalogue-5bcb5b9b49-x2fxx.catalogue)
     -> service.namespace: Str(roboshop)
     -> service.version: Str(1.0.0)
     -> service.name: Str(catalogue)
     -> process.pid: Int(1)
     -> process.executable.name: Str(node)
     -> process.executable.path: Str(/usr/local/bin/node)
     -> process.command_args: Slice(["/usr/local/bin/node","/opt/server/server.js"])
     -> process.runtime.version: Str(18.19.1)
     -> process.runtime.name: Str(nodejs)
     -> process.runtime.description: Str(Node.js)
     -> process.command: Str(/opt/server/server.js)
     -> process.owner: Str(roboshop)
     -> os.type: Str(linux)
     -> os.version: Str(6.6.87.2-microsoft-standard-WSL2)
     -> host.name: Str(catalogue-5bcb5b9b49-x2fxx)
     -> host.arch: Str(amd64)
     -> telemetry.sdk.language: Str(nodejs)
     -> telemetry.sdk.name: Str(opentelemetry)
     -> telemetry.sdk.version: Str(2.9.0)
ScopeMetrics #0
ScopeMetrics SchemaURL:
InstrumentationScope @opentelemetry/instrumentation-http 0.220.0
Metric #0
Descriptor:
     -> Name: http.client.duration
     -> Description: Measures the duration of outbound HTTP requests.
     -> Unit: ms
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> http.method: Str(GET)
     -> net.peer.name: Str(169.254.169.254)
StartTimestamp: 2026-09-11 09:21:38.135 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Count: 1
Sum: 25.668065
Min: 25.668065
Max: 25.668065
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 1
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
HistogramDataPoints #1
Data point attributes:
     -> http.method: Str(GET)
     -> net.peer.name: Str(metadata.google.internal.)
StartTimestamp: 2026-09-11 09:21:38.179 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Count: 1
Sum: 62.296378
Min: 62.296378
Max: 62.296378
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 1
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
HistogramDataPoints #2
Data point attributes:
     -> http.method: Str(POST)
     -> net.peer.name: Str(opentelemetry-collector.opentelemetry.svc.cluster.local)
     -> net.peer.port: Int(4318)
     -> http.status_code: Int(200)
     -> http.flavor: Str(1.1)
StartTimestamp: 2026-09-11 09:21:42.15 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Count: 38
Sum: 899.927619
Min: 5.871870
Max: 261.634589
ExplicitBounds #0: 0.000000
ExplicitBounds #1: 5.000000
ExplicitBounds #2: 10.000000
ExplicitBounds #3: 25.000000
ExplicitBounds #4: 50.000000
ExplicitBounds #5: 75.000000
ExplicitBounds #6: 100.000000
ExplicitBounds #7: 250.000000
ExplicitBounds #8: 500.000000
ExplicitBounds #9: 750.000000
ExplicitBounds #10: 1000.000000
ExplicitBounds #11: 2500.000000
ExplicitBounds #12: 5000.000000
ExplicitBounds #13: 7500.000000
ExplicitBounds #14: 10000.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 17
Buckets #3, Count: 13
Buckets #4, Count: 5
Buckets #5, Count: 0
Buckets #6, Count: 2
Buckets #7, Count: 0
Buckets #8, Count: 1
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Buckets #15, Count: 0
ScopeMetrics #1
ScopeMetrics SchemaURL:
InstrumentationScope @opentelemetry/instrumentation-runtime-node 0.33.0
Metric #0
Descriptor:
     -> Name: nodejs.eventloop.utilization
     -> Description: Event loop utilization
     -> Unit: 1
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.005653
Metric #1
Descriptor:
     -> Name: nodejs.eventloop.time
     -> Description: Cumulative duration of time the event loop has been in each state.
     -> Unit: s
     -> DataType: Sum
     -> IsMonotonic: true
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> nodejs.eventloop.state: Str(active)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 15.783705
NumberDataPoints #1
Data point attributes:
     -> nodejs.eventloop.state: Str(idle)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 2262.548304
Metric #2
Descriptor:
     -> Name: nodejs.eventloop.delay.min
     -> Description: Event loop minimum delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.000743
Metric #3
Descriptor:
     -> Name: nodejs.eventloop.delay.max
     -> Description: Event loop maximum delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.030933
Metric #4
Descriptor:
     -> Name: nodejs.eventloop.delay.mean
     -> Description: Event loop mean delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.010251
Metric #5
Descriptor:
     -> Name: nodejs.eventloop.delay.stddev
     -> Description: Event loop standard deviation delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.000480
Metric #6
Descriptor:
     -> Name: nodejs.eventloop.delay.p50
     -> Description: Event loop 50 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.010215
Metric #7
Descriptor:
     -> Name: nodejs.eventloop.delay.p90
     -> Description: Event loop 90 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.010379
Metric #8
Descriptor:
     -> Name: nodejs.eventloop.delay.p99
     -> Description: Event loop 99 percentile delay.
     -> Unit: s
     -> DataType: Gauge
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.011043
Metric #9
Descriptor:
     -> Name: v8js.gc.duration
     -> Description: Garbage collection duration by kind, one of major, minor, incremental or weakcb.
     -> Unit: s
     -> DataType: Histogram
     -> AggregationTemporality: Cumulative
HistogramDataPoints #0
Data point attributes:
     -> v8js.gc.type: Str(minor)
StartTimestamp: 2026-09-11 09:21:37.202 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Count: 39
Sum: 0.489161
Min: 0.001311
Max: 0.106107
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 13
Buckets #1, Count: 7
Buckets #2, Count: 17
Buckets #3, Count: 1
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 1
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
HistogramDataPoints #1
Data point attributes:
     -> v8js.gc.type: Str(incremental)
StartTimestamp: 2026-09-11 09:21:37.579 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Count: 5
Sum: 0.009636
Min: 0.000004
Max: 0.008901
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 4
Buckets #1, Count: 1
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 0
Buckets #6, Count: 0
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
HistogramDataPoints #2
Data point attributes:
     -> v8js.gc.type: Str(major)
StartTimestamp: 2026-09-11 09:22:35.25 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Count: 2
Sum: 0.230786
Min: 0.099846
Max: 0.130940
ExplicitBounds #0: 0.005000
ExplicitBounds #1: 0.010000
ExplicitBounds #2: 0.025000
ExplicitBounds #3: 0.050000
ExplicitBounds #4: 0.075000
ExplicitBounds #5: 0.100000
ExplicitBounds #6: 0.250000
ExplicitBounds #7: 0.500000
ExplicitBounds #8: 0.750000
ExplicitBounds #9: 1.000000
ExplicitBounds #10: 2.500000
ExplicitBounds #11: 5.000000
ExplicitBounds #12: 7.500000
ExplicitBounds #13: 10.000000
Buckets #0, Count: 0
Buckets #1, Count: 0
Buckets #2, Count: 0
Buckets #3, Count: 0
Buckets #4, Count: 0
Buckets #5, Count: 1
Buckets #6, Count: 1
Buckets #7, Count: 0
Buckets #8, Count: 0
Buckets #9, Count: 0
Buckets #10, Count: 0
Buckets #11, Count: 0
Buckets #12, Count: 0
Buckets #13, Count: 0
Buckets #14, Count: 0
Metric #10
Descriptor:
     -> Name: v8js.memory.heap.limit
     -> Description: Maximum heap size allowed by the V8 engine, as set by --max-old-space-size or V8 defaults.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 2197815296.000000
Metric #11
Descriptor:
     -> Name: v8js.memory.heap.space.size
     -> Description: Total heap memory size pre-allocated for a heap space.
     -> Unit: By
     -> DataType: Sum
     -> IsMonotonic: false
     -> AggregationTemporality: Cumulative
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 29241344.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 2306048.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 1843200.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 3944448.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 1048576.000000
Metric #12
Descriptor:
     -> Name: v8js.memory.heap.used
     -> Description: Heap Memory size allocated.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 27405168.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 2152192.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 1161416.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 3861384.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 444592.000000
Metric #13
Descriptor:
     -> Name: v8js.memory.heap.space.available_size
     -> Description: Heap space available size.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 1278392.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 6400.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 646584.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 1030976.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 586384.000000
Metric #14
Descriptor:
     -> Name: v8js.memory.heap.space.physical_size
     -> Description: Committed size of a heap space.
     -> Unit: By
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.heap.space.name: Str(read_only_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.heap.space.name: Str(old_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 29241344.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.heap.space.name: Str(code_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 2195456.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.heap.space.name: Str(map_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 1589248.000000
NumberDataPoints #4
Data point attributes:
     -> v8js.heap.space.name: Str(large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 3944448.000000
NumberDataPoints #5
Data point attributes:
     -> v8js.heap.space.name: Str(code_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.000000
NumberDataPoints #6
Data point attributes:
     -> v8js.heap.space.name: Str(new_large_object_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 0.000000
NumberDataPoints #7
Data point attributes:
     -> v8js.heap.space.name: Str(new_space)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 532480.000000
Metric #15
Descriptor:
     -> Name: v8js.resource.active
     -> Description: Count of the active resources that are currently keeping the event loop alive.
     -> Unit: {resource}
     -> DataType: Gauge
NumberDataPoints #0
Data point attributes:
     -> v8js.resource.type: Str(PipeWrap)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 2.000000
NumberDataPoints #1
Data point attributes:
     -> v8js.resource.type: Str(TCPSocketWrap)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 1.000000
NumberDataPoints #2
Data point attributes:
     -> v8js.resource.type: Str(TCPServerWrap)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 1.000000
NumberDataPoints #3
Data point attributes:
     -> v8js.resource.type: Str(Timeout)
StartTimestamp: 2026-09-11 09:22:36.558 +0000 UTC
Timestamp: 2026-09-11 10:03:41.014 +0000 UTC
Value: 5.000000
        {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics"}
2026-09-11T10:03:44.151Z        info    Traces  {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "traces", "resource spans": 1, "spans": 160}
2026-09-11T10:03:44.162Z        info    ResourceSpans #0
Resource SchemaURL:
Resource attributes:
     -> k8s.container.name: Str(user)
     -> k8s.deployment.name: Str(user)
     -> k8s.namespace.name: Str(roboshop)
     -> k8s.node.name: Str(desktop-worker)
     -> k8s.pod.name: Str(user-74bcc7d99c-jw4sg)
     -> k8s.replicaset.name: Str(user-74bcc7d99c)
     -> service.instance.id: Str(roboshop.user-74bcc7d99c-jw4sg.user)
     -> service.namespace: Str(roboshop)
     -> service.version: Str(1.0.0)
     -> service.name: Str(user)
     -> process.pid: Int(1)
     -> process.executable.name: Str(node)
     -> process.executable.path: Str(/usr/local/bin/node)
     -> process.command_args: Slice(["/usr/local/bin/node","/opt/server/server.js"])
     -> process.runtime.version: Str(18.19.1)
     -> process.runtime.name: Str(nodejs)
     -> process.runtime.description: Str(Node.js)
     -> process.command: Str(/opt/server/server.js)
     -> process.owner: Str(roboshop)
     -> os.type: Str(linux)
     -> os.version: Str(6.6.87.2-microsoft-standard-WSL2)
     -> host.name: Str(user-74bcc7d99c-jw4sg)
     -> host.arch: Str(amd64)
     -> telemetry.sdk.language: Str(nodejs)
     -> telemetry.sdk.name: Str(opentelemetry)
     -> telemetry.sdk.version: Str(2.9.0)
ScopeSpans #0
ScopeSpans SchemaURL:
InstrumentationScope @opentelemetry/instrumentation-express 0.68.0
Span #0
    Trace ID       : 982bc53cc62a6622200480fce10c4e0e
    Parent ID      : 495e85534f5a3ffe
    ID             : 43bc63058efa3658
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:38.988 +0000 UTC
    End time       : 2026-09-11 10:03:38.988445873 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #1
    Trace ID       : 982bc53cc62a6622200480fce10c4e0e
    Parent ID      : 495e85534f5a3ffe
    ID             : 450205100df3c38c
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:38.989 +0000 UTC
    End time       : 2026-09-11 10:03:38.989078173 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #2
    Trace ID       : 982bc53cc62a6622200480fce10c4e0e
    Parent ID      : 495e85534f5a3ffe
    ID             : 13b840b6d10a359e
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:38.989 +0000 UTC
    End time       : 2026-09-11 10:03:38.989232802 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #3
    Trace ID       : 982bc53cc62a6622200480fce10c4e0e
    Parent ID      : 495e85534f5a3ffe
    ID             : f8b21874e6f74d9e
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:38.989 +0000 UTC
    End time       : 2026-09-11 10:03:38.989037299 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #4
    Trace ID       : 982bc53cc62a6622200480fce10c4e0e
    Parent ID      : 495e85534f5a3ffe
    ID             : dd1a7786614a86b5
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:38.989 +0000 UTC
    End time       : 2026-09-11 10:03:38.989030865 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #5
    Trace ID       : 982bc53cc62a6622200480fce10c4e0e
    Parent ID      : 495e85534f5a3ffe
    ID             : 3e052f10987550ff
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:38.989 +0000 UTC
    End time       : 2026-09-11 10:03:38.989012404 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #6
    Trace ID       : 982bc53cc62a6622200480fce10c4e0e
    Parent ID      : 495e85534f5a3ffe
    ID             : 18e3897d4b851b96
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:38.989 +0000 UTC
    End time       : 2026-09-11 10:03:38.99748967 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #7
    Trace ID       : 5f94c6edb8cd0878ed7a2a14b025e7cb
    Parent ID      : f21d2d42db7412c5
    ID             : 3e90f0c7f699e4f0
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.01 +0000 UTC
    End time       : 2026-09-11 10:03:39.010043212 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #8
    Trace ID       : 5f94c6edb8cd0878ed7a2a14b025e7cb
    Parent ID      : f21d2d42db7412c5
    ID             : c233281495e37f42
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.01 +0000 UTC
    End time       : 2026-09-11 10:03:39.010056623 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #9
    Trace ID       : 5f94c6edb8cd0878ed7a2a14b025e7cb
    Parent ID      : f21d2d42db7412c5
    ID             : 76fd84422522cf8c
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.01 +0000 UTC
    End time       : 2026-09-11 10:03:39.010165981 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #10
    Trace ID       : 5f94c6edb8cd0878ed7a2a14b025e7cb
    Parent ID      : f21d2d42db7412c5
    ID             : 47f64c28b132a7a7
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.01 +0000 UTC
    End time       : 2026-09-11 10:03:39.010029923 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #11
    Trace ID       : 5f94c6edb8cd0878ed7a2a14b025e7cb
    Parent ID      : f21d2d42db7412c5
    ID             : 63478f2b6993d177
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.01 +0000 UTC
    End time       : 2026-09-11 10:03:39.010026565 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #12
    Trace ID       : 5f94c6edb8cd0878ed7a2a14b025e7cb
    Parent ID      : f21d2d42db7412c5
    ID             : 82536511dd5c6a6d
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.01 +0000 UTC
    End time       : 2026-09-11 10:03:39.010017836 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #13
    Trace ID       : 5f94c6edb8cd0878ed7a2a14b025e7cb
    Parent ID      : f21d2d42db7412c5
    ID             : faef4b4bee9bab92
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.01 +0000 UTC
    End time       : 2026-09-11 10:03:39.011153282 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #14
    Trace ID       : 39d0826de7e148e4faf578499a96050f
    Parent ID      : a361db6eac2b8fc3
    ID             : d2547f64ea135745
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.023 +0000 UTC
    End time       : 2026-09-11 10:03:39.023118844 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #15
    Trace ID       : 39d0826de7e148e4faf578499a96050f
    Parent ID      : a361db6eac2b8fc3
    ID             : ed6aebaa728baeeb
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.023 +0000 UTC
    End time       : 2026-09-11 10:03:39.023064799 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #16
    Trace ID       : 39d0826de7e148e4faf578499a96050f
    Parent ID      : a361db6eac2b8fc3
    ID             : 9c1f9a073d6e51a7
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.023 +0000 UTC
    End time       : 2026-09-11 10:03:39.02312941 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #17
    Trace ID       : 39d0826de7e148e4faf578499a96050f
    Parent ID      : a361db6eac2b8fc3
    ID             : 85751648e41096b8
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.023 +0000 UTC
    End time       : 2026-09-11 10:03:39.023030753 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #18
    Trace ID       : 39d0826de7e148e4faf578499a96050f
    Parent ID      : a361db6eac2b8fc3
    ID             : 5d10bc7819067540
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.024 +0000 UTC
    End time       : 2026-09-11 10:03:39.024116154 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #19
    Trace ID       : 39d0826de7e148e4faf578499a96050f
    Parent ID      : a361db6eac2b8fc3
    ID             : baef27fd78bfb1b6
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.024 +0000 UTC
    End time       : 2026-09-11 10:03:39.024030097 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #20
    Trace ID       : 39d0826de7e148e4faf578499a96050f
    Parent ID      : a361db6eac2b8fc3
    ID             : ca4e20108748d26b
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.024 +0000 UTC
    End time       : 2026-09-11 10:03:39.025195127 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #21
    Trace ID       : 3f2303934b742e9cf6d03d05b019e61b
    Parent ID      : cce375033a7e34e3
    ID             : 72b25068a9c610d6
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.04 +0000 UTC
    End time       : 2026-09-11 10:03:39.040145383 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #22
    Trace ID       : 3f2303934b742e9cf6d03d05b019e61b
    Parent ID      : cce375033a7e34e3
    ID             : 61718b747a0cd765
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.04 +0000 UTC
    End time       : 2026-09-11 10:03:39.040189004 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #23
    Trace ID       : 3f2303934b742e9cf6d03d05b019e61b
    Parent ID      : cce375033a7e34e3
    ID             : f07da9d643e0b393
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.041 +0000 UTC
    End time       : 2026-09-11 10:03:39.041383499 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #24
    Trace ID       : 3f2303934b742e9cf6d03d05b019e61b
    Parent ID      : cce375033a7e34e3
    ID             : 09b2437471bfe677
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.041 +0000 UTC
    End time       : 2026-09-11 10:03:39.041162474 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #25
    Trace ID       : 3f2303934b742e9cf6d03d05b019e61b
    Parent ID      : cce375033a7e34e3
    ID             : 1d43d0cab49ff1b0
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.042 +0000 UTC
    End time       : 2026-09-11 10:03:39.042119851 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #26
    Trace ID       : 3f2303934b742e9cf6d03d05b019e61b
    Parent ID      : cce375033a7e34e3
    ID             : 150c1d7911a9e760
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.042 +0000 UTC
    End time       : 2026-09-11 10:03:39.042107978 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #27
    Trace ID       : 3f2303934b742e9cf6d03d05b019e61b
    Parent ID      : cce375033a7e34e3
    ID             : 6ff0a4d6be420f80
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.042 +0000 UTC
    End time       : 2026-09-11 10:03:39.04410372 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #28
    Trace ID       : f4c2f396762964196b8effd2b731d155
    Parent ID      : b1ebfadc8e3598c6
    ID             : b35caadf4f59e696
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.054 +0000 UTC
    End time       : 2026-09-11 10:03:39.054055432 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #29
    Trace ID       : f4c2f396762964196b8effd2b731d155
    Parent ID      : b1ebfadc8e3598c6
    ID             : 3376ed9e35642c92
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.055 +0000 UTC
    End time       : 2026-09-11 10:03:39.055055293 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #30
    Trace ID       : f4c2f396762964196b8effd2b731d155
    Parent ID      : b1ebfadc8e3598c6
    ID             : e183c3cf82cde0ac
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.055 +0000 UTC
    End time       : 2026-09-11 10:03:39.05571202 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #31
    Trace ID       : f4c2f396762964196b8effd2b731d155
    Parent ID      : b1ebfadc8e3598c6
    ID             : bce1f3bf2687bc31
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.056 +0000 UTC
    End time       : 2026-09-11 10:03:39.05605666 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #32
    Trace ID       : f4c2f396762964196b8effd2b731d155
    Parent ID      : b1ebfadc8e3598c6
    ID             : 365d0958c761a5af
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.056 +0000 UTC
    End time       : 2026-09-11 10:03:39.056041864 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #33
    Trace ID       : f4c2f396762964196b8effd2b731d155
    Parent ID      : b1ebfadc8e3598c6
    ID             : 34fea58b2cfafdbe
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.056 +0000 UTC
    End time       : 2026-09-11 10:03:39.056014242 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #34
    Trace ID       : f4c2f396762964196b8effd2b731d155
    Parent ID      : b1ebfadc8e3598c6
    ID             : 936a3116253c2535
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.056 +0000 UTC
    End time       : 2026-09-11 10:03:39.056971492 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #35
    Trace ID       : b343b7c23726f8474f2cff96167a1edc
    Parent ID      : f5fd9887a7a0fcee
    ID             : 4c04602a92de2191
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.067 +0000 UTC
    End time       : 2026-09-11 10:03:39.067052396 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #36
    Trace ID       : b343b7c23726f8474f2cff96167a1edc
    Parent ID      : f5fd9887a7a0fcee
    ID             : 34c489d4894e6e5e
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.067 +0000 UTC
    End time       : 2026-09-11 10:03:39.067066831 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #37
    Trace ID       : b343b7c23726f8474f2cff96167a1edc
    Parent ID      : f5fd9887a7a0fcee
    ID             : 43349dfd5d5b172e
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.068 +0000 UTC
    End time       : 2026-09-11 10:03:39.068163662 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #38
    Trace ID       : b343b7c23726f8474f2cff96167a1edc
    Parent ID      : f5fd9887a7a0fcee
    ID             : 784b7eccb88d733b
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.068 +0000 UTC
    End time       : 2026-09-11 10:03:39.068049415 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #39
    Trace ID       : b343b7c23726f8474f2cff96167a1edc
    Parent ID      : f5fd9887a7a0fcee
    ID             : daf49e34c2adb541
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.068 +0000 UTC
    End time       : 2026-09-11 10:03:39.068043136 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #40
    Trace ID       : b343b7c23726f8474f2cff96167a1edc
    Parent ID      : f5fd9887a7a0fcee
    ID             : a3571176ef49511d
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.068 +0000 UTC
    End time       : 2026-09-11 10:03:39.068017768 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #41
    Trace ID       : b343b7c23726f8474f2cff96167a1edc
    Parent ID      : f5fd9887a7a0fcee
    ID             : 7104687a6f7fa7e2
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.068 +0000 UTC
    End time       : 2026-09-11 10:03:39.069327939 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #42
    Trace ID       : 2cc785a88f27dcc9eff80e98f236b925
    Parent ID      : 3f9ac443c705b12f
    ID             : 7fae2ac4aba7d44c
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.081 +0000 UTC
    End time       : 2026-09-11 10:03:39.081152255 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #43
    Trace ID       : 2cc785a88f27dcc9eff80e98f236b925
    Parent ID      : 3f9ac443c705b12f
    ID             : 7e1f55545f333715
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.082 +0000 UTC
    End time       : 2026-09-11 10:03:39.082138701 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #44
    Trace ID       : 2cc785a88f27dcc9eff80e98f236b925
    Parent ID      : 3f9ac443c705b12f
    ID             : b7ebb92df48b4438
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.082 +0000 UTC
    End time       : 2026-09-11 10:03:39.082360609 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #45
    Trace ID       : 2cc785a88f27dcc9eff80e98f236b925
    Parent ID      : 3f9ac443c705b12f
    ID             : 962a27aa300a2aa5
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.083 +0000 UTC
    End time       : 2026-09-11 10:03:39.083338711 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #46
    Trace ID       : 2cc785a88f27dcc9eff80e98f236b925
    Parent ID      : 3f9ac443c705b12f
    ID             : c009dccc464e196c
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.083 +0000 UTC
    End time       : 2026-09-11 10:03:39.083178636 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #47
    Trace ID       : 2cc785a88f27dcc9eff80e98f236b925
    Parent ID      : 3f9ac443c705b12f
    ID             : ff2df4f2dfeceecd
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.083 +0000 UTC
    End time       : 2026-09-11 10:03:39.083063843 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #48
    Trace ID       : 2cc785a88f27dcc9eff80e98f236b925
    Parent ID      : 3f9ac443c705b12f
    ID             : 3047202106dee5d2
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.084 +0000 UTC
    End time       : 2026-09-11 10:03:39.085207837 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #49
    Trace ID       : 6fa88befd9d3e9344566ffa9c2b69c61
    Parent ID      : b46f9b052c5ba53d
    ID             : 2c09db57be5674a1
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.097 +0000 UTC
    End time       : 2026-09-11 10:03:39.097070509 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #50
    Trace ID       : 6fa88befd9d3e9344566ffa9c2b69c61
    Parent ID      : b46f9b052c5ba53d
    ID             : a1e72a67c5a471b4
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.097 +0000 UTC
    End time       : 2026-09-11 10:03:39.097074865 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #51
    Trace ID       : 6fa88befd9d3e9344566ffa9c2b69c61
    Parent ID      : b46f9b052c5ba53d
    ID             : e7917b0765ffe28f
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.097 +0000 UTC
    End time       : 2026-09-11 10:03:39.097169867 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #52
    Trace ID       : 6fa88befd9d3e9344566ffa9c2b69c61
    Parent ID      : b46f9b052c5ba53d
    ID             : d06126a422b3c92e
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.098 +0000 UTC
    End time       : 2026-09-11 10:03:39.098056159 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #53
    Trace ID       : 6fa88befd9d3e9344566ffa9c2b69c61
    Parent ID      : b46f9b052c5ba53d
    ID             : 9fe1fcda741a3792
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.098 +0000 UTC
    End time       : 2026-09-11 10:03:39.098066553 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #54
    Trace ID       : 6fa88befd9d3e9344566ffa9c2b69c61
    Parent ID      : b46f9b052c5ba53d
    ID             : afe164880962a7a5
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.098 +0000 UTC
    End time       : 2026-09-11 10:03:39.098021374 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #55
    Trace ID       : 6fa88befd9d3e9344566ffa9c2b69c61
    Parent ID      : b46f9b052c5ba53d
    ID             : 9dad1c765d7d6393
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.098 +0000 UTC
    End time       : 2026-09-11 10:03:39.101322606 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #56
    Trace ID       : bb5dab93ef5adea6c7a77527f2ab6bb4
    Parent ID      : 75eecb6a0701085f
    ID             : 9a011d5e55d6ca7a
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.113 +0000 UTC
    End time       : 2026-09-11 10:03:39.113101509 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #57
    Trace ID       : bb5dab93ef5adea6c7a77527f2ab6bb4
    Parent ID      : 75eecb6a0701085f
    ID             : 86d88e92002e99a6
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.113 +0000 UTC
    End time       : 2026-09-11 10:03:39.113207813 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #58
    Trace ID       : bb5dab93ef5adea6c7a77527f2ab6bb4
    Parent ID      : 75eecb6a0701085f
    ID             : 84d49e04084dd719
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.114 +0000 UTC
    End time       : 2026-09-11 10:03:39.114175619 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #59
    Trace ID       : bb5dab93ef5adea6c7a77527f2ab6bb4
    Parent ID      : 75eecb6a0701085f
    ID             : 753ef9f33a18b88e
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.114 +0000 UTC
    End time       : 2026-09-11 10:03:39.114042278 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #60
    Trace ID       : bb5dab93ef5adea6c7a77527f2ab6bb4
    Parent ID      : 75eecb6a0701085f
    ID             : 8201579a98eb8e41
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.114 +0000 UTC
    End time       : 2026-09-11 10:03:39.114035107 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #61
    Trace ID       : bb5dab93ef5adea6c7a77527f2ab6bb4
    Parent ID      : 75eecb6a0701085f
    ID             : a47d8b7db9519f0b
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.114 +0000 UTC
    End time       : 2026-09-11 10:03:39.114038776 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #62
    Trace ID       : bb5dab93ef5adea6c7a77527f2ab6bb4
    Parent ID      : 75eecb6a0701085f
    ID             : 85bfc1315024bcd9
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.114 +0000 UTC
    End time       : 2026-09-11 10:03:39.1156728 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #63
    Trace ID       : e1839b2331956147721edd4429496cd5
    Parent ID      : 03d3ebac7387e040
    ID             : 9b0b4380a438a42c
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.129 +0000 UTC
    End time       : 2026-09-11 10:03:39.129119392 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #64
    Trace ID       : e1839b2331956147721edd4429496cd5
    Parent ID      : 03d3ebac7387e040
    ID             : 032466786b8ee799
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.129 +0000 UTC
    End time       : 2026-09-11 10:03:39.129079175 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #65
    Trace ID       : e1839b2331956147721edd4429496cd5
    Parent ID      : 03d3ebac7387e040
    ID             : 03c12ad6f335af36
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.129 +0000 UTC
    End time       : 2026-09-11 10:03:39.129180682 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #66
    Trace ID       : e1839b2331956147721edd4429496cd5
    Parent ID      : 03d3ebac7387e040
    ID             : 91e1e8c27d54e63f
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.129 +0000 UTC
    End time       : 2026-09-11 10:03:39.129038851 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #67
    Trace ID       : e1839b2331956147721edd4429496cd5
    Parent ID      : 03d3ebac7387e040
    ID             : 3bfacfae1d26c6b7
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.13 +0000 UTC
    End time       : 2026-09-11 10:03:39.130034594 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #68
    Trace ID       : e1839b2331956147721edd4429496cd5
    Parent ID      : 03d3ebac7387e040
    ID             : d81365fd5da06731
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.13 +0000 UTC
    End time       : 2026-09-11 10:03:39.130038246 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #69
    Trace ID       : e1839b2331956147721edd4429496cd5
    Parent ID      : 03d3ebac7387e040
    ID             : 1520152167f1f25e
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.13 +0000 UTC
    End time       : 2026-09-11 10:03:39.131859498 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #70
    Trace ID       : 65c651667b20e1ad735f84db436cf496
    Parent ID      : 1eecd2d8c8506d62
    ID             : 831509665cb23339
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.145 +0000 UTC
    End time       : 2026-09-11 10:03:39.145163615 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #71
    Trace ID       : 65c651667b20e1ad735f84db436cf496
    Parent ID      : 1eecd2d8c8506d62
    ID             : d68dec806fdc1019
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.146 +0000 UTC
    End time       : 2026-09-11 10:03:39.146304852 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #72
    Trace ID       : 65c651667b20e1ad735f84db436cf496
    Parent ID      : 1eecd2d8c8506d62
    ID             : c8ae00e3b1dae22d
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.146 +0000 UTC
    End time       : 2026-09-11 10:03:39.146550206 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #73
    Trace ID       : 65c651667b20e1ad735f84db436cf496
    Parent ID      : 1eecd2d8c8506d62
    ID             : abe095a5b8862d45
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.147 +0000 UTC
    End time       : 2026-09-11 10:03:39.147092178 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #74
    Trace ID       : 65c651667b20e1ad735f84db436cf496
    Parent ID      : 1eecd2d8c8506d62
    ID             : df29b798b069c1af
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.147 +0000 UTC
    End time       : 2026-09-11 10:03:39.147059346 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #75
    Trace ID       : 65c651667b20e1ad735f84db436cf496
    Parent ID      : 1eecd2d8c8506d62
    ID             : f6c37933ac7cd9d5
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.147 +0000 UTC
    End time       : 2026-09-11 10:03:39.147018378 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #76
    Trace ID       : 65c651667b20e1ad735f84db436cf496
    Parent ID      : 1eecd2d8c8506d62
    ID             : 1447089d1fd1ff4f
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.147 +0000 UTC
    End time       : 2026-09-11 10:03:39.148317219 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #77
    Trace ID       : 0fdd9f9dbd38cdbda3d7ec2232c95e58
    Parent ID      : ad423d4d6c1e39bd
    ID             : d75ab88c14c57be2
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.163 +0000 UTC
    End time       : 2026-09-11 10:03:39.163078864 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #78
    Trace ID       : 0fdd9f9dbd38cdbda3d7ec2232c95e58
    Parent ID      : ad423d4d6c1e39bd
    ID             : 68f0c9563e07bc84
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.163 +0000 UTC
    End time       : 2026-09-11 10:03:39.163078728 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #79
    Trace ID       : 0fdd9f9dbd38cdbda3d7ec2232c95e58
    Parent ID      : ad423d4d6c1e39bd
    ID             : fe011b514f0c6b1e
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.163 +0000 UTC
    End time       : 2026-09-11 10:03:39.163157915 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #80
    Trace ID       : 0fdd9f9dbd38cdbda3d7ec2232c95e58
    Parent ID      : ad423d4d6c1e39bd
    ID             : b86cfa1257886f41
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.163 +0000 UTC
    End time       : 2026-09-11 10:03:39.163038613 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #81
    Trace ID       : 0fdd9f9dbd38cdbda3d7ec2232c95e58
    Parent ID      : ad423d4d6c1e39bd
    ID             : 5c0695676ba662c0
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.164 +0000 UTC
    End time       : 2026-09-11 10:03:39.164034507 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #82
    Trace ID       : 0fdd9f9dbd38cdbda3d7ec2232c95e58
    Parent ID      : ad423d4d6c1e39bd
    ID             : fed05192c4bb26a3
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.164 +0000 UTC
    End time       : 2026-09-11 10:03:39.164030248 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #83
    Trace ID       : 0fdd9f9dbd38cdbda3d7ec2232c95e58
    Parent ID      : ad423d4d6c1e39bd
    ID             : b384a1132131bcac
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.164 +0000 UTC
    End time       : 2026-09-11 10:03:39.165371347 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #84
    Trace ID       : 6494f7705df631569f0d4b4c7d95437e
    Parent ID      : 4efb53b89250cdfb
    ID             : b7e880aabb10a6e2
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.178 +0000 UTC
    End time       : 2026-09-11 10:03:39.178080804 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #85
    Trace ID       : 6494f7705df631569f0d4b4c7d95437e
    Parent ID      : 4efb53b89250cdfb
    ID             : c5624b93164baed0
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.178 +0000 UTC
    End time       : 2026-09-11 10:03:39.178073865 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #86
    Trace ID       : 6494f7705df631569f0d4b4c7d95437e
    Parent ID      : 4efb53b89250cdfb
    ID             : 85491aac2fd1c379
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.179 +0000 UTC
    End time       : 2026-09-11 10:03:39.179366965 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #87
    Trace ID       : 6494f7705df631569f0d4b4c7d95437e
    Parent ID      : 4efb53b89250cdfb
    ID             : e33038939849b8a9
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.179 +0000 UTC
    End time       : 2026-09-11 10:03:39.179061022 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #88
    Trace ID       : 6494f7705df631569f0d4b4c7d95437e
    Parent ID      : 4efb53b89250cdfb
    ID             : bd29338c0dcd3a51
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.179 +0000 UTC
    End time       : 2026-09-11 10:03:39.17904385 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #89
    Trace ID       : 6494f7705df631569f0d4b4c7d95437e
    Parent ID      : 4efb53b89250cdfb
    ID             : b47970092707d13d
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.179 +0000 UTC
    End time       : 2026-09-11 10:03:39.17902199 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #90
    Trace ID       : 6494f7705df631569f0d4b4c7d95437e
    Parent ID      : 4efb53b89250cdfb
    ID             : 871794286ff5139f
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.179 +0000 UTC
    End time       : 2026-09-11 10:03:39.180389518 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #91
    Trace ID       : af404f5da7c027039efa4d2c466dbcfe
    Parent ID      : 889edcc0891bfcdc
    ID             : 6a86a36416889474
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.195 +0000 UTC
    End time       : 2026-09-11 10:03:39.195062305 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #92
    Trace ID       : af404f5da7c027039efa4d2c466dbcfe
    Parent ID      : 889edcc0891bfcdc
    ID             : 4cbf3c61c2a08d31
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.196 +0000 UTC
    End time       : 2026-09-11 10:03:39.196074355 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #93
    Trace ID       : af404f5da7c027039efa4d2c466dbcfe
    Parent ID      : 889edcc0891bfcdc
    ID             : 26cc8151b70586a6
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.196 +0000 UTC
    End time       : 2026-09-11 10:03:39.196169684 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #94
    Trace ID       : af404f5da7c027039efa4d2c466dbcfe
    Parent ID      : 889edcc0891bfcdc
    ID             : 2b47186987f96bbe
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.196 +0000 UTC
    End time       : 2026-09-11 10:03:39.196038153 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #95
    Trace ID       : af404f5da7c027039efa4d2c466dbcfe
    Parent ID      : 889edcc0891bfcdc
    ID             : e62218959ea5c1fe
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.196 +0000 UTC
    End time       : 2026-09-11 10:03:39.196036074 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #96
    Trace ID       : af404f5da7c027039efa4d2c466dbcfe
    Parent ID      : 889edcc0891bfcdc
    ID             : 8daf21eaf0ffe7c7
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.196 +0000 UTC
    End time       : 2026-09-11 10:03:39.196019504 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #97
    Trace ID       : af404f5da7c027039efa4d2c466dbcfe
    Parent ID      : 889edcc0891bfcdc
    ID             : 2a9f20af98ac4c85
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.196 +0000 UTC
    End time       : 2026-09-11 10:03:39.197836639 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #98
    Trace ID       : 38daff0754f7f7e36f2906061e20a04b
    Parent ID      : 26f147299db1ca47
    ID             : 99704dd05241bdaa
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.212 +0000 UTC
    End time       : 2026-09-11 10:03:39.212062177 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #99
    Trace ID       : 38daff0754f7f7e36f2906061e20a04b
    Parent ID      : 26f147299db1ca47
    ID             : 6b079f4012778056
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.213 +0000 UTC
    End time       : 2026-09-11 10:03:39.213100768 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #100
    Trace ID       : 38daff0754f7f7e36f2906061e20a04b
    Parent ID      : 26f147299db1ca47
    ID             : a0b64db3900fe645
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.213 +0000 UTC
    End time       : 2026-09-11 10:03:39.213198583 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #101
    Trace ID       : 38daff0754f7f7e36f2906061e20a04b
    Parent ID      : 26f147299db1ca47
    ID             : 3208300543d963c3
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.213 +0000 UTC
    End time       : 2026-09-11 10:03:39.213053427 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #102
    Trace ID       : 38daff0754f7f7e36f2906061e20a04b
    Parent ID      : 26f147299db1ca47
    ID             : 82d06fe6624aa146
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.213 +0000 UTC
    End time       : 2026-09-11 10:03:39.21304093 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #103
    Trace ID       : 38daff0754f7f7e36f2906061e20a04b
    Parent ID      : 26f147299db1ca47
    ID             : a88c5e904589db1e
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.213 +0000 UTC
    End time       : 2026-09-11 10:03:39.213016803 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #104
    Trace ID       : 38daff0754f7f7e36f2906061e20a04b
    Parent ID      : 26f147299db1ca47
    ID             : 8570aed0b631f8ed
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.213 +0000 UTC
    End time       : 2026-09-11 10:03:39.2242892 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #105
    Trace ID       : 711cdaa2ebdfe119a7241c7b12c316bc
    Parent ID      : 36506c0a1638a12c
    ID             : 5a7919df6b0a0647
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.231 +0000 UTC
    End time       : 2026-09-11 10:03:39.231108729 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #106
    Trace ID       : 711cdaa2ebdfe119a7241c7b12c316bc
    Parent ID      : 36506c0a1638a12c
    ID             : eb2fadb43a7def74
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.231 +0000 UTC
    End time       : 2026-09-11 10:03:39.231087522 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #107
    Trace ID       : 711cdaa2ebdfe119a7241c7b12c316bc
    Parent ID      : 36506c0a1638a12c
    ID             : f5c3e0491edd6da2
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.231 +0000 UTC
    End time       : 2026-09-11 10:03:39.231186254 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #108
    Trace ID       : 711cdaa2ebdfe119a7241c7b12c316bc
    Parent ID      : 36506c0a1638a12c
    ID             : cca3824f142df18c
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.231 +0000 UTC
    End time       : 2026-09-11 10:03:39.231042764 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #109
    Trace ID       : 711cdaa2ebdfe119a7241c7b12c316bc
    Parent ID      : 36506c0a1638a12c
    ID             : 9b2e0c87baf8b46b
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.232 +0000 UTC
    End time       : 2026-09-11 10:03:39.232065315 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #110
    Trace ID       : 711cdaa2ebdfe119a7241c7b12c316bc
    Parent ID      : 36506c0a1638a12c
    ID             : b888e932b05bdd64
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.232 +0000 UTC
    End time       : 2026-09-11 10:03:39.232041622 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #111
    Trace ID       : 711cdaa2ebdfe119a7241c7b12c316bc
    Parent ID      : 36506c0a1638a12c
    ID             : a3f38f56ee5a27fb
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.232 +0000 UTC
    End time       : 2026-09-11 10:03:39.241282819 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #112
    Trace ID       : ac15c27b670b6f5e7a68936201a2ee39
    Parent ID      : f5ebd970640378ff
    ID             : be52f58bbaeaea0a
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.256 +0000 UTC
    End time       : 2026-09-11 10:03:39.25606537 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #113
    Trace ID       : ac15c27b670b6f5e7a68936201a2ee39
    Parent ID      : f5ebd970640378ff
    ID             : 86de27043e2a8e04
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.256 +0000 UTC
    End time       : 2026-09-11 10:03:39.256075937 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #114
    Trace ID       : ac15c27b670b6f5e7a68936201a2ee39
    Parent ID      : f5ebd970640378ff
    ID             : a11e5e333929034c
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.256 +0000 UTC
    End time       : 2026-09-11 10:03:39.256179582 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #115
    Trace ID       : ac15c27b670b6f5e7a68936201a2ee39
    Parent ID      : f5ebd970640378ff
    ID             : 9bf61c07ed981c9e
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.257 +0000 UTC
    End time       : 2026-09-11 10:03:39.257042822 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #116
    Trace ID       : ac15c27b670b6f5e7a68936201a2ee39
    Parent ID      : f5ebd970640378ff
    ID             : 2332c2aab5e910f6
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.257 +0000 UTC
    End time       : 2026-09-11 10:03:39.257046419 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #117
    Trace ID       : ac15c27b670b6f5e7a68936201a2ee39
    Parent ID      : f5ebd970640378ff
    ID             : 6085d09f417bf138
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.257 +0000 UTC
    End time       : 2026-09-11 10:03:39.257016784 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #118
    Trace ID       : ac15c27b670b6f5e7a68936201a2ee39
    Parent ID      : f5ebd970640378ff
    ID             : 3cbdcc3a408fbc7a
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.257 +0000 UTC
    End time       : 2026-09-11 10:03:39.258313129 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #119
    Trace ID       : 79b5ff4b7418823f4d6834819ba6d945
    Parent ID      : ce132964123cf739
    ID             : 86d5c0a0a7ee8575
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.277 +0000 UTC
    End time       : 2026-09-11 10:03:39.277059586 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #120
    Trace ID       : 79b5ff4b7418823f4d6834819ba6d945
    Parent ID      : ce132964123cf739
    ID             : fbc349b5c4597f30
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.278 +0000 UTC
    End time       : 2026-09-11 10:03:39.278069797 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #121
    Trace ID       : 79b5ff4b7418823f4d6834819ba6d945
    Parent ID      : ce132964123cf739
    ID             : d522d9d5a0608362
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.278 +0000 UTC
    End time       : 2026-09-11 10:03:39.278164307 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #122
    Trace ID       : 79b5ff4b7418823f4d6834819ba6d945
    Parent ID      : ce132964123cf739
    ID             : 400be26a58554970
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.278 +0000 UTC
    End time       : 2026-09-11 10:03:39.278041117 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #123
    Trace ID       : 79b5ff4b7418823f4d6834819ba6d945
    Parent ID      : ce132964123cf739
    ID             : 6f749cee9947fb5c
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.278 +0000 UTC
    End time       : 2026-09-11 10:03:39.278036636 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #124
    Trace ID       : 79b5ff4b7418823f4d6834819ba6d945
    Parent ID      : ce132964123cf739
    ID             : efb94e331580cac6
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.278 +0000 UTC
    End time       : 2026-09-11 10:03:39.27801974 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #125
    Trace ID       : 79b5ff4b7418823f4d6834819ba6d945
    Parent ID      : ce132964123cf739
    ID             : 071e4dfacf91ebba
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.278 +0000 UTC
    End time       : 2026-09-11 10:03:39.279580715 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #126
    Trace ID       : 12146c9bc627e90ed23bb80cd745b586
    Parent ID      : 0c972388534de520
    ID             : 5465c0a26773c5c8
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.295 +0000 UTC
    End time       : 2026-09-11 10:03:39.295087193 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #127
    Trace ID       : 12146c9bc627e90ed23bb80cd745b586
    Parent ID      : 0c972388534de520
    ID             : 7e52649a96665f1e
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.295 +0000 UTC
    End time       : 2026-09-11 10:03:39.295108337 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #128
    Trace ID       : 12146c9bc627e90ed23bb80cd745b586
    Parent ID      : 0c972388534de520
    ID             : e3bfa0179f639bd5
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.295 +0000 UTC
    End time       : 2026-09-11 10:03:39.29520114 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #129
    Trace ID       : 12146c9bc627e90ed23bb80cd745b586
    Parent ID      : 0c972388534de520
    ID             : a15865bbaf170522
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.295 +0000 UTC
    End time       : 2026-09-11 10:03:39.295048957 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #130
    Trace ID       : 12146c9bc627e90ed23bb80cd745b586
    Parent ID      : 0c972388534de520
    ID             : 1680663165e861b8
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.295 +0000 UTC
    End time       : 2026-09-11 10:03:39.295042942 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #131
    Trace ID       : 12146c9bc627e90ed23bb80cd745b586
    Parent ID      : 0c972388534de520
    ID             : 1a8c64d3e5f68535
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.295 +0000 UTC
    End time       : 2026-09-11 10:03:39.29501973 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #132
    Trace ID       : 12146c9bc627e90ed23bb80cd745b586
    Parent ID      : 0c972388534de520
    ID             : 481c336e25f8db10
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.296 +0000 UTC
    End time       : 2026-09-11 10:03:39.297457962 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
Span #133
    Trace ID       : 344172eaf36413ee45baa905669cb1a0
    Parent ID      : 714532393028e8c9
    ID             : 80e62f4788c720dd
    Name           : middleware - query
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.318 +0000 UTC
    End time       : 2026-09-11 10:03:39.31817786 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(query)
     -> express.type: Str(middleware)
Span #134
    Trace ID       : 344172eaf36413ee45baa905669cb1a0
    Parent ID      : 714532393028e8c9
    ID             : 7ffc2eefe160742c
    Name           : middleware - expressInit
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.318 +0000 UTC
    End time       : 2026-09-11 10:03:39.318145664 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(expressInit)
     -> express.type: Str(middleware)
Span #135
    Trace ID       : 344172eaf36413ee45baa905669cb1a0
    Parent ID      : 714532393028e8c9
    ID             : c0ca12bcd87f6ff3
    Name           : middleware - loggingMiddleware
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.318 +0000 UTC
    End time       : 2026-09-11 10:03:39.318193703 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(loggingMiddleware)
     -> express.type: Str(middleware)
Span #136
    Trace ID       : 344172eaf36413ee45baa905669cb1a0
    Parent ID      : 714532393028e8c9
    ID             : 45d40aba4e2e2ba7
    Name           : middleware - <anonymous>
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.319 +0000 UTC
    End time       : 2026-09-11 10:03:39.319091415 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(<anonymous>)
     -> express.type: Str(middleware)
Span #137
    Trace ID       : 344172eaf36413ee45baa905669cb1a0
    Parent ID      : 714532393028e8c9
    ID             : 7bf266e06562b4a1
    Name           : middleware - urlencodedParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.319 +0000 UTC
    End time       : 2026-09-11 10:03:39.319105927 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(urlencodedParser)
     -> express.type: Str(middleware)
Span #138
    Trace ID       : 344172eaf36413ee45baa905669cb1a0
    Parent ID      : 714532393028e8c9
    ID             : 553eae973ab44415
    Name           : middleware - jsonParser
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.319 +0000 UTC
    End time       : 2026-09-11 10:03:39.319026621 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> express.name: Str(jsonParser)
     -> express.type: Str(middleware)
Span #139
    Trace ID       : 344172eaf36413ee45baa905669cb1a0
    Parent ID      : 714532393028e8c9
    ID             : 6c57b20773d59c4a
    Name           : request handler - /health
    Kind           : Internal
    Start time     : 2026-09-11 10:03:39.319 +0000 UTC
    End time       : 2026-09-11 10:03:39.320370377 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.route: Str(/health)
     -> express.name: Str(/health)
     -> express.type: Str(request_handler)
ScopeSpans #1
ScopeSpans SchemaURL:
InstrumentationScope @opentelemetry/instrumentation-http 0.220.0
Span #0
    Trace ID       : 982bc53cc62a6622200480fce10c4e0e
    Parent ID      :
    ID             : 495e85534f5a3ffe
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:38.988 +0000 UTC
    End time       : 2026-09-11 10:03:38.997967407 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53068)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #1
    Trace ID       : 5f94c6edb8cd0878ed7a2a14b025e7cb
    Parent ID      :
    ID             : f21d2d42db7412c5
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.01 +0000 UTC
    End time       : 2026-09-11 10:03:39.011814678 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53084)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #2
    Trace ID       : 39d0826de7e148e4faf578499a96050f
    Parent ID      :
    ID             : a361db6eac2b8fc3
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.022 +0000 UTC
    End time       : 2026-09-11 10:03:39.024748052 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53088)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #3
    Trace ID       : 3f2303934b742e9cf6d03d05b019e61b
    Parent ID      :
    ID             : cce375033a7e34e3
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.039 +0000 UTC
    End time       : 2026-09-11 10:03:39.043767283 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53100)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #4
    Trace ID       : f4c2f396762964196b8effd2b731d155
    Parent ID      :
    ID             : b1ebfadc8e3598c6
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.054 +0000 UTC
    End time       : 2026-09-11 10:03:39.056469542 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53112)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #5
    Trace ID       : b343b7c23726f8474f2cff96167a1edc
    Parent ID      :
    ID             : f5fd9887a7a0fcee
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.067 +0000 UTC
    End time       : 2026-09-11 10:03:39.069109524 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53114)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #6
    Trace ID       : 2cc785a88f27dcc9eff80e98f236b925
    Parent ID      :
    ID             : 3f9ac443c705b12f
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.081 +0000 UTC
    End time       : 2026-09-11 10:03:39.085045209 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53128)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #7
    Trace ID       : 6fa88befd9d3e9344566ffa9c2b69c61
    Parent ID      :
    ID             : b46f9b052c5ba53d
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.097 +0000 UTC
    End time       : 2026-09-11 10:03:39.101214659 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53132)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #8
    Trace ID       : bb5dab93ef5adea6c7a77527f2ab6bb4
    Parent ID      :
    ID             : 75eecb6a0701085f
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.113 +0000 UTC
    End time       : 2026-09-11 10:03:39.116146982 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53144)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #9
    Trace ID       : e1839b2331956147721edd4429496cd5
    Parent ID      :
    ID             : 03d3ebac7387e040
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.128 +0000 UTC
    End time       : 2026-09-11 10:03:39.131145666 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53148)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #10
    Trace ID       : 65c651667b20e1ad735f84db436cf496
    Parent ID      :
    ID             : 1eecd2d8c8506d62
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.145 +0000 UTC
    End time       : 2026-09-11 10:03:39.148825315 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53154)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #11
    Trace ID       : 0fdd9f9dbd38cdbda3d7ec2232c95e58
    Parent ID      :
    ID             : ad423d4d6c1e39bd
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.163 +0000 UTC
    End time       : 2026-09-11 10:03:39.165504321 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53156)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #12
    Trace ID       : 6494f7705df631569f0d4b4c7d95437e
    Parent ID      :
    ID             : 4efb53b89250cdfb
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.178 +0000 UTC
    End time       : 2026-09-11 10:03:39.180615433 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53158)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #13
    Trace ID       : af404f5da7c027039efa4d2c466dbcfe
    Parent ID      :
    ID             : 889edcc0891bfcdc
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.195 +0000 UTC
    End time       : 2026-09-11 10:03:39.197356911 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53168)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #14
    Trace ID       : 38daff0754f7f7e36f2906061e20a04b
    Parent ID      :
    ID             : 26f147299db1ca47
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.212 +0000 UTC
    End time       : 2026-09-11 10:03:39.224314262 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53176)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #15
    Trace ID       : 711cdaa2ebdfe119a7241c7b12c316bc
    Parent ID      :
    ID             : 36506c0a1638a12c
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.23 +0000 UTC
    End time       : 2026-09-11 10:03:39.240743016 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53190)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #16
    Trace ID       : ac15c27b670b6f5e7a68936201a2ee39
    Parent ID      :
    ID             : f5ebd970640378ff
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.256 +0000 UTC
    End time       : 2026-09-11 10:03:39.25828515 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53204)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #17
    Trace ID       : 79b5ff4b7418823f4d6834819ba6d945
    Parent ID      :
    ID             : ce132964123cf739
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.277 +0000 UTC
    End time       : 2026-09-11 10:03:39.279406426 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53212)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #18
    Trace ID       : 12146c9bc627e90ed23bb80cd745b586
    Parent ID      :
    ID             : 0c972388534de520
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.294 +0000 UTC
    End time       : 2026-09-11 10:03:39.296583757 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53218)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
Span #19
    Trace ID       : 344172eaf36413ee45baa905669cb1a0
    Parent ID      :
    ID             : 714532393028e8c9
    Name           : GET /health
    Kind           : Server
    Start time     : 2026-09-11 10:03:39.317 +0000 UTC
    End time       : 2026-09-11 10:03:39.320372164 +0000 UTC
    Status code    : Unset
    Status message :
    DroppedAttributesCount: 0
    DroppedEventsCount: 0
    DroppedLinksCount: 0
Attributes:
     -> http.url: Str(http://user:8080/health)
     -> http.host: Str(user:8080)
     -> net.host.name: Str(user)
     -> http.method: Str(GET)
     -> http.scheme: Str(http)
     -> http.target: Str(/health)
     -> http.user_agent: Str(curl/8.22.0)
     -> http.flavor: Str(1.1)
     -> net.transport: Str(ip_tcp)
     -> net.host.ip: Str(::ffff:10.244.1.34)
     -> net.host.port: Int(8080)
     -> net.peer.ip: Str(::ffff:10.244.1.40)
     -> net.peer.port: Int(53234)
     -> http.status_code: Int(200)
     -> http.status_text: Str(OK)
     -> http.route: Str(/health)
        {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.39", "k8s.pod.name": "opentelemetry-collector-95c4b445-856r7", "service.instance.id": "f6c03c02-1f59-4de1-b633-b02083577b66", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "traces"}

venka@Think-VVRAM MINGW64 /c/azure/roboshop/monitoring/observability (main)
$ ^C

venka@Think-VVRAM MINGW64 /c/azure/roboshop/monitoring/observability (main)
$
```
