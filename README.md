# php-5.6-alpine

## Presentation

The entrypoint run `apache2` daemon by default and expose port 80.

The default workdir is `/var/www/` and the default Apache DocumentRoot path is `/var/www/localhost/htdocs`.

## Environment variables


### Load PHP Extensions

The PHP Extensions are load on start. Just add environment variable `PHP_php5enmod` with list of your extensions

Example with docker-compose :

    ...
    environment:
        PHP_php5enmod: 'memcached mysqli opcache'


#### Extensions available
`bcmath gd gmp intl ldap mbstring memcached mongo mysql mysqli pcntl pdo_mysql redis soap zip blackfire ftp sockets xdebug opcache zlib` 

### Set your apache.conf

The apache configuration is dynamic.

Example with docker-compose :

    ...
    environment:
        HTTPD__DocumentRoot: '/var/www/public'
        HTTPD__DirectoryIndex: 'app.php'

### Load Apache modules

The apache modules are load on start. Just add environment variable `HTTPD_a2enmod` with list of your modules

Example with docker-compose :

    environment:
        HTTPD_a2enmod:  'rewrite status expires'

Modules available :

    access_compat actions alias allowmethods asis auth_basic auth_digest auth_form authn_anon authn_core authn_dbd authn_dbm authn_file authn_socache authnz_fcgi authnz_ldap authz_core authz_dbd authz_dbm authz_groupfile authz_host authz_owner authz_user autoindex buffer cache cache_disk cache_socache cgi cgid charset_lite data dav dav_fs dav_lock dbd deflate dialup dir dump_io echo env expires ext_filter file_cache filter headers heartbeat heartmonitor ident include info lbmethod_bybusyness lbmethod_byrequests lbmethod_bytraffic lbmethod_heartbeat ldap log_debug log_forensic lua macro mime mime_magic mpm_event mpm_prefork mpm_worker negotiation php5 proxy proxy_ajp proxy_balancer proxy_connect proxy_express proxy_fcgi proxy_fdpass proxy_ftp proxy_html proxy_http proxy_scgi proxy_wstunnel ratelimit reflector remoteip reqtimeout request rewrite sed session session_cookie session_crypto session_dbd setenvif slotmem_plain slotmem_shm socache_dbm socache_memcache socache_shmcb speling ssl status substitute suexec unique_id userdir usertrack vhost_alias xml2enc