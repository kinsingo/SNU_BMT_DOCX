# How to Use AIBMT GUI via SSH

## 📌 Common Requirement (All Platforms)
* Ensure **X11 forwarding** is enabled when connecting via SSH.
* You must use the **-Y** flag:
  `$ ssh -Y -p (portnum) (username)@(remote IP address)`

---
### 💻 If your SSH client is WINDOWS
Choose one of the following methods:
* **(Recommended) Use WSL** to connect to the SSH remote server.
* **(Recommended) Use MobaXterm**, which has built-in X11 support.
* **Use Xshell** with an additional X11 extension.
* **Use PowerShell**:
  Install and run an **Xserver** (e.g., Xming, VcXsrv) in the background **before connecting** via SSH.

### 🍎 If your SSH client is MACOS
1. **Install XQuartz** (macOS X11 server)
   `$ brew install --cask xquartz`
2. **Launch XQuartz** and keep it running **in the background**.
3. In a new terminal window, **set the following**:
   `$ export DISPLAY=:0`
   `$ xhost +`
4. **Connect via SSH** with the **-Y** flag and run the AI-BMT.

### 🐧If your SSH client is LINUX
* **No additional setup** is required.
* Ubuntu and most modern distros have X11 server running by default.