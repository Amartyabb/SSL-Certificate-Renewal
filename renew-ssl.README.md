# Playbook: renew-ssl.yml

Purpose
- Run the ssl_renewal role against hosts in the web_servers group to check and renew certificates.

Usage
- ansible-playbook -i inventory/hosts.ini renew-ssl.yml

Notes
- Ensure inventory defines web_servers and any control variables (ssl_renewal_server, etc.).
- Dry-run before production: add --check to validate expected changes.
- Consider running the playbook from a control node with appropriate SSH access and minimal privileges.
