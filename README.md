# ArkDeploy Driver Hub

[![Version](https://img.shields.io/badge/version-1.0.0--beta.1-purple.svg)](https://github.com/ArkDeployDev/ArkDeploy.DriverHub/releases)
[![Platform](https://img.shields.io/badge/platform-Windows%2010%20%7C%2011%20%7C%20Server-blue.svg)](https://www.ArkDeploy.com)
[![Architecture](https://img.shields.io/badge/arch-x64-lightgrey.svg)](https://www.ArkDeploy.com)
[![License](https://img.shields.io/badge/license-ArkDeploy%20Commercial%20%2F%20Free%20Tier-green.svg)](https://www.ArkDeploy.com)

**ArkDeploy Driver Hub** is a high-performance on-premises driver repository and hardware matching daemon designed for IT workshops, deployment benches, and enterprise imaging. It replaces slow vendor packs with native Win32 SetupAPI bus scans and content-addressable storage (CAS) to deliver exact silicon driver matches in seconds.

---

## 📥 Downloads

| Installer | Description | Version | Size | Direct Download |
| :--- | :--- | :---: | :---: | :---: |
| **ArkDeploy-DriverHub-Setup-v1.0.0-beta.1.exe** | Versioned Windows Installer | `1.0.0-beta.1` | ~10.8 MB | [⬇️ Download](https://github.com/ArkDeployDev/ArkDeploy.DriverHub/raw/main/releases/ArkDeploy-DriverHub-Setup-v1.0.0-beta.1.exe) |
| **ArkDeploy-DriverHub-Setup.exe** | Latest Release Pointer | Latest | ~10.8 MB | [⬇️ Download](https://github.com/ArkDeployDev/ArkDeploy.DriverHub/raw/main/releases/ArkDeploy-DriverHub-Setup.exe) |

### 🔒 Checksums (SHA-256)

| File | SHA-256 Checksum |
| :--- | :--- |
| `ArkDeploy-DriverHub-Setup-v1.0.0-beta.1.exe` | `e12768872029750143d0fe12aad17314e8c7359f82d6da32ef4ea528accfaa6a` |
| `ArkDeploy-DriverHub-Setup.exe` | `e12768872029750143d0fe12aad17314e8c7359f82d6da32ef4ea528accfaa6a` |

---

## 🚀 Installation

### Interactive Setup (GUI)
1. Download **`ArkDeploy-DriverHub-Setup-v1.0.0-beta.1.exe`**.
2. Run the executable as **Administrator**.
3. Choose your desired HTTP service port (default: `5050`).
4. Click **Install**. The installer automatically creates and starts the `ArkDeployHub` Windows Service and adds the required Windows Firewall inbound rule.

### Unattended / Silent Installation
To deploy silently via script or automated provisioning:

```cmd
ArkDeploy-DriverHub-Setup-v1.0.0-beta.1.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART
```

To specify a custom port during silent installation:

```cmd
ArkDeploy-DriverHub-Setup-v1.0.0-beta.1.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART /PORT=8080
```

---

## 🖥️ Getting Started

### 1. Access the Hub Dashboard
Once installed, open your web browser and navigate to:
```
http://localhost:5050
```
*(Or `http://<your-server-ip>:5050` from any computer on your local network)*

### 2. Connect a Bench PC or WinPE
On any client PC or WinPE session, open an elevated PowerShell prompt and run:

```powershell
irm http://<hub-ip>:5050/bootstrap | iex
```

### 3. Deploy & Match Drivers
- **Simulate & Audit (Preview without installing):**
  ```powershell
  Invoke-ArkDriverSync -Audit
  ```
- **Match & Install Drivers:**
  ```powershell
  Invoke-ArkDriverSync
  ```
- **Export Drivers to Hub:**
  ```powershell
  Export-ArkDriver
  ```
- **Contribute / Install and Export Drivers to Hub:**
  ```powershell
  Invoke-ArkDriverSync -Contribute
  ```

---

## 📋 System Requirements

- **Operating System:** Windows 10 (1809+), Windows 11, or Windows Server 2016/2019/2022/2025 (64-bit).
- **Privileges:** Local Administrator rights required for service creation and driver injection.
- **Client Requirements:** Windows PowerShell 5.1 or PowerShell 7+ on target bench machines.

---

## 🌐 Official Resources

- **Website:** [ArkDeploy.com](https://www.ArkDeploy.com)
- **Documentation & Issues:** [ArkDeploy Driver Hub Issues](https://github.com/ArkDeployDev/ArkDeploy.DriverHub/issues)
