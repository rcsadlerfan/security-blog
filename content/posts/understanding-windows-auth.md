---
title: 'Understanding Windows Authentication'
description: 'When investigating events in a Windows domain environment, the logs can be misleading'
tags: ['featured', 'windows', 'kerberos']
---
# Understanding Windows Authentication
Windows logs are a great way to gain insight into what is happening in your network and on your workstaions and servers, but there are some nuances when trying to interpret what they mean. One of the biggest examples of this is authentication with domain controllers.

Before we get into that, lets take a look at the Windows authentication logs:
- [4264](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4624): An account was successfully logged on. (Workstation and Domain Controller)
- [4625](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4625): An account failed to log on. (Workstation and Domain Controller)
- [4768](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4768): A Kerberos authentication ticket (TGT) was requested. (Domain Controller)
- [4769](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4769): A Kerberos service ticket was requested. (Domain Controller)
- [4771](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4771): Kerberos pre-authentication failed. (Domain Controller)

As you can see, there are a multitude of events that can generate during an authentication. As you can *also* see, some events can generate on both machines whereas others can only generate on the domain controller. This is where the confusion lies.

Based on the descriptions of these event IDs, one would think "Obviously the 4624 event would generate when I log in!" and they would be correct. But *where* this event generates is key. Logically, the 4624 event should generate because I successfully logged in, and this does happen on the workstation. But the domain controller is different. While you are "successfully logged on" as the event ID portrays, the domain controller **DOES NOT** generate a 4624 event. Even though you are authenticating against the domain controller (since that is where your user is stored), you are not logging into the domain controller itself. Instead, you will end up seeing an NTLM or Kerberos event generate on the domain controller that comes from the workstation you are logging into.

![Basic Windows Authentication Flow](/img/win_auth_basic.svg)