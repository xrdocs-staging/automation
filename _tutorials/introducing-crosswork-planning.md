---
published: true
date: '2024-08-15 00:00 +0800'
title: Introduction to Crosswork Planning user interface
tags:
  - cisco
  - WAE
  - Crosswork Planning
  - Automation
  - Design
  - Capacity Planning
author: Fung Lim
excerpt: Introducing Crosswork Planning
---
{% include toc %}

# Overview


Crosswork Planning, the latest addition to the Crosswork Automation  suite, provides a comprehensive suite of tools to empower operators to proactively manage their network infrastructure. These tools offer capabilities for network discovery, analysis, simulation, and optimization.

With Crosswork Planning, operators can unlock a host of benefits, including enhanced visibility and insights, improved performance, reliability, and resiliency, and efficient capacity management.

# Key Benefits

**Enhanced Visibility and Insights:** Besides providing basic topology and traffic utilization in a visual representation, Crosswork Planning provides additional insights, such as visibility into traffic demands and how these demands behave under changing network conditions. Similar insights could be provided for both RSVP And Segment routing-based LSPs deployed in the network. 

**Improved Performance, Reliability, and Resiliency:** At the core of Crosswork Planning is a predictive AI-based simulation engine that aims to mimic real-world behavior, allowing for a digital twin representation of the deployed network. These capabilities may be used to identify potential issues and perform optimizations that could improve the quality of experience for end users. It can help identify possible weaknesses in the network and provide actionable insights to enhance reliability and resiliency.

**Capacity Management:** Crosswork Planning provides comprehensive toolsets for a holistic approach to capacity management. These helps the operators evaluate the most effective physical topology and how much capacity (and where) is required to support continued growth. Crosswork Planning also provides tools for offline traffic optimization to allow for the most efficient routing of demands, allowing operators to maximize their return on investment (ROI) on their deployed network infrastructure.

This tutorial provides a brief overview of Crosswork Planning’s user interface.

# Introduction to Crosswork Planning User Interface

## Dashboard ##

After Crosswork Planning is installed, the user can interact with Crosswork Planning using a web based interface. Upon login, the user will be presented with a Dashboard which presents an overall summary of its status.

![Crosswork Planning Dashboard]({{site.baseurl}}/images/intro-cp-dashboard-001.png)

The key benefit of adopting a web based interface is to allow for the application to be agnostic to client computing platforms. Support is no longer limited to a few select platforms.

## Network Models ##

The Network Models selection allows us to create new plan files and import existing plan files to Crosswork Planning. It also provides us with the ability to Open, Make a copy, Download or Delete the plan files. 

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-network-models-001.png)

If we have configured collection with archival, the Local archive subection will allow us to view the list of archived plan files for the configured collections.

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-network-models-archive-001.png)

In the future, we may extend support for Network Models to leverage on the use of cloud based storage for closer collaboration.

## Network Design ##

The Network Design selection allows us to access the Design Application. Using the Design Application, we can visualize an existing network model (plan-file), run simulations as well as perform optimizations for example.

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-network-design-main-001.png)

Some of the simulation capabilities include predictive What-If analysis, and Simulation Analysis with Worst Case Traffic view.

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-network-design-demands-001.png)

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-network-design-sim-analysis-001.png)

Because Crosswork Planning is designed to be a multi-user system, a team of planners and engineers can now leverage on the increased compute footprint to perform simulation and optimizations concurrently, on multiple unique network models.

## Job Manager ##

The Job Manager selection allows us to view the details and status of Jobs, as well as to provide a means of submitting CLI or scripted jobs. These jobs will be executed asynchornously on the system and the results of jobs are self-contained in an output tar archive.

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-job-manager-001.png)

The use of job manager provides a user friendly interface for the submission and scheduling of jobs so that the user can focus on the task at hand, instead of spending cycles performing the administraton of such jobs.

## Collector ##

The Collector selection allow us to configure network collection and model buidling. The user may select different methods of collection for basic and advanced model building as well as for traffic and demands. The collection process is designed to be extensible, allowing the use of scripts for custom collection.

Collections may be scheduled at a user specified cadence, with the network models archived. These models may be opened by Design for simulation and optimization, or exported from the system.

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-collection-001.png)

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-collection-002.png)

The user may choose to configure and schedule the collection process through an intuitive wizard, which helps minimize the complexities required to build a network model from a physical network. This translates to the ability for a more rapid deployment and reduces the overheads required to set up the system.

## Licensing ##

The Licensing selection allows the user to register the system to Cisco Smart Licensing, or to configure the system for evaluation mode.

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-smart-license-001.png)


## Alerts ##

The Alerts selection allows the user to view system alarms and events and could be useful for gaining visibility to the overall operations and performance of the system, and to view any notifications which may require user action.

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-alerts-001.png)


## Administration ##

The Administration selection allows the user to view a status summary of the installed platform and applications. This selection also allows users to perform backup and restore, manage certificates, users and roles as well as to edit system settings.

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-admin-001.png)

![Crosswork Planning Network Models]({{site.baseurl}}/images/intro-cp-admin-settings-001.png)



















