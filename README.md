# Enterprise Network Infrastructure Project

## Executive Summary

This project demonstrates the design, implementation, validation, monitoring, and troubleshooting of a multi-router enterprise network
using Cisco Packet Tracer.
The environment integrates dynamic routing, DHCP services, DNS concepts, NAT translation, ACL-based security, network monitoring, 
and structured troubleshooting procedures.
The project simulates a small enterprise connecting multiple LANs to a simulated Internet Service Provider while providing hands-on experience with 
network operations, validation, and fault isolation.
This project focuses on how enterprise networking services work together as a complete system. 
The final environment demonstrates not only network deployment, but also monitoring, troubleshooting, operational maintenance, 
and documentation practices that mirror real-world infrastructure management.



# Project Background
The objective was to progress from understanding basic networking concepts to designing, building, validating, monitoring, 
and troubleshooting a complete enterprise network.
Throughout the project, individual technologies were gradually integrated into a single operational environment capable of:

- Dynamic Routing
- Automatic Host Configuration
- Internet Connectivity
- Network Security Enforcement
- Monitoring and Operational Validation
- Structured Troubleshooting

The final network represents the cumulative knowledge and skills developed throughout the Networking Fundamentals phase.



# Project Objectives

The network was designed to achieve the following objectives:

## Connectivity

Provide communication between multiple local area networks.

## Routing

Implement dynamic route exchange between routers.

## DHCP

Provide automatic IP address assignment for client devices.

## DNS Concepts

Demonstrate enterprise service infrastructure and hostname resolution concepts.

## NAT

Enable communication between private networks and external networks.

## ACL Security

Control communication between network segments through policy enforcement.

## Monitoring

Develop operational monitoring procedures and health validation methods.

## Troubleshooting

Develop repeatable root-cause analysis and fault isolation workflows.

## Enterprise Network Validation

Verify successful integration of all deployed services.








# Network Device Roles

## Router0

Responsibilities:

- LAN10 connectivity
- RIP participation
- DHCP services
- Client traffic forwarding



## Router1

Responsibilities:

- Core router functionality
- Dynamic route exchange
- Inter-router communication



## Router2

Responsibilities:

- LAN30 connectivity
- ACL enforcement
- NAT services
- Server connectivity
- External network communication



## Router3

Responsibilities:

- ISP simulation
- External network representation
- NAT validation target



## Switches

Responsibilities:

- Layer 2 connectivity
- Device aggregation
- LAN connectivity



## Server0

Responsibilities:

- Enterprise service simulation
- DNS concept implementation
- Internal server infrastructure representation



# Addressing Plan

## LAN10
Network: 192.168.10.0/26
Gateway: 192.168.10.1

## LAN20
Network: 192.168.20.0/26
Gateway: 192.168.20.1

## LAN30
Network: 192.168.30.0/26
Gateway: 192.168.30.1


## Router Interconnect Networks
10.0.0.0/30
10.0.0.4/30

Used for:
R0 ↔ R1

R1 ↔ R2 
communication.



## External Network
209.165.200.224/30

Used for:

- ISP Simulation
- NAT Validation
- Public Network Connectivity

# Routing Architecture

## Dynamic Routing Protocol
The network utilizes:
RIP Version 2 for automatic route exchange.

## Why RIP Was Chosen

RIP was selected because it allows routers to:

- Automatically learn routes
- Share network information
- Reduce manual configuration
- Maintain connectivity dynamically

This project focused on understanding routing concepts rather than implementing advanced enterprise routing protocols.



## Verification Commands
show ip route
show ip protocols

## Skills Demonstrate
Dynamic Routing
Route Advertisement
Route Learning
Routing Verification
Routing Troubleshooting

# Enterprise Network Services
## DHCP
### Purpose
DHCP provides automatic client configuration.

Assigned settings include:

IP Address

Subnet Mask

Default Gateway

Network Configuration Information

### Verification
show ip dhcp binding

### Skills Demonstrated

DHCP Pool Configuration

Automatic Address Assignment

Lease Verification

## DNS Concepts

### Purpose

DNS concepts were introduced to demonstrate how human-readable names relate to IP addresses.

Example:
server.local

↓

192.168.30.100

### Skills Demonstrated


Hostname Resolution

Enterprise Service Awareness

Server Infrastructure Concepts

## NAT

### Purpose

NAT allows internal devices using private IP addresses to communicate with external networks.

Example:

192.168.10.x

↓

209.165.200.225




### Verification
show ip nat translation

### Skills Demonstrated

Private Addressing

Public Addressing

PAT

Internet Connectivity

## ACL Security

### Purpose

ACLs enforce communication policies between networks.

Example:

LAN10

cannot reach

LAN30


while:


LAN20

can reach

LAN30




### Verification
show access-lists

### Skills Demonstrated

Traffic Filtering

Security Enforcement

Policy Verification


# Network Monitoring Procedures

Enterprise networks require continuous validation and monitoring.

The following procedures were developed during the project.



## Interface Monitoring

### Command


show ip interface brief


### Purpose

