# msgpack-rpc-jersey-blank

Maven archetype to create a modern Java RPC stack using Jetty + Jersey + Jackson + MessagePack on Spring Boot


[![Build Status](https://travis-ci.org/making/msgpack-rpc-jersey-blank.svg)](https://travis-ci.org/making/msgpack-rpc-jersey-blank)

## How to use

with Bash

``` bash
mvn archetype:generate\
 -DarchetypeGroupId=am.ik.archetype\
 -DarchetypeArtifactId=msgpack-rpc-jersey-blank-archetype\
 -DarchetypeVersion=1.0.2
```

with CommandPrompt (Windows)

``` bash
mvn archetype:generate^
 -DarchetypeGroupId=am.ik.archetype^
 -DarchetypeArtifactId=msgpack-rpc-jersey-blank-archetype^
 -DarchetypeVersion=1.0.2
```

### Example

#### Create a project

```
$ mvn archetype:generate -B
  -DarchetypeGroupId=am.ik.archetype
  -DarchetypeArtifactId=msgpack-rpc-jersey-blank-archetype
  -DarchetypeVersion=1.0.2
  -DgroupId=com.example
  -DartifactId=hello-modern-rpc
  -Dversion=1.0.0-SNAPSHOT
$ cd hello-modern-rpc
```

#### Run

``` bash
$ mvn spring-boot:run
```

``` bash
$ curl -v -H "Accept: application/x-msgpack" "localhost:8080/calc?left=100&right=300"
> GET /calc?left=100&right=300 HTTP/1.1
> User-Agent: curl/7.30.0
> Host: localhost:8080
> Accept: application/x-msgpack
>
< HTTP/1.1 200 OK
< Server: Apache-Coyote/1.1
< Content-Type: application/x-msgpack;charset=UTF-8
< Content-Length: 26
< Date: Fri, 16 Jan 2015 16:32:05 GMT
<
��leftd�right�,�answer��
```

Content negotiation is supported.

``` bash
$ curl -v -H "Accept: application/json" "localhost:8080/calc?left=100&right=300"
> GET /calc?left=100&right=300 HTTP/1.1
> User-Agent: curl/7.30.0
> Host: localhost:8080
> Accept: application/json
>
< HTTP/1.1 200 OK
< Server: Apache-Coyote/1.1
< Content-Type: application/json;charset=UTF-8
< Content-Length: 37
< Date: Fri, 16 Jan 2015 16:32:52 GMT
<
{"left":100,"right":300,"answer":400}
```

#### Test

``` bash
$ mvn test
```

#### Build executable jar

``` bash
$ mvn clean package
$ java -jar target/*.jar
```

## License

Licensed under the Apache License, Version 2.0.
