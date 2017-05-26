Reproducer based on https://docs.oracle.com/javase/8/docs/technotes/guides/security/jsse/JSSERefGuide.html#SecureConnSample .
Necessary changes to origin source is marked with "Adjust" in comment

0. cd ${project/bin/dir}
1. keytool -genkeypair   -keystore testkeys   -alias test   -keyalg RSA   -keysize 3072   -validity 36500   -storepass passphrase   -keypass passphrase -dname "CN=test, OU=QE, O=Redhat, L=Brno, C=CZ"
2. java ClassFileServer 8443 /tmp TLS

3. From another terminal run
openssl s_client -connect localhost:8443 -cipher AES128-GCM-SHA256:AES128-SHA256
