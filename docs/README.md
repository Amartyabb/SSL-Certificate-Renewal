# Docs: running.md

This document contains quick run instructions for the renew-ssl playbook.

Contents
- How to run: ansible-playbook -i inventory/hosts.ini renew-ssl.yml
- Suggested crontab: 0 4 * * 1 ansible-playbook -i /path/to/inventory renew-ssl.yml

Recommendations
- Use absolute paths in crontab entries and redirect output to a logfile.
- Ensure the control node environment (PATH, ansible.cfg) is consistent when cron runs the playbook.
