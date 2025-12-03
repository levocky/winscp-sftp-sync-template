# winsscp-sftp-sync.ps1

PowerShell template for downloading or synchronizing files from an SFTP server using the WinSCP .NET assembly.  
All sensitive values such as IP addresses, usernames, and file paths are removed and replaced with configurable parameters and safe dummy defaults.

The script supports two primary operations:

1. **Download**  
   Recursively searches a remote SFTP directory using a file pattern and downloads all matching files.

2. **SyncRemote**  
   Synchronizes a local directory to a remote directory using WinSCP’s built-in mirror functionality (equivalent to `synchronize remote -delete`).

This template is intended for engineers who need fast, reliable, repeatable SFTP automation without embedding personal or environment-specific data.

## Features

- Full SFTP integration using WinSCP .NET API  
- Recursive remote file discovery  
- Pattern-based downloading  
- Option to preserve the remote folder structure locally  
- Directory synchronization mode  
- Clean parameterized design  
- Includes safe dummy defaults for easy onboarding  
- No personal or sensitive values in the template

## Requirements

- PowerShell 5.x or newer  
- WinSCP installed  
- `WinSCPnet.dll` available locally (installed with WinSCP)  
- Valid SFTP private key (`.ppk`)  

## Usage

## 1. Basic download mode

```powershell
.\winsscp-sftp-sync.ps1 `
  -PpkPath "C:\Keys\mykey.ppk" `
  -LocalPath "C:\Data\Downloads" `
  -RemoteRoot "/remote/messages" `
  -RemoteHost "sftp.example.com" `
  -UserName "myuser" `
  -Pattern "*msg*"
```

---

## 2. Download while preserving remote folder structure

```powershell
.\winsscp-sftp-sync.ps1 `
  -PpkPath "C:\Keys\mykey.ppk" `
  -LocalPath "C:\Data\Tree" `
  -RemoteRoot "/remote/logs" `
  -RemoteHost "sftp.example.com" `
  -UserName "myuser" `
  -Pattern "*.gz" `
  -PreserveRemoteStructure $true
```

---

## 3. Download everything (no pattern filter)

```powershell
.\winsscp-sftp-sync.ps1 `
  -PpkPath "C:\Keys\mykey.ppk" `
  -LocalPath "C:\Dump" `
  -RemoteRoot "/data/archive" `
  -RemoteHost "sftp.example.com" `
  -UserName "myuser" `
  -Pattern "*"
```

---

## 4. Use a custom SFTP port

```powershell
.\winsscp-sftp-sync.ps1 `
  -PpkPath "C:\Keys\mykey.ppk" `
  -LocalPath "C:\Downloads" `
  -RemoteRoot "/export/messages" `
  -RemoteHost "10.20.30.40" `
  -RemotePort 8022 `
  -UserName "myuser"
```

---

## 5. Synchronize local → remote (mirror with delete)

```powershell
.\winsscp-sftp-sync.ps1 `
  -PpkPath "C:\Keys\mykey.ppk" `
  -LocalPath "C:\Data\Out" `
  -RemoteRoot "/remote/inbound" `
  -RemoteHost "sftp.example.com" `
  -UserName "myuser" `
  -Mode "SyncRemote"
```

---

## 6. Synchronize with a custom remote path

```powershell
.\winsscp-sftp-sync.ps1 `
  -PpkPath "D:\SSH\prod_key.ppk" `
  -LocalPath "D:\Payload" `
  -RemoteRoot "/opt/app/input" `
  -RemoteHost "host.example.net" `
  -UserName "deploy_user" `
  -Mode "SyncRemote"
```

---

## 7. Minimal example (uses placeholder defaults)

```powershell
.\winsscp-sftp-sync.ps1
```

---

