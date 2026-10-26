<div align="center">

<!-- ANIMATED TYPING SVG -->
<a href="https://git.io/typing-svg">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=800&size=35&pause=1000&color=00FF41&background=00000000&center=true&vCenter=true&width=800&lines=%5B+INITIALIZING+CYBER+LAB+%5D;%5B+LOADING+KALI+LINUX+%5D;%5B+ESTABLISHING+NAT+NETWORK+%5D;%5B+STATIC+IP%3A+10.0.0.2+SECURED+%5D" alt="Typing SVG" />
</a>

<!-- ANIMATED MATRIX RAIN GIF -->
<img src="https://user-images.githubusercontent.com/74038190/216122065-2f028bae-25d6-4a3c-bc9f-175394ed5011.gif" width="100%" height="10" />

# 🐉 𝕂 𝔸 𝕃 𝕀  ℂ 𝕐 𝔹 𝔼 ℝ 𝕃 𝔸 𝔹 🐉

### ⚡ *The Ultimate VirtualBox Penetration Testing Environment* ⚡

[![Kali Linux](https://img.shields.io/badge/Kali_Linux-2026.2-557C94?style=for-the-badge&logo=kalilinux&logoColor=white&labelColor=000000)](#)
[![VirtualBox](https://img.shields.io/badge/VirtualBox-7.0+-2F61B4?style=for-the-badge&logo=virtualbox&logoColor=white&labelColor=000000)](#)
[![Network](https://img.shields.io/badge/Network-10.0.0.0%2F24-00FF41?style=for-the-badge&logo=cisco&logoColor=white&labelColor=000000)](#)
[![Status](https://img.shields.io/badge/System_Status-ONLINE-00FF41?style=for-the-badge&logo=statuspage&logoColor=white&labelColor=000000)](#)

<img src="https://user-images.githubusercontent.com/74038190/216122065-2f028bae-25d6-4a3c-bc9f-175394ed5011.gif" width="100%" height="10" />

</div>

<br />

> 🚨 **"𝕋𝕙𝕖 𝕢𝕦𝕚𝕖𝕥𝕖𝕤𝕥 𝕙𝕒𝕔𝕜𝕖𝕣𝕤 𝕒𝕣𝕖 𝕥𝕙𝕖 𝕕𝕖𝕒𝕕𝕝𝕚𝕖𝕤𝕥."** 🚨

Welcome to the **Kali Cyber Lab**. This repository provides an automated, fully reproducible configuration for deploying a Kali Linux virtual machine inside an isolated VirtualBox NAT Network. 

By abandoning the default DHCP configurations, we force a **Static IP (`10.0.0.2`)**. This ensures your exploits, payloads, and reverse shells always know exactly where home is.

---

## 📡 𝕃 𝕒 𝕓   𝔸 𝕣 𝕔 𝕙 𝕚 𝕥 𝕖 𝕔 𝕥 𝕦 𝕣 𝕖

```text
 ██████╗  █████╗ ██╗     ██╗    ██╗   ██╗██████╗ 
 ██╔══██╗██╔══██╗██║     ██║    ██║   ██║██╔══██╗
 ██║  ██║███████║██║     ██║    ██║   ██║██████╔╝
 ██║  ██║██╔══██║██║     ██║    ╚██╗ ██╔╝██╔══██╗
 ██████╔╝██║  ██║███████╗███████╗╚████╔╝ ██████╔╝
 ╚═════╝ ╚═╝  ╚═╝╚══════╝╚══════╝ ╚═══╝  ╚═════╝ 
```

<div align="center">

```text
┌─────────────────────────────────────────────────────────────┐
│                     🌐 VIRTUALBOX HOST                      │
│                                                             │
│   ┌─────────────────────────────────────────────────────┐   │
│   │          NAT NETWORK (10.0.0.0/24)                  │   │
│   │                                                     │   │
│   │   [ GATEWAY ] ─── 10.0.0.1 (Virtual Router)         │   │
│   │       │                                             │   │
│   │       ├── 🐉 KALI LINUX (Attacker)                  │   │
│   │       │   ├── IP: 10.0.0.2 (Static)                 │   │
│   │       │   └── DNS: 8.8.8.8                          │   │
│   │       │                                             │   │
│   │       └── 🎯 TARGET VM (Victim)                     │   │
│   │           └── IP: 10.0.0.x (Dynamic)                │   │
│   └─────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
```

</div>

---

## ⚙️ ℙ 𝕙 𝕒 𝕤 𝕖  𝟙 : ℕ 𝕖 𝕥 𝕨 𝕠 𝕣 𝕜   𝔹 𝕒 𝕔 𝕜 𝕓 𝕠 𝕟 𝕖

Before booting the VM, we must construct the virtual router that binds our machines together.

1. Launch **VirtualBox**.
2. Navigate to `File` ➔ `Tools` ➔ `Network Manager`.
3. Select the **NAT Networks** tab and click **Create**.
4. Configure the network with these exact parameters:
   *   **Name:** `NatNetwork`
   *   **IPv4 Prefix:** `10.0.0.0/24`
   *   **DHCP Server:** `Enabled` *(Crucial for auto-assigning IPs to future target VMs)*
5. Click **Apply**.

<div align="center">
  <img src="images/vbox-nat-network.png" alt="VirtualBox NAT Network" width="800" style="border-radius: 10px; border: 1px solid #00FF41;"/>
</div>

---

## 🐉 ℙ 𝕙 𝕒 𝕤 𝕖  𝟚 : 𝕊 𝕥 𝕒 𝕥 𝕚 𝕔   𝕀 ℙ   𝔸 𝕤 𝕤 𝕚 𝕘 𝕟 𝕞 𝕖 𝕟 𝕥

To ensure our scripts always find the attacker, we assign a static IP.

1. Attach the Kali VM's Network Adapter to the `NatNetwork` in VirtualBox settings.
2. Boot Kali and open the **Network Settings** GUI (`nm-connection-editor`).
3. Edit `Wired connection 1` and navigate to the **IPv4 Settings** tab:

| Setting | Value | Description |
| :--- | :--- | :--- |
| **Method** | `Manual` | Disables DHCP |
| **Address** | `10.0.0.2` | The attacker's IP |
| **Netmask** | `24` | `255.255.255.0` |
| **Gateway** | `10.0.0.1` | VirtualBox NAT Gateway |
| **DNS Servers**| `8.8.8.8` | Google DNS (for internet access) |

4. **Save** and toggle the network connection off/on.

<div align="center">
  <img src="images/kali-network-settings.png" alt="Kali IPv4 Settings" width="600" style="border-radius: 10px; border: 1px solid #00FF41;"/>
</div>

---

## 🚀 ℙ 𝕙 𝕒 𝕤 𝕖  𝟛 : 𝔸 𝕦 𝕥 𝕠 𝕞 𝕒 𝕥 𝕖 𝕕   ℂ 𝕠 𝕟 𝕗 𝕚 𝕘

Hate clicking through GUIs? Use this terminal script to instantly configure the network via `nmcli`. 

```bash
#!/bin/bash
# ─── ⚡ KALI CYBER LAB NETWORK SETUP ⚡ ───

CON="Wired connection 1"
IP="10.0.0.2/24"
GW="10.0.0.1"
DNS="8.8.8.8"

echo -e "\e[1;32m[*] Applying Static IP Configuration to $CON...\e[0m"

sudo nmcli connection modify "$CON" ipv4.method manual
sudo nmcli connection modify "$CON" ipv4.addresses $IP
sudo nmcli connection modify "$CON" ipv4.gateway $GW
sudo nmcli connection modify "$CON" ipv4.dns $DNS

echo -e "\e[1;33m[*] Restarting NetworkManager...\e[0m"
sudo systemctl restart NetworkManager

echo -e "\e[1;32m[+] Configuration Complete! Target Acquired.\e[0m"
ip a show $(nmcli -g GENERAL.DEVICE connection show "$CON")
```

---

## 🧪 𝕊 𝕪 𝕤 𝕥 𝕖 𝕞   𝕍 𝕖 𝕣 𝕚 𝕗 𝕚 𝕔 𝕒 𝕥 𝕚 𝕠 𝕟

Run these diagnostic checks inside your Kali terminal to ensure the lab is fully operational:

```bash
# 1. Verify IP Assignment
[>] ip a | grep 10.0.0.2

# 2. Check Gateway Connectivity
[>] ping -c 3 10.0.0.1

# 3. Verify External Internet Access
[>] ping -c 3 8.8.8.8

# 4. Verify DNS Resolution
[>] dig google.com +short
```

---

## 💀 𝕋 𝕣 𝕠 𝕦 𝕓 𝕝 𝕖 𝕤 𝕙 𝕠 𝕠 𝕥 𝕚 𝕟 𝕘

<details>
<summary><b>❌ No Internet Access on Kali</b></summary>
<br>
Verify that you did not disable the DHCP server on the VirtualBox NAT Network. Also, double-check that your Gateway is set exactly to <code>10.0.0.1</code>.
</details>

<details>
<summary><b>❌ VM has a 169.254.x.x IP</b></summary>
<br>
This is an APIPA address, meaning Kali failed to apply the manual config. Run <code>sudo systemctl restart NetworkManager</code> or reboot the VM.
</details>

<details>
<summary><b>❌ Host cannot ping the VM</b></summary>
<br>
VirtualBox NAT networks isolate VMs from the host by design. If you need host-to-VM communication, add a second <b>Host-Only Adapter</b> to the VM settings.
</details>

---

## 📁 ℝ 𝕖 𝕡 𝕠 𝕤 𝕚 𝕥 𝕠 𝕣 𝕪   𝕊 𝕥 𝕣 𝕦 𝕔 𝕥 𝕦 𝕣 𝕖

```text
kali-cyber-lab/
├── README.md
├── setup-network.sh
└── images/
    ├── vbox-nat-network.png
    ├── kali-desktop.png
    └── kali-network-settings.png
```

---

<div align="center">

<!-- ANIMATED WARNING GIF -->
<img src="https://user-images.githubusercontent.com/74038190/212284100-561aa473-3905-4a80-b561-0d28506553ee.gif" width="300" />

### ⚠️ 𝕄 𝕀 𝕊 𝕊 𝕀 𝕆 ℕ   𝔻 𝕀 ℝ 𝔼 ℂ 𝕋 𝕀 𝕍 𝔼 ⚠️

*This repository and its contents are for **educational and ethical purposes only**. The author is not responsible for any misuse or damage caused by the material provided. Always obtain proper written authorization before testing any network or system.*

<br/>

**[⬆ Back to Top](#-𝕂-𝔸-𝕃-𝕀--ℂ-𝕐-𝔹-𝔼-ℝ--𝕃-𝔸-𝔹-)**

*Made with 🖤 and ☕ by **Kavan Joshi***

</div>
