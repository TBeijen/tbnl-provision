Cheat Sheet
===========

Ansible
-------

```sh
# run playbook, from appropriate 'deploy' folder
ansible-playbook -i production.inventory site.yml
```

Server
------

```sh
systemctl restart caddy

journalctl -u caddy |tail -n100
journalctl -u caddy -f
```

Online resources
----------------


Cloudflare

* Naked domain redirect: https://community.cloudflare.com/t/redirect-naked-https-domain-com-to-https-www-domain-com/35273/6