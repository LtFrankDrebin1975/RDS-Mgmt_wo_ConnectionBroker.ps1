# RDS-Mgmt_wo_ConnectionBroker.ps1
Manage Windows 2012 R2 Remote Desktop sessions using a GUI w/o Connection Broker
With Windows Server 2012 R2 your companies helpdesk does not have any possibility to manage Remote Desktop User Sessions as there is simply no tool to accomplish that on Windows 2012 R2.

This is where this script comes into play as a replacement for the Remote Desktop Services Manager of Windows 2008.

What it does:


Connect to the Connection broker and import all Session Collections
After choosing a collection it imports all user sessions in this collection
Letting you choose one or more user sessions, you can:
send a message to these users
logoff the user from a session
disconnect a user from the session
mirror the user session
 

This script is based on the script of Denis Cooper (thank you very much for your work!).

There are some prereqs for this to work:

you need to set the following on each of your Remote Desktop Session Host(s) to the helpdesk group:
wmic /namespace:\\root\CIMV2\TerminalServices PATH Win32_TSPermissionsSetting WHERE (TerminalName ="RDP-Tcp") CALL AddAccount "<domain\group>",2

Note: Figured out that you have to REBOOT your RDSH(s) after this step!

Call the script with the following params: -RDSServerName <RDSH1.your.domain>,<RDSH2.your.domain>,<RDSH<n>.your.domain>
in order to mirror a session you need an up-to-date Remote Desktop Client
In this version your helpdesk there's no need for admin rights on the connection broker!

Hope you enjoy it!
