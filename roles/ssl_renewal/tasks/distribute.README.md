# Distributing Certificates to Multiple Servers (roles/ssl_renewal/tasks/distribute.yml)

Purpose
- Fetch renewed certificates from the renewal server to the control node.
- Create per-domain certificate directories on target load balancers.
- Copy fullchain.pem and privkey.pem to /etc/ssl/<domain>/ on load balancers.
- Notify nginx to reload after deployment.

Required variables
- ssl_renewal_server — host that holds the renewed certificates (used as delegate_to).
- ssl_domains — list of domains (from defaults).
- ssl_cert_dir — path to cert files on the renewal server.

Security and operational notes
- Fetched private keys are stored temporarily under /tmp/certs/<domain>/ on the control node — ensure they are cleaned up and access is restricted.
- Use secure control-node permissions and consider using an ephemeral, restricted account for fetch/copy actions.
- Ensure run_once + delegate_to behaviors are acceptable for your inventory topology.
- Verify target unit names (e.g., nginx) and whether reload vs restart is required.
