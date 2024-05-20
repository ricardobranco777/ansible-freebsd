
## SSD trim

- On UFS2, boot as single user and run `tunefs -t enable /` or `fsck_ffs -dE /` periodically.
- On ZFS, run `zfs zpool trim` periodically.

## Golang port management

- `make gomod-vendor` (needs ports-mgmt/modules2tuple)
- `make makesum`
