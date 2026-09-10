
Grafana complete view for Roboshop project:
-------------------------------------------

------------------------------------------------------------------------------------------------------------
<img width="931" height="475" alt="image" src="https://github.com/user-attachments/assets/88f33b41-7202-48fe-ab84-483ccd83807a" />
-----------------------------------------------------------------------------------------------------------

kubernetes-cluster-overview:
----------------------------
--------------------------------------------------------------------------------------------------------
<img width="1918" height="531" alt="image" src="https://github.com/user-attachments/assets/f722660c-7ca4-4c0f-b474-1d95b48a66d3" />

-----------------------------------------------------------------------------------------------------------
login into your grafana , In home click on dashboard, go top right corner, clcik on  new as shown above and click on import kubernetes-cluster-overview.json (which we have created in our repository)  


---------------------------------------------------------------------------------------------------------

```
{
  "annotations": {
    "list": [
      {
        "builtIn": 1,
        "datasource": {
          "type": "grafana",
          "uid": "-- Grafana --"
        },
        "enable": true,
        "hide": true,
        "iconColor": "rgba(0,211,255,1)",
        "name": "Annotations & Alerts",
        "type": "dashboard"
      }
    ]
  },
  "editable": true,
  "fiscalYearStartMonth": 0,
  "graphTooltip": 1,
  "id": null,
  "links": [],
  "panels": [
    {
      "id": 1,
      "type": "stat",
      "title": "Total Nodes",
      "gridPos": {
        "h": 4,
        "w": 8,
        "x": 0,
        "y": 0
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "expr": "count(kube_node_info)",
          "refId": "A"
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "short"
        },
        "overrides": []
      },
      "options": {
        "reduceOptions": {
          "calcs": [
            "lastNotNull"
          ],
          "fields": "",
          "values": false
        },
        "orientation": "auto",
        "textMode": "auto",
        "colorMode": "value"
      }
    },
    {
      "id": 2,
      "type": "stat",
      "title": "Total Pods",
      "gridPos": {
        "h": 4,
        "w": 8,
        "x": 8,
        "y": 0
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "expr": "count(kube_pod_info)",
          "refId": "A"
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "short"
        },
        "overrides": []
      },
      "options": {
        "reduceOptions": {
          "calcs": [
            "lastNotNull"
          ],
          "fields": "",
          "values": false
        },
        "orientation": "auto",
        "textMode": "auto",
        "colorMode": "value"
      }
    },
    {
      "id": 3,
      "type": "stat",
      "title": "Running Pods",
      "gridPos": {
        "h": 4,
        "w": 8,
        "x": 16,
        "y": 0
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "expr": "count(kube_pod_status_phase{phase=\"Running\"})",
          "refId": "A"
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "short"
        },
        "overrides": []
      },
      "options": {
        "reduceOptions": {
          "calcs": [
            "lastNotNull"
          ],
          "fields": "",
          "values": false
        },
        "orientation": "auto",
        "textMode": "auto",
        "colorMode": "value"
      }
    },
    {
      "id": 4,
      "type": "timeseries",
      "title": "Node CPU Usage",
      "gridPos": {
        "h": 8,
        "w": 12,
        "x": 0,
        "y": 5
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "expr": "sum by (instance) (rate(node_cpu_seconds_total{mode!=\"idle\"}[5m]))",
          "refId": "A",
          "legendFormat": "{{instance}}"
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "cores"
        },
        "overrides": []
      },
      "options": {
        "legend": {
          "displayMode": "list",
          "placement": "bottom"
        },
        "tooltip": {
          "mode": "multi"
        }
      }
    },
    {
      "id": 5,
      "type": "timeseries",
      "title": "Node Memory Usage",
      "gridPos": {
        "h": 8,
        "w": 12,
        "x": 12,
        "y": 5
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "expr": "node_memory_MemTotal_bytes - node_memory_MemAvailable_bytes",
          "refId": "A",
          "legendFormat": "{{instance}}"
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "bytes"
        },
        "overrides": []
      },
      "options": {
        "legend": {
          "displayMode": "list",
          "placement": "bottom"
        },
        "tooltip": {
          "mode": "multi"
        }
      }
    },
    {
      "id": 6,
      "type": "timeseries",
      "title": "Pods by Namespace",
      "gridPos": {
        "h": 8,
        "w": 12,
        "x": 0,
        "y": 13
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "expr": "sum by (namespace) (kube_pod_info)",
          "refId": "A",
          "legendFormat": "{{namespace}}"
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "short"
        },
        "overrides": []
      },
      "options": {
        "legend": {
          "displayMode": "list",
          "placement": "bottom"
        },
        "tooltip": {
          "mode": "multi"
        }
      }
    },
    {
      "id": 7,
      "type": "timeseries",
      "title": "Pod Restarts",
      "gridPos": {
        "h": 8,
        "w": 12,
        "x": 12,
        "y": 13
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "expr": "sum by (namespace,pod) (kube_pod_container_status_restarts_total)",
          "refId": "A",
          "legendFormat": "{{namespace}} / {{pod}}"
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "short"
        },
        "overrides": []
      },
      "options": {
        "legend": {
          "displayMode": "list",
          "placement": "bottom"
        },
        "tooltip": {
          "mode": "multi"
        }
      }
    }
  ],
  "refresh": "30s",
  "schemaVersion": 39,
  "tags": [
    "kubernetes",
    "prometheus"
  ],
  "templating": {
    "list": []
  },
  "time": {
    "from": "now-1h",
    "to": "now"
  },
  "timepicker": {},
  "timezone": "",
  "title": "Kubernetes Cluster Overview",
  "uid": "k8s-cluster",
  "version": 2
}
```
-----------------------------------------------------------------------------------------------------------
Finaly kubernetes-cluster-overview:
----------------------------
<img width="1903" height="946" alt="image" src="https://github.com/user-attachments/assets/40fe38e5-c146-4198-8fad-216b5893983c" />

