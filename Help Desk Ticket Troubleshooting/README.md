# Help Desk Ticket Troubleshooting

## Project Overview

Completed a simulated Tier 1 IT support incident using
the SysDesks help desk simulator.

The objective was to investigate and resolve a Windows
workstation's inability to access the internet.

## Environment

- Operating System: Simulated Windows workstation
- Device: Lenovo ThinkPad T14 Gen 4
- Connection: Ethernet
- Tools: Command Prompt and ipconfig
- Platform: SysDesks

## Problem

The simulated user reported that websites would not load
and email connectivity was unavailable.

Windows displayed "Unidentified network no internet."

## Initial Diagnosis

I ran `ipconfig /all` to inspect the network configuration.

Findings:
- IPv4 address: `169.254.23.11`
- Subnet mask: `255.255.0.0`
- Default gateway: Missing
- DNS servers: Missing
- DHCP: Enabled

The APIPA address indicated that the workstation had
failed to obtain a usable IPv4 configuration through DHCP.

## Troubleshooting

I attempted to renew the IP configuration.

The initial DHCP renewal request timed out.

Following the simulator's guided troubleshooting steps,
I ran:

```cmd
ipconfig /release
ipconfig /renew
