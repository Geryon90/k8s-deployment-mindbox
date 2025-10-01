# Web App Kubernetes Deployment

## Task
- Multi-zone cluster (3 zones, 5 nodes)
- Application requires 5–10 seconds for initialization
- Peak load: 4 pods handle the load
- Resources: CPU 0.1 (stable), memory 128Mi
- Daily load cycle: much lower traffic at night
- High availability required with minimal resource usage

## Solution
- Deployment with 2 replicas and HPA scaling up to 4 replicas
- PodDisruptionBudget ensures minimum availability
- PodAntiAffinity + podTopologySpreadConstraints for even distribution across nodes and zones
- Configured probes (startup, readiness, liveness) for correct application startup
- Pod resources tuned for average and peak load
- YAML manifest includes comments explaining the decisions made
