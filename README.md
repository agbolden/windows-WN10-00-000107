
# STIG Fix: WN10-00-000107 – Disable Windows Copilot

## 📋 Description
This STIG requires that Windows Copilot be disabled to prevent unauthorized network communications and data leakage.

- **STIG ID:** WN10-00-000107  
- **Severity:** CAT II  
- **Fix Method:** Registry (Manual + PowerShell)

---

## 🔧 Manual Remediation Steps

1. Open `regedit`
2. Navigate to:
3. Create a new key named: `WindowsCopilot`
4. Inside that key, create a new DWORD:
- **Name:** `TurnOffWindowsCopilot`
- **Value:** `1` (Decimal)
5. Restart the machine

---

## ⚙️ Automated Fix (PowerShell)

Open **PowerShell ISE as Administrator** and run:

```powershell
$regPath = "HKCU:\Software\Policies\Microsoft\Windows\WindowsCopilot"
New-Item -Path $regPath -Force
New-ItemProperty -Path $regPath -Name "TurnOffWindowsCopilot" -PropertyType DWORD -Value 1 -Force

---

### ✅ Once You Paste It:
1. Scroll down
2. Type commit message: `Updated README to display screenshots inline`
3. Click **Commit changes**

Let me know when it’s saved — I’ll double-check that everything renders correctly for you.
