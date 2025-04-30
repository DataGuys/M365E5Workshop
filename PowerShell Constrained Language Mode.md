# Implementing PowerShell Constrained Language Mode on Intune-Managed Endpoints

## Overview

This document describes the implementation of PowerShell Constrained Language Mode (CLM) on Windows 10/11 endpoints managed through Microsoft Intune. This security control restricts PowerShell's functionality to help protect against script-based attacks.

## What is PowerShell Constrained Language Mode?

PowerShell Constrained Language Mode limits PowerShell's capabilities by:

- Restricting types that can be used
- Preventing access to COM objects
- Blocking Win32 API access through Add-Type
- Disabling script dot-sourcing
- Limiting usage of certain language elements and classes
- Preventing arbitrary code execution

## Security Benefits

- **Reduces Attack Surface**: Limits the functionality available to malicious scripts
- **PowerShell Security**: Complements other security measures like AMSI and Script Block Logging
- **Defense-in-Depth**: Adds another layer to your security strategy
- **Malware Protection**: Many PowerShell-based malware payloads fail to execute properly
- **Living-off-the-Land Defense**: Prevents attackers from using legitimate PowerShell capabilities for malicious purposes

## How It Mitigates Script Attacks

1. **Prevents Reflective Loading**: Blocks attackers from loading arbitrary DLLs into memory
2. **Limits Obfuscation**: Reduces effectiveness of obfuscated malicious scripts
3. **Blocks Credential Access**: Restricts access to credential objects and LSASS memory
4. **Prevents Type Manipulation**: Blocks creation of custom types used for exploitation
5. **COM Interaction Restrictions**: Limits access to COM objects often used for lateral movement

## Implementation via Microsoft Intune

### Method: Registry Configuration

The following registry key enables PowerShell Constrained Language Mode system-wide:

```powershell
reg add "HKLM\System\CurrentControlSet\Control\Session Manager\Environment" /v "__PSLockdownPolicy" /t REG_SZ /d "4" /f
```

### Deployment Steps

1. In the Microsoft Endpoint Manager admin center, create a new PowerShell Script policy
2. Upload the script that sets the registry key
3. Configure to run in system context with highest privileges
4. Assign to desired device groups
5. Set the script to run during computer startup

### Proof of Concept Testing with Intune

Before deploying to production, it's recommended to test this implementation:

#### Test Group Setup
1. Create a dedicated test device group in Intune named "CLM POC Testing"
2. Add 2-3 representative test machines to this group

#### Implementation Script
Create a PowerShell script file named `Enable-ConstrainedLanguageMode.ps1`:

```powershell
# Set registry key to enable Constrained Language Mode
reg add "HKLM\System\CurrentControlSet\Control\Session Manager\Environment" /v "__PSLockdownPolicy" /t REG_SZ /d "4" /f

# Optional: Log the change to Event Log
Write-EventLog -LogName "Application" -Source "Microsoft-Windows-PowerShell" -EventID 800 -EntryType Information -Message "PowerShell Constrained Language Mode has been enabled via Intune policy." -Category 0
```

#### Intune Deployment for POC
1. In Microsoft Endpoint Manager admin center, navigate to **Devices** > **Scripts**
2. Click **+ Add** and select **Windows 10 and later**
3. Provide a name: "PowerShell CLM Implementation - POC"
4. Add a description explaining this is a proof of concept
5. Upload the `Enable-ConstrainedLanguageMode.ps1` script
6. Configure these settings:
   - Run script in 64-bit PowerShell: **Yes**
   - Run script with signed-in credentials: **No**
   - Run this script using the logged-on credentials: **No**
   - Enforce script signature check: **No**
   - Run script in 64-bit PowerShell host: **Yes**
7. Click **Next** and assign to your "CLM POC Testing" group
8. Complete the wizard to deploy

#### Verification Steps
On your test machines:
1. Wait for policy to apply (usually 1-2 hours) or force sync from Intune
2. Open PowerShell and run: `$ExecutionContext.SessionState.LanguageMode`
3. Confirm it returns "ConstrainedLanguage"
4. Test a benign script that uses functionality restricted in CLM, such as:
   ```powershell
   Add-Type -TypeDefinition "public class Test {}"
   ```
   This should fail in Constrained Language Mode

#### Functionality Impact Assessment
Document any issues with legitimate scripts by:
1. Creating a spreadsheet to track tested scripts/tools
2. For each administrative script used in your environment:
   - Run in test environment
   - Document success/failure
   - Note any error messages
   - Identify potential workarounds

#### Rollback Procedure
If needed, deploy this script to remove the restriction:
```powershell
reg delete "HKLM\System\CurrentControlSet\Control\Session Manager\Environment" /v "__PSLockdownPolicy" /f
```

## Testing and Verification

To verify that Constrained Language Mode is enabled:

```powershell
$ExecutionContext.SessionState.LanguageMode
```

This should return "ConstrainedLanguage" if properly configured.

## Limitations and Considerations

- May impact legitimate PowerShell automation and administrative scripts
- Some management tools and applications may rely on Full Language features
- Should be tested thoroughly in a controlled environment before wide deployment
- Consider exclusions for specific service accounts if needed

## Bypass Mitigations

- Combine with AppLocker or Windows Defender Application Control (WDAC) policies
- Implement Just Enough Administration (JEA) endpoints for administrative tasks
- Enable comprehensive logging and monitoring
- Keep systems patched to prevent known CLM bypass techniques

## Additional Resources

- [PowerShell Constrained Language Mode - Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_language_modes)
- [Device configuration profiles in Microsoft Intune - Microsoft Docs](https://docs.microsoft.com/en-us/mem/intune/configuration/device-profile-create)
- [Windows Defender Application Control - Microsoft Docs](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)
