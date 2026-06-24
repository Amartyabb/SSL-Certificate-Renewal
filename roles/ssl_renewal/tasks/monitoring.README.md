# Certificate Monitoring Task (roles/ssl_renewal/tasks/monitoring.yml)

What it deploys
- A script at /usr/local/bin/check-ssl-certs.sh that:
  - Iterates certificate directories under {{ ssl_cert_dir }}
  - Uses openssl to extract certificate end dates
  - Computes days left and prints OK/WARNING/CRITICAL messages
  - Exits with 0/1/2 depending on highest-severity finding

- A daily cron job that runs the script and logs via logger.

Configuration
- WARN_DAYS is set inside the script (default 14). You can expose this as a variable if you want it configurable.
- Ensure the control node has openssl and a compatible date command.

Operational notes
- Exit codes: 0 OK, 1 WARNING, 2 CRITICAL — useful for monitoring integrations.
- Consider redirecting output to a file or integrating with system monitoring/alerting.
- Secure the script and its invocation (root-only cron, proper permissions).
