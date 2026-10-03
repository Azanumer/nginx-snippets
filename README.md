# Nginx Snippets

Production-ready Nginx configuration snippets for WordPress & general hosting: speed, caching, rate limiting, and SSL best practice. Each file in `snippets/` is self-contained with comments showing where it goes.

## Snippets

| Snippet | What it does |
|---|---|
| `snippets/wordpress-php-fpm.conf` | WordPress site block on PHP-FPM: permalinks, blocks hidden/sensitive files, no PHP in uploads |
| `snippets/fastcgi-cache-wordpress.conf` | Full-page FastCGI cache for WordPress (bypasses cache for logged-in users, POSTs, cart/checkout) |
| `snippets/rate-limiting.conf` | Rate limits wp-login/xmlrpc to 5 req/min per IP, general cap 30 req/s — blunts brute force & scraping |
| `snippets/ssl-best-practice.conf` | TLS 1.2+ only, strong ciphers, OCSP stapling, HSTS |
| `snippets/static-caching-gzip.conf` | GZIP compression + 1-year immutable caching for static assets |

## Usage

```bash
# 1. Always test before reloading:
sudo nginx -t

# 2. Reload when it passes:
sudo systemctl reload nginx
```

Enable HSTS in `ssl-best-practice.conf` only once HTTPS works everywhere on the domain.

MIT licensed.
