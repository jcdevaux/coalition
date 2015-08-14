# Introduction #

This feature works only under a linux system with the "su" command available.

server.py can use LDAP to authenticate the users in order to control access to the monitor and run the jobs with the users's privileges.

# Details #

To use a LDAP server, you have to run the server with the two following options :

```
--ldaphost=LDAPHOST
--ldaptemplate=LDAPTEMPALTE
```

LDAPHOST is the host name of the LDAP server.
LDAPTEMPALTE is a template like "uid=%login,ou=people,dc=exemple,dc=com" used to test the password. "%login" will be replaced by the user login.

The worker have to be run as root because it will now run the jobs with the user rights.

If the server is started with the --ldapserver option, the user will be asked for their login and password. The jobs will be added with the user's login. The workers will execute
the jobs with the user's privileges.