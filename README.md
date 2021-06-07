Keycloak Auth Server

How to run

On mac use
```shell
sudo ./standalone.sh -Djboss.socket.binding.port-offset=100 -Dkeycloak.frontendUrl=http://10.0.2.2:8090/auth
```

keycloak.frontendUrl configures keycloak to generate the login page for example with the ip address
of the reverse proxy and not with its own.

As of now to acess the console you have to start the server with the command

```shell
sudo ./standalone.sh -Djboss.socket.binding.port-offset=100
```

and the link below should do it
http://localhost:8180/auth/admin

How to add audiences

For each microservice available, a resource id has to be set to it
For each client(mobile, web) that needs to access this microservice, it has to contain
the correspondent audiences

https://github.com/keycloak/keycloak-documentation/blob/master/server_admin/topics/clients/oidc/audience.adoc
https://www.fatalerrors.org/a/resource-of-spring-security-oauth2_-id-configuration-and-verification.html
https://stackoverflow.com/questions/53550321/keycloak-gatekeeper-aud-claim-and-client-id-do-not-match
Configure audience in Keycloak
Add realm or configure existing
Add client my-app or use existing
Goto to the newly added "Client Scopes" menu [1]
Add Client scope 'good-service'
Within the settings of the 'good-service' goto Mappers tab
Create Protocol Mapper 'my-app-audience'
Name: my-app-audience
Choose Mapper type: Audience
Included Client Audience: my-app
Add to access token: on
Configure client my-app in the "Clients" menu
Client Scopes tab in my-app settings
Add available client scopes "good-service" to assigned default client scopes