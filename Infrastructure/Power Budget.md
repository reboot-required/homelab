---
type: note
tags:
  - infrastructure
  - power
---

# Power Budget

> [!info] Estimates
> These are nameplate and observed-idle estimates, not metered figures. The two
> [[Smart Plugs|smart plugs]] measure real draw at the rack and in the living
> room — once [[Grafana]] has a power dashboard, replace this page's numbers
> with measured ones.

## Always-on

| Node | kWh / year |
|---|---:|
| [[bill-the-pony.shire]] | 166 |
| [[rohan.shire]] | 166 |
| [[gondor.shire]] | 166 |
| [[isengard.shire]] | 140 |
| [[valinor.shire]] | 263 |
| [[the.shire]] | 92 |
| [[bree.shire]] | 79 |
| [[tuckborough.shire]] | 74 |
| [[greenway.shire]] | 61 |
| [[hobbiton.shire]] | 57 |
| [[bywater.shire]] | 33 |
| [[gondolin.shire]] | ~33 (estimated — see below) |
| [[buckland.shire]] | 26 |
| [[overhill.shire]] | 20 |
| [[stock.shire]] | 20 |
| [[crickhollow.shire]] | 20 |
| [[proudfoot-00.shire]] – [[proudfoot-04.shire]] | 15 combined |
| [[took-00.shire]], [[took-01.shire]] | ~13 combined |
| **Total** | **≈ 1 444 kWh / year** |

At €0.30/kWh that is roughly **€430 a year**. Substitute your own tariff — the
number moves a lot.

## Not counted

| Device | Why |
|---|---|
| [[iron-hills.shire]] | Workstation — on only while in use |
| TP-Link TL-SG105 | Bench switch — powered only during testing |

> [!bug] gondolin.shire was missing entirely
> The Raspberry Pi 2B running the MQTT broker did not appear in the old power
> table at all. It is estimated here at the same 33 kWh/year as the identical
> board in [[bywater.shire]]. Confirm it is actually powered continuously.

## Where the power goes

Four machines — the hypervisor, the two K3s workers and the LLM server —
account for roughly **530 kWh/year**, about 40% of the total. The entire fleet
of SBCs and IoT devices together is under 200.

That ratio is the argument for the consolidation in [[Future Hardware]]: one
efficient host doing the work of several mini-PCs saves more than retiring every
Pi in the rack.

## Related

- [[Hardware Summary]]
- [[Smart Plugs]]
- [[Dashboards]]
