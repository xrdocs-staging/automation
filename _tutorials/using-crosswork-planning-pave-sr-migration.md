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


Segment Routing has been deployed in many customers till date. The benefits of Segment Routing cannot be overstated - It offers simplification of the network with no maintenance of network state, with most of the best-effort traffic being carried by IGP shortest path, leveraging on equal cost multi-path for load balancing. It minimizes the number of protocols required for operations; It brings with it enhanced flexibility and resiliency and at the same time introduces operational simplification.

Service Providers and large enterprises who have considered migrating to segment routing as an end state has traditionally been concerned about the quality of experience that they can provide to their customers, especially those who have deployed full meshed RSVP-TE auto bandwidth tunnels. Some of these customers are concerned if without the auto bandwidth tunnels, if the network would be able to provide the same resiliency and responsiveness in dealing with changing network conditions. 

Crosswork Planning provides capabilities for network model building and simulation. It provides predictive simulation for a wide range of use cases including routing protocol migration and network migration scenarios. In this tutorial, we explore how Crosswork Planning may be used to model an existing network with full meshed RSVP-TE tunnels and if migrating this network to segment-routing will provide the same performance and resiliency.

The methodology described in this tutorial was performed on real-world network models. However, this document uses modified sample network files for the purpose of illustration due to customer confidentiality. The considerations and modelling of the network through intermediate states with the co-existence of RSVP-TE and segment routing is outside the scope of this document.


# Key Benefits

## Dashboard ##


# Conclusion

Crosswork Planning provides an intuitive, easy to use web based interface for operators to proactively manage their network infrastructure through a suite of tools which provides enhanced visibility and insights, improved performance, reliability, and resiliency, and efficient capacity management just to name a few.

For more information, please refer to the Crosswork Planning Installation Guide, Collection Setup and Administration Guide, and Design User Guide.
