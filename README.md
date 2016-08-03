# Spring OAuth2 JWT example for microservices

This example shows how to use spring oauth2 to secure resource servers, for example in spring cloud microservices.


## How to Setup?
To create the keystore and public key, the auth server will be using the keystore and the resource server will be using the public key, which will load all configuraiton information into memory

keytool -genkeypair -alias jwt -keyalg RSA -dname "CN=jwt, L=Campbell, S=Campbell, C=US" -keypass password1 -keystore jwt.jks -storepass password2
keytool -list -rfc --keystore jwt.jks | openssl x509 -inform pem -pubkey

Just check and update all build.gradle files to reflect the related gradle version and springboot versions

``` 
$ gradle wrapper
```

and start both spring boot application using 

```
$ gradlew bootRun


To verify:

curl "web_app:@localhost:9999/oauth/token" -d "grant_type=password&username=reader&password=reader"

will return the token


 
