# Module: Endpoint Security Automation

## Objectives
- Understand how automated endpoint investigations work in Microsoft Defender.
- Learn to approve automated remediation actions for endpoints.
- Configure isolation policies for compromised devices.
- Set up automated file remediation thresholds.

## Prerequisites
- Access to a Microsoft 365 E5 tenant with Microsoft Defender for Endpoint configured.
- At least 5-10 devices onboarded into Microsoft Defender.
- Appropriate permissions to access the Microsoft 365 Defender portal.

## Step-by-Step Instructions

### Step 1: Review an Automated Endpoint Investigation
1. Log into the Microsoft 365 Defender portal.
2. Navigate to the "Incidents & Alerts" section.
3. Select an incident related to an endpoint.
4. Click on the "Investigation" tab to review the automated investigation details.

### Step 2: Approve an Automated Remediation Action
1. In the selected investigation, locate the "Actions Taken" section.
2. Identify pending remediation actions.
3. Click on "Approve" or "Reject" for each action based on the investigation details.

### Step 3: Configure an Isolation Policy for Compromised Devices
1. Go to the "Settings" section in the Microsoft Defender portal.
2. Navigate to "Endpoints" > "Device Isolation".
3. Configure the isolation policy to automatically isolate devices marked as compromised.

### Step 4: Set Up Automated File Remediation Thresholds
1. In the "Settings" section, navigate to "Endpoints" > "Remediation".
2. Define thresholds for automated file remediation.
   - Example: Automatically remediate files with a high confidence level of being malicious.

## Expected Outcomes
- Enhanced understanding of endpoint security automation workflows.
- Improved ability to configure and approve endpoint remediation actions.
- Reduction in manual intervention for endpoint-related incidents.

## Additional Resources
- [Microsoft Defender for Endpoint Documentation](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/)
- [Automated Investigation and Response Overview](https://learn.microsoft.com/en-us/microsoft-365/security/defender/air-overview)
