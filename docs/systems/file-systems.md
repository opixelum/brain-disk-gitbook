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
