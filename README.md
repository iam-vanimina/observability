
Grafana complete view for Roboshop project:


<img width="931" height="475" alt="image" src="https://github.com/user-attachments/assets/88f33b41-7202-48fe-ab84-483ccd83807a" />


<img width="944" height="466" alt="image" src="https://github.com/user-attachments/assets/f8bd1daf-0fe4-4c61-90e1-7e5fc061b499" />


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
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<img width="1908" height="957" alt="image" src="https://github.com/user-attachments/assets/2296b181-5070-4c9c-bc8e-46e1efd10763" />
-----------------------------------------------------------------------------------------------------------

<img width="1900" height="939" alt="image" src="https://github.com/user-attachments/assets/bfeed73d-d2d3-4119-adac-10d3fded8a2e" />

-----------------------------------------------------------------------------------------------------------

```
{
  "id": null,
  "uid": "roboshop-logs",
  "title": "Roboshop Logs Overview",
  "tags": [
    "roboshop",
    "loki",
    "logs"
  ],
  "timezone": "",
  "schemaVersion": 39,
  "version": 1,
  "editable": true,
  "refresh": "30s",
  "graphTooltip": 1,
  "time": {
    "from": "now-1h",
    "to": "now"
  },
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
  "templating": {
    "list": [
      {
        "name": "DS_LOKI",
        "label": "Loki",
        "type": "datasource",
        "query": "loki",
        "refresh": 1,
        "current": {},
        "options": [],
        "includeAll": false,
        "multi": false
      },
      {
        "name": "namespace",
        "label": "Namespace",
        "type": "custom",
        "query": "roboshop",
        "current": {
          "text": "roboshop",
          "value": "roboshop"
        },
        "options": [
          {
            "text": "roboshop",
            "value": "roboshop",
            "selected": true
          }
        ],
        "includeAll": false,
        "multi": false
      }
    ]
  },
  "panels": [
    {
      "id": 1,
      "type": "logs",
      "title": "All Roboshop Logs",
      "gridPos": {
        "x": 0,
        "y": 0,
        "w": 24,
        "h": 10
      },
      "datasource": {
        "type": "loki",
        "uid": "loki"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "{namespace=\"$namespace\"}",
          "queryType": "range"
        }
      ],
      "options": {
        "showTime": true,
        "showLabels": true,
        "showCommonLabels": false,
        "wrapLines": true,
        "prettifyLogMessage": false,
        "enableLogDetails": true,
        "sortOrder": "Descending"
      }
    },
    {
      "id": 2,
      "type": "logs",
      "title": "Errors",
      "gridPos": {
        "x": 0,
        "y": 10,
        "w": 12,
        "h": 10
      },
      "datasource": {
        "type": "loki",
        "uid": "loki"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "{namespace=\"$namespace\"} |~ \"(?i)error|exception|failed|fatal\"",
          "queryType": "range"
        }
      ],
      "options": {
        "showTime": true,
        "showLabels": true,
        "showCommonLabels": false,
        "wrapLines": true,
        "prettifyLogMessage": false,
        "enableLogDetails": true,
        "sortOrder": "Descending"
      }
    },
    {
      "id": 3,
      "type": "logs",
      "title": "Warnings",
      "gridPos": {
        "x": 12,
        "y": 10,
        "w": 12,
        "h": 10
      },
      "datasource": {
        "type": "loki",
        "uid": "loki"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "{namespace=\"$namespace\"} |~ \"(?i)warn|warning\"",
          "queryType": "range"
        }
      ],
      "options": {
        "showTime": true,
        "showLabels": true,
        "showCommonLabels": false,
        "wrapLines": true,
        "prettifyLogMessage": false,
        "enableLogDetails": true,
        "sortOrder": "Descending"
      }
    },
    {
      "id": 4,
      "type": "logs",
      "title": "Frontend",
      "gridPos": {
        "x": 0,
        "y": 20,
        "w": 12,
        "h": 10
      },
      "datasource": {
        "type": "loki",
        "uid": "loki"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "{namespace=\"$namespace\", app=\"frontend\"}",
          "queryType": "range"
        }
      ],
      "options": {
        "showTime": true,
        "showLabels": true,
        "showCommonLabels": false,
        "wrapLines": true,
        "prettifyLogMessage": false,
        "enableLogDetails": true,
        "sortOrder": "Descending"
      }
    },
    {
      "id": 5,
      "type": "logs",
      "title": "Catalogue",
      "gridPos": {
        "x": 12,
        "y": 20,
        "w": 12,
        "h": 10
      },
      "datasource": {
        "type": "loki",
        "uid": "loki"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "{namespace=\"$namespace\", app=\"catalogue\"}",
          "queryType": "range"
        }
      ],
      "options": {
        "showTime": true,
        "showLabels": true,
        "showCommonLabels": false,
        "wrapLines": true,
        "prettifyLogMessage": false,
        "enableLogDetails": true,
        "sortOrder": "Descending"
      }
    },
    {
      "id": 6,
      "type": "logs",
      "title": "Cart",
      "gridPos": {
        "x": 0,
        "y": 30,
        "w": 12,
        "h": 10
      },
      "datasource": {
        "type": "loki",
        "uid": "loki"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "{namespace=\"$namespace\", app=\"cart\"}",
          "queryType": "range"
        }
      ],
      "options": {
        "showTime": true,
        "showLabels": true,
        "showCommonLabels": false,
        "wrapLines": true,
        "prettifyLogMessage": false,
        "enableLogDetails": true,
        "sortOrder": "Descending"
      }
    },
    {
      "id": 7,
      "type": "logs",
      "title": "Payment",
      "gridPos": {
        "x": 12,
        "y": 30,
        "w": 12,
        "h": 10
      },
      "datasource": {
        "type": "loki",
        "uid": "loki"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "{namespace=\"$namespace\", app=\"payment\"}",
          "queryType": "range"
        }
      ],
      "options": {
        "showTime": true,
        "showLabels": true,
        "showCommonLabels": false,
        "wrapLines": true,
        "prettifyLogMessage": false,
        "enableLogDetails": true,
        "sortOrder": "Descending"
      }
    },
    {
      "id": 8,
      "type": "logs",
      "title": "Shipping",
      "gridPos": {
        "x": 0,
        "y": 40,
        "w": 12,
        "h": 10
      },
      "datasource": {
        "type": "loki",
        "uid": "loki"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "{namespace=\"$namespace\", app=\"shipping\"}",
          "queryType": "range"
        }
      ],
      "options": {
        "showTime": true,
        "showLabels": true,
        "showCommonLabels": false,
        "wrapLines": true,
        "prettifyLogMessage": false,
        "enableLogDetails": true,
        "sortOrder": "Descending"
      }
    },
    {
      "id": 9,
      "type": "logs",
      "title": "Dispatch",
      "gridPos": {
        "x": 12,
        "y": 40,
        "w": 12,
        "h": 10
      },
      "datasource": {
        "type": "loki",
        "uid": "loki"
      },
      "targets": [
        {
          "refId": "A",
          "expr": "{namespace=\"$namespace\", app=\"dispatch\"}",
          "queryType": "range"
        }
      ],
      "options": {
        "showTime": true,
        "showLabels": true,
        "showCommonLabels": false,
        "wrapLines": true,
        "prettifyLogMessage": false,
        "enableLogDetails": true,
        "sortOrder": "Descending"
      }
    }
  ]
}
```
