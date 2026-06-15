# aap
Operator pods:
- automation-controller-operator-controller-manager
- automation-hub-operator-controller-manager
- resource-operator-controller-manager
- aap-gateway-operator-controller-manager
- eda-server-operator-controller-manager
- ansible-lightspeed-operator-controller-manager nếu bật

Automation Controller:
- controller-web
- controller-task
- controller-postgres nếu dùng DB nội bộ
- mesh ingress

Automation Hub:
- hub-api
- hub-content
- hub-worker
- hub-redis
- hub-postgres nếu dùng DB nội bộ

EDA:
- eda-api
- eda-activation-worker
- eda-default-worker
- eda-event-stream
- eda-scheduler

Platform Gateway:
- platform-gateway
- platform-gateway-redis
## GitOps và quản lý nội dung automation
Git Repository
├── inventories/
├── playbooks/
├── roles/
├── collections/
├── rulebooks/
├── group_vars/
├── host_vars/
├── workflows/
├── docs/
└── tests/

### Production banking
OpenShift:
- 3 master
- >= 3 worker dedicated hoặc infra worker
- Worker: 16-32 vCPU, 64-128 GB RAM tùy job volume
- StorageClass block + RWX/object storage

AAP:
- Platform Gateway HA
- Controller HA
- Hub HA
- EDA HA nếu dùng event-driven
- External PostgreSQL HA
- Automation Mesh execution nodes theo zone
- Backup + DR runbook