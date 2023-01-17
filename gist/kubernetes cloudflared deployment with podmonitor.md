---
date created: Tuesday, January 17th 2023, 5:32:26 am
date modified: Tuesday, January 17th 2023, 5:32:54 am
tags: 
  - k8s
  - kubernetes
  - prometheus
  - podmonitor
  - cloudflared
  - cloudflare
  - cloudflare_tunnel
---

# Kubernetes cloudflared Deployment with PodMonitor

I'm using this with the [prometheus-community/kube-prometheus-stack](https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack). The snippet below is only for the Cloudflare Tunnel deployment, the secret for authentication and the PodMonitor for Prometheus to scrape the information.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: cloudflared
    release: monitoring
  name: cf-tunnel
  namespace: default
spec:
  replicas: 2
  selector:
    matchLabels:
      tunnel: cf-tunnel
  strategy:
    rollingUpdate:
      maxSurge: 0
      maxUnavailable: 1
  template:
    metadata:
      labels:
        app: cloudflared
        release: monitoring
    spec:
      containers:
        - args:
            - tunnel
            - --no-autoupdate
            - --metrics
            - 0.0.0.0:8081
            - run
            - --token
            - $(token)
          envFrom:
            - secretRef:
                name: cf-tunnel
          env:
            - name: GOMAXPROCS
              value: "2"
            - name: TZ
              value: UTC
          image: cloudflare/cloudflared:latest
          imagePullPolicy: Always
          livenessProbe:
            failureThreshold: 3
            httpGet:
              path: /ready
              port: 8081
            initialDelaySeconds: 10
            periodSeconds: 10
          name: tunnel
          ports:
            - containerPort: 8081
              name: http-metrics
---
apiVersion: v1
data:
  token: <your secret token base64 encoded>
kind: Secret
metadata:
  name: cf-tunnel
  namespace: default
type: Opaque
---
apiVersion: monitoring.coreos.com/v1
kind: PodMonitor
metadata:
  name: cf-tunnel
  namespace: default
  labels:
    release: monitoring
    app: cloudflared
spec:
  selector:
    matchLabels:
      app: cloudflared
  podMetricsEndpoints:
  - port: http-metrics
```
