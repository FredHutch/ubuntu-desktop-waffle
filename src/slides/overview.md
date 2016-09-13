
1. Select Hardware
2. Insert USB Installer (a bootable iso)
3. Boot and monitor installation progress
4. When complete, perform remaining manual steps.

---

# Manual Steps

## Join Workstation to Domain 

```
rm /etc/krb5.keytab

kinit <windows login>

msktutil --verbose --dont-expire-password --no-pac \
  --computer-name `hostname -s` --server dc \
  -b "ou=Workstations,ou=Computers,ou=SciComp" \
  -k /etc/krb5.keytab -h `hostname -f` \
  -s host/`hostname -f` --upn host/`hostname \
  -f` --description "Kerberos Account by msktutil"

msktjoin
```
