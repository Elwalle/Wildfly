# Wildfly

Add Camel into Wildfly

Download Camel patch for Wildfly

WildFly Patch - wildfly-camel-patch : https://github.com/wildflyext/wildfly-camel/releases

Installing the Camel Subsystem
==============================
Simply unpack the provided patch into the a supported WildFly installation. For possible WildFly target versions, see the compatibility matrix below
The WildFly compatibility matrix

11.0.0.Final => 5.0, 5.1

10.1.0.Final => 4.3, 4.4, 4.5, 4.6, 4.7, 4.8, 4.9

10.0.0.Final => 4.0, 4.1, 4.2

9.0.2.Final => 3.2, 3.3

9.0.1.Final => 3.1

9.0.0.CR1 => 3.0

8.2.0.Final => 2.1, 2.2, 2.3

8.1.0.Final => 2.0


Standalone Server
In your WildFly home directory run …​

$ bin/standalone.sh -c standalone-camel.xml
...
10:50:02,833 INFO  [org.jboss.as.server] (ServerService Thread Pool -- 31) JBAS018559: Deployed "wildfly-camel.war" (runtime-name : "wildfly-camel.war")
10:50:02,834 INFO  [org.jboss.as.server] (ServerService Thread Pool -- 31) JBAS018559: Deployed "hawtio.war" (runtime-name : "hawtio.war")
10:50:02,848 INFO  [org.jboss.as] (Controller Boot Thread) JBAS015961: Http management interface listening on http://127.0.0.1:9990/management
10:50:02,849 INFO  [org.jboss.as] (Controller Boot Thread) JBAS015951: Admin console listening on http://127.0.0.1:9990
10:50:02,849 INFO  [org.jboss.as] (Controller Boot Thread) JBAS015874: WildFly 8.1.0.Final "Kenny" started in 10804ms

Enable Camel Subsystem
The patch does not modify existing configuration files. Instead it comes with a number of additional configurations files that end in -camel.xml.

If you should want to add the Camel subsystem to existing configurations you can run the following command.

$ bin/fuseconfig.sh --configs=camel --enable
Processing config for: camel
   Writing 'layers=fuse' to: .../wildfly-9.0.0.CR1/modules/layers.conf
   Enable camel configuration in: .../wildfly-9.0.0.CR1/standalone/configuration/standalone.xml
   Enable camel configuration in: .../wildfly-9.0.0.CR1/standalone/configuration/standalone-full.xml
There are currently three triggers that can be used to enable Camel for a deployment

a deployment that contains a *-camel-context.xml descriptor

a deployment that contains a type annotated with @CamelAware

a deployment that contains a type annotated with @ContextName
