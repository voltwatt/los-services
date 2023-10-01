- Add self-signed wildcard domain certificates in traefik volumes. Use mkcert in you home folder
- Add self-signed localhost certificates. Use mkcert in you home/certs folder

```bash
    mkcert localhost
    mkcert "*.online-store.com" "online-store.com"
```
- Add to etc/hosts:
127.0.0.1 kibana.online-store.com  
127.0.0.1 traefik.online-store.com  
127.0.0.1 rabbitmq.online-store.com  
