# Deployment Guides

Netdata can monitor all types of infrastructure, from small IoT devices to complex hybrid environments that combine on-premise and cloud setups, including bare-metal servers, virtual machines, and containers.

There are 3 components to structure your Netdata ecosystem:

1. **Netdata Agents**

   To monitor the physical or virtual nodes of your infrastructure, including all applications and containers running on them.

   Netdata Agents are Open-Source, licensed under GPL v3+.

2. **Netdata Parents**

   To create [observability centralization points](/docs/observability-centralization-points/README.md) within your infrastructure, to offload Netdata Agents functions from your production systems, to provide high-availability of your data, increased data retention and isolation of your nodes.

   Netdata Parents are implemented using the Netdata Agent software. Any Netdata Agent can be an Agent for a node and a Parent  for other Agents, at the same time.

   It is recommended to set up multiple Netdata Parents. They will all seamlessly be integrated by Netdata Cloud into one monitoring solution.

3. **Netdata Cloud**

   
Our SaaS unifies all your infrastructure, Netdata Agents, and Parents into a single, scalable, distributed monitoring database. It offers advanced data analysis, custom dashboards, troubleshooting tools, user and alert management, and more.

The Netdata Agent is a modular software solution that collects data through various plugins, includes a custom time-series database, query engine, health monitoring and alerts, machine learning for anomaly detection, and supports metric export to third-party systems.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjI2OTY0NjA3LC03Mzk3MTM4ODddfQ==
-->