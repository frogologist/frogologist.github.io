---
layout: post
title:  "Windows 10 cannot connect to a VPN"
date:   2019-05-17 10:39:29 +1000
categories: software
---

When attempting to connect to a customer's VPN, I encountered the following error:

> "A connection to the remote computer could not be established. You might need to change the network settings for this connection."

The VPN connection settings were fine; Windows wouldn't play ball.

I resolved the issue by uninstalling and reinstalling the WAN Miniport adapters. Refer to my [knowledge base article]({% link /collections/_kb/windows-10-cannot-connect-to-vpn.md %}) for more information.