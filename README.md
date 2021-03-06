# AuthAndResourceServer

  This repository consists two spring boot project.
## Authorisation server
  Authorisation server will be responsible to play following roles.
  1. Provide access token for the resource server.

  ```
  localhost:9999/oauth/token
  ```
  ![alt text](https://raw.githubusercontent.com/gyanicit/ScreenShots/master/token1.PNG)

  ![alt text](https://raw.githubusercontent.com/gyanicit/ScreenShots/master/token2.PNG)

  2. It will validate the token passed  to the resource server. Actually when you will make request to the resource server with particular Rest enpoint. Internally resource server will make a call to authorization Server to validate the token. (Check following configuration in application.yml in ResourceServer)
 
 ```
  security:
  oauth2:
    client:
      client-id: client1
      client-secret: secret1
    resource:
      token-info-uri: http://localhost:9999/oauth/check_token
  ```
## Resource Server
  Resource server is kind of target microservice which will be responsible to provide access of a resource exposed by using different Rest endpoints.

  ![alt text](https://raw.githubusercontent.com/gyanicit/ScreenShots/master/req1.PNG)

  ![alt text](https://raw.githubusercontent.com/gyanicit/ScreenShots/master/req2.PNG)


  ```
  localhost:8080/hello
  ```

   Whenever you require to access this resource always you need a access token. So that first you have to make a request to the Authorisation server with BasicAuth and you will get access token.



   ```
   localhost:9999/oauth/token
   ```
```
   {
    "access_token": "60855ad5-b5a2-4ba8-a91f-35151f9bc8f2",
    "token_type": "bearer",
    "refresh_token": "50d100fe-ec22-49f5-be91-ec6233e79b7f",
    "expires_in": 237,
    "scope": "read write truest"
    }
```

