[Home](../README.md) › [Monitoring](README.md) › Alerting

# Alerting

> 🚧 This page is a stub. Content to be added.

Alerting is planned as the next phase of monitoring maturity. Prometheus AlertManager or Grafana alerting will be used to send notifications when homelab services or nodes are unhealthy.

---

## Planned Alert Rules

| Alert | Condition | Severity |
|---|---|---|
| Node down | Host unreachable for > 5 min | Critical |
| Disk usage high | > 85% used | Warning |
| VM memory pressure | > 90% RAM used | Warning |
| Service restart loop | Container/service restarted > 3× in 10 min | Warning |
| IoT sensor offline | Sensor not reporting for > 15 min | Info |

---

## Planned Notification Channels

| Channel | Use Case |
|---|---|
| Telegram / Matrix | Push notifications to mobile |
| Email | Summary digests |
| Webhook (n8n) | Trigger automated remediation via `radagast.shire` |

---

## Planned Content

- AlertManager or Grafana alerting configuration
- Alert rule definitions
- Notification channel setup
- Silence and inhibition rules
- On-call / escalation policy (if applicable)

---

## See Also

- [stack-overview.md](stack-overview.md) — monitoring architecture
- [dashboards.md](dashboards.md) — Grafana dashboards
- [services/n8n.md](../services/n8n.md) — n8n workflow automation
