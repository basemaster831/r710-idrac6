## How to access IDRAC6(-Enterprise) (on the Dell PowerEdge R710) on the Linux OS in 2021.
1. Make sure you've set up ip address, user and password for the IDRAC6 before attempting to continue.                                                      
  _(You can configure IDRAC6 in the R710 boot menus.)_
1. Install JRE (I used `openjdk-11-jre-headless` from apt on debian.).
1. Remove `RC4` from `java.tls.disabledAlgorithms` in `/etc/java-*-openjdk/security/java.security`.
1. Run the following:
```bash
#If you don't have curl, you'll probably have wget.
curl -O 'http://CHANGEME/software/avctKVM.jar';
java -cp avctKVM.jar com.avocent.idrac.kvm.Main ip=CHANGEME kmport=5900 vport=5900 
user=CHANGEME passwd=CHANGEME apcp=1 version=2
```
**Warning: This leaves your username and password in the** `history`.

**Don't forget to revert changes to `java.security` file when you're done.**
