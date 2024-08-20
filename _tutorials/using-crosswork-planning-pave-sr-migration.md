---
published: true
date: '2024-08-15 00:00 +0800'
title: Using Crosswork Planning to pave the way for Segment Routing migration
tags:
  - cisco
  - WAE
  - Crosswork Planning
  - Automation
  - Segment Routing
  - Migration
  - Design
  - Capacity Planning
author: Fung Lim
excerpt: Crosswork Planning Segment Routing migration
---
{% include toc %}

# Overview

Many customers have deployed Segment Routing to date. The benefits of Segment Routing cannot be overstated. Segment routing eliminates the need to create forwarding state instructions in the network, minimizes the number of protocols required for operations, drastically simplifying the network. In other words, it brings enhanced flexibility and resiliency and operational simplification. Most of the traffic is being carried by IGP shortest path, leveraging on equal cost multi-path for load balancing. 

The use of controllers such as Crosswork Network Controller provides a layer of abstraction by exposing easy to consume APIs at the transport and services level, effectively making the network programmable. This enables the rollout of advanced traffic engineering use cases with fine grained control while providing operational simplicity.

Service Providers and large enterprises considering migrating to segment routing as an end state have traditionally been concerned about maintaining the same quality of experience for their customers, especially those who have deployed full-meshed RSVP-TE auto bandwidth tunnels. Some of these customers are concerned that without the deployment of auto bandwidth tunnels, the network would not be able to provide the same resiliency and responsiveness in dealing with changing network conditions. 

Crosswork Planning provides capabilities for network model building and simulation. It offers predictive simulation for a variety of use cases, including routing protocol migration and network migration scenarios. In this tutorial, we provide a simple demonstration on how operators may leverage on Crosswork Planning to model the existing network which has been deployed with full-meshed RSVP-TE tunnels and if migrating this network to segment routing will allow us to provide the same performance and resiliency.

The methodology described in this tutorial has been applied on real-world network models with promising results. However, please note that the outcome of the modelling exercise is unique to those networks and the same conclusion cannot be drawn across all networks deployed with RSVP-TE auto bandwidth tunnels without proper modelling and simulation. In addition, additional considerations in migrating the network through intermediate states, e.g., co-existence of RSVP-TE and segment routing, are outside the scope of this document.

Due to customer confidentiality, this document uses modified sample network files in the screenshots. 

# A Paradigm Shift

As customers transition to segment routing, we advocate a shift from the full-mesh RSVP-TE tunnel mindset. This transition promises significant benefits in terms of operational simplification. By embracing the use of IGP shortest path to handle the bulk of best-effort traffic and with proper capacity planning and optimization, full-mesh RSVP-TE tunnels should not be necessary for most customer scenarios. This is particularly true for customer networks designed with high levels of redundancy and proper capacity planning.

For traffic that requires special treatment, such as low-latency or avoidance of specific links, countries, or continents, we have the flexibility of using Segment Routing policies or FlexAlgo. These tools are designed for use cases that go beyond bandwidth considerations, providing a robust solution for handling exceptions.

