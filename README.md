# Firewall-Testing-Windows
# Windows Firewall Lab
This repository documents the setup, configuration, and testing of *Windows Defender Firewall rules* as part of a networking and security exercise.  
The goal is to understand how firewalls control inbound and outbound traffic on specific ports.

##  Objectives
- Configure basic inbound firewall rules.
- Block traffic on a specific port (e.g., Telnet on TCP 23).
- Test firewall behavior using PowerShell commands.
- Allow/deny traffic and restore original state.
- Document findings with screenshots.

##  Tools Used
- *Windows Defender Firewall with Advanced Security*
- *PowerShell*
- Optional: Telnet client, Test-NetConnection for testing

## Steps Performed
1. Open *Windows Defender Firewall with Advanced Security* (wf.msc).
2. View and list existing inbound rules.
3. Create a new *Inbound Rule*:
   - Type: *Port*
   - Protocol: *TCP*
   - Local Port: 23
   - Action: *Block the connection*
   - Apply to: Domain, Private, Public
   - Name: Block Telnet Inbound
4. Verify the rule:
   - Inbound Rules list
   - Rule properties (General + Protocols/Ports)
   - PowerShell:
     powershell
     Get-NetFirewallRule -DisplayName "Block Telnet Inbound" | Get-NetFirewallPortFilter
     
5. (Optional) Test locally:
   ```powershell
   Test-NetConnection -ComputerName localhost -Port 23
