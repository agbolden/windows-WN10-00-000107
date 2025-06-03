
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
4. Inside it, create a new `DWORD (32-bit)` value:
- Name: `TurnOffWindowsCopilot`
- Value: `1` (Decimal)
5. Restart the system

---

## ⚙️ Automated Fix (PowerShell)

Open **PowerShell ISE as Administrator** and run:

```powershell
$regPath = "HKCU:\Software\Policies\Microsoft\Windows\WindowsCopilot"
New-Item -Path $regPath -Force
New-ItemProperty -Path $regPath -Name "TurnOffWindowsCopilot" -PropertyType DWORD -Value 1 -Force

5. Scroll down  
6. In the **Commit changes** box, type:  
   `Updated README with full STIG documentation`
7. Click the green **Commit changes** button

---

Once that’s done, you’re officially done with your first fully documented STIG project!

Want me to check the repo and confirm it’s good to go?
