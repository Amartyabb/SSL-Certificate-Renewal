# Main Tasks (roles/ssl_renewal/tasks/main.yml)

Purpose
- Install certbot and required plugins.
- Check installed certificate expiration dates.
- Build a list of certificates needing renewal.
- Request/renew certificates using certbot --webroot for each domain and its SANs.
- Verify renewed certificates and show verification output.
- Install a cron job to run certbot renew regularly, with a deploy-hook to reload affected services.

Important variables
- ssl_domains (from defaults) — domains, SANs, webroot, services.
- ssl_cert_dir — path where certs live (used for checking/verifying).
- ssl_email — contact email for certbot.
- ssl_renewal_threshold — days-before-expiry to trigger renewal.

Notes and recommendations
- Run a dry-run first: ansible-playbook renew-ssl.yml -i <inventory> --check.
- Ensure ansible_date_time fact is available on hosts for date calculations.
- Confirm service names in ssl_domains.services match systemd unit names.
- Consider making the cron schedule and certbot flags configurable.
