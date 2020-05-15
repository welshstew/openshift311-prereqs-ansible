Instal prereqs on the host.

```
subscription-manager register --username a --password b
POOL_ID=$(sudo subscription-manager list --available | sed -n '/Employee SKU/,/System Type/p' | grep "Pool ID" | tail -1 | cut -d':' -f2 | xargs)
subscription-manager attach --pool=$POOL_ID
subscription-manager repos --disable="*"
yum-config-manager --disable \*
subscription-manager repos     --enable="rhel-7-server-rpms"     --enable="rhel-7-server-extras-rpms"     --enable="rhel-7-server-ose-3.11-rpms"     --enable="rhel-7-server-ansible-2.9-rpms"
```

Vars:

```
redhat_username:
redhat_password:
redhat_poolid:
```

Run with:

```
--extra-vars "redhat_username=1.23.45 redhat_password=foo redhat_poolid=123"
```