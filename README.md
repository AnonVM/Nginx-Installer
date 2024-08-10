# NGINX Auto Install Script

Easily compile and install NGINX from source with custom features, modules, and patches.

## Supported Systems

- **Debian** 9 and later
- **Ubuntu** 16.04 and later

## Key Features

- Compile the latest mainline or stable NGINX from source.
- Integrate optional modules and patches.
- Use a [custom nginx.conf](https://github.com/AnonVM/Nginx-Installer/blob/master/conf/nginx.conf) for enhanced performance.
- Include a [systemd init script](https://github.com/AnonVM/Nginx-Installer/blob/master/conf/nginx.service) (not provided by default).
- Configure [logrotate](https://github.com/AnonVM/Nginx-Installer/blob/master/conf/nginx-logrotate) for efficient log management.
- Block APT-based NGINX installations to avoid conflicts.

### Optional Modules and Enhancements

- **LibreSSL or OpenSSL from Source:** Enable cutting-edge TLS features like HTTP/2, CHACHA20, and TLS 1.3.
- **Cloudflare Patches:** Add HTTP/3, TLS Dynamic Record Resizing, and HPACK encoding.
- **Performance Modules:** Integrate [ngx_pagespeed](https://github.com/pagespeed/ngx_pagespeed) for optimization and [ngx_brotli](https://github.com/google/ngx_brotli) for Brotli compression.
- **Security Enhancements:** Use [ModSecurity](https://github.com/SpiderLabs/ModSecurity) for WAF, [testcookie-nginx-module](https://github.com/kyprizel/testcookie-nginx-module) for bot protection, and [nginx-ultimate-bad-bot-blocker](https://github.com/mitchellkrogza/nginx-ultimate-bad-bot-blocker) for blocking malicious traffic.
- **Cache Modules:** Incorporate Redis-based caching with [redis2-nginx-module](https://github.com/openresty/redis2-nginx-module) and [ngx_http_redis](https://www.nginx.com/resources/wiki/modules/redis/).
- **Additional Modules:** Extend functionality with [lua-nginx-module](https://github.com/openresty/lua-nginx-module), [RTMP module](https://github.com/arut/nginx-rtmp-module) for streaming, and more.

## How to Use

Download and execute the script to:

- Install or update NGINX
- Uninstall with optional cleanup
- Self-update the script

```sh
wget https://raw.githubusercontent.com/AnonVM/Nginx-Installer/main/setup.sh
chmod +x setup.sh
./setup.sh
```

Check out [configuration examples](https://github.com/AnonVM/Nginx-Installer/tree/master/conf) for custom modules.

### Headless Mode

For automated installations, run the script in headless mode by setting `HEADLESS=y`.

```sh
HEADLESS=y ./setup.sh
```

Example commands:

- **Install NGINX with Brotli:**  
  ```sh
  HEADLESS=y NGINX_VER=MAINLINE BROTLI=y ./setup.sh
  ```
- **Install with GeoIP:**  
  ```sh
  HEADLESS=y GEOIP=y GEOIP2_ACCOUNT_ID=YOUR_ACCOUNT_ID_HERE GEOIP2_LICENSE_KEY=YOUR_LICENSE_KEY_HERE ./setup.sh
  ```
- **Uninstall with Cleanup:**  
  ```sh
  HEADLESS=y OPTION=2 RM_CONF=y RM_LOGS=y ./setup.sh
  ```
