Keycloak Auth Server

How to run

On mac use
```shell
sudo ./standalone.sh -Djboss.socket.binding.port-offset=100 -Dkeycloak.frontendUrl=http://10.0.2.2:8090/auth
```

keycloak.frontendUrl configures keycloak to generate the login page for example with the ip address
of the reverse proxy and not with its own.
