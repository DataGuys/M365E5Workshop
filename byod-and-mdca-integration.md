# Module: Solving the BYOD Challenge with Intune MAM and MDCA Integration

## Objectives
- Understand how to configure Intune Mobile Application Management (MAM) for BYOD scenarios.
- Force non-Entra ID-joined or non-compliant desktops to browser-only access.
- Enforce session controls via Microsoft Defender for Cloud Apps (MDCA) to block cut, copy, paste, and print actions.

## Prerequisites
- Access to a Microsoft 365 E5 tenant with:
  - Microsoft Intune and Microsoft Defender for Cloud Apps configured.
  - Entra ID (Azure Active Directory) properly set up.
- Test mobile devices and desktops for configuration validation.
- Appropriate permissions to configure Intune, MDCA, and Conditional Access policies.

## Step-by-Step Instructions

### Part 1: Configure Intune MAM for Mobile BYOD
1. Log into the Microsoft Endpoint Manager admin center.
2. Navigate to **Apps** > **App protection policies**.
3. Create a new policy for BYOD devices:
   - Platform: Select **iOS** or **Android**.
   - Assign targeted apps (e.g., Microsoft Outlook, Teams, SharePoint).
   - Configure data protection settings:
     - Block backup to cloud storage.
     - Restrict cut, copy, and paste to managed apps only.
   - Set access requirements:
     - Require PIN for access.
     - Require device to be at least **MAM-compliant**.
4. Assign the policy to the appropriate user groups.

### Part 2: Restrict Non-Compliant Desktops to Browser-Only Access
1. Log into the Entra ID (Azure AD) portal.
2. Navigate to **Security** > **Conditional Access** and create a new policy.
3. Configure the policy:
   - **Assignments**:
     - Users: Target all users or specific BYOD user groups.
     - Devices: Exclude devices that are **Azure AD-joined** or **Intune-compliant**.
   - **Cloud Apps or Actions**: Select **All cloud apps** or specific apps (e.g., Office 365).
   - **Conditions**: 
     - Platform: Target **Windows** and **macOS**.
   - **Access Controls**:
     - Grant: Require access via **browser only** (block desktop apps).
4. Enable the policy and monitor its enforcement.

### Part 3: Enforce MDCA Session Controls to Block Cut, Copy, Paste, and Print
1. Log into the Microsoft Defender for Cloud Apps portal.
2. Navigate to **Control** > **Policies** and create a new session policy.
3. Configure the session policy:
   - Policy type: **Session control**.
   - Session control type: **Block activities**.
   - Targeted apps: Select **Office 365 apps** or other supported apps.
   - Conditions:
     - User risk: Target users flagged as medium or high risk.
     - Device compliance: Target devices that are not compliant.
   - Actions:
     - Block **download, cut, copy, paste, and print** actions.
4. Save the policy and test its functionality with a non-compliant device.

## Expected Outcomes
- Mobile BYOD devices are secured using Intune MAM policies.
- Non-compliant desktops are restricted to browser-only access.
- Cut, copy, paste, and print actions are blocked for non-compliant sessions via MDCA.

## Additional Resources
- [Microsoft Intune App Protection Policies Guide](https://learn.microsoft.com/en-us/microsoft-365/intune/apps/app-protection-policies)
- [Conditional Access Policies in Azure AD](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/)
- [Microsoft Defender for Cloud Apps Session Controls](https://learn.microsoft.com/en-us/cloud-app-security/session-policy-aad)
