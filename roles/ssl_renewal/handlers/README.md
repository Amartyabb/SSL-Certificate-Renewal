# Handlers for ssl_renewal (roles/ssl_renewal/handlers/main.yml)

Handlers provided
- reload affected services
  - Loops over all services listed in ssl_domains[*].services
  - Calls systemd with state: reloaded for each service

- reload nginx
  - Calls systemd to reload nginx specifically

Recommendations
- Confirm the names listed in ssl_domains.services are valid systemd unit names on target hosts.
- Some services may require restart instead of reload — consider making handler behavior configurable.
- If you add other services, ensure they are included in ssl_domains.services so the first handler picks them up.