------------------------------------------------------------------------------------------------------------

Roboshop Logs Overview:
-----------------------
--------------------------------------------------------------------------------------------------------
<img width="1918" height="531" alt="image" src="https://github.com/user-attachments/assets/f722660c-7ca4-4c0f-b474-1d95b48a66d3" />

-----------------------------------------------------------------------------------------------------------
login into your grafana , In home click on dashboard, go top right corner, clcik on  new as shown above and click on import kubernetes-logs-overview.json (which we have created in our repository)  
--------------------------------------------------------------------------------------------------------------

```
{
  "$schema": "https://json.schemastore.org/grafana-dashboard.json",
  "annotations": {
    "list": [
      {
        "builtIn": 1,
        "datasource": {
          "type": "grafana",
          "uid": "-- Grafana --"
        },
        "enable": true,
        "hide": true,
        "iconColor": "rgba(0,211,255,1)",
        "name": "Annotations & Alerts",
        "type": "dashboard"
      }
    ]
  },
  "editable": true,
  "fiscalYearStartMonth": 0,
  "graphTooltip": 1,
  "id": null,
  "links": [],
  "liveNow": false,
  "panels": [
    {
      "datasource": {
        "type": "loki",
        "uid": "${DS_LOKI}"
      },
      "gridPos": {
        "h": 10,
        "w": 24,
        "x": 0,
        "y": 0
      },
      "id": 1,
      "options": {
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": true,
        "showTime": true,
        "sortOrder": "Descending",
        "wrapLines": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "${DS_LOKI}"
          },
          "editorMode": "code",
          "expr": "{namespace=\"$namespace\"}",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "All Roboshop Logs",
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "${DS_LOKI}"
      },
      "gridPos": {
        "h": 10,
        "w": 12,
        "x": 0,
        "y": 10
      },
      "id": 2,
      "options": {
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": true,
        "showTime": true,
        "sortOrder": "Descending",
        "wrapLines": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "${DS_LOKI}"
          },
          "editorMode": "code",
          "expr": "{namespace=\"$namespace\"} |~ \"(?i)error|exception|failed|fatal\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "Errors",
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "${DS_LOKI}"
      },
      "gridPos": {
        "h": 10,
        "w": 12,
        "x": 12,
        "y": 10
      },
      "id": 3,
      "options": {
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": true,
        "showTime": true,
        "sortOrder": "Descending",
        "wrapLines": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "${DS_LOKI}"
          },
          "editorMode": "code",
          "expr": "{namespace=\"$namespace\"} |~ \"(?i)warn|warning\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "Warnings",
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "${DS_LOKI}"
      },
      "gridPos": {
        "h": 10,
        "w": 12,
        "x": 0,
        "y": 20
      },
      "id": 4,
      "options": {
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": true,
        "showTime": true,
        "sortOrder": "Descending",
        "wrapLines": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "${DS_LOKI}"
          },
          "editorMode": "code",
          "expr": "{namespace=\"$namespace\", app=\"frontend\"}",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "Frontend",
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "${DS_LOKI}"
      },
      "gridPos": {
        "h": 10,
        "w": 12,
        "x": 12,
        "y": 20
      },
      "id": 5,
      "options": {
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": true,
        "showTime": true,
        "sortOrder": "Descending",
        "wrapLines": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "${DS_LOKI}"
          },
          "editorMode": "code",
          "expr": "{namespace=\"$namespace\", app=\"catalogue\"}",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "Catalogue",
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "${DS_LOKI}"
      },
      "gridPos": {
        "h": 10,
        "w": 12,
        "x": 0,
        "y": 30
      },
      "id": 6,
      "options": {
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": true,
        "showTime": true,
        "sortOrder": "Descending",
        "wrapLines": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "${DS_LOKI}"
          },
          "editorMode": "code",
          "expr": "{namespace=\"$namespace\", app=\"cart\"}",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "Cart",
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "${DS_LOKI}"
      },
      "gridPos": {
        "h": 10,
        "w": 12,
        "x": 12,
        "y": 30
      },
      "id": 7,
      "options": {
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": true,
        "showTime": true,
        "sortOrder": "Descending",
        "wrapLines": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "${DS_LOKI}"
          },
          "editorMode": "code",
          "expr": "{namespace=\"$namespace\", app=\"payment\"}",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "Payment",
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "${DS_LOKI}"
      },
      "gridPos": {
        "h": 10,
        "w": 12,
        "x": 0,
        "y": 40
      },
      "id": 8,
      "options": {
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": true,
        "showTime": true,
        "sortOrder": "Descending",
        "wrapLines": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "${DS_LOKI}"
          },
          "editorMode": "code",
          "expr": "{namespace=\"$namespace\", app=\"shipping\"}",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "Shipping",
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "${DS_LOKI}"
      },
      "gridPos": {
        "h": 10,
        "w": 12,
        "x": 12,
        "y": 40
      },
      "id": 9,
      "options": {
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": true,
        "showTime": true,
        "sortOrder": "Descending",
        "wrapLines": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "${DS_LOKI}"
          },
          "editorMode": "code",
          "expr": "{namespace=\"$namespace\", app=\"dispatch\"}",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "Dispatch",
      "type": "logs"
    }
  ],
  "refresh": "30s",
  "schemaVersion": 39,
  "tags": [
    "roboshop",
    "loki",
    "logs"
  ],
  "templating": {
    "list": [
      {
        "current": {},
        "includeAll": false,
        "label": "Loki",
        "multi": false,
        "name": "DS_LOKI",
        "options": [],
        "query": "loki",
        "refresh": 1,
        "type": "datasource"
      },
      {
        "current": {
          "selected": true,
          "text": "roboshop",
          "value": "roboshop"
        },
        "includeAll": false,
        "label": "Namespace",
        "multi": false,
        "name": "namespace",
        "options": [
          {
            "selected": true,
            "text": "roboshop",
            "value": "roboshop"
          }
        ],
        "query": "roboshop",
        "type": "custom"
      }
    ]
  },
  "time": {
    "from": "now-1h",
    "to": "now"
  },
  "timepicker": {},
  "timezone": "browser",
  "title": "Roboshop Logs Overview",
  "uid": "roboshop-logs",
  "version": 1
}
```
Finally kuberenetes logs view: 
-----------------------------------------------------------------------------------------------------------
<img width="1885" height="937" alt="image" src="https://github.com/user-attachments/assets/ade2e01d-91df-4eaa-ac5e-fb13b0f379b6" />
-----------------------------------------------------------------------------------------------------------

