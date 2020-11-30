nginx
=====

Install Nginx package

Role Variables
--------------

```yaml
nginx_cache_path: CACHE_PATH (default: /var/cache/nginx)
nginx_proxy_cache_enabled: ENABLE_PROXY_CACHE (default: false)
nginx_proxy_cache_path: PROXY_CACHE_PATH (default: "{{ nginx_cache_path }} levels=1:2 keys_zone=proxy_cache:10m inactive=1d max_size=10g;")
nginx_proxy_cache_key: PROXY_CACHE_KEY (default: "$scheme$proxy_host$uri$is_args$args;")
nginx_uwsgi_cache_enabled: ENABLE_UWSGI_CACHE (default: false)
nginx_uwsgi_cache_path: UWSGI_CACHE_PATH (default: "{{ nginx_cache_path }} levels=1:2 keys_zone=uwsgi_cache:10m inactive=1d max_size=10g;")
nginx_uwsgi_cache_key: UWSGI_CACHE_KEY (default: "$scheme$proxy_host$uri$is_args$args;")
```

Dependencies
------------

- pylabs.sysbase

Example Playbook
----------------

```yaml
- hosts: servers
  vars:
    nginx_cache_path: "/var/cache/nginx"
    nginx_uwsgi_cache_enabled: yes
    nginx_uwsgi_cache_path: "{{ nginx_cache_path }} levels=1:2 keys_zone=uwsgi_cache:10m inactive=1d max_size=10g;"
    nginx_uwsgi_cache_key: "$scheme$proxy_host$uri$is_args$args;"
  roles:
    - role: pylabs.nginx
```

License
-------

MIT

Author Information
------------------

William Wu
