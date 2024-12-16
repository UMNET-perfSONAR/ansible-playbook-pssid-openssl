# ansible-playbook-pssid-openssl
manage and distribute openssl certs for probe / archiver communication

# Validate from client to server
```bash
openssl s_client -connect <hostname>:9400 -CAfile ./ca.crt
```

# Run playbook
Two-factor authentication is disabled for Ansible on the target host. Add the following line to /etc/group.
```bash
not2fa:x:650:<username>
```

Run playbook on pssid-dev server (GUI server) with root. 
``` bash
ansible-playbook \
    --inventory inventory/hosts.ini \
    --become \
    --user <username> \
    --become-method sudo \
    --become-user root \
    --ask-become-pass \
    --ask-pass \
    playbook.yml
'''