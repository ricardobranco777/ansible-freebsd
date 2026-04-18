
Make sure that you have:

- `kern.coredump` sysctl set to 1
- `dumpdev="AUTO"` in /etc/rc.conf
- `sw,late` for options in swap
- `FreeBSD-kernel-generic-dbg-` package

On `db>` prompt run `dump` then `reset`
