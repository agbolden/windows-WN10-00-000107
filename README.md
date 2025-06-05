# 🛡️ STIG Fix: WN10-00-000107 – Disable Windows Copilot

## 📋 Overview

This STIG requires that **Windows Copilot** be disabled on Windows 10 systems to reduce unauthorized data leakage and AI-driven system interactions in secure environments.

- **STIG ID:** WN10-00-000107  
- **Severity:** CAT II  
- **Validation Tool:** Tenable.sc  
- **Remediation Methods:** Manual (Registry) & Automated (PowerShell)

---

## ❌ Initial Compliance Scan – Failed

The system was scanned using **Tenable**, and flagged as **non-compliant** due to Windows Copilot being enabled.

📸 **Screenshot – Failed STIG Scan**  
![Initial Failed Scan](screenshots/scanfailed.png)
---

## 🛠️ Manual Remediation via Registry Editor

The vulnerability was manually remediated using the Windows Registry Editor:

1. Open `regedit`
2. Navigate to:  
   `HKEY_CURRENT_USER\Software\Policies\Microsoft\Windows`
3. Create a new key named: `WindowsCopilot`
4. Inside that key, create a `DWORD (32-bit)` value:
   - Name: `TurnOffWindowsCopilot`
   - Value: `1` (Decimal)
5. Reboot the system to apply the policy

📸 **Screenshot – Manual Registry Fix**  
![Registry Fix](screenshots/registryfix.png)
---

## ⚙️ Automated Remediation via PowerShell

After resetting the registry, the fix was re-applied using PowerShell to demonstrate automation.

```powershell
$regPath = "HKCU:\Software\Policies\Microsoft\Windows\WindowsCopilot"
New-Item -Path $regPath -Force
New-ItemProperty -Path $regPath -Name "TurnOffWindowsCopilot" -PropertyType DWORD -Value 1 -Force
---

## ✅ Final Compliance Scan – Passed

After applying the PowerShell fix, a follow-up Tenable STIG scan was conducted.  
The system is now **fully compliant** with STIG ID `WN10-00-000107`.

📸 **Screenshot – Passed STIG Scan**  
![Final Passed Scan](screenshots/scanpassed.png)



