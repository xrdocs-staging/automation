---
published: false
date: '2024-08-15 00:00 +0800'
title: Getting started with Crosswork Planning Collector
tags:
  - cisco
  - WAE
  - Crosswork Planning
  - Crosswork Planning Collector
  - Collector
  - Automation
  - Design
  - Capacity Planning
author: Fung Lim
excerpt: Getting started with Crosswork Planning Collector
---
{% include toc %}

# Overview

Crosswork Planning provides a comprehensive suite of tools to empower operators to proactively manage their network infrastructure. These tools offer capabilities for network discovery, analysis, simulation, and optimization. With Crosswork Planning, operators can unlock a host of benefits, including enhanced visibility and insights, improved performance, reliability, and resiliency, and efficient capacity management.

The Design application may be used to visualize topology, run simulations as well as perform optimizations and uses network models which has been created prior, or built using the Collector application.

The Collector application allow us to perform network discovery, collection and model buildling using a variety of supported methods. The collector application takes as its input configuration pertaining to basic and advanced model building and for traffic and demands. Based on these configuration, the collector application reaches out to the network elements to perform collection of the desired attributes to populate the network model. It will produce an output network model (ie. plan file) for the collection, containing objects such as nodes, interfaces, demands, etc. The collection process is designed to be extensible, allowing for the use of scripts to augment basic collection, or for custom collection.

This tutorial provides a brief overview of setting up Crosswork Planning collector.

Note: Please ensure that Smart Licensing has been setup prior to running collection.

# Getting started with Collection

After logging in to Crosswork Planning, we select the Collector option to access the Collector configuration.

The Collector may be configured by either of the following methods
* Wizard based guided setup using Getting started selection
* Manual setup by setting up Credentials, Network Profiles, Agents and Collections
* Importing configuration file from WAN Automation Engine (using WAE configuration migration tool)

By default, Crosswork will provide a wizard based setup if no existing configuration exists.

![Getting started with collection]({{site.baseurl}}/images/cp-getting-started-collection-wizard.png) 


## Setting up Credentials

Credential profiles are required to be setup for Crosswork Planning to connect to network devices for the purpose of collection. There are two profiles which must be setup.

* Authentication Profile - This will need to contain the user credentials (username and password) which the Collector will use when connecting to the network devices. Authentication Profiles are used for collection methods which require device login, e.g. IGP based topology discovery where Crosswork Planning will login to the device to collect the IGP database
* SNMP Profile - This needs to contain the SNMP type (v2c, v3) and credentials for connecting to the network devices. SNMP is used to enrich the topology information collected via IGP or SR-PCE (e.g. interface name and interface description). In addition, SNMP is used used by some collection methods such as SNMP based LSP collection and interface traffic collection.

## Setting up Network Profile

The creation of Network Profiles allows us to specify the authentication and SNMP profile used for accessing network devices. Optionally, a Node list may be created to specify the Management IP, SNMP profile and Authentication profile associated with a particular Node IP address. Specifying the Management IP is especially important if the Node IP which is typically the Router ID or Loopback0 address is not directly accessible from Crosswork Planning.

In addition, Node filter may be used to restrict the scope of collection to certain nodes only. This may be specified using  an include or exclude list based on regular expressions, or individual IP addresses.

## Setting up Agent (Optional)

SR-PCE or Netflow agents need to be setup if we are using either for collection. An agent will need to be setup per SR-PCE instance. After the agent has been setup, we may select the ellipsis icon to verify the connectivity between the agent and the specified SR-PCE. Note that the LSP status will indicate valid data if LSPs has been discovered, or otherwise it may indicate invalid data.

## Setting up Collection

The next step is to setup collection by going to Collector > Collections > Add collection. Select the collection methods for Basic topology, Advanced modeling and Traffic and Demands. 

### Example: SR-PCE based topology and LSP collection ###

SR-PCE based topology and LSP collection is usually used for Segment Routing (SR/MPLS) networks with SR-PCEs deployed. In the example below, we select SR-PCE for basic topology collection and PCEP LSP for discovering LSPs using SR-PCE. In addition, we have enabled Traffic collection for Crosswork Planning to populate the interface and LSP traffic statistics.

For SR-PCE based topology and LSP collection, we need to ensure that the mandatory parameters have been entered under the SR-PCE, PCEP LSP and Traffic collection subsections.

### Example: IGP based topology and SNMP based LSP collection ###

This collection method is usually used for IP transit, or IP/MPLS networks without the SR-PCE deployed.

# Methodology

![RSVP with Sim Analysis]({{site.baseurl}}/images/using-cp-pave-sr-sim-analysis-rsvp-autobw.png) 

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

# Conclusion

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

For more information, please refer to the Crosswork Planning Installation Guide, Collection Setup and Administration Guide, and Design User Guide.
