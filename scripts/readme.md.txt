# STIG Fix: WN10-00-000107 – Disable Windows Copilot

## 📋 Description
This STIG requires that Windows Copilot be disabled to prevent potential data leakage or unauthorized network communication.

- **STIG ID:** WN10-00-000107
- **Severity:** CAT II
- **Fix Method:** Registry Policy

## 🔧 Remediation Steps

### Manual Fix
1. Open `regedit`.
2. Navigate to:
3. Create a new key called `WindowsCopilot`.
4. Inside that key, create a new `DWORD (32-bit)` value:
- Name: `TurnOffWindowsCopilot`
- Value: `1` (Decimal)
5. Restart the system.

### Automated Fix (PowerShell)
Run this script in **PowerShell ISE as Administrator**:
```powershell
$regPath = "HKCU:\Software\Policies\Microsoft\Windows\WindowsCopilot"
New-Item -Path $regPath -Force
New-ItemProperty -Path $regPath -Name "TurnOffWindowsCopilot" -PropertyType DWORD -Value 1 -Force
