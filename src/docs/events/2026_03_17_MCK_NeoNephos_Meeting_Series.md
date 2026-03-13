---
title: "MCK Meeting Series"
date: "2026-03-17"
banner: "assets/events/20263017_mck_neonephos_series_banner.svg"
bannerMobile: "assets/events/20263017_mck_neonephos_series_banner_mobile.svg"
bannerSmall: "assets/events/20263017_mck_neonephos_series_banner_small.svg"
backgroundhex: "#128256ff"
tags: ["neonephos", "mck","ipcei"]
published: true
---

# NeoNephos Meeting Series

The next IPCEI-CIS Workstream 2 Multi Cluster Kubernetes (MCK) meeting session will be held on the **17th of March from 10:00-11:30 am CET**. 

Agenda:
 
- 40 min: **Designing for Energy Efficiency: Eliminating Waste in Power, Capacity, and Cooling**: Modern data centers are highly energy intensive environments, and a significant share of this energy is unintentionally wasted due to inefficient use of ICT power, oversized infrastructure, and sub optimal cooling. This presentation explores how data center observability helps us use energy in the most effective way by identifying and eliminating inefficiencies across both power and temperature domains.
We will examine three major sources of avoidable energy consumption: Ghost ICT equipment, Power infrastructure efficiency gaps, Cooling inefficiencies.
By combining accurate power telemetry, environmental data, and capacity insights, we show how observability enables right sizing, consolidation, and better load placement—ultimately reducing operational energy, lowering embodied emissions, and improving the sustainability footprint of our data center landscape.

- 40 min: **Modular Integrated Sustainable Datacenter: Chantico energy controller**: During this presentation, we introduce the goals, architecture, components and current functionality of the energy-aware domain controller, Chantico. TNO is developing Chantico as part of the Modular Integrated Sustainable Datacenter (MISD) project under the IPCEI-CIS 8ra Initiative, in orchestration and energy flexibility efforts.
This cloud-native solution consists of a Kubernetes operator named Chantico which integrates with existing open source software for collecting energy measurements. We monitor devices like PDUs and bare metal servers but also higher-level resources, aggregating data and eventually splitting up timeseries to report VM and K8S services. We consider fair distribution algorithms of unallocated overhead between data center operations and tenant workloads. Chantico also becomes extensible with carbon emission measurements and enables green workload shifting.
We present our graph-based K8s custom resource model, our technical approach in reconciliation/validation/configuration loops and our use cases so far. We round up with a demo of the Chantico software and demonstrate our open sourcing and documentation efforts for this project.

---

👉 Join the meeting [here](https://teams.microsoft.com/l/meetup-join/19%3ameeting_NjgzOGUxNTItYjBjYy00NWZlLThkMjktNGZhMzM0NTg3MjZl%40thread.v2/0?context=%7b%22Tid%22%3a%2242f7676c-f455-423c-82f6-dc2d99791af7%22%2c%22Oid%22%3a%22f448159f-8442-4772-945c-ad5c1d621625%22%7d).
