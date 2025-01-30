# Linux-Management-User-management-and-file-system-access
# User and File Permissions Setup

## 1. Creating Users
- Used `adduser` for Tupu. - Command used: `sudo adduser tupu`
- Used `useradd` for Lupu with similar properties. - Command used: `sudo useradd -m -d /home/lupu -s /bin/bash -G lupu lupu`
- Created Hupu as a system user. - Command used: `sudo useradd --system --shell /bin/false hupu`

## 2. Granting Sudo Access
- Edited `visudo` to add Tupu and Lupu.
- Alternatively, used `usermod -aG sudo` to grant access.

## 3. Securing `/opt/projekti`
- Created `projekti` group.
- Assigned Tupu and Lupu as members.
- Set `2770` permissions to restrict access.

*Commands used:*
- sudo mkdir -p /opt/projekti
- sudo groupadd projekti
- sudo usermod -aG projekti tupu
- sudo usermod -aG projekti lupu
- sudo chown :projekti /opt/projekti
- sudo chmod 2770 /opt/projekti

*Explanation:*
- A directory /opt/projekti was created.
- A group projekti was created, and tupu and lupu were added to it.
- The setgid bit was set to ensure new files inherit the projekti group ownership.
- Permissions were set to 2770 to restrict access to only tupu and lupu.

## 4. Testing
- Confirmed access using `su - user`.
- Ensured files inherit `projekti` ownership.
