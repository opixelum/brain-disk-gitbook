# File Systems

## Quota

- **Limit on disk usage (inodes or blocks)**;
- Can be set on a **per-user** or **per-group** basis;
- Max number of **files** is related to the limit on **inodes** (1 file = 1
  inode);
- Max **disk space** is related to the limit on **blocks**;
- Hard limit: user **cannot exceed** the limit;
- Soft limit: user can exceed the limit for a **certain amount of time** (grace
  period) before the hard limit is enforced;

### Quota Packages

| Package       | Description                   |
|---------------|-------------------------------|
| `quota`       | **user** and **group** quotas |
| `quota-tools` | **project** quotas            |

- Mount options:
  - `usrquota`: **user** quotas;
  - `grpquota`: **group** quotas;
  - `prjquota`: **project** quotas;
- Quota configuration files are located at partition root:
  - `/aquota.user`: **user** quotas;
  - `/aquota.group`: **group** quotas;
  - `/aquota.project`: **project** quotas;

### Quota Commands

| Command              | Description                         |
|----------------------|-------------------------------------|
| `edquota -u <user>`  | Edit user quota                     | 
| `edquota -g <group>` | Edit group quota                    |
| `edquota -t`         | Edit grace period                   |
| `quota -u <user>`    | Show user quota                     |
| `quota -g <group>`   | Show group quota                    |
| `quota -P <project>` | Show project quota                  |
| `quotacheck -u`      | Check user quota                    |
| `quotacheck -g`      | Check group quota                   |
| `quotacheck -P`      | Check project quota                 |
| `quotaoff -u`        | Disable user quota                  |
| `quotaoff -g`        | Disable group quota                 |
| `quotaoff -P`        | Disable project quota               |
| `quotaon -u`         | Enable user quota                   |
| `quotaon -g`         | Enable group quota                  |
| `quotaon -P`         | Enable project quota                |
| `repquota -u`        | Show user quota for all users       |
| `repquota -g`        | Show group quota for all groups     |
| `repquota -P`        | Show project quota for all projects |
