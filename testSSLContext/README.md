Reproducer for 
* https://bugzilla.redhat.com/show_bug.cgi?id=1455029
* https://issues.jboss.org/browse/JBEAP-8267

Reproducer is based on https://docs.oracle.com/javase/8/docs/technotes/guides/security/jsse/JSSERefGuide.html#SecureConnSample .
Necessary changes to origin source is marked with "Adjust" in comment

1. Set IBM java on PATH
2. cd ${project/bin/dir}
3. keytool -genkeypair   -keystore testkeys   -alias test   -keyalg RSA   -keysize 3072   -validity 36500   -storepass passphrase   -keypass passphrase -dname "CN=test, OU=QE, O=Redhat, L=Brno, C=CZ"
4. java ClassFileServer 8443 /tmp TLS

5. From another terminal run
openssl s_client -connect localhost:8443 -cipher AES128-GCM-SHA256:AES128-SHA256
