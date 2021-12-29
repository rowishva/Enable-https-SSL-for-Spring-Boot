# Enable https(SSL) for Spring Boot

In this example, I will explain how to enable HTTPS(SSL) in Spring Boot. The self-signed certificate is used in this example, and configure a simple REST Spring Boot application.


###### Technology Stack
```
+ Java 11
+ Spring Boot 2.5.8
+ Spring Boot Rest API
+ SSL
```

#### Generate Self-signed Certificate
The first step is to generate will use the JDK’s keytool to generate a self-sign certificate in PKCS12 format using JDK Keytool. Below command will create a PKCS12 cert after that  put this file into the resources folder under SpringBoot project
```
keytool -genkeypair -keyalg RSA -keysize 2048 -storetype PKCS12 -keystore springboothttps.p12 -validity 365
```
![image](https://user-images.githubusercontent.com/67745525/147640548-75270a22-b86a-4b13-941d-5926ce8673ad.png)

#### Configure Properties
```
server.port=8443
server.ssl.key-store=classpath:springboothttps.p12
server.ssl.key-store-password=password
server.ssl.keyStoreType=PKCS12
```