We are mindful that there could be scenarios where capacity planning and optimization could not have anticipated (e.g., multiple links going down simultaneously, flash crowd, or unexpected failures occurring concurrently when nodes/links are taken out for maintenance). This is where tactical traffic engineering capabilities such as that provided by [Local Congestion Mitigation (LCM)](https://www.cisco.com/c/en/us/products/collateral/cloud-systems-management/crosswork-network-automation/local-congestion-mitigation-wp.html) will help. 

LCM is designed to be used on best-effort traffic, leaving traffic which are already in SR policies unaffected. The deployment of LCM allows us to divert the minimum amount of traffic from the congested link (to bring it below the congestion threshold) to a detour path for the duration of the congestion. LCM leverages spare capacity elsewhere to carry this traffic (potentially over a longer path), which would otherwise be discarded.

# Methodology

In the modeling exercise, we aim to build an accurate network model with the current network with RSVP-TE auto bandwidth tunnels deployed. Crosswork Planning can assist in the network collection and model-building process. This would provide us with an accurate network model (plan file) complete with topology, LSPs, and traffic that is suitable for simulation studies.

Next, we leverage Crosswork Planning Design to perform various simulations to characterize this network and its failure modes. This may include using simulation analysis to simulate permutation of failures on selected objects such as nodes and links to provide the worst-case traffic utilization per link. The same analysis will also allow us to gain insights into which failure scenarios will lead to these worst-case traffic utilization. 

In the example below, we load the plan file containing a model of the topology, LSPs, and traffic and perform a simulation analysis to obtain the worst-case interface utilization. The report shows that 5.88% of the failure cases will cause the interfaces to be oversubscribed.

![RSVP with Sim Analysis]({{site.baseurl}}/images/using-cp-pave-sr-sim-analysis-rsvp-autobw.png) 

Next, we remove the RSVP-TE LSPs and rely on IGP routing. We performed a simulation analysis and found that now, 23.53% of the failures will cause the interfaces to be oversubscribed. This shows that the RSVP-TE LSPs do help lower the percentage of failure cases which causes the interfaces to be oversubscribed. However, this is only part of the story.

Another conclusion which can be drawn from the simulation analysis exercise might be the nature of failures which lead to worst case traffic utilization. If the failures are caused by failed link bundles for example, the probability of this happening would be lower as compared to a single port failure, provided the link bundle members are carried over diverse paths and terminate on different linecards on distributed routing platforms which supports high availability.

![RSVP with Sim Analysis]({{site.baseurl}}/images/using-cp-pave-sr-sim-analysis-rsvp-removed.png) 

Crosswork Planning's toolset encompasses various optimizers that can be used to improve the performance of networks under stressful conditions. We leverage IGP Metric Optimization to provide optimal link metrics in order to minimize the maximum interface utilization under failure scenarios.

![RSVP with Sim Analysis]({{site.baseurl}}/images/using-cp-pave-sr-sim-analysis-rsvp-removed-mopt-next.png) 

We perform another simulation analysis on the optimized network model and observe that now none of the failure cases will lead to any links being oversubscribed. This means that inspite of removing RSVP auto bandwidth tunnels, no link or mode failures will now lead to any links being oversubscribed and customers should not experience any degradation of service caused by link oversubscription. 

![RSVP with Sim Analysis]({{site.baseurl}}/images/using-cp-pave-sr-sim-analysis-rsvp-removed-mopt.png) 

Very broadly speaking, some networks are designed with good redundancy (i.e. meshy topology) with multiple parallel paths allowing for equal cost multipath, and has sufficient capacity to deal with failure scenarios. Other networks may have very limited capacity and links and are not able to upgrade capacity in accordance to requirements, and have multiple links over capacity. In the latter case RSVP-TE may be serveing more as a band-aid to resolve issues which could otherwise be handled with capacity planning and network design best practices. 

In the segment routing space, toolsets such as Local Congestion Mitigation can help operators deal with these exceptions on a as needed basis. 

# Conclusion

When planning for migration from full-mesh RSVP-TE to Segment Routing, a worth-while exercise would be to build an accurate model of the network, complete with topology, LSPs and traffic. This  allows us to simulate how traffic would flow, and what possible issues we may face in the event of failures, or if the existing demands continue to grow. 

Optimizations may be performed on this model to minimize the maximum interface utilization under failures scenarios. Simulations can be used to compare the worst case interface utilization for both RSVP-TE auto bandwidth and segment routing scenarios. Networks with sufficient capacity and resiliency should not see the removal of full meshed RSVP-TE auto bandwidth tunnels being worst off. 

Crosswork Planning provides an intuitive, easy to use suite of tools for operators to proactively manage their network infrastructure and helps to provide enhanced visibility and insights, improved performance, reliability, and resiliency, and efficient capacity management.

For more information, please refer to the Crosswork Planning Installation Guide, Collection Setup and Administration Guide, and Design User Guide.
