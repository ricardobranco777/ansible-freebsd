
## Cleanup of binaries / libraries not needed in custom kernel configuration

```
cd /usr/src
make check-old
make -DBATCH_DELETE_OLD_FILES delete-old delete-old-libs
```
