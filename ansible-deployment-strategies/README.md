# ANSIBLE Deployment Strategies

- Single Server Deployment
  - `ansible-playbook -i ansible-deployment-strategies/inventory/hosts ansible-deployment-strategies/playbook.yml`
- Multi Server with Blue / Green Deployment
  - `ansible-playbook -i ansible-deployment-strategies/inventory/hosts ansible-deployment-strategies/playbook.yml --limit green`
  - `ansible-playbook -i ansible-deployment-strategies/inventory/hosts ansible-deployment-strategies/playbook.yml --limit blue`
