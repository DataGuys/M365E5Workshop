# Module: Deep Dive into Microsoft Purview Features in M365 E5

## Objectives
- Explore Microsoft Purview's capabilities for GDPR compliance and Insider Risk management.
- Understand Adaptive Controls and their applications.
- Learn how to integrate SAP HR systems for employee data management.
- Utilize Trainable Classifiers for advanced Data Loss Prevention (DLP) workflows.
- Conduct a deep dive into DLP capabilities, including endpoint controls for USB blocking and dual enrollment with Defender XDR.

## Prerequisites
- Access to a Microsoft 365 E5 tenant with Microsoft Purview features enabled.
- Familiarity with GDPR requirements, Insider Risk concepts, DLP policies, and endpoint security.
- Permissions to configure Purview Compliance Portal, DLP policies, and endpoint management in Microsoft Defender.

---

## Section 1: GDPR Compliance with Microsoft Purview

### Step 1: Configure GDPR Data Discovery
1. Log into the **Microsoft Purview Compliance Portal**.
2. Navigate to **Data Classification** > **Content Explorer**.
3. Use built-in sensitive information types for GDPR, such as:
   - Personal Identifiable Information (PII).
   - Financial data (e.g., credit card numbers).
   - Health-related data.
4. Create a data discovery policy to scan and identify GDPR-related data.

### Step 2: Set Up GDPR Retention Policies
1. Navigate to **Information Governance** > **Retention Policies**.
2. Create a policy that retains GDPR-related data for the legally mandated duration.
3. Ensure the policy applies to all relevant data locations (e.g., SharePoint, OneDrive, Exchange).

### Step 3: Implement Subject Rights Requests (DSARs)
1. Navigate to **Privacy Management** > **Data Subject Requests**.
2. Create a workflow to automate the process of responding to DSARs.
3. Test the workflow by simulating a request for data export or deletion.

---

## Section 2: Insider Risk Management

### Step 1: Configure Insider Risk Policies
1. Navigate to **Insider Risk Management** in the Compliance Portal.
2. Set up risk indicators for:
   - Data exfiltration (e.g., downloading sensitive files to personal devices).
   - Unauthorized sharing via email or cloud apps.
   - Suspicious behavior such as accessing files during off-hours.
3. Assign policies to specific user groups (e.g., high-risk roles like IT admins).

### Step 2: Investigate Insider Risk Alerts
1. Monitor alerts generated by the policies.
2. Use the **Activity Explorer** to trace user actions (e.g., downloads, file deletions).
3. Take action by assigning cases for further investigation or escalating security controls.

---

## Section 3: Adaptive Controls

### Step 1: Create Adaptive Access Policies
1. Navigate to **Conditional Access** in Azure AD.
2. Set policies for adaptive access based on:
   - User risk (e.g., block high-risk users).
   - Location (e.g., restrict access from untrusted locations).
   - Device compliance (e.g., enforce access only on Intune-compliant devices).
3. Test the policies by simulating access attempts under different conditions.

### Step 2: Enforce Risk-Based Data Access
1. Navigate to **Information Protection** > **Sensitivity Labels**.
2. Apply adaptive rules to sensitivity labels, such as:
   - Restricting external sharing for confidential files.
   - Requiring MFA for access to sensitive documents.
3. Monitor label usage and data access patterns for adjustments.

---

## Section 4: SAP HR System Integration for Employee Data

### Step 1: Enable SAP Connector in Microsoft Purview
1. Log into the Purview Compliance Portal.
2. Navigate to **Data Connectors** and select the **SAP Connector**.
3. Configure the connector with the necessary SAP credentials and endpoints.

### Step 2: Sync Employee Data
1. Map the SAP HR fields to Purview's data schema.
2. Ensure employee data is classified under sensitive information types.
3. Use data discovery tools to monitor and protect employee data.

### Step 3: Monitor Data Access and Usage
1. Configure DLP policies to monitor access to employee data.
2. Set up alerts for unauthorized access or sharing of sensitive HR information.

---

## Section 5: Trainable Classifiers for DLP Work

### Step 1: Create a Trainable Classifier
1. Navigate to **Data Classification** > **Trainable Classifiers**.
2. Select a classifier template or create a custom one for specific use cases (e.g., GDPR data, insider threats).
3. Upload sample data and train the classifier.

### Step 2: Test and Deploy Classifiers
1. Apply the classifier to a DLP policy.
2. Test the policy by simulating real-world data types.
3. Monitor accuracy and refine the classifier as needed.

---

## Section 6: DLP Deep Dive – Endpoint Controls

### Step 1: Block USB Devices
1. Navigate to **Endpoint Data Loss Prevention** in Microsoft Intune.
2. Create a policy to block USB storage devices while allowing approved devices (e.g., encrypted USBs).
3. Deploy the policy to test devices.

### Step 2: Dual Enrollment with Defender XDR
1. Ensure devices are dual-enrolled in Microsoft Defender for Endpoint and Intune.
2. Use Defender XDR to monitor endpoint activities and enforce DLP controls.
3. Configure automated responses for violations, such as quarantining devices.

### Step 3: Enforce Advanced DLP Session Controls
1. Navigate to Microsoft Defender for Cloud Apps.
2. Create session policies for cloud apps to restrict actions:
   - Block downloads, uploads, and sharing.
   - Enforce restrictions like blocking cut, copy, paste, and print.
3. Deploy the session controls and test with different compliance scenarios.

---

## Expected Outcomes
- Comprehensive understanding of Purview features for GDPR compliance, Insider Risk, and Adaptive Controls.
- Successful integration of SAP HR systems for data classification and protection.
- Enhanced DLP strategy using trainable classifiers and endpoint controls.
- Improved security posture through advanced endpoint and session restrictions.

## Additional Resources
- [Microsoft Purview Overview](https://learn.microsoft.com/en-us/microsoft-365/compliance/purview-overview)
- [GDPR Compliance with Microsoft Purview](https://learn.microsoft.com/en-us/microsoft-365/compliance/gdpr-compliance)
- [Insider Risk Management Guide](https://learn.microsoft.com/en-us/microsoft-365/compliance/insider-risk-management)
- [Trainable Classifiers Documentation](https://learn.microsoft.com/en-us/microsoft-365/compliance/classifier-overview)
- [Endpoint DLP Policies](https://learn.microsoft.com/en-us/microsoft-365/compliance/endpoint-dlp-learn-about)
