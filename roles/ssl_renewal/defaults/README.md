# Defaults for ssl_renewal role

This file documents the default variables provided by roles/ssl_renewal/defaults/main.yml.

Variables

- ssl_email (string)
  - Email address used when requesting certificates from Let's Encrypt.
  - Default: admin@example.com

- ssl_cert_dir (string)
  - Directory where certificates are stored on the renewal server.
  - Default: /etc/letsencrypt/live

- ssl_renewal_threshold (integer)
  - Number of days remaining before a certificate is considered for renewal.
  - Default: 30

- ssl_domains (list)
  - List of domain objects to manage. Each item should include:
    - name: primary domain (string)
    - sans: list of subject alternative names (list of strings)
    - webroot: webroot path used for certbot --webroot (string)
    - services: list of services to reload after renewal (list of strings)

Example

ssl_domains:
  - name: example.com
    sans:
      - www.example.com
      - api.example.com
    webroot: /var/www/html
    services:
      - nginx

Override

These defaults can be overridden in inventory/group_vars, host_vars, or extra-vars when running the playbook.