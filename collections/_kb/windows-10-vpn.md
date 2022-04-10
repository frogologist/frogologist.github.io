---
layout: post
title:  "Windows 10 cannot connect to a VPN"
date:   2019-05-17 10:39:29 +1000
categories: windows
---

![The error message returned when Windows cannot connect to a VPN.]({{ site.url }}/assets/images/windows_10_vpn_error.jpg)

>A connection to the remote computer could not be established. You might need to change the network settings for this connection.

The [verified answer](https://social.technet.microsoft.com/Forums/en-US/5a63e743-36a0-4cc1-927b-79dfec166d0e/vpn-setup-in-windows-10-is-not-working?forum=win10itpronetworking) to this question worked for me:

1. Open File Explorer e.g. `Windows key` + `E`.
2. Right click on `This PC` and select `Manage`.
3. When Computer Management opens, click `Device Manager`.
4. Under Network Adapters, uninstall all adapters starting with `WAN Miniport`: right click, `Uninstall`.
5. Once you've uninstalled them, go to the menu (or right click on `Network Adaptors` in the hierarchy) and select `Scan for Hardware Changes`. The WAN Miniport adapters are reinstalled automatically without restarting.  
6. Retry the VPN connection.
