- Add self-signed wildcard domain certificates in traefik volumes. Use mkcert in you home/certs folder
- Add self-signed localhost certificates. Use mkcert in you home/certs folder

```bash
    mkcert localhost
    mkcert "*.online-store.com" "online-store.com"
```
- Add to etc/hosts:  
  127.0.0.1 online-store.com  
  127.0.0.1 kibana.online-store.com  
  127.0.0.1 traefik.online-store.com  
  127.0.0.1 rabbitmq.online-store.com  
  127.0.0.1 sonarqube.online-store.com

```bash
docker run -it --rm \
  --name maven-build \
  --network online-store-network \
  -v "$(pwd)":/usr/src/mymaven \
  -v "$HOME/.m2":/root/.m2 \
  -w /usr/src/mymaven \
  maven:3.8.4-openjdk-17 \
  mvn clean verify sonar:sonar \
  -Dsonar.projectKey=online-store \
  -Dsonar.projectName='online-store' \
  -Dsonar.host.url=https://sonarqube.online-store.com \
  -Dsonar.token=EDITME
```
