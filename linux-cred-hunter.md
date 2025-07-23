# 🔑 linux-cred-hunter

## ✅ `find_credentials.sh`

```
#!/bin/bash

# Color definitions
GREEN='\033[1;32m'
RED='\033[1;31m'
NC='\033[0m' # No Color

echo -e "${GREEN}[*] Searching for common credential files on the system...${NC}"
echo

# List of potential credential file paths (some use wildcards)
files=(
  "/etc/passwd"
  "/etc/shadow"
  "/etc/group"
  "/etc/gshadow"
  "/var/log/auth.log"
  "/etc/mysql/my.cnf"
  "/var/www/html/*config*.php"
  "/home/*/.bash_history"
  "/home/*/.ssh/id_rsa"
  "/home/*/.ssh/known_hosts"
  "/root/.bash_history"
  "/home/*/.netrc"
  "/home/*/.git-credentials"
  "/home/*/.aws/credentials"
  "/home/*/.config/**"
  "/etc/openvpn/*.conf"
  "/etc/samba/smb.conf"
  "/var/www/html/wp-config.php"
  "/opt/**"
)

# Search and display results
for path in "${files[@]}"; do
  matches=$(find $path 2>/dev/null)
  if [[ ! -z "$matches" ]]; then
    echo -e "${GREEN}[+] Found:${NC} $path"
    echo "$matches" | sed 's/^/    - /'
    echo
  else
    echo -e "${RED}[-] Not Found:${NC} $path"
  fi
done

echo -e "${GREEN}[*] Done.${NC}"

```

## 🛠️ How to Use:
- Save the script:
```
nano find_credentials.sh
```

> (Paste the script and save with Ctrl+O, Enter, Ctrl+X)

- Make it executable:
```
chmod +x find_credentials.sh
```

- Run the script:
```
./find_credentials.sh
```
