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
The DHCP lease was successfully renewed.

## Results

After renewing the DHCP lease, the workstation received the following network configuration:

- **IPv4 address:** `10.20.14.88`
- **Subnet mask:** `255.255.255.0`
- **Default gateway:** `10.20.14.1`
- **DNS servers:** `10.20.14.10` and `10.20.14.11`

The workstation no longer had the original APIPA address.

The SysDesks guided scenario confirmed that the machine was fixed.

## Skills Demonstrated

- Windows network troubleshooting
- IPv4 addressing and APIPA
- DHCP troubleshooting
- Command-line diagnostics
- Network configuration analysis
- Technical documentation
- Incident resolution

## Key Takeaway

An APIPA address (`169.254.x.x`) can indicate that a workstation failed to obtain a usable IPv4 configuration through DHCP.

Using `ipconfig /all` helps identify missing network settings, while `ipconfig /release` and `ipconfig /renew` can refresh the DHCP lease.

This exercise provided practical experience diagnosing a simulated network connectivity incident and documenting the troubleshooting process.

