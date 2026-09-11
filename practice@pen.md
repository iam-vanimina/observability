```
venka@Think-VVRAM MINGW64 ~
$ cd /c/
$Recycle.Bin/                  Users/
3-Tier-DevSecOps-Mega-Project/ Vaniminadevops/
3-Tier-GitOps-CD/              Voiceover/
AMTAG.BIN                      Windows/
AZURE/                         ai-agent/
Boot/                          bootTel.dat
Config.Msi/                    drives/
DRIVERS/                       inetpub/
Documents and Settings/        k8s-2026/
DumpStack.log                  k8sai/
DumpStack.log.tmp              k8sgpt/
GitLab-Runner/                 logUploaderSettings.ini
OneDriveTemp/                  logUploaderSettings_temp.ini
PerfLogs/                      pagefile.sys
Program Files/                 roboshop/
Program Files (x86)/           softwares/
ProgramData/                   swapfile.sys
Recovery/                      terra/
System Volume Information/     tools/

venka@Think-VVRAM MINGW64 ~
$ cd /c/

venka@Think-VVRAM MINGW64 /c
$ cd /c/AZURE/
.terraform/               main.tf                   terraform.tfstate
.terraform.lock.hcl       modules/                  terraform.tfstate.backup
acr.tf                    provider.tf               vm/
bootstrap-hosts.sh        roboshop/

venka@Think-VVRAM MINGW64 /c
$ cd /c/AZURE/roboshop/CD/

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD
$ ls
cart-argocd/       frontend-argocd/  payments-argocd/  resource-quota.yaml
catalogue-argocd/  mongodb-argocd/   rabbitmq-argocd/  shipping-argocd/
dispatch-argocd/   mysql-argocd/     redis-argocd/     user-argocd/

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD
$ cd frontend-argocd/

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/frontend-argocd (main)
$ git add .
warning: in the working copy of 'templates/deployment.yaml', LF will be replaced by CRLF the next time Git touches it

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/frontend-argocd (main)
$ git commit -m "open telemetery anonation"
[main ccc5a40] open telemetery anonation
 1 file changed, 2 insertions(+)

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/frontend-argocd (main)
$ git pull origin main
From https://github.com/iam-vanimina/frontend-argocd
 * branch            main       -> FETCH_HEAD
Already up to date.

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/frontend-argocd (main)
$ git push origin main
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 12 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 498 bytes | 498.00 KiB/s, done.
Total 4 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/iam-vanimina/frontend-argocd.git
   aaed15c..ccc5a40  main -> main

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/frontend-argocd (main)
$ cd ../catalogue-argocd/

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/catalogue-argocd (main)
$ git add .

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/catalogue-argocd (main)
$ git commit -m "open telemetery anonation"
[main 033c387] open telemetery anonation
 1 file changed, 2 insertions(+)

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/catalogue-argocd (main)
$ git pull origin main
From https://github.com/iam-vanimina/catalogue-argocd
 * branch            main       -> FETCH_HEAD
Already up to date.

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/catalogue-argocd (main)
$ git push origin main
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 12 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 432 bytes | 432.00 KiB/s, done.
Total 4 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/iam-vanimina/catalogue-argocd.git
   441cf4c..033c387  main -> main

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/catalogue-argocd (main)
$ cd ../user-argocd/

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/user-argocd (main)
$ git add .
warning: in the working copy of 'templates/manifest.yaml', LF will be replaced by CRLF the next time Git touches it

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/user-argocd (main)
$ git commit -m "open telemetery anonation"
[main 47530e6] open telemetery anonation
 1 file changed, 2 insertions(+)

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/user-argocd (main)
$ git pull origin main
From https://github.com/iam-vanimina/user-argocd
 * branch            main       -> FETCH_HEAD
Already up to date.

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/user-argocd (main)
$ git push origin main
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 12 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 434 bytes | 434.00 KiB/s, done.
Total 4 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/iam-vanimina/user-argocd.git
   8b64e2c..47530e6  main -> main

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/user-argocd (main)
$

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/user-argocd (main)
$ cd ../cart-argocd/

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/cart-argocd (main)
$ git add .
warning: in the working copy of 'templates/manifest.yaml', LF will be replaced by CRLF the next time Git touches it

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/cart-argocd (main)
$ git commit -m "open telemetery anonation"
[main c0f45b8] open telemetery anonation
 1 file changed, 2 insertions(+)

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/cart-argocd (main)
$ git pull origin main
From https://github.com/iam-vanimina/cart-argocd
 * branch            main       -> FETCH_HEAD
Already up to date.

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/cart-argocd (main)
$ git push origin main
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 12 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 430 bytes | 215.00 KiB/s, done.
Total 4 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/iam-vanimina/cart-argocd.git
   7210fb5..c0f45b8  main -> main

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/cart-argocd (main)
$ cd ../shipping-argocd/

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/shipping-argocd (main)
$ git add .
warning: in the working copy of 'templates/manifest.yaml', LF will be replaced by CRLF the next time Git touches it

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/shipping-argocd (main)
$ git commit -m "open telemetery anonation"
[main a2b4923] open telemetery anonation
 1 file changed, 2 insertions(+)

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/shipping-argocd (main)
$ git pull origin main
From https://github.com/iam-vanimina/shipping-argocd
 * branch            main       -> FETCH_HEAD
Already up to date.

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/shipping-argocd (main)
$ git push origin main
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 12 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 427 bytes | 427.00 KiB/s, done.
Total 4 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/iam-vanimina/shipping-argocd.git
   71204b5..a2b4923  main -> main

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/shipping-argocd (main)
$ cd ../dispatch-argocd/

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ git add .
warning: in the working copy of 'templates/manifest.yaml', LF will be replaced by CRLF the next time Git touches it

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ git commit -m "open telemetery anonation"
[main 0b7d925] open telemetery anonation
 1 file changed, 2 insertions(+)

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ git pull origin main
From https://github.com/iam-vanimina/dispatch-argocd
 * branch            main       -> FETCH_HEAD
Already up to date.

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ git push origin main
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 12 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 426 bytes | 142.00 KiB/s, done.
Total 4 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/iam-vanimina/dispatch-argocd.git
   4f8d380..0b7d925  main -> main

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl get opentelemetrycollector -n opentelemetry
No resources found in opentelemetry namespace.

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl restart deployment -n roboshop
error: unknown command "restart" for "kubectl"

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl rollout restart deployment -n roboshop
deployment.apps/cart restarted
deployment.apps/catalogue restarted
deployment.apps/dispatch restarted
deployment.apps/frontend restarted
deployment.apps/mongodb restarted
deployment.apps/payment restarted
deployment.apps/rabbitmq restarted
deployment.apps/redis restarted
deployment.apps/shipping restarted
deployment.apps/user restarted

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl get svc -n roboshop
NAME             TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
cart             ClusterIP   10.96.67.47     <none>        8080/TCP       7d19h
catalogue        ClusterIP   10.96.196.186   <none>        8080/TCP       7d19h
dispatch         ClusterIP   10.96.152.141   <none>        8080/TCP       7d19h
frontend         NodePort    10.96.88.171    <none>        80:30080/TCP   7d19h
mongodb          ClusterIP   10.96.53.129    <none>        27017/TCP      7d19h
mysql            ClusterIP   10.96.130.58    <none>        3306/TCP       5d18h
mysql-headless   ClusterIP   None            <none>        3306/TCP       5d18h
payment          ClusterIP   10.96.206.41    <none>        8080/TCP       5d15h
rabbitmq         ClusterIP   10.96.62.195    <none>        5672/TCP       7d19h
redis            ClusterIP   10.96.82.163    <none>        6379/TCP       7d19h
shipping         ClusterIP   10.96.48.234    <none>        8080/TCP       7d19h
user             ClusterIP   10.96.222.50    <none>        8080/TCP       7d19h

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl logs -n opentelemetry \
  deployment/opentelemetry-collector \
  --tail=200
2026-09-11T09:07:40.511Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:07:46.332Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 59}
2026-09-11T09:07:50.556Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:07:57.383Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 2, "metrics": 45, "data points": 118}
2026-09-11T09:08:00.606Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:08:01.008Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 58}
2026-09-11T09:08:10.438Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:08:20.473Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:08:30.508Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:08:40.540Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:08:46.361Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 59}
2026-09-11T09:08:50.574Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:08:57.401Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 2, "metrics": 45, "data points": 118}
2026-09-11T09:09:00.612Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:09:01.014Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 58}
2026-09-11T09:09:10.448Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:09:20.486Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:09:30.529Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:09:40.559Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:09:46.382Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 59}
2026-09-11T09:09:50.597Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:09:57.423Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 2, "metrics": 45, "data points": 118}
2026-09-11T09:10:00.432Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:10:01.034Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 58}
2026-09-11T09:10:10.467Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:10:20.504Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:10:30.540Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:10:40.566Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:10:46.398Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 59}
2026-09-11T09:10:50.408Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:10:57.433Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 2, "metrics": 45, "data points": 118}
2026-09-11T09:11:00.445Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:11:00.848Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 58}
2026-09-11T09:11:10.480Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:11:20.524Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:11:30.560Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:11:40.589Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:11:46.209Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 59}
2026-09-11T09:11:50.424Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:11:57.450Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 2, "metrics": 45, "data points": 118}
2026-09-11T09:12:00.460Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:12:00.862Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 58}
2026-09-11T09:12:10.490Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:12:20.520Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:12:30.556Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:12:40.585Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:12:46.203Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 59}
2026-09-11T09:12:50.419Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:12:57.440Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 2, "metrics": 45, "data points": 118}
2026-09-11T09:13:00.450Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:13:00.851Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 58}
2026-09-11T09:13:10.486Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:13:20.523Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:13:30.558Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:13:40.393Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:13:46.213Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 59}
2026-09-11T09:13:50.429Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:13:57.455Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 2, "metrics": 45, "data points": 118}
2026-09-11T09:14:00.463Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:14:00.866Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 58}
2026-09-11T09:14:10.496Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:14:20.532Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:14:30.574Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:14:40.407Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:14:46.225Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 59}
2026-09-11T09:14:50.455Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:14:57.487Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 2, "metrics": 45, "data points": 118}
2026-09-11T09:15:00.505Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:15:00.907Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 58}
2026-09-11T09:15:10.541Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:15:14.100Z        info    Traces  {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "traces", "resource spans": 2, "spans": 36}
2026-09-11T09:15:19.324Z        info    Traces  {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "traces", "resource spans": 2, "spans": 36}
2026-09-11T09:15:20.379Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:15:28.964Z        info    Traces  {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "traces", "resource spans": 2, "spans": 27}
2026-09-11T09:15:30.613Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:15:40.432Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:15:46.252Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 59}
2026-09-11T09:15:50.465Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:15:57.293Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 27, "data points": 63}
2026-09-11T09:15:57.494Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 55}
2026-09-11T09:16:00.506Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:16:00.909Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 58}
2026-09-11T09:16:10.536Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:16:20.574Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:16:30.609Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:16:40.425Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:16:46.445Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 59}
2026-09-11T09:16:50.463Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:16:57.291Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 27, "data points": 63}
2026-09-11T09:16:57.497Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 55}
2026-09-11T09:17:00.711Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:17:00.912Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 58}
2026-09-11T09:17:10.790Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:17:14.832Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 59}
2026-09-11T09:17:14.892Z        info    Traces  {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "traces", "resource spans": 2, "spans": 20}
2026-09-11T09:17:19.866Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 58}
2026-09-11T09:17:19.921Z        info    Traces  {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "traces", "resource spans": 2, "spans": 22}
2026-09-11T09:17:20.474Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:17:24.103Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 16, "data points": 25}
2026-09-11T09:17:24.388Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:17:25.753Z        info    Traces  {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "traces", "resource spans": 1, "spans": 2}
2026-09-11T09:17:30.352Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:17:31.175Z        info    Traces  {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "traces", "resource spans": 1, "spans": 2}
2026-09-11T09:17:35.375Z        info    Traces  {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "traces", "resource spans": 1, "spans": 5}
2026-09-11T09:17:40.379Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:17:50.419Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:17:57.245Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 55}
2026-09-11T09:18:00.456Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:18:07.144Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 2}
2026-09-11T09:18:10.290Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:18:20.329Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:18:20.393Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:18:21.597Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:18:22.337Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 50}
2026-09-11T09:18:24.606Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:18:25.609Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:18:27.767Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 51}
2026-09-11T09:18:29.626Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 3}
2026-09-11T09:18:30.382Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:18:30.629Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 2}
2026-09-11T09:18:35.645Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:18:36.196Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 16, "data points": 44}
2026-09-11T09:18:38.659Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:18:39.663Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:18:40.411Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:18:43.679Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:18:45.887Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 2}
2026-09-11T09:18:47.891Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:18:50.448Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:18:51.906Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:18:56.120Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:18:57.488Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 55}
2026-09-11T09:19:00.300Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:19:01.686Z        info    Traces  {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "traces", "resource spans": 1, "spans": 1}
2026-09-11T09:19:03.045Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 2}
2026-09-11T09:19:04.049Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:19:05.052Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 2}
2026-09-11T09:19:09.071Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:19:10.074Z        info    Logs    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "logs", "resource logs": 1, "log records": 1}
2026-09-11T09:19:10.238Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:19:20.276Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:19:22.284Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 52}
2026-09-11T09:19:27.503Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 51}
2026-09-11T09:19:30.315Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:19:35.488Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 25, "data points": 58}
2026-09-11T09:19:40.303Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:19:50.136Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:19:57.160Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 55}
2026-09-11T09:20:00.169Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:20:10.384Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:20:20.222Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:20:22.231Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 52}
2026-09-11T09:20:27.451Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 51}
2026-09-11T09:20:30.260Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:20:35.676Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 25, "data points": 58}
2026-09-11T09:20:40.295Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:20:50.127Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:20:57.150Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 55}
2026-09-11T09:21:00.161Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:21:10.212Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:21:12.191Z        info    Traces  {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "traces", "resource spans": 2, "spans": 11}
2026-09-11T09:21:20.257Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:21:22.265Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 52}
2026-09-11T09:21:27.484Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 51}
2026-09-11T09:21:30.295Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:21:31.100Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 18, "data points": 55}
2026-09-11T09:21:35.507Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 25, "data points": 58}
2026-09-11T09:21:40.329Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:21:42.329Z        info    Traces  {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "traces", "resource spans": 1, "spans": 2}
2026-09-11T09:21:50.159Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:22:00.226Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:22:11.388Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:22:21.229Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:22:23.442Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 52}
2026-09-11T09:22:28.661Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 51}
2026-09-11T09:22:31.274Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:22:36.711Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 2, "metrics": 42, "data points": 111}
2026-09-11T09:22:41.329Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:22:51.390Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:23:01.233Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:23:11.272Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:23:21.325Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:23:23.332Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 52}
2026-09-11T09:23:28.550Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 51}
2026-09-11T09:23:31.361Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:23:36.580Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 25, "data points": 58}
2026-09-11T09:23:36.781Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 53}
2026-09-11T09:23:41.196Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:23:51.231Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:24:01.269Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:24:11.301Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:24:21.339Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:24:23.348Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 52}
2026-09-11T09:24:28.776Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 51}
2026-09-11T09:24:31.387Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:24:36.602Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 2, "metrics": 42, "data points": 111}
2026-09-11T09:24:41.218Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:24:51.259Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:25:01.301Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}
2026-09-11T09:25:11.338Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.19", "k8s.pod.name": "opentelemetry-collector-5576df4994-6m44s", "service.instance.id": "a97b1283-ccc5-4f1d-92ce-aedf1da184ba", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 33, "data points": 43}

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl get svc -n monitoring | grep -i tempo
tempo                                     ClusterIP   10.96.114.113   <none>        6831/UDP,6832/UDP,3200/TCP,14268/TCP,14250/TCP,9411/TCP,55680/TCP,55681/TCP,4317/TCP,4318/TCP,55678/TCP   14h

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl get opentelemetrycollector -n opentelemetry -o yaml
apiVersion: v1
items: []
kind: List
metadata:
  resourceVersion: ""

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl get pods -n opentelemetry
NAME                                      READY   STATUS    RESTARTS   AGE
opentelemetry-collector-9cccb6864-p7kk5   1/1     Running   0          30s
opentelemetry-operator-75684646f7-ssfvs   1/1     Running   0          176m

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl logs -n opentelemetry deployment/opentelemetry-collector --tail=100
2026-09-11T09:30:27.110Z        warn    otelconftelemetry/logger.go:143 Using legacy service.telemetry.resource inline map format; prefer service.telemetry.resource.attributes (array of maps with `name` and `value` keys)        {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "legacy_resource_attributes": ["host.name", "k8s.namespace.name", "k8s.node.ip", "k8s.node.name", "k8s.pod.ip", "k8s.pod.name"]}
2026-09-11T09:30:27.151Z        info    otelconftelemetry/tracer.go:47  Internal trace telemetry disabled       {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}}
2026-09-11T09:30:27.166Z        info    memorylimiter@v0.160.0/memorylimiter.go:185     Using percentage memory limiter {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.kind": "processor", "total_memory_mib": 7779, "limit_percentage": 80, "spike_limit_percentage": 25}
2026-09-11T09:30:27.171Z        info    memorylimiter@v0.160.0/memorylimiter.go:109     Memory limiter configured       {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.kind": "processor", "limit_mib": 6223, "spike_limit_mib": 1944, "check_interval": 5}
2026-09-11T09:30:27.192Z        info    service@v0.160.0/service.go:261 Starting otelcol-k8s... {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "Version": "0.160.0", "NumCPU": 12}
2026-09-11T09:30:27.193Z        info    extensions/extensions.go:44     Starting extensions...  {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}}
2026-09-11T09:30:27.195Z        info    extensions/extensions.go:48     Extension is starting...        {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "health_check", "otelcol.component.kind": "extension"}
2026-09-11T09:30:27.196Z        info    healthcheckextension@v0.160.0/healthcheckextension.go:32        Starting health_check extension {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "health_check", "otelcol.component.kind": "extension", "config": {"Config":{"ServerConfig":{"NetAddr":{"Endpoint":"10.244.1.35:13133","Transport":"tcp","DialerConfig":{"Timeout":0}},"TLS":{},"CORS":{},"Auth":{},"MaxRequestBodySize":0,"IncludeMetadata":false,"ResponseHeaders":null,"CompressionAlgorithms":null,"ReadTimeout":0,"ReadHeaderTimeout":0,"WriteTimeout":0,"Middlewares":null,"Keepalive":{},"IdleTimeout":0,"KeepAlivesEnabled":false},"Path":"/","ResponseBody":null,"CheckCollectorPipeline":{"Enabled":false,"Interval":"5m","ExporterFailureThreshold":5},"UseV2":false,"GRPCConfig":null,"HTTPConfig":null,"ComponentHealthConfig":null}}}
2026-09-11T09:30:27.205Z        info    extensions/extensions.go:66     Extension started.      {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "health_check", "otelcol.component.kind": "extension"}
2026-09-11T09:30:27.207Z        info    otlpreceiver@v0.160.0/otlp.go:120       Starting GRPC server    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "otlp", "otelcol.component.kind": "receiver", "endpoint": "10.244.1.35:4317"}
2026-09-11T09:30:27.214Z        info    otlpreceiver@v0.160.0/otlp.go:175       Starting HTTP server    {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "otlp", "otelcol.component.kind": "receiver", "endpoint": "10.244.1.35:4318"}
2026-09-11T09:30:27.215Z        info    healthcheck/handler.go:131      Health Check state change       {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "health_check", "otelcol.component.kind": "extension", "status": "ready"}
2026-09-11T09:30:27.215Z        info    service@v0.160.0/service.go:284 Everything is ready. Begin running and processing data. {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}}
2026-09-11T09:30:29.624Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 1, "metrics": 17, "data points": 51}
2026-09-11T09:30:36.645Z        info    Metrics {"resource": {"host.name": "desktop-worker", "k8s.namespace.name": "opentelemetry", "k8s.node.ip": "172.18.0.4", "k8s.node.name": "desktop-worker", "k8s.pod.ip": "10.244.1.35", "k8s.pod.name": "opentelemetry-collector-9cccb6864-p7kk5", "service.instance.id": "232bdd17-d6c3-49be-a1aa-04e63039354c", "service.name": "otelcol-k8s", "service.version": "0.160.0"}, "otelcol.component.id": "debug", "otelcol.component.kind": "exporter", "otelcol.signal": "metrics", "resource metrics": 2, "metrics": 42, "data points": 111}

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
~ $ exit
Session ended, resume using 'kubectl attach test-curl -c test-curl -n roboshop -i -t' command
pod "test-curl" deleted from roboshop namespace

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl logs -n opentelemetry deployment/opentelemetry-collector --since=5m | grep -i -E "traces|span|tempo|error"

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl get pods -n roboshop | grep user
user-74bcc7d99c-jw4sg        1/1     Running   0               28m

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl get instrumentation roboshop-auto -n roboshop -o yaml
apiVersion: opentelemetry.io/v1alpha1
kind: Instrumentation
metadata:
  annotations:
    instrumentation.opentelemetry.io/default-auto-instrumentation-apache-httpd-image: ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-apache-httpd:1.0.4
    instrumentation.opentelemetry.io/default-auto-instrumentation-dotnet-image: ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-dotnet:1.16.0
    instrumentation.opentelemetry.io/default-auto-instrumentation-go-image: ghcr.io/open-telemetry/opentelemetry-go-instrumentation/autoinstrumentation-go:v0.24.0
    instrumentation.opentelemetry.io/default-auto-instrumentation-java-image: ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-java:2.30.0
    instrumentation.opentelemetry.io/default-auto-instrumentation-nginx-image: ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-apache-httpd:1.0.4
    instrumentation.opentelemetry.io/default-auto-instrumentation-nodejs-image: ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-nodejs:0.78.0
    instrumentation.opentelemetry.io/default-auto-instrumentation-python-image: ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-python:0.64b0
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"opentelemetry.io/v1alpha1","kind":"Instrumentation","metadata":{"annotations":{},"name":"roboshop-auto","namespace":"roboshop"},"spec":{"exporter":{"endpoint":"http://opentelemetry-collector.opentelemetry.svc.cluster.local:4318"},"go":{"image":"ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-go:latest"},"java":{"image":"ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-java:latest"},"nodejs":{"image":"ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-nodejs:latest"},"propagators":["tracecontext","baggage"],"python":{"image":"ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-python:latest"},"sampler":{"argument":"1","type":"parentbased_traceidratio"}}}
  creationTimestamp: "2026-09-11T08:09:30Z"
  generation: 2
  name: roboshop-auto
  namespace: roboshop
  resourceVersion: "712817"
  uid: bb99b690-6d61-4b40-85dd-da7ae974c1d8
spec:
  apacheHttpd:
    configPath: /usr/local/apache2/conf
    image: ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-apache-httpd:1.0.4
    resourceRequirements:
      limits:
        cpu: 500m
        memory: 256Mi
      requests:
        cpu: 1m
        memory: 128Mi
    version: "2.4"
    volumeClaimTemplate:
      metadata: {}
      spec:
        resources: {}
  defaults: {}
  dotnet:
    image: ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-dotnet:1.16.0
    resourceRequirements:
      limits:
        cpu: 500m
        memory: 256Mi
      requests:
        cpu: 50m
        memory: 128Mi
    volumeClaimTemplate:
      metadata: {}
      spec:
        resources: {}
  exporter:
    endpoint: http://opentelemetry-collector.opentelemetry.svc.cluster.local:4318
  go:
    image: ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-go:latest
    resourceRequirements:
      limits:
        cpu: 500m
        memory: 256Mi
      requests:
        cpu: 50m
        memory: 64Mi
    volumeClaimTemplate:
      metadata: {}
      spec:
        resources: {}
  java:
    image: ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-java:latest
    resources:
      limits:
        cpu: 500m
        memory: 256Mi
      requests:
        cpu: 50m
        memory: 64Mi
    volumeClaimTemplate:
      metadata: {}
      spec:
        resources: {}
  nginx:
    configFile: /etc/nginx/nginx.conf
    image: ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-apache-httpd:1.0.4
    resourceRequirements:
      limits:
        cpu: 500m
        memory: 256Mi
      requests:
        cpu: 1m
        memory: 128Mi
    volumeClaimTemplate:
      metadata: {}
      spec:
        resources: {}
  nodejs:
    image: ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-nodejs:latest
    resourceRequirements:
      limits:
        cpu: 500m
        memory: 256Mi
      requests:
        cpu: 50m
        memory: 128Mi
    volumeClaimTemplate:
      metadata: {}
      spec:
        resources: {}
  propagators:
  - tracecontext
  - baggage
  python:
    image: ghcr.io/open-telemetry/opentelemetry-operator/autoinstrumentation-python:latest
    resourceRequirements:
      limits:
        cpu: 500m
        memory: 256Mi
      requests:
        cpu: 50m
        memory: 64Mi
    volumeClaimTemplate:
      metadata: {}
      spec:
        resources: {}
  resource: {}
  sampler:
    argument: "1"
    type: parentbased_traceidratio

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl get pod -n roboshop <USER-POD> \
  -o jsonpath='{range .spec.containers[0].env[*]}{.name}={.value}{"\n"}{end}' \
  | grep -E '^OTEL|^NODE_OPTIONS'
bash: USER-POD: No such file or directory

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl get pods -n roboshop | grep user
user-74bcc7d99c-jw4sg        1/1     Running   0               29m

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl get pod -n roboshop user-74bcc7d99c-jw4sg   -o jsonpath='{range .spec.containers[0].env[*]}{.name}={.value}{"\n"}{end}'   | grep -E '^OTEL|^NODE_OPTIONS'
OTEL_NODE_IP=
OTEL_POD_IP=
NODE_OPTIONS= --require /otel-auto-instrumentation-nodejs/autoinstrumentation.js
OTEL_METRICS_EXPORTER=otlp
OTEL_SERVICE_NAME=user
OTEL_EXPORTER_OTLP_ENDPOINT=http://opentelemetry-collector.opentelemetry.svc.cluster.local:4318
OTEL_RESOURCE_ATTRIBUTES_POD_NAME=
OTEL_RESOURCE_ATTRIBUTES_NODE_NAME=
OTEL_PROPAGATORS=tracecontext,baggage
OTEL_TRACES_SAMPLER=parentbased_traceidratio
OTEL_TRACES_SAMPLER_ARG=1
OTEL_RESOURCE_ATTRIBUTES=k8s.container.name=user,k8s.deployment.name=user,k8s.namespace.name=roboshop,k8s.node.name=$(OTEL_RESOURCE_ATTRIBUTES_NODE_NAME),k8s.pod.name=$(OTEL_RESOURCE_ATTRIBUTES_POD_NAME),k8s.replicaset.name=user-74bcc7d99c,service.instance.id=roboshop.$(OTEL_RESOURCE_ATTRIBUTES_POD_NAME).user,service.namespace=roboshop,service.version=1.0.0

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl logs -n opentelemetry deployment/opentelemetry-collector --since=5m \
  | grep -i -E "traces|span|tempo|error"

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl run otel-test \
  --rm -it \
  --image=curlimages/curl \
  -n opentelemetry \
  -- sh
All commands and output from this session will be recorded in container logs, including credentials and sensitive information passed through the command prompt.
If you don't see a command prompt, try pressing enter.
~ $ for i in $(seq 1 20); do
>   curl -s http://user:8080/health
>   echo
> done



^C
~ $ kubectl get opentelemetrycollector -n opentelemetry -o yaml
sh: kubectl: not found
~ $ ^C

~ $ ^C

~ $ ^C

~ $ exit
Session ended, resume using 'kubectl attach otel-test -c otel-test -n opentelemetry -i -t' command
pod "otel-test" deleted from opentelemetry namespace

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl get opentelemetrycollector -n opentelemetry -o yaml
apiVersion: v1
items: []
kind: List
metadata:
  resourceVersion: ""

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl get opentelemetrycollector -n opentelemetry
No resources found in opentelemetry namespace.

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ helm get values opentelemetry-collector -n opentelemetry -a
COMPUTED VALUES:
additionalLabels: {}
affinity: {}
alternateConfig: {}
annotations: {}
apiVersion: apps/v1
autoscaling:
  additionalMetrics: []
  behavior: {}
  enabled: false
  maxReplicas: 10
  minReplicas: 1
  targetCPUUtilizationPercentage: 80
clusterRole:
  annotations: {}
  clusterRoleBinding:
    annotations: {}
    name: ""
  create: false
  name: ""
  rules: []
command:
  extraArgs: []
  name: otelcol-k8s
config:
  exporters:
    debug: {}
    otlp/tempo:
      endpoint: tempo.monitoring.svc.cluster.local:4317
      tls:
        insecure: true
  extensions:
    health_check:
      endpoint: ${env:MY_POD_IP}:13133
  processors:
    batch: {}
    memory_limiter:
      check_interval: 5s
      limit_percentage: 80
      spike_limit_percentage: 25
  receivers:
    jaeger:
      protocols:
        grpc:
          endpoint: ${env:MY_POD_IP}:14250
        thrift_compact:
          endpoint: ${env:MY_POD_IP}:6831
        thrift_http:
          endpoint: ${env:MY_POD_IP}:14268
    otlp:
      protocols:
        grpc:
          endpoint: ${env:MY_POD_IP}:4317
        http:
          endpoint: ${env:MY_POD_IP}:4318
    prometheus:
      config:
        scrape_configs:
        - job_name: opentelemetry-collector
          scrape_interval: 10s
          static_configs:
          - targets:
            - ${env:MY_POD_IP}:8888
    zipkin:
      endpoint: ${env:MY_POD_IP}:9411
  service:
    extensions:
    - health_check
    pipelines:
      logs:
        exporters:
        - debug
        processors:
        - memory_limiter
        - batch
        receivers:
        - otlp
      metrics:
        exporters:
        - debug
        processors:
        - memory_limiter
        - batch
        receivers:
        - otlp
      traces:
        exporters:
        - otlp/tempo
        processors:
        - memory_limiter
        - batch
        receivers:
        - otlp
    telemetry:
      metrics:
        readers:
        - pull:
            exporter:
              prometheus:
                host: ${env:MY_POD_IP}
                port: 8888
      resource:
        host.name: ${env:OTEL_K8S_NODE_NAME}
        k8s.namespace.name: ${env:OTEL_K8S_NAMESPACE}
        k8s.node.ip: ${env:OTEL_K8S_NODE_IP}
        k8s.node.name: ${env:OTEL_K8S_NODE_NAME}
        k8s.pod.ip: ${env:OTEL_K8S_POD_IP}
        k8s.pod.name: ${env:OTEL_K8S_POD_NAME}
configMap:
  create: true
  existingName: ""
dnsConfig: {}
dnsPolicy: ""
enableConfigChecksumAnnotation: true
extraContainers: []
extraEnvs: []
extraEnvsFrom: []
extraManifests: []
extraVolumeMounts: []
extraVolumes: []
fullnameOverride: ""
hostAliases: []
hostNetwork: false
hostPID: false
httproute:
  annotations: {}
  apiVersion: ""
  enabled: false
  hostnames: []
  parentRefs: []
  rules: []
image:
  digest: ""
  pullPolicy: IfNotPresent
  repository: ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-k8s
  tag: ""
imagePullSecrets: []
ingress:
  additionalIngresses: []
  enabled: false
initContainers: []
internalTelemetryViaOTLP:
  endpoint: ""
  headers: []
  logs:
    enabled: false
    endpoint: ""
    headers: []
  metrics:
    enabled: false
    endpoint: ""
    headers: []
  traces:
    enabled: false
    endpoint: ""
    headers: []
lifecycleHooks: {}
livenessProbe:
  httpGet:
    path: /
    port: 13133
mode: deployment
nameOverride: ""
namespaceOverride: ""
networkPolicy:
  allowIngressFrom: []
  annotations: {}
  egressRules: []
  enabled: false
  extraIngressRules: []
nodeSelector: {}
podAnnotations: {}
podDisruptionBudget:
  enabled: false
podLabels: {}
podMonitor:
  enabled: false
  extraLabels: {}
  metricsEndpoints:
  - port: metrics
podSecurityContext: {}
ports:
  jaeger-compact:
    containerPort: 6831
    enabled: true
    hostPort: 6831
    protocol: UDP
    servicePort: 6831
  jaeger-grpc:
    containerPort: 14250
    enabled: true
    hostPort: 14250
    protocol: TCP
    servicePort: 14250
  jaeger-thrift:
    containerPort: 14268
    enabled: true
    hostPort: 14268
    protocol: TCP
    servicePort: 14268
  metrics:
    containerPort: 8888
    enabled: false
    protocol: TCP
    servicePort: 8888
  otlp:
    appProtocol: grpc
    containerPort: 4317
    enabled: true
    hostPort: 4317
    protocol: TCP
    servicePort: 4317
  otlp-http:
    containerPort: 4318
    enabled: true
    hostPort: 4318
    protocol: TCP
    servicePort: 4318
  zipkin:
    containerPort: 9411
    enabled: true
    hostPort: 9411
    protocol: TCP
    servicePort: 9411
presets:
  annotationDiscovery:
    logs:
      enabled: false
    metrics:
      enabled: false
  clusterMetrics:
    enabled: false
  hostMetrics:
    enabled: false
  kubeletMetrics:
    enabled: false
  kubernetesAttributes:
    enabled: false
    extractAllPodAnnotations: false
    extractAllPodLabels: false
  kubernetesEvents:
    enabled: false
    useK8sEventsReceiver: false
  kubernetesObjects:
    apiExtensions:
      enabled: true
    autoscaling:
      enabled: true
      vpa:
        enabled: false
    core:
      enabled: true
    enabled: false
    events:
      enabled: false
    networking:
      enabled: true
    policy:
      enabled: true
    rbac:
      enabled: true
    storage:
      enabled: true
    watch: false
  logsCollection:
    enabled: false
    includeCollectorLogs: false
    maxRecombineLogSize: 102400
    storeCheckpoints: false
  profiling:
    enabled: false
  resourceDetection:
    aks:
      enabled: false
    eks:
      enabled: false
    enabled: false
    env:
      enabled: true
    gcp:
      enabled: false
    k8s_api:
      enabled: true
priorityClassName: ""
prometheusRule:
  defaultRules:
    additionalRuleAnnotations: {}
    additionalRuleLabels: {}
    enabled: false
  enabled: false
  extraLabels: {}
  groups: []
readinessProbe:
  httpGet:
    path: /
    port: 13133
replicaCount: 1
resizePolicy: []
resources: {}
revisionHistoryLimit: 10
rewriteDeprecatedComponentNames: true
rollout:
  rollingUpdate: {}
  strategy: RollingUpdate
runtimeClassName: ""
schedulerName: ""
securityContext: {}
service:
  annotations: {}
  type: ClusterIP
serviceAccount:
  annotations: {}
  automountServiceAccountToken: true
  create: true
  name: ""
serviceMonitor:
  enabled: false
  extraLabels: {}
  metricRelabelings: []
  metricsEndpoints:
  - port: metrics
  relabelings: []
  sampleLimit: 0
shareProcessNamespace: false
startupProbe: {}
statefulset:
  persistentVolumeClaimRetentionPolicy:
    enabled: false
    whenDeleted: Retain
    whenScaled: Retain
  podManagementPolicy: Parallel
  volumeClaimTemplates: []
terminationGracePeriodSeconds: 30
tolerations: []
topologySpreadConstraints: []
useGOMEMLIMIT: true

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl get configmap -n opentelemetry
NAME                      DATA   AGE
kube-root-ca.crt          1      4h18m
opentelemetry-collector   1      4h14m

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl port-forward -n opentelemetry \
  deployment/opentelemetry-collector 8888:8888
Forwarding from 127.0.0.1:8888 -> 8888
Forwarding from [::1]:8888 -> 8888
Handling connection for 8888
Handling connection for 8888
E0911 15:22:39.880102   16884 portforward.go:522] "Unhandled Error" err="an error occurred forwarding 8888 -> 8888: error forwarding port 8888 to pod db1ba8d30dda776dd6ed9e4393e96ca1ac3be9fbcae575c4fe0e2053159b2682, uid : failed to execute portforward in network namespace \"/var/run/netns/cni-2871ff7c-8191-1535-defd-ab75a2eab811\": failed to connect to localhost:8888 inside namespace \"db1ba8d30dda776dd6ed9e4393e96ca1ac3be9fbcae575c4fe0e2053159b2682\", IPv4: dial tcp4 127.0.0.1:8888: connect: connection refused IPv6 dial tcp6 [::1]:8888: connect: connection refused "
error: lost connection to pod

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl port-forward -n opentelemetry   deployment/opentelemetry-collector 8888:8888
Forwarding from 127.0.0.1:8888 -> 8888
Forwarding from [::1]:8888 -> 8888
Handling connection for 8888
Handling connection for 8888
E0911 15:23:22.365572    3216 portforward.go:522] "Unhandled Error" err="an error occurred forwarding 8888 -> 8888: error forwarding port 8888 to pod db1ba8d30dda776dd6ed9e4393e96ca1ac3be9fbcae575c4fe0e2053159b2682, uid : failed to execute portforward in network namespace \"/var/run/netns/cni-2871ff7c-8191-1535-defd-ab75a2eab811\": failed to connect to localhost:8888 inside namespace \"db1ba8d30dda776dd6ed9e4393e96ca1ac3be9fbcae575c4fe0e2053159b2682\", IPv4: dial tcp4 127.0.0.1:8888: connect: connection refused IPv6 dial tcp6 [::1]:8888: connect: connection refused "
error: lost connection to pod

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl describe pod -n opentelemetry \
  $(kubectl get pod -n opentelemetry \
    -l app.kubernetes.io/instance=opentelemetry-collector \
    -o jsonpath='{.items[0].metadata.name}') \
  | grep -A20 -B5 "Ports:"
Containers:
  opentelemetry-collector:
    Container ID:  containerd://87159dcc7e0d8427807e7b3d1dcb85548373a9d74ec3212541151e7d711b63bb
    Image:         ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-k8s:0.160.0
    Image ID:      ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-k8s@sha256:76d7a04f2291da1d8b7ce259468d09f0f9f44f71f67a5737539f64ca82b5bdb1
    Ports:         6831/UDP (jaeger-compact), 14250/TCP (jaeger-grpc), 14268/TCP (jaeger-thrift), 4317/TCP (otlp), 4318/TCP (otlp-http), 9411/TCP (zipkin)
    Host Ports:    0/UDP (jaeger-compact), 0/TCP (jaeger-grpc), 0/TCP (jaeger-thrift), 0/TCP (otlp), 0/TCP (otlp-http), 0/TCP (zipkin)
    Command:
      /otelcol-k8s
    Args:
      --config=/conf/relay.yaml
    State:          Running
      Started:      Fri, 11 Sep 2026 15:00:26 +0530
    Ready:          True
    Restart Count:  0
    Liveness:       http-get http://:13133/ delay=0s timeout=1s period=10s #success=1 #failure=3
    Readiness:      http-get http://:13133/ delay=0s timeout=1s period=10s #success=1 #failure=3
    Environment:
      MY_POD_IP:            (v1:status.podIP)
      OTEL_K8S_NODE_NAME:   (v1:spec.nodeName)
      OTEL_K8S_NODE_IP:     (v1:status.hostIP)
      OTEL_K8S_NAMESPACE:  opentelemetry (v1:metadata.namespace)
      OTEL_K8S_POD_NAME:   opentelemetry-collector-9cccb6864-p7kk5 (v1:metadata.name)
      OTEL_K8S_POD_IP:      (v1:status.podIP)
    Mounts:
      /conf from opentelemetry-collector-configmap (rw)
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-rwjg8 (ro)

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ kubectl run otel-test \
  --rm -it \
  --image=curlimages/curl \
  -n roboshop \
  -- sh
All commands and output from this session will be recorded in container logs, including credentials and sensitive information passed through the command prompt.
If you don't see a command prompt, try pressing enter.
~ $ curl -v http://opentelemetry-collector.opentelemetry.svc.cluster.local:4318
* Host opentelemetry-collector.opentelemetry.svc.cluster.local:4318 was resolved.
* IPv6: (none)
* IPv4: 10.96.112.155
*   Trying 10.96.112.155:4318...
* Established connection to opentelemetry-collector.opentelemetry.svc.cluster.local (10.96.112.155 port 4318) from 10.244.1.38 port 52894
* using HTTP/1.x
> GET / HTTP/1.1
> Host: opentelemetry-collector.opentelemetry.svc.cluster.local:4318
> User-Agent: curl/8.22.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 404 Not Found
< Content-Type: text/plain; charset=utf-8
< X-Content-Type-Options: nosniff
< Date: Fri, 11 Sep 2026 09:56:30 GMT
< Content-Length: 19
<
404 page not found
* Connection #0 to host opentelemetry-collector.opentelemetry.svc.cluster.local:4318 left intact
~ $ exit
Session ended, resume using 'kubectl attach otel-test -c otel-test -n roboshop -i -t' command
pod "otel-test" deleted from roboshop namespace

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD/dispatch-argocd (main)
$ cd ../

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD
$ ls
cart-argocd/       dispatch-argocd/  mongodb-argocd/  payments-argocd/  redis-argocd/        shipping-argocd/
catalogue-argocd/  frontend-argocd/  mysql-argocd/    rabbitmq-argocd/  resource-quota.yaml  user-argocd/

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/CD
$ cd ../

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop
$ cd monitoring/

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/monitoring
$ ls
alloy-values.yaml  elasticsearch.yaml  grafana-values.yaml  kibana.yaml  loki-values.yaml  observability/  otel-value-debug.yaml  otel-values.yaml

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/monitoring
$ ls
alloy-values.yaml  elasticsearch.yaml  grafana-values.yaml  kibana.yaml  loki-values.yaml  observability/  otel-value-debug.yaml  otel-values.yaml

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/monitoring
$ helm upgrade opentelemetry-collector \
  open-telemetry/opentelemetry-collector \
  -n opentelemetry \
  -f otel-values-debug.yaml
Error: open otel-values-debug.yaml: The system cannot find the file specified.

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/monitoring
$ helm upgrade opentelemetry-collector   open-telemetry/opentelemetry-collector   -n opentelemetry   -f otel-values-debug.yaml
Error: open otel-values-debug.yaml: The system cannot find the file specified.

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/monitoring
$ helm upgrade opentelemetry-collector   open-telemetry/opentelemetry-collector   -n opentelemetry   -f otel-values-debug.yaml
Release "opentelemetry-collector" has been upgraded. Happy Helming!
NAME: opentelemetry-collector
LAST DEPLOYED: Fri Sep 11 15:32:27 2026
NAMESPACE: opentelemetry
STATUS: deployed
REVISION: 3
TEST SUITE: None
NOTES:
[WARNING] No resource limits or requests were set. Consider setting resource requests and limits for your collector(s) via the `resources` field.

[WARNING] "useGOMEMLIMIT" is enabled but memory limits have not been supplied so the GOMEMLIMIT env var could not be added. Solve this problem by setting resources.limits.memory or disabling useGOMEMLIMIT

[DEPRECATION] Exporter 'otlp' has been renamed to 'otlp_grpc'. Your config has been automatically rewritten for this release. Please update your values.yaml — auto-rewrite will be removed in a future release. See UPGRADING.md.
[DEPRECATION] Pipeline 'traces' references renamed exporter 'otlp'. It has been automatically rewritten to 'otlp_grpc' for this release. Please update your values.yaml — auto-rewrite will be removed in a future release. See UPGRADING.md.

venka@Think-VVRAM MINGW64 /c/AZURE/roboshop/monitoring
$
```
