# Help Desk Ticket Troubleshooting

## Project Overview

This project documents a simulated Tier 1 IT support incident completed using the SysDesks help desk simulator.

The objective was to diagnose and resolve a Windows workstation's inability to access the internet.

## Environment

- **Operating System:** Simulated Windows workstation
- **Device:** Lenovo ThinkPad T14 Gen 4
- **Network Connection:** Ethernet
- **Tools:** Command Prompt and Windows IP configuration utilities
- **Platform:** SysDesks

## Problem Description

The simulated user reported that websites would not load and email connectivity was unavailable.

Windows displayed the following message:

**Unidentified network no internet access**

The workstation had an APIPA address and could not obtain a usable network configuration through DHCP.

## Initial Diagnosis

I used the following command to inspect the workstation's network configuration:

```cmd
ipconfig /all
```

The initial results showed:

- **IPv4 address:** `169.254.23.11`
- **Subnet mask:** `255.255.0.0`
- **Default gateway:** Missing
- **DNS servers:** Missing
- **DHCP:** Enabled

The `169.254.x.x` address indicated that Windows had assigned itself an APIPA address after failing to obtain a usable IPv4 configuration through DHCP.

Without a valid default gateway, the workstation could not route traffic to external networks.

## Troubleshooting Process

### Step 1: Inspect the Network Configuration

I ran `ipconfig /all` to review the Ethernet adapter's IP address, subnet mask, default gateway, DNS servers, and DHCP settings.

### Step 2: Attempt to Renew the DHCP Lease

I ran:

```cmd
ipconfig /renew
```

The initial attempt failed because the DHCP request timed out.

### Step 3: Release and Renew the IP Configuration

Following the SysDesks guided troubleshooting instructions, I ran:

```cmd
ipconfig /release
```

Then:

```cmd
ipconfig /renew
```

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
- Command line diagnostics
- Network configuration analysis
- Technical documentation
- Incident resolution

## Key Takeaway

An APIPA address (`169.254.x.x`) can indicate that a workstation failed to obtain a usable IPv4 configuration through DHCP.

Using `ipconfig /all` helps identify missing network settings, while `ipconfig /release` and `ipconfig /renew` can refresh the DHCP lease.

This exercise provided practical experience diagnosing a simulated network connectivity incident and documenting the troubleshooting process.
