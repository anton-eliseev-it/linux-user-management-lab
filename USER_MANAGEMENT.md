# User and Permission Management

This document describes the user, group, and permission model configured
in this Linux lab environment. The goal is to demonstrate a simple and clear
access control structure following least-privilege principles.

---

## Users and Groups

### Groups
- developers  
  Used for users who need access to application source code.

- support  
  Used for support staff responsible for logs and troubleshooting.

### Users
- alice  
  Member of the `developers` group.

- bob  
  Member of the `developers` group.

- support1  
  Member of the `support` group and `sudo` group for administrative tasks.

---

## Directory Structure

/srv/projectX/
├── code/
└── logs/

- `/srv/projectX/code`  
  Contains application source code.

- `/srv/projectX/logs`  
  Contains application and system logs.

---

## Ownership and Permissions

### Base Directory
- Owner: root
- Group: developers
- Permissions: 750

This allows developers to access project files while preventing access
from unauthorized users.

### Logs Directory
- Owner: root
- Group: support
- Permissions: 770

Only support staff can access and modify logs. Developers do not have
access to log files.

---

## Access Model Summary

- Developers (`alice`, `bob`)
  - Can access `/srv/projectX/code`
  - Cannot access `/srv/projectX/logs`

- Support (`support1`)
  - Can access `/srv/projectX/logs`
  - Has sudo privileges for administrative tasks

- Other users
  - No access to project directories

---

## Verification

Access was verified by switching users and attempting to list directories
using standard Linux commands (`su`, `ls`).

This setup demonstrates a basic but realistic permission model commonly
used in Linux-based environments.
