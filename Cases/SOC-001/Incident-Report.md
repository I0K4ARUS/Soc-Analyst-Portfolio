# SOC-0001 - Windows Service Startup Type Changed Investigation

## Executive Summary 
Wazuh generated a low-severity ( lvl 3 ) alert after indicating that the startup type of a windows service had changed. This investigation identified the affected service as the Bachground Intellignece Transfer sERVICE ( BITS ). Analysis determined that the startup type changed from Demand start ( manual ) to Automatic. No indicators of malicious activity were observed, and the event was assessed as normal windows administrator. The alert was closed without escalation.


## Alert Information

| Field - Value |

Case ID - SOC-0001 
Alert Source - Wazuh 
Rule ID - 61104 
Rule Level - 3 (Low) 
Agent - windows10-lab 
Username - socagent 
Event ID - 7040 
Event Source - Service Control Manager 
Alert Description - Service startup type was changed 
Timestamp - Jul 8, 2026 @ 23:01:13 

## Initial Triage

The alert indicated that the startup configuration of a Windows service was modified. As service configuration changes can be associated with both legitimate administrative actions and malicious activity, additional investigation was required to identify the affected service and assess the impact.

## Evidence Collected

- Event ID: 7040
- Event Source: Service Control Manager
- Service Name: Background Intelligent Transfer Service (BITS)
- Previous Startup Type: Demand Start (Manual)
- New Startup Type: Automatic
- User: socagent
- Host: windows10-lab

## Investigation

The investigation confirmed that the modified service was the Windows Background Intelligent Transfer Service (BITS). BITS is a legitimate Microsoft Windows service responsible for transferring files in the background, including Windows Updates and Microsoft Defender updates.

No evidence was identified indicating that the service was replaced, disabled, or modified by unauthorized software. No additional suspicious alerts were observed during the investigation.

## MITRE ATT&CK Analysis

Although service configuration changes can be associated with adversary techniques involving Windows services or defense evasion, the evidence collected during this investigation does not indicate malicious activity.

MITRE ATT&CK mapping was reviewed but was determined to be not applicable for this event because the service modification was consistent with legitimate Windows operating system behavior.

## Risk Assessment

Risk Level: Low

The affected service was a legitimate Windows service (BITS), and the startup type was changed from Manual to Automatic. This behavior is commonly observed during Windows maintenance or update operations. No indicators of compromise were identified.

## Analyst Assessment

Detection Classification: False Positive
Incident Classification: Benign Administrative Activity
Severity: Low
Escalation Required: No

## Analyst Decision

The alert was reviewed and validated.
The service modification involved a legitimate Windows service and no suspicious activity was identified.
The alert was closed by the L1 analyst without escalation.
