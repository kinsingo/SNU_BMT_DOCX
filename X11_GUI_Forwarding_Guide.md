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

---
### 🛠️ Troubleshooting (Host Side)
> **Note**: In most standard Linux server distributions (Ubuntu, Debian, etc.), the following are configured by default. You only need to check these if the GUI does not appear after following the steps above.

If the GUI does not appear, ensure the following settings on the **Remote Server**:

1. **Check SSH Configuration**:
   In `/etc/ssh/sshd_config`, verify that `X11Forwarding` is enabled.
   ```bash
   # On the remote server
   cat /etc/ssh/sshd_config | grep X11Forwarding
   # It should say: X11Forwarding yes

2. **Install xauth**:
    Even with the `-Y` flag, the remote server requires `xauth` to generate and manage X11 authentication cookies. Without it, the SSH daemon cannot set up the display forwarding.
    ```bash
    # Check if xauth is installed
    which xauth

    # If not found, install it:
    # For Ubuntu/Debian
    sudo apt-get update && sudo apt-get install xauth

    # For CentOS/RHEL/Fedora
    sudo yum install xorg-x11-xauth