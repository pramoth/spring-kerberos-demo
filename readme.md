## How to setup AD and setup Kerberos Authentication
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


1. [https://www.ibm.com/support/knowledgecenter/en/SSAW57_8.5.5/com.ibm.websphere.nd.multiplatform.doc/ae/csec_SPNEGO_explain.html]()
2. https://docs.oracle.com/javase/6/docs/technotes/guides/security/jgss/lab/part5.html
3. https://docs.oracle.com/javase/1.5.0/docs/api/javax/security/sasl/SaslClient.html
4. https://docs.oracle.com/cd/E23824_01/html/819-2145/sasl.intro.20.html
5. https://docs.oracle.com/javase/6/docs/technotes/guides/security/
