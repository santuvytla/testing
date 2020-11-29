# Building  and running the application

In order to build the application us the following command:

```
    ./gradlew bootJar
```
This will produce a jar file in the `build/libs` folder. 

To start the application use the following command:

```
 java -jar demo-0.0.1-SNAPSHOT.jar
```

The `application.properties` file must be located in the folder from which the jar started. 
If it is not provided the one inside the jar will be used.

By default the application will run on the port 8080. 
The following request should be used to check the application status:

```
Httpie: http :8080/actuator/health/
curl:   curl localhost:8080/actuator/health/
```

if the application configured correctly you should see similar output:

```
$ http  :8080/actuator/health
HTTP/1.1 200 
Connection: keep-alive
Content-Type: application/vnd.spring-boot.actuator.v3+json
Date: Wed, 07 Oct 2020 18:00:58 GMT
Keep-Alive: timeout=60
Transfer-Encoding: chunked

{
    "components": {
        "db": {
            "details": {
                "database": "MySQL",
                "validationQuery": "isValid()"
            },
            "status": "UP"
        },
        "diskSpace": {
            "details": {
                "exists": true,
                "free": 5822443520,
                "threshold": 10485760,
                "total": 5824397312
            },
            "status": "UP"
        },
        "ping": {
            "status": "UP"
        }
    },
    "status": "UP"
}

```