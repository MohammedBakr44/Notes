
Summarise how can we start to get a foothold in a web application

- We start with simple `nmap` and `gobuster` scan to check potential open ports and exposed directories.
- We traverse to the directories we found, in the case of this machine we found `/nibbleblog` and `/admin`.
- We analyse the technologies used using `webalayzer` extension or `whatweb` from terminal.
- We found `admin.php` and used it to login to an admin account, creds might be present in one the folders we discovered earlier.
- Checked for password brute-force protections.
- Found alleged clues for an admin password.

bonus: [ippsec's walkthrough](https://youtu.be/s_0GcRGv6Ds)
