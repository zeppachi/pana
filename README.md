# pana
Anonymization of Linux communications.  
Tor Transparent Proxy & DNS over Tor & Kill Switch

## Install/Update
```bash
# git clone https://github.com/zeppachi/pana.git
# cd pana
# python3 pana install
```
\* It will be automatically enabled when the installation is completed.
## Rebuild the Tor Circuit
```bash
# pana renew
```
or
```bash
# systemctl restart pana
```
## How to Enable/Disable
```bash
# pana [enable|disable]
```
\* It also disables KillSwitch!
