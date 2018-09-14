##How to setup AD and set up Kerberos Authentication
1. create domain user for service (application server like tomcat for authentication) we use ```dai``` for this exmple
2. create DN. we use ```myserver.geniustree.local``` for example
3. create keytab file
```
ktpass /out dai.keytab /mapuser dai /princ HTTP/myserver.geniustree.local@GENIUSTREE.LOCAL  /pass computer_123  /ptype KRB5_NT_PRINCIPAL /crypto All /target GENIUSTREE.LOCAL -kvno 0
```
where:

```/mapuser dai```  is user that we create at 1.
```/princ HTTP/myserver.geniustree.local@GENIUSTREE.LOCAL``` is service principal that we will serve a http service.
this value will be use for authentication  handshaking

we not need to use ```setsp``` command because ```ktpass``` command will generate servicePrincipal automatically.

**see ```resources/application.yml``` for application server setting**
