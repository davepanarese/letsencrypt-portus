
# Letsencrypt Portus Docker Registry

Deploy Portus docker registry with auto-generated ssl certificate with letsencrypt.  
Using the idea of thpham/portus-registry-tls-compose.


# How to deploy

- Edit .env variables
- NOTE: PORTUS_FQDN and REGISTRY_FQDN must be reachable domain from internet to work
- Deploy

```
docker-compose up -d
```


# Configure

After the deploy access to your PORTUS_FQDN address:
- Set an Administrator user
- Set _Name_ with `registry.example.com`
- Set _Hostname_ with `registry:5000`
- Go to advanced option
- Set _External Registry Name_ with `registry.example.com`


# LDAP Integration (Optional)
The system can be authenticated with your LDAP server (local authentication will be disabled)
Adding this parameters into docker-compose.yml

```
environment:
      # ldap
      PORTUS_LDAP_ENABLED: 'true'
      PORTUS_LDAP_HOSTNAME: '<ldap server address or ip>'
      PORTUS_LDAP_PORT: '389'
      PORTUS_LDAP_BASE: 'dc=department,dc=example,dc=com'
      PORTUS_LDAP_AUTHENTICATON_ENABLED: 'true'
      PORTUS_LDAP_AUTHENTICATON_BIND_DN: 'cn=<ldap user query>,ou=People,dc=department,dc=example,dc=com'
      PORTUS_LDAP_AUTHENTICATON_PASSWORD: '<ldap cn user password>'
```
