To install development tools:

`sudo pkg install -g 'GhostBSD*-dev'`

Add these to /etc/rc.conf:

```
firewall_myservices="22/tcp"
firewall_allowservices="any"
```

Disable in /etc/rc.conf:

- cups
- webcamd