roboshop-application-overview:
-----------------------------
-----------------------------------------------------------------------------------------------------------
<img width="1917" height="957" alt="image" src="https://github.com/user-attachments/assets/0a5c5d0b-ae94-4b02-a01f-fd8b740987d7" />

-----------------------------------------------------------------------------------------------------------
login into your grafana , In home click on dashboard, go top right corner, clcik on  new as shown above and click on import roboshop-application-overview.json (which we have created in our repository)  

-----------------------------------------------------------------------------------------------------------

```
{
  "annotations": {
    "list": [
      {
        "builtIn": 1,
        "datasource": {
          "type": "grafana",
          "uid": "-- Grafana --"
        },
        "enable": true,
        "hide": true,
        "iconColor": "rgba(0,211,255,1)",
        "name": "Annotations & Alerts",
        "type": "dashboard"
      }
    ]
  },
  "editable": true,
  "fiscalYearStartMonth": 0,
  "graphTooltip": 1,
  "id": null,
  "links": [],
  "panels": [
    {
      "id": 1,
      "type": "stat",
      "title": "Running Roboshop Pods",
      "gridPos": {
        "h": 4,
        "w": 6,
        "x": 0,
        "y": 0
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "sum(kube_pod_status_phase{namespace=\"roboshop\",phase=\"Running\"})",
          "instant": true
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "short"
        },
        "overrides": []
      },
      "options": {
        "reduceOptions": {
          "calcs": [
            "lastNotNull"
          ],
          "fields": "",
          "values": false
        },
        "orientation": "auto",
        "textMode": "auto",
        "colorMode": "value"
      }
    },
    {
      "id": 2,
      "type": "stat",
      "title": "Pod Restarts",
      "gridPos": {
        "h": 4,
        "w": 6,
        "x": 6,
        "y": 0
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "sum(kube_pod_container_status_restarts_total{namespace=\"roboshop\"})",
          "instant": true
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "short"
        },
        "overrides": []
      },
      "options": {
        "reduceOptions": {
          "calcs": [
            "lastNotNull"
          ],
          "fields": "",
          "values": false
        },
        "orientation": "auto",
        "textMode": "auto",
        "colorMode": "value"
      }
    },
    {
      "id": 3,
      "type": "stat",
      "title": "CPU Usage",
      "gridPos": {
        "h": 4,
        "w": 6,
        "x": 12,
        "y": 0
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "sum(rate(container_cpu_usage_seconds_total{namespace=\"roboshop\",container!=\"\",container!=\"POD\",image!=\"\"}[5m]))",
          "instant": true
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "cores"
        },
        "overrides": []
      },
      "options": {
        "reduceOptions": {
          "calcs": [
            "lastNotNull"
          ],
          "fields": "",
          "values": false
        },
        "orientation": "auto",
        "textMode": "auto",
        "colorMode": "value"
      }
    },
    {
      "id": 4,
      "type": "stat",
      "title": "Memory Usage",
      "gridPos": {
        "h": 4,
        "w": 6,
        "x": 18,
        "y": 0
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "sum(container_memory_working_set_bytes{namespace=\"roboshop\",container!=\"\",container!=\"POD\",image!=\"\"})",
          "instant": true
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "bytes"
        },
        "overrides": []
      },
      "options": {
        "reduceOptions": {
          "calcs": [
            "lastNotNull"
          ],
          "fields": "",
          "values": false
        },
        "orientation": "auto",
        "textMode": "auto",
        "colorMode": "value"
      }
    },
    {
      "id": 5,
      "type": "timeseries",
      "title": "CPU Usage by Pod",
      "gridPos": {
        "h": 8,
        "w": 12,
        "x": 0,
        "y": 5
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "sum by (pod) (rate(container_cpu_usage_seconds_total{namespace=\"roboshop\",container!=\"\",container!=\"POD\",image!=\"\"}[5m]))",
          "legendFormat": "{{pod}}"
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "cores"
        },
        "overrides": []
      },
      "options": {
        "legend": {
          "displayMode": "list",
          "placement": "bottom"
        },
        "tooltip": {
          "mode": "multi"
        }
      }
    },
    {
      "id": 6,
      "type": "timeseries",
      "title": "Memory Usage by Pod",
      "gridPos": {
        "h": 8,
        "w": 12,
        "x": 12,
        "y": 5
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "sum by (pod) (container_memory_working_set_bytes{namespace=\"roboshop\",container!=\"\",container!=\"POD\",image!=\"\"})",
          "legendFormat": "{{pod}}"
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "bytes"
        },
        "overrides": []
      },
      "options": {
        "legend": {
          "displayMode": "list",
          "placement": "bottom"
        },
        "tooltip": {
          "mode": "multi"
        }
      }
    },
    {
      "id": 7,
      "type": "timeseries",
      "title": "Pod Restarts by Pod",
      "gridPos": {
        "h": 8,
        "w": 12,
        "x": 0,
        "y": 13
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "sum by (pod) (kube_pod_container_status_restarts_total{namespace=\"roboshop\"})",
          "legendFormat": "{{pod}}"
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "short"
        },
        "overrides": []
      },
      "options": {
        "legend": {
          "displayMode": "list",
          "placement": "bottom"
        },
        "tooltip": {
          "mode": "multi"
        }
      }
    },
    {
      "id": 8,
      "type": "timeseries",
      "title": "CPU Requests by Pod",
      "gridPos": {
        "h": 8,
        "w": 12,
        "x": 12,
        "y": 13
      },
      "datasource": {
        "type": "prometheus",
        "uid": "efxpgykv5oef4a"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "sum by (pod) (kube_pod_container_resource_requests{namespace=\"roboshop\",resource=\"cpu\"})",
          "legendFormat": "{{pod}}"
        }
      ],
      "fieldConfig": {
        "defaults": {
          "unit": "cores"
        },
        "overrides": []
      },
      "options": {
        "legend": {
          "displayMode": "list",
          "placement": "bottom"
        },
        "tooltip": {
          "mode": "multi"
        }
      }
    }
  ],
  "refresh": "30s",
  "schemaVersion": 39,
  "tags": [
    "roboshop",
    "kubernetes",
    "prometheus"
  ],
  "templating": {
    "list": []
  },
  "time": {
    "from": "now-1h",
    "to": "now"
  },
  "timepicker": {},
  "timezone": "",
  "title": "Roboshop Application Overview",
  "uid": "roboshop-app",
  "version": 2
}

```
----------------------------------------------------------------------------------------------------------


Author: Venkata Ram Vanimina
