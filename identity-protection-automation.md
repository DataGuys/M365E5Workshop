# Module: Identity Protection Automation

## Objectives
- Understand how identity-based risk detection and automated responses work in Microsoft Defender.
- Learn to review identity-based alerts in the Action Center.
- Approve or reject recommended actions for suspicious authentication activities.
- Configure conditional access policies based on risk levels.

## Prerequisites
- Access to a Microsoft 365 E5 tenant with Microsoft Defender for Identity configured.
- Appropriate permissions to access the Microsoft 365 Defender portal.
- Basic understanding of identity risk concepts (e.g., suspicious sign-in activities, compromised accounts).

## Step-by-Step Instructions

### Step 1: Review Identity-Based Alerts
1. Log into the Microsoft 365 Defender portal.
2. Navigate to the "Incidents & Alerts" section.
3. Select an incident related to identity alerts.
4. Review details such as:
   - Risk level (e.g., high, medium, low)
   - User account involved
   - Associated activities (e.g., sign-in attempts, privilege escalation)

### Step 2: Approve or Reject Recommended Actions
1. In the selected incident, locate the "Actions Taken" section.
2. Identify pending actions for suspicious authentication activities.
3. Click on "Approve" or "Reject" for each action based on the investigation details.

### Step 3: Configure Conditional Access Policies
1. Go to the "Settings" section in the Microsoft Defender portal.
2. Navigate to "Identity" > "Conditional Access".
3. Create or modify a conditional access policy:
   - Example: Block access for users flagged with high-risk sign-ins.
   - Define conditions (e.g., device type, location) and actions (e.g., MFA enforcement, access block).

### Step 4: Enable Automated Identity Monitoring
1. Open the "Identity Protection" section in the Microsoft Defender portal.
2. Configure automated notifications for identity-related risks.
3. Set up thresholds to trigger automated responses:
   - Example: Automatically suspend accounts involved in high-risk activities.

## Expected Outcomes
- Improved understanding of identity protection automation workflows.
- Enhanced ability to manage identity-based alerts and conditional access policies.
- Reduction in manual intervention for identity-related security incidents.

## Additional Resources
- [Microsoft Defender for Identity Documentation](https://learn.microsoft.com/en-us/microsoft-365/security/defender-identity/)
- [Conditional Access Policy Guide](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/)
- [Identity Protection Overview](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/)
