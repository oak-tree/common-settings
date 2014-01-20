http://tomcat.apache.org/tomcat-7.0-doc/cluster-howto.html


To run session replication in your Tomcat 7.0 container, the following steps should be completed:

All your session attributes must implement java.io.Serializable
Uncomment the Cluster element in server.xml
If you have defined custom cluster valves, make sure you have the ReplicationValve defined as well under the Cluster element in server.xml
If your Tomcat instances are running on the same machine, make sure the tcpListenPort attribute is unique for each instance, in most cases Tomcat is smart enough to resolve this on it's own by autodetecting available ports in the range 4000-4100
Make sure your web.xml has the <distributable/> element
If you are using mod_jk, make sure that jvmRoute attribute is set at your Engine <Engine name="Catalina" jvmRoute="node01" > and that the jvmRoute attribute value matches your worker name in workers.properties
Make sure that all nodes have the same time and sync with NTP service!
Make sure that your loadbalancer is configured for sticky session mode.