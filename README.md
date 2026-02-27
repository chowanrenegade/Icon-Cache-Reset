# Windows Icon Cache Reset Script

A high-performance PowerShell one-liner designed to repair broken, white, or corrupted file icons in the Windows taskbar and File Explorer. This script automates the process of flushing the Windows icon database and restarting the shell environment.

---

## 🚀 Features

* **Automation:** Combines three manual troubleshooting steps into a single execution.
* **Forceful Execution:** Uses the `/f` flag to ensure `explorer.exe` is terminated immediately, preventing file-lock errors.
* **Targeted Cleanup:** Specifically filters for `iconcache*` files to avoid touching unrelated app data.
* **Instant Recovery:** Automatically restarts the Windows Explorer shell so the user isn't left with a blank desktop.

---

## 🧠 How It Works

The script executes three distinct commands linked by semicolons:

1.  **`taskkill /f /im explorer.exe`**: Forcefully terminates the Windows Explorer process. This is necessary because the icon cache files are in use while the shell is running.
2.  **`Get-ChildItem ... | Remove-Item -Force`**: 
    * Navigates to the hidden Windows directory: `%localappdata%\Microsoft\Windows\Explorer`.
    * Locates all files starting with `iconcache`.
    *
