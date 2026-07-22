NOTES
=====

The package **systemd-container** contains:

* systemd-nspawn
* systemd-machined + machinectl
* systemd-importd
* systemd-portabled + portablectl

These are the corresponding manpages:
- https://manpages.debian.org/trixie/systemd-container/index.html

USAGE
=====

```yml
systemd_networkd_systemd_enable:
- systemd-machined.service
```