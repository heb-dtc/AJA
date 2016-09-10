# Fix slow startup of Java application

Java application seems to launch more slowly if network is slow, turns out that configuring properly
the hostname of the workstation fixes it. 

1. open `/etc/hosts`
2. add the following entry  
`12.0.0.1 <machinehostname>.localdomain <machinehostname>`
