---
type: note
tags:
  - monitoring
  - alerting
---

# Alerting

Nothing alerts on anything today. If a node dies, the way you find out is that
something you were using stops working.

> [!info] Not yet
> Alerting depends on metrics that are not being collected — see
> [[Monitoring Stack]]. This page is a plan, not a description.

## Planned rules

| Alert | Condition | Severity |
|---|---|---|
| Node down | Unreachable > 5 min | Critical |
| Disk usage high | > 85% used | Warning |
| Memory pressure | > 90% RAM used | Warning |
| Restart loop | Service restarted > 3× in 10 min | Warning |
| Sensor offline | No report for > 15 min | Info |

Two additions the fleet argues for:

| Alert | Why |
|---|---|
| Rack temperature | [[proudfoot-00.shire]] measures it and nothing watches it |
| Backup did not run | [[Backup Strategy]] is the thing whose silent failure costs most |

## Planned channels

| Channel | For |
|---|---|
| Telegram or Matrix | Push to phone — critical only |
| Email | Digests |
| Webhook to [[n8n]] | Automated remediation via [[radagast.shire]] |

> [!warning] Alert on what you would act on
> Five rules that always fire teach you to ignore all five. Start with "node
> down" and "backup did not run", and add a rule only after it would have caught
> something real.

## To document

> [!todo] Stub
> - AlertManager or Grafana alerting — pick one
> - Rule definitions and where they live
> - Notification channel configuration (no tokens on this page)
> - Silences and inhibition

## Related

- [[Monitoring Stack]]
- [[Dashboards]]
- [[n8n]]
