# Ansible Vault

## Ansible Vault Secrets using a plain text password
- Creating Ansible Vault Secrets
    - `ansible-vault create /path/to/secret.yml`
- View the ansible secret
    - `ansible-vault view /path/to/secret.yml`
- Editing the ansible secret
    - `ansible-vault edit /path/to/secret.yml`
- Updating the vault secret key for the ansible secret
    - `ansible-vault rekey /path/to/secret.yml`
- To access the ansible vault secret inside the playbook we can use the below command
    - `ansible-vault playbook.yml -e "@group-vars/my-vault.yml" --ask-vault-pass`

## Ansible Vault using base64 password file
- Using a base64 password key file to create ansible vault secret
    - `openssl rand -base64 2048 >> pass-file/ansible-vault.pass`
    - `ansible-vault create group-vars/my-vault-base64.yml --vault-password-file=pass-file/ansible-vault.pass`
    - We can perform all the operations on this ansible vault file using the `view` `edit` and `rekey` commands by passing the password file using `--vault-password-file` flag

- Accessing the vault secrets inside a playbook using base64 password file
    - `ansible-playbook playbook.yml -e "@group-vars/my-vault-base64.yml" --vault-password-file=pass-file/ansible-vault.pass`
- exporing the ansible vault file environment variable to automatically pick the vault file.
    - `export ANSIBLE_VAULT_FILE=pass-file/ansible-vault.pass`
    - `ansible-playbook playbook.yml -e "@group-vars/my-vault-base64.yml"`
