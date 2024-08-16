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

Many customers have deployed Segment Routing to date. The benefits of Segment Routing cannot be overstated. It offers simplification of the network with no maintenance of network state, with most of the best-effort traffic being carried by IGP shortest path, leveraging on equal cost multi-path for load balancing. It minimizes the number of protocols required for operations. In other words, it brings enhanced flexibility and resiliency and, at the same time, provides operational simplification.

Service Providers and large enterprises considering migrating to segment routing as an end state have traditionally been concerned about maintaining the same quality of experience for their customers, especially those who have deployed full-meshed RSVP-TE auto bandwidth tunnels. Some of these customers are concerned that without the deployment of auto bandwidth tunnels, the network would not be able to provide the same resiliency and responsiveness in dealing with changing network conditions. 

Crosswork Planning provides capabilities for network model building and simulation. It offers predictive simulation for a variety of use cases, including routing protocol migration and network migration scenarios. In this tutorial, we provide a simple demonstration on how operators may use Crosswork Planning to model an existing network with full-meshed RSVP-TE tunnels and if migrating this network to segment routing will allow us to provide the same performance and resiliency.

The methodology described in this tutorial was performed on real-world network models. However, due to customer confidentiality, this document uses modified sample network files for illustration. Please note that additional considerations in migrating the network through intermediate states, e.g., co-existence of RSVP-TE and segment routing, are outside the scope of this document.


# Considerations

As customers move to segment routing, we want to move away from the full-mesh RSVP-TE tunnel mindset since doing so will not allow us to reap the benefits of overall operational simplification. The IGP shortest path should be used to carry the bulk of the best effort traffic, leveraging on natural ECMP where available. With proper capacity planning and optimization, it should deem full mesh RSVP-TE tunnel deployments unnecessary for select customer cases. This is especially so if the customer network has multiple redundant paths providing for natural ECMP and has been engineered with proper capacity planning.

If there are traffic which needs to be treated with special intent (e.g. low-latency, or to avoid certain links, countries or continent) then Segment Routing policies or FlexAlgo may be used for these traffic types. These are use cases which are not related to bandwidth and are the exception rather than the norm.

We are mindful that there could be scenarios where capacity planning and optimization could not have anticipated (e.g. multiple links going down at the same time, flash crowd, or unexpected failures occuring concurrently when nodes/links are taken out for maintenance). This is where tactical traffic engineering capabilities such as that provided by Local Congestion Mitigation (LCM) should help. 

The deployment of LCM allows us to route the minimum amount of traffic away from the congested link (to bring it below the congestion threshold) in a transient manner for as long as the duration of the event. The rationale for doing so is to leveraging on spare capacity elsewhere to carry these best effort traffic (potentially over a longer path) which would otherwise be discarded.

# Methodology

In the modelling exercise, we build an accurate model of the network deployed with RSVP-TE autobandwidth tunnels. Crosswork Planning can assist in the network collection and model building process. This would provide us with a network model (plan file) complete with topology, LSPs and traffic, that is representative of the network with RSVP-TE autobandwidth tunnels.

Next, we leverage on Crosswork Planning Design to perform various simulations to characterise the network and its failure modes. This may include using simulation analysis to fail combinations of nodes and links to provide the worst case traffic utilization for each links. The same analysis will also allow us to gain insights as to which link or node failures will lead to these worst case traffic utilization.

In the example below, we load the plan file containing a model of the topology, LSPs and traffic and perform a simulation analysis in order to obtain the worst case interface utilization. The report shows that 5.88% of the failure cases will cause the interfaces to be oversubscribed.

![RSVP with Sim Analysis]({{site.baseurl}}/images/using-cp-pave-sr-sim-analysis-rsvp-autobw.png) 

In the next plan file, we remove the RSVP-TE LSPs and rely solely on IGP for routing. We perform the same simulation analysis and find that 23.53% of the failures will cause the interfaces to be oversubscribed. This shows that the RSVP-TE LSPs does help lower the percentage of failure cases which causes the interfaces to be oversubscribed. However, this is not the end of the story.

![RSVP with Sim Analysis]({{site.baseurl}}/images/using-cp-pave-sr-sim-analysis-rsvp-removed.png) 

What if we perform further optimization in the network by using IGP Metric Optimization? In this case, we select the options to minimize the maximum interface utilization in the face of node and link failures.

![RSVP with Sim Analysis]({{site.baseurl}}/images/using-cp-pave-sr-sim-analysis-rsvp-removed-mopt-next.png) 

We run the same simulation analysis on the resultant network model with the optimized IGP metrics and observe that none of the failure cases will lead to any links being oversubscribed.

![RSVP with Sim Analysis]({{site.baseurl}}/images/using-cp-pave-sr-sim-analysis-rsvp-removed-mopt.png) 

Very broadly speaking, some networks are designed with good redundancy (i.e. meshy topology) with multiple parallel paths allowing for equal cost multipath, and has sufficient capacity to deal with failure scenarios. Other networks may have very limited capacity and links and are not able to upgrade capacity in accordance to requirements, and have multiple links over capacity. In the latter case RSVP-TE may serves more as a band-aid to resolve issues which could otherwise be handled with capacity planning and network best practices. 

# Conclusion

When planning for migration from full-mesh RSVP-TE to Segment Routing, a worth-while exercise would be to build a model of the network, complete with topology, LSPs and traffic. The demand matrix could be obtained using demand deduction if a direct measurement is not possible, or not available. This would allow us to see how traffic would flow, and what possible issues we may face in the event of failures, or if the existing demands continue to grow. With this model, we may perform optimisations to provide for a better balance of traffic across the network (e.g. minimize the maximum interface utilization).

With this model, we can run simulation to compare the worst case utilization for the original network with full-mesh RSVP-TE tunnels, and after these tunnels have been removed. Most of the time, networks with sufficient capacity should now see the removal of RSVP-TE Auto bandwidth being worst off. This is especially after further optimizations has been performed on the network. This allows us to conclude that removing the full-mesh RSVP-TE tunnels does not make the network any worst off when it comes to worst case utilization.

Crosswork Planning provides intuitive, easy to use suite of tools for operators to proactively manage their network infrastructure. This helps provides enhanced visibility and insights, improved performance, reliability, and resiliency, and efficient capacity management.

For more information, please refer to the Crosswork Planning Installation Guide, Collection Setup and Administration Guide, and Design User Guide.
