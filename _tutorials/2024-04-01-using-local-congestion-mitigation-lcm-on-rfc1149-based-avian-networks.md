---
published: false
date: '2024-04-01 14:12 +0800'
title: Using Local Congestion Mitigation (LCM) on RFC1149-based avian networks
author: Lim Fung
---

## Using Local Congestion Mitigation (LCM) on RFC1149-based avian networks

Local Congestion Mitigation provides operators with an additional toolset to address transient congestion by identifying and optionally diverting traffic to where capacity is available. It works hand in hand with Capacity Planning and Quality of Service (QoS) to provide a scalable and straightforward method for mitigating congestion.

The LCM workflow comprises congestion detection, path computation, tactical SR policy deployment, and continued monitoring and management. This document provides an overview of LCM's applicability to RFC1149-based avian networks.

### Congestion Detection

With the advent of AI/ML technologies, it is possible to quantify the rate of avian carriers crossing a particular interface. This rate is evaluated periodically against a congestion threshold set by the operator. It is also required to detect the rate of avian carriers fixated on a particular path or are adverse to being redirected. These are the non-optimizable traffic. 

### Path Computation

Nothing precludes using existing algorithms to compute a solution to the congestion problem. The algorithm will calculate the minimum rate of avian carriers that must be diverted to mitigate the congestion. Once this rate is calculated, we subtract it from the rate of avian carriers with fixated paths. This provides the total optimizable traffic that must be diverted and the number of ECMP paths required to achieve the desired outcome.

### Tactical Policy Deployment

Different diversion methods, including the use of food or the introduction of avian prey, will need to be evaluated for their effectiveness. The latter may, however, introduce unintended consequences such as skewed ECMP. Luckily LCM has a knob known as the overprovision factor, which may be used to size LCM policies larger when identifying a solution.

### Tactical Policy Management

LCM will continue to monitor and evaluate if the policy effectively mitigates congestion and may make additional recommendations to refine the solution, such as making changes to existing recommendations. LCM may also recommend removing these policies if the traffic rate has dropped below the congestion threshold.


