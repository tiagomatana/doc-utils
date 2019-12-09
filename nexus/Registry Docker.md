# CONFIGURAÇAO DE ACESSO

User: docker<br>
Pass: docker


**/etc/default/docker**

add value in DOCKER_OPTS to insecure registry:

```bash
DOCKER_OPTS="$DOCKER_OPTS -insecure-registry=<docker-repo>:<port>"
```
**/etc/docker/daemon.json**

add host in insecure-registries:

```bash
{
	"insecure-registries" : [ "<docker-repo>:<port>"]
}
```

**~/.docker/config.json**

add manual auth to registry
```bash
echo -n 'docker:docker' | base64
```
Output: ZG9ja2VyOmRvY2tlcg==

```bash
{
	"auths": {
		"<docker-repo>:<port>": {
			"auth": "ZG9ja2VyOmRvY2tlcg=="
		},
		"https://index.docker.io/v1/": {
			"auth": "asdfasdfag"
		}
	},
	"HttpHeaders": {
		"User-Agent": "Docker-Client/18.09.7 (linux)"
	}
}
```

Obs.: execute command post action -> **sudo service docker restart**