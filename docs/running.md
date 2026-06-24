# Check and renew certificates
ansible-playbook -i inventory/hosts.ini renew-ssl.yml

# Schedule weekly renewal check from the control node
# Add to crontab: 0 4 * * 1 ansible-playbook -i /path/to/inventory renew-ssl.yml
