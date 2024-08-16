---
published: false
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

Segment Routing has been deployed in many customers till date. The benefits of Segment Routing cannot be overstated - It offers simplification of the network with no maintenance of network state, with most of the best-effort traffic being carried by IGP shortest path, leveraging on equal cost multi-path for load balancing. It minimizes the number of protocols required for operations; In addition, it brings enhanced flexibility and resiliency and at the same time introduces operational simplification.

Service Providers and large enterprises who have considered migrating to segment routing as an end state has traditionally been concerned about maintaining the same quality of experience for their customers, especially those who have deployed full meshed RSVP-TE auto bandwidth tunnels. Some of these customers are concerned that without the deployment of auto bandwidth tunnels, if the network would be able to provide the same resiliency and responsiveness in dealing with changing network conditions. 

Crosswork Planning provides capabilities for network model building and simulation. It provides predictive simulation for a wide range of use cases including routing protocol migration and network migration scenarios. In this tutorial, we explore how Crosswork Planning may be used to model an existing network with full meshed RSVP-TE tunnels and if migrating this network to segment-routing will allow us to provide the same performance and resiliency prior.

The methodology described in this tutorial was performed on real-world network models. However, this document uses modified sample network files for the purpose of illustration due to customer confidentiality. Please note that additional considerations in migrating the network through intermediate states e.g. co-existence of RSVP-TE and segment routing is outside the scope of this document.


# Considerations

As customers move to segment routing, we want to move away from the full-mesh RSVP-TE tunnel mindset since doing so will not allow us to reap the benefits of overall operational simplification. The IGP shortest path should be used to carry the bulk of the best effort traffic, leveraging on nature ECMP where available. With proper capacity planning and optimization, it should deem full mesh RSVP-TE tunnel deployments unnecessary for the majority of the cases.

Now if there are traffic which needs to be treated with special intent (e.g. low-latency, or to avoid certain links, countries or continent) then Segment Routing policies or FlexAlgo may be used for these traffic types. These are use cases which are not related to bandwidth and are the exception rather than the norm.

We are mindful that there could be scenarios where capacity planning and optimization could not have anticipated (e.g. multiple links going down at the same time, flash crowd, or unexpected failures occuring concurrently when nodes/links are taken out for maintenance). This is where tactical traffic engineering capabilities such as that provided by Local Congestion Mitigation (LCM) should help. 

The deployment of LCM allows us to route the minimum amount of traffic away from the congested link (to bring it below the congestion threshold) in a transient manner for as long as the duration of the event. The rationale for doing so is to leveraging on spare capacity elsewhere to carry these best effort traffic (potentially over a longer path) which would otherwise be discarded.

# Methodology

In the modelling exercise, we build an accurate model of the network deployed with RSVP-TE autobandwidth tunnels. Crosswork Planning can assist in the network collection and model building process. This would provide us with a network model (plan file) complete with topology, LSPs and traffic, that is representative of the network with RSVP-TE autobandwidth tunnels.

Next, we leverage on Crosswork Planning Design to perform various simulations to characterise the network and its failure modes. This may include using simulation analysis to fail combinations of nodes and links to provide the worst case traffic utilization for each links. The same analysis will also allow us to gain insights as to which link or node failures will lead to these worst case traffic utilization.



...


# Conclusion

Crosswork Planning provides an intuitive, easy to use web based interface for operators to proactively manage their network infrastructure through a suite of tools which provides enhanced visibility and insights, improved performance, reliability, and resiliency, and efficient capacity management just to name a few.

For more information, please refer to the Crosswork Planning Installation Guide, Collection Setup and Administration Guide, and Design User Guide.
