---
published: false
date: '2024-08-15 00:00 +0800'
title: Introduction to Crosswork Planning
tags:
  - cisco
  - WAE
  - Crosswork Planning
  - Automation
  - Design
  - Capacity Planning
author: Lim Fung
excerpt: Introducing Crosswork Planning
---
{% include toc %}

# Overview


Crosswork Planning, the latest addition to the Crosswork Automation  suite, provides a comprehensive suite of tools to empower operators to proactively manage their network infrastructure. These tools offer capabilities, including network discovery, analysis, simulation, and optimization.

With Crosswork Planning, operators can unlock a host of benefits, including enhanced visibility and insights, improved performance, reliability, and resiliency, and efficient capacity management.

# Key Benefits

Enhanced Visibility and Insights: Besides providing basic topology and traffic utilization in a visual representation, Crosswork Planning provides additional insights, such as visibility into traffic demands and how these demands behave under changing network conditions. Similar insights could be provided for both RSVP And Segment routing-based LSPs deployed in the network. 

Improved Performance, Reliability, and Resiliency: At the core of Crosswork Planning is a predictive AI-based simulation engine that aims to mimic real-world behavior, allowing for a digital twin representation of the deployed network. These capabilities may be used to identify potential issues and perform optimizations that could improve the quality of experience for end users. It can help identify possible weaknesses in the network and provide actionable insights to enhance reliability and resiliency.

Capacity Management: Crosswork Planning provides comprehensive toolsets for a holistic approach to capacity management. This helps the operators evaluate the most effective physical topology and how much capacity (and where) is required to support continued growth. Crosswork Planning also provides tools for offline traffic optimization to allow for the most efficient routing of demands, allowing operators to maximize their return on investment (ROI) on their deployed network infrastructure.
This tutorial provides an overview of Crosswork Planning’s user interface.


# Introduction to Crosswork Planning User Interface

After Crosswork Planning has been installed successfully, the user can interact with Crosswork Planning using a web based interface. Upon login, the user will be presented with a Dashboard which presents an overall summary of its status.

![Crosswork Planning Dashboard]({{site.baseurl}}/images/intro-cp-dashboard-001.png)


The Network Models selection allows us to create new plan files and import existing plan files to Crosswork Planning. It also provides us with the ability to Open, Make a copy, Download or Delete the plan files. 

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-network-models-001.png)

If we have configured collection with archival, the Local archive subection will allow us to view the list of archived plan files for the configured collections.

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-network-models-archive-001.png)

The Network Design selection allows us to access the Design Application. Using the Design Application, we can visualize an existing network model (plan-file), run simulations as well as perform optimizations for example.

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-network-design-main-001.png)

Some of the simulation capabilities include predictive What-If analysis, and Simulation Analysis with Worse Case Traffic view.

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-network-design-demands-001.png)

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-network-design-sim-analysis-001.png)