Verify:


Interface availability

Link status

Connectivity health


### Warning Signs


down/down

administratively down




## Routing Monitoring

### Command


show ip route


### Purpose

Verify:


Expected network reachability

Route availability


### Warning Signs


Missing RIP routes

Missing destination networks




## RIP Monitoring

### Command


show ip protocols


### Purpose

Verify:


Routing protocol participation

Advertised networks

Routing operation


### Warning Signs


Missing network statements

Unexpected protocol behavior




## ACL Monitoring

### Command


show access-lists


### Purpose

Monitor:


Permit activity

Deny activity

ACL usage


### Warning Signs


Large deny counts

Unexpected ACL matches




## DHCP Monitoring

### Command


show ip dhcp binding


### Purpose

Verify:


Active DHCP leases


### Warning Signs


Missing leases

Unexpected client counts




## NAT Monitoring

### Command


show ip nat translations


### Purpose

Verify:


Translation activity

Internet access functionality


### Warning Signs


No translations

Unexpected translation volume




# Troubleshooting Methodology

One of the most important outcomes of this project was developing a repeatable troubleshooting process.

The methodology used throughout the project was:


Observe Symptoms

↓

Gather Evidence

↓

Identify Root Cause

↓

Implement Fix

↓

Verify Resolution




# Troubleshooting Scenario 1

## Interface Failure

### Symptom

Devices lost connectivity to remote networks.

### Investigation


show ip interface brief


### Root Cause

Router interface manually disabled.

### Resolution


no shutdown


### Verification

Successful connectivity restored.

### Lesson Learned

A failed ping does not automatically indicate a routing problem.



# Troubleshooting Scenario 2

## RIP Failure

### Symptom

Remote networks became unreachable.

### Investigation


show ip protocols


### Root Cause

Missing RIP network statement.

### Resolution


network 10.0.0.0


### Verification

Routes successfully reappeared.

### Lesson Learned

Interfaces can remain healthy while routing fails.



# Troubleshooting Scenario 3

## ACL Failure

### Symptom

Traffic became unexpectedly blocked.

### Investigation


show access-lists


### Root Cause

Incorrect deny policy.

### Resolution

ACL removed or corrected.

### Verification

Connectivity restored.

### Lesson Learned

Security policies can create connectivity symptoms that resemble routing failures.



# Challenges Encountered

Several real troubleshooting situations occurred throughout the project.

## Routing Validation Challenges

During NAT implementation, connectivity initially failed despite correct NAT configuration.

Resolution:


RIP advertisements were incomplete.


Lesson:


Routing happens before NAT.




## ACL Verification Challenges

Traffic failures required distinguishing between:


Routing Problems

vs

Security Policy Problems


Lesson:


Connectivity failure alone does not reveal root cause.




## Troubleshooting Methodology Development

Early troubleshooting attempts focused on direct fixes.

As the project progressed, troubleshooting became evidence-driven.

Lesson:


Always investigate before making changes.




# Enterprise Lessons Learned

## Lesson 1

Routing happens before NAT.

A packet must successfully route to the NAT device before translation can occur.



## Lesson 2

A failed ping is a symptom.

It is not a diagnosis.

The problem may involve:

- Interfaces
- Routing
- ACLs
- DHCP
- NAT



## Lesson 3

Always gather evidence before changing configurations.

Good troubleshooting follows a process.



## Lesson 4

Monitoring requires understanding what normal behavior looks like.

Without a baseline, anomalies are difficult to identify.



## Lesson 5

Enterprise networking is the integration of multiple services working together.

No individual technology operates in isolation.



# Skills Demonstrated

## Networking

 Routing

 Static Routing

 RIP

 DHCP

 DNS Concepts

 NAT

 ACLs

 VLAN Concepts

 Enterprise Network Integration



## Operations

 Monitoring

 Validation

 Documentation

 Service Auditing

 Operational Verification



## Troubleshooting

 Root Cause Analysis

 Interface Diagnostics

 Routing Diagnostics

 ACL Diagnostics

 Fault Isolation

 Network Verification



# Project Outcome

This project successfully demonstrates:

 Network Design

 Network Implementation

 Routing Architecture

 Enterprise Services

 Security Controls

 Monitoring Procedures

 Troubleshooting Procedures

 Operational Validation

 Documentation Standards

The final environment represents a fully documented enterprise networking project that demonstrates practical 
experience with enterprise infrastructure deployment, operations, troubleshooting, and support.



# Conclusion

The value of this project is not contained within any single technology such as RIP, DHCP, NAT, or ACLs. 
Its value comes from demonstrating the ability to design, implement, validate, monitor, troubleshoot, and document a complete enterprise network.

The project represents the progression from studying networking concepts to applying engineering practices used in real operational environments.
It demonstrates technical configuration skills, operational awareness, troubleshooting methodology, and professional documentation standards.

Most importantly, the project shows the ability to think beyond individual commands and understand how enterprise systems function as integrated environments.

This project represents the successful completion of Phase 4 and the transition from networking student to aspiring infrastructure and cloud professional.
