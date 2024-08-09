# Downloaders and Launchers

Downloaders download malware from internet and executes it, they commonly use `URLDownloadToFileA` followed by a `WinExec`.
*Launchers* AKA *loaders* is an executable that installs malware.

# Backdoors
Allows remote access over `HTTP` with port **80** to hide in plain sight.

## Windows Reverse Shells 
### Basic Technique
It starts `cmd.exe` to run `netcat`. It involves `CreateProcess` and manipulation of `STARTUPINFO` struct that's passed to `CreateProcess`. A socket is created and a connection to remove server established.

## Multi-threaded Technique
It involves creation of the `socket`, two pipes, and two threads. Utilising `CreateThread` and `CreatePipe`.

## GINA Interception
Third-party DLLs are found in the following register
`HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\GinaDLL`
Malicious DLLs intercept the communication between `msgina.dll` and `Winlogon`; hence if there's a DLL that exports many functions that starts with `Wlx` it's an indication that a GINA interception is occuring.

## Hash Dumping
Grab `NTLM` and `LM` hashes using a `pass-the-hash` attack to authenticate a remote host.
One of the most popular `Hash Dumping` tools `pwdump` which uses `lsaext.dll`, once it's running inside `lsass.exe`; `pwdump` calls `GetHash` which exported by `lsaext.dll`.

## User-Space Keyloggers
Uses either `Hooking` or `Polling`. `Hooking` uses Windows API to notify the malware whenever a key is pressed, typically with `SetWindowHookEx` function.
`Polling` uses the windows API to constantly *poll* the state of the keys usually using `GetAsyncKeyState` and `GetForegroundWindow` functions.

Can be identified from checking strings or API calls.

# Persistence Mechanisms
## Windows Registery
- `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run`
- `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Windows`  APPInit_DLLs
- `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\` Winlogon Notify
> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\ 
- `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Svchost` SvcHost DLL.