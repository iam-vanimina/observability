```

venka@Think-VVRAM MINGW64 ~
$ kubectl get pods -A | grep -Ei 'mongo|mysql|redis|user'
argocd               argocd-redis-5f664b9b9c-kcxzx                            1/1     Running   2 (31m ago)       7d15h
roboshop             mongodb-9f4d77799-9z9fp                                  1/1     Running   2 (31m ago)       7d14h
roboshop             mysql-0                                                  1/1     Running   3 (31m ago)       5d13h
roboshop             mysql-1                                                  1/1     Running   3 (31m ago)       5d13h
roboshop             mysql-2                                                  1/1     Running   3 (31m ago)       5d13h
roboshop             redis-6bff6bc79b-nbbhk                                   1/1     Running   2 (31m ago)       7d14h
roboshop             user-658fc5dc-kbdml                                      1/1     Running   1 (31m ago)       18h

venka@Think-VVRAM MINGW64 ~
$ kubectl get pods -A | grep -Ei 'mongo|mysql|redis|user'
argocd               argocd-redis-5f664b9b9c-kcxzx                            1/1     Running   2 (31m ago)       7d15h
roboshop             mongodb-9f4d77799-9z9fp                                  1/1     Running   2 (31m ago)       7d14h
roboshop             mysql-0                                                  1/1     Running   3 (31m ago)       5d13h
roboshop             mysql-1                                                  1/1     Running   3 (31m ago)       5d13h
roboshop             mysql-2                                                  1/1     Running   3 (31m ago)       5d13h
roboshop             redis-6bff6bc79b-nbbhk                                   1/1     Running   2 (31m ago)       7d14h
roboshop             user-658fc5dc-kbdml                                      1/1     Running   1 (31m ago)       18h

venka@Think-VVRAM MINGW64 ~
$ kubectl get pvc -A
NAMESPACE    NAME             STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   VOLUMEATTRIBUTESCLASS   AGE
monitoring   grafana          Bound    pvc-f7c24d72-f112-4b36-a5e7-163b481395ce   5Gi        RWO            standard       <unset>                 3d17h
monitoring   storage-loki-0   Bound    pvc-89bf7324-99eb-470d-97b1-7b69e96c85f2   10Gi       RWO            standard       <unset>                 3d22h
roboshop     mysql-mysql-0    Bound    pvc-2e2df331-5914-47dd-9580-a7cb17cf2f47   3Gi        RWO            standard       <unset>                 5d13h
roboshop     mysql-mysql-1    Bound    pvc-322da47d-2046-4524-ad49-ed161f0436ce   3Gi        RWO            standard       <unset>                 5d13h
roboshop     mysql-mysql-2    Bound    pvc-9ade0018-be5f-4b10-ae9c-208a8feca925   3Gi        RWO            standard       <unset>                 5d13h

venka@Think-VVRAM MINGW64 ~
$ kubectl get pod mongodb-9f4d77799-9z9fp -n roboshop \
  -o jsonpath='{range .spec.containers[*].volumeMounts[*]}{.name}{" -> "}{.mountPath}{"\n"}{end}'
kube-api-access-mgbwq -> /var/run/secrets/kubernetes.io/serviceaccount

venka@Think-VVRAM MINGW64 ~
$ kubectl get pod mongodb-9f4d77799-9z9fp -n roboshop \
  -o jsonpath='{range .spec.volumes[*]}{.name}{" -> "}{.persistentVolumeClaim.claimName}{"\n"}{end}'
kube-api-access-mgbwq ->

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
orders: 1venka@Think-VVRAM MINGW64 ~
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

=====================================================================================================

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
$



venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl run test-curl \
  --rm -it \
  --image=curlimages/curl \
  -n roboshop \
  -- sh
All commands and output from this session will be recorded in container logs, including credentials and sensitive information passed through the command prompt.
If you don't see a command prompt, try pressing enter.
~ $
~ $ curl http://user:8080/health
{"app":"OK","mongo":true}~ $



enka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl run test-curl \
  --rm -it \
  --image=curlimages/curl \
  -n roboshop \
  -- sh
All commands and output from this session will be recorded in container logs, including credentials and sensitive information passed through the command prompt.
If you don't see a command prompt, try pressing enter.
~ $
~ $ curl http://user:8080/health
{"app":"OK","mongo":true}~ $ for i in $(seq 1 20); do curl -s http://user:8080/health; echo; done
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
~ $

```
