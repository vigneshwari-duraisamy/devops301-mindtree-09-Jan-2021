# Installing & Configuring Tomcat Server

## Let be super user: root
```
sudo su - 
```

## Download Tomcat Binary 
```
wget https://archive.apache.org/dist/tomcat/tomcat-8/v8.5.56/bin/apache-tomcat-8.5.56.zip
```

## Extract Tomcat
```
apt-get install unzip -y
unzip apache-tomcat-8.5.56.zip
cp -rf apache-tomcat-8.5.56 /opt/tomcat
```

## Configure the Tomcat for User Auth. ( Please copy tomcat-user & context file into their respective locations ) 
```
edit   /opt/tomcat/conf/tomcat-users.xml
edit  /opt/tomcat/webapps/manager/META-INF/context.xml
```

## Excutable Permission
```
cd /opt/tomcat/
chmod +x bin/catalina.sh 
./bin/catalina.sh start
```

## To check status of Tomcat 
```
ps -ef | grep -i tomcat
netstat -tulnp | grep -i 8080
```




# Now Setup an Tomcat intergation  with Jenkins 

1. Install "Deploy to Container Plugin" 
2. Go to Petclinic-Free-Style-Job -> Configure -> PostBuildAction -> Deploy war/ear to a Container.
   WAR File Path : 02-Jenkins/petclinic-code/target/*.war
   Context Path  : petclinic
   Containers : Tomcat 8.x Remote
   
   Note : After Perfrom Step 3 ( Adding credentions for deployer, please select the same here ) 

3. Add the credentails:
   Click Add 
     Username : deployer
     Password : deployer
     ID       : 03
     Description: Tomcat 8 - Deployer
   -> Submit 

-> Save Job -> Trigger Build Now. 













