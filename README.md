# Enterprise Gateway Redundancy Lab

A high-availability enterprise gateway network designed and implemented using **Cisco Packet Tracer**.

This project demonstrates **HSRP-based gateway redundancy**, Active/Standby routers, virtual IP addressing, HSRP priority, preemption, WAN connectivity, default routing, interface tracking, automatic failover, and network troubleshooting.

---

## Project Overview

In a traditional network, end devices normally depend on a single default gateway.

If that gateway fails, users may lose network connectivity.

This project solves that problem by implementing **Hot Standby Router Protocol (HSRP)**.

Two Cisco routers share a **virtual gateway IP address**. One router operates as the **Active** router while the other operates as the **Standby** router.

If the Active router or its upstream WAN connection fails, the Standby router can automatically take over.

### Main Scenario

```text
                    ┌─────────────┐
                    │     ISP     │
                    │   Cisco     │
                    │    2911     │
                    └─────┬───┬───┘
                          │   │
                     WAN  │   │  WAN
                          │   │
                    ┌─────┘   └─────┐
                    │               │
                ┌───▼───┐       ┌───▼───┐
                │  R1   │       │  R2   │
                │ACTIVE │       │STANDBY│
                │  110  │       │  100  │
                └───┬───┘       └───┬───┘
                    │               │
                    └───────┬───────┘
                            │
                       ┌────▼────┐
                       │   SW1   │
                       │  2960   │
                       └────┬────┘
                       ┌────┼────┐
                      PC1  PC2  PC3  PC4
