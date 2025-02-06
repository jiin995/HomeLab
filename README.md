# HomeLab

## History

I've had a homelab for several years, now, and the time has come to put into practice everything I've learned in the professional world so that it doesn't just remain a pile of things without any structure.

## Create user ansible on host

```Bash
```

## Configure

```Bash
mv 
ansible-vault create group_vars/public/vault.yml
```

## Apply

```Bash
ansible-playbook -i inventory.yml --ask-vault-pass site.yml
```
