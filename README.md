
Role Name
=========
ashish_backbase


Pre-Requisite/Requirements
--------------------------

The code will run on CENTOS/RHEL OS version 7.

Please make sure that the git and ansible version 2.5 or above should be installed on the system. Rest all the required packages for the project will be installed by the role itself.
          
If the testing environment for this code is AWS/GCP/AZURE or any other public/private cloud. Please make sure that the inbound traffic is allowed to the server for port numbers 8090,8161 and 8080 in a security group. Here 8090 is for tomcat, 8161 is for Activemq and 8080 is for nginx. 
 
Check Ansible by below command:

ansible --version

This code was tested and written in the version 2.7.0, But it will work with other versions(above 2.5) as well.

Run the role with the user having sudo privileges or direct from root.


SCOPE
-----

This code contains single role which include seperate task files for the below mention applications that will be executing sequentially and will install/configure the below applications. Also Tomcat and ActiveMQ is configured for systemctl enabled on boot.

1. Oracle JDK v8 – Install Oracle jdk v8 and will Configure $JAVA_HOME variable for all users
2. Tomcat v8 (8.5.9) – Install tomcat v8 from a given tar.gz link and Deploy sample.war to tomcat.
3. Activemq (5.14.0) – Install Activemq v5 from a given tar.gz link.
4. Nginx - Install from Yum repository and include a simple &quot;hello world&quot; in the index.html of nginx.


EXECUTION
---------

- Clone the repository on local Centos/RHEL 7 server with the following command : "git clone <<<<<<<<URL>>>>>>>>>"

Make sure git is installed on the system before running the above command, if not installed then please install the git first with yum command.

- Jump to directory project
 
cd project

- Run below command 

ansible-playbook main.yml


VERIFICATION
------------

1. To verify java please execute java -version command
  
a) java -version

Java version "1.8.0_191" 
Java(TM) SE Runtime Environment (build 1.8.0_191-b12)
Java HotSpot(TM) 64-Bit Server VM (build 25.191-b12, mixed mode)         

b) Run the below command to check the java path, keeping in mind that the requirement for this variable is set for all the users in the system. The role is setting the Java Path for all the users available on the system and will be setting the java path automatically for the new users also.

echo $JAVA_HOME
/opt/jdk1.8.0_191


2. To verify the application tomcat please use the below steps:

a)      Execute the “systemctl status tomcat” command, it will show the tomcat service running and enabled.

b)      Type http://[ip-address]:8090 in browser where ip-address is ip address of your system, you will get the below message as per the sample.war file.

  Sample "Hello, World" Application



3. To verify the application Activemq please use the below steps:

a) 	Execute the “systemctl status activemq” command, it will show the activemq service running and enabled.

a)      Type http://[ip-address]:8161/admin in browser with username= admin, password= admin



4. To verify Nginx please use the below steps:

a) please type http://[ip-address]:8080 in the browser, the message will be displayed as "hello world".

b) Execute the “systemctl status nginx” command, it will show the nginx service running and enabled.

 
Dependencies
------------
ansible version -> 2.5 or above
git rpm package

Author Information
------------------
Ashish Arora, connectashisharora@gmail.com

