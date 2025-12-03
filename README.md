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

[winscp-sync-examples.md](https://github.com/user-attachments/files/23899272/winscp-sync-examples.md)
