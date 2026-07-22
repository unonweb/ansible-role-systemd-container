ABOUT
=====

Radically simple Ansible role to create systemd-nspawn config files and overrides for the corresponding service unit.


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
# systemd-containers
- ansible.builtin.import_role:
	name: systemd-containers
	vars:
	systemd_container_nspawn_containers:
	# nextcloud-db
	- name: nextcloud-db
		config:
		Exec:
			Boot: true
			PrivateUsers: pick
			Hostname: nextcloud-db
			Timezone: copy
			NoNewPrivileges: true
		Files:
			PrivateUsersOwnership: auto
			Bind:
			- /srv/data/nextcloud-db/cloud:/var/www/nextcloud/data
			- /srv/data/nextcloud-db/mysql:/var/lib/mysql
		Network:
			Private: true
			VirtualEthernet: true
			Bridge: br0
		service_overrides:
		Unit:
			Description: Nextcloud systemd-nspawn container
```