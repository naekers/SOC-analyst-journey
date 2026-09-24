# CAse 002 - Failed logons and suspicious powerwhell activity

## AKert summary

A SIEM alert identified repeated failed network logon attempts against host "HR-PC04"

The failed logons originated from the internal IP address "10.0.0.57", which was identified as a user workstation in the finance depsartment.

Shortly after the authentication activity, a suspicious powershell process using an encoded command was observed.

## Evidence

- Multiple Windows Event ID "4625" failed logons
- Logon Type 3, indicating a network logon attempt
- Source IP: 10.0.0.57
- Target Host: HR-PC04
- Account targeted: Admin
- Source system identified as a finance user workstation
- "powershell.exe" launched shortly after the authentication attempts
- Powershell command contained encoded content
- No Expected administrative activity was identified at the time

  ## Analyst Decision

  I classified the activity as suspicious and decided to escalate the alert for further investigation

  The authentication activity alone could potentially have been caused by a configuration issue or incorrect credentials. But the PowerShell execution shortly after was what warranted the escalation, as it significantly increase the level of concern.

  ## Why I Escalated

  The combination of repeated failed authentication attempts and encoded PowerShell activity could indicate that access was gained to the system and then attempts to execute commands made shortly after.

  Encoded PowerShell is not always malicious, but it can be used to hide the contents of commands from casual inspection.

  Because the activity suggested potential compromise and command execute, I would escalate this to a senior SOC analyst or incident response team for further investigation.

  ## skills practiced
  - Windows Event ID analysis
  - Authentication log investigation
  - Internal IP address investigation
  - Basic Process analysis
  - SIEM alert triage
  - Idntifying suspicious PowerShell activity
  - Incident escalation
