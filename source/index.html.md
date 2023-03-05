---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell
  - java
  - kotlin
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Introduction

URL : https://goose-auth.synology.me

[https://github.com/GHGHGHKO/goose-auth-api-server](https://github.com/GHGHGHKO/goose-auth-api-server)  
Repository의 API 문서입니다.  

Bitwarden의 API 서버를 clone 했습니다.   
name, userName, userPassword, folder, notes, uri을 입력하여  
로그인 정보를 저장해두고 언제든지 가져올 수 있습니다.  

[slate Pull request](https://github.com/GHGHGHKO/slate/pulls)  
[goose-auth Pull request](https://github.com/GHGHGHKO/goose-auth-api-server/pulls)  
대환영입니다.

방문해주셔서 감사합니다. :)


# Common response body

> Default response body

```json
{
    "success": true,
    "code": 0,
    "message": "성공하였습니다."
}
```

> Single response body

```json
{
    "success": true,
    "code": 0,
    "message": "성공하였습니다.",
    "data": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiIzIiwicm9sZXMiOlsiUk9MRV9VU0VSIl0sImlhdCI6MTY3NzY1ODkwOSwiZXhwIjoxNjc3NjYyNTA5fQ.lLWl2bA_pLrgJw0pPXebv9P85lQTGLwNSoz4N8KguCs"
}
```


> List response body

```json
{
    "success": true,
    "code": 0,
    "message": "성공하였습니다.",
    "list": [
        {
            "itemIdentity": 12,
            "name": "swagger 테스트test",
            "userName": "gudrb963@gmail.com"
        },
        {
            "itemIdentity": 21,
            "name": "duck",
            "userName": "duck@goose.com"
        }
    ]
}
```

> Fail response body

```json
{
    "success": false,
    "code": -1005,
    "message": "You are an existing member."
}
```

### Default response body
`success` : 응답 성공여부 true/false  
`code` : 응답 성공 번호 >= 0 success, < 0 fail  
`message` : 응답 메시지

### Single response body
`data` : single response 데이터

### List response body
`list` : list response 데이터

# i18n

> i18n 적용 방법

```shell
curl "api_endpoint_here" \
-H "Accept-Language: en"
```

```java
import java.net.HttpURLConnection;
import java.net.URL;

public class HttpExample {
  public static void main(String[] args) {
    URL url = new URL("http://example.com/api_endpoint_here");
    HttpURLConnection conn = (HttpURLConnection) url.openConnection();
    
    // "Accept-Language" 헤더 설정
    conn.setRequestProperty("Accept-Language", "en");

    // HTTP 요청 메서드 설정
    conn.setRequestMethod("GET");

    // 요청 전송
    int responseCode = conn.getResponseCode();
    System.out.println("Response Code : " + responseCode);
  }
}
```

```kotlin
import java.net.HttpURLConnection
import java.net.URL

fun main() {
  val url = URL("http://example.com/api_endpoint_here")
  val conn = url.openConnection() as HttpURLConnection

  // "Accept-Language" 헤더 설정
  conn.setRequestProperty("Accept-Language", "en")

  // HTTP 요청 메서드 설정
  conn.requestMethod = "GET"

  // 요청 전송
  val responseCode = conn.responseCode
  println("Response Code : $responseCode")
}
```

```python
import urllib.request

url = "http://example.com/api_endpoint_here"
headers = {"Accept-Language": "en"}
req = urllib.request.Request(url, headers=headers)

with urllib.request.urlopen(req) as response:
   the_page = response.read()
   print(the_page)
```

```javascript
const http = new XMLHttpRequest();
const url = 'http://example.com/api_endpoint_here';
const lang = 'en';
http.open('GET', url);
http.setRequestHeader('Accept-Language', lang);
http.send();

http.onreadystatechange = (e) => {
  if (http.readyState === XMLHttpRequest.DONE && http.status === 200) {
    console.log(http.responseText);
  }
}
```

response body에 한국어, 영어를 지원하고 있습니다.  
headers에서 아래 내용을 추가하면 됩니다.

한국어 : `Accept-Language: ko_KR`  
english : `Accept-Language: en`

# Authentication

> To authorize, use this code:

```shell
curl "api_endpoint_here" \
-H "X-AUTH-TOKEN: some-jwt-token"
```

```java
import java.net.HttpURLConnection;
import java.net.URL;

public class HttpExample {
  public static void main(String[] args) {
    URL url = new URL("http://example.com/api_endpoint_here");
    HttpURLConnection conn = (HttpURLConnection) url.openConnection();
    
    // "X-AUTH-TOKEN" 헤더 설정
    conn.setRequestProperty("X-AUTH-TOKEN", "some-jwt-token");

    // HTTP 요청 메서드 설정
    conn.setRequestMethod("GET");

    // 요청 전송
    int responseCode = conn.getResponseCode();
    System.out.println("Response Code : " + responseCode);
  }
}
```

```kotlin
import java.net.HttpURLConnection
import java.net.URL

fun main() {
  val url = URL("http://example.com/api_endpoint_here")
  val conn = url.openConnection() as HttpURLConnection

  // "X-AUTH-TOKEN" 헤더 설정
  conn.setRequestProperty("X-AUTH-TOKEN", "some-jwt-token")

  // HTTP 요청 메서드 설정
  conn.requestMethod = "GET"

  // 요청 전송
  val responseCode = conn.responseCode
  println("Response Code : $responseCode")
}
```

```python
import urllib.request

url = "http://example.com/api_endpoint_here"
headers = {"X-AUTH-TOKEN": "some-jwt-token"}
req = urllib.request.Request(url, headers=headers)

with urllib.request.urlopen(req) as response:
   the_page = response.read()
   print(the_page)
```

```javascript
const http = new XMLHttpRequest();
const url = 'http://example.com/api_endpoint_here';
const token = 'some-jwt-token';
http.open('GET', url);
http.setRequestHeader('X-AUTH-TOKEN', token);
http.send();

http.onreadystatechange = (e) => {
  if (http.readyState === XMLHttpRequest.DONE && http.status === 200) {
    console.log(http.responseText);
  }
}
```

> `some-jwt-token` 토큰을 /v1/signIn response body의 jwt token으로 바꿔주세요.

API를 호출하기 위해선 jwt token이 있어야 합니다.  
`/v1/signIn` API를 호출하여 jwt token을 받을 수 있습니다.   
jwt token headers는 아래처럼 넣을 수 있습니다.

`X-AUTH-TOKEN: some-jwt-token`

<aside class="notice">
<code>some-jwt-token</code>을 jwt token으로 변경해야 합니다.
</aside>

<aside class="warning">토큰의 유효기간은 1시간입니다.</aside>


## SignUp

> To SignUp, use this code:

```shell
curl --location --request POST 'https://goose-auth.synology.me/v1/signUp' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userEmail": "pepe-Slate@github.com",
    "userPassword": "drink-party1!",
    "userNickname": "pepe"
}'
```

```java
import java.net.HttpURLConnection;
import java.net.URL;
import java.io.OutputStream;
import java.io.BufferedReader;
import java.io.InputStreamReader;

public class HttpPostExample {
    public static void main(String[] args) {
        try {
            URL url = new URL("https://goose-auth.synology.me/v1/signUp");
            HttpURLConnection conn = (HttpURLConnection) url.openConnection();
            conn.setRequestMethod("POST");
            conn.setRequestProperty("Content-Type", "application/json");
            conn.setDoOutput(true);

            String payload = "{\"userEmail\":\"pepe-Slate@github.com\",\"userPassword\":\"drink-party1!\",\"userNickname\":\"pepe\"}";
            OutputStream os = conn.getOutputStream();
            os.write(payload.getBytes());
            os.flush();

            BufferedReader br = new BufferedReader(new InputStreamReader((conn.getInputStream())));
            String output;
            while ((output = br.readLine()) != null) {
                System.out.println(output);
            }

            conn.disconnect();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

```kotlin
import java.net.HttpURLConnection
import java.net.URL

fun main(args: Array<String>) {
    val url = URL("https://goose-auth.synology.me/v1/signUp")
    val conn = url.openConnection() as HttpURLConnection
    conn.requestMethod = "POST"
    conn.setRequestProperty("Content-Type", "application/json")
    conn.doOutput = true

    val payload = "{\"userEmail\":\"pepe-Slate@github.com\",\"userPassword\":\"drink-party1!\",\"userNickname\":\"pepe\"}"
    val os = conn.outputStream
    os.write(payload.toByteArray())
    os.flush()

    val br = conn.inputStream.bufferedReader()
    var output: String?
    while (br.readLine().also { output = it } != null) {
        println(output)
    }

    conn.disconnect()
}
```

```python
import requests
import json

url = "https://goose-auth.synology.me/v1/signUp"
payload = {
    "userEmail": "pepe-Slate@github.com",
    "userPassword": "drink-party1!",
    "userNickname": "pepe"
}
headers = {
    "Content-Type": "application/json"
}
response = requests.post(url, data=json.dumps(payload), headers=headers)

print(response.text)
```

```javascript
const https = require('https');

const options = {
    hostname: 'goose-auth.synology.me',
    port: 443,
    path: '/v1/signUp',
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    }
};

const payload = JSON.stringify({
    "userEmail": "pepe-Slate@github.com",
    "userPassword": "drink-party1!",
    "userNickname": "pepe"
});

const req = https.request(options, res => {
    console.log(`statusCode: ${res.statusCode}`);

    res.on('data', d => {
        process.stdout.write(d);
    });
});

req.on('error', error => {
    console.error(error);
});

req.write(payload);
req.end();
```

> SignUp Request body:

```json
{
  "userEmail": "pepe-Slate@github.com",
  "userPassword": "drink-party1!",
  "userNickname": "pepe"
}
```

> SignUp Response body:

```json
{
    "success": true,
    "code": 0,
    "message": "성공하였습니다."
}
```

`/v1/signIn` API를 호출하기 전  
userEmail, userPassword를 발급하기 위한 API 입니다.

해당 API를 기반으로 `/v1/signUp` API를 호출하면 토큰을 발급 받을 수 있습니다.

### HTTP Request

`POST https://goose-auth.synology.me/v1/signUp`

### Request body

key | Required | Description
--------- | ------- | -----------
userEmail | true | 로그인을 위한 userEmail
userPassword | true | 로그인을 위한 userPassword
userNickname | true | 개인 닉네임


## SignIn

> To SignIn, use this code:

```shell
curl --location --request POST 'https://goose-auth.synology.me/v1/signIn' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userEmail": "pepe-Slate@github.com",
    "userPassword": "drink-party1!"
}'
```

```java
import java.net.HttpURLConnection;
import java.net.URL;
import java.io.OutputStream;
import java.io.BufferedReader;
import java.io.InputStreamReader;

public class HttpPostExample {
    public static void main(String[] args) {
        try {
            URL url = new URL("https://goose-auth.synology.me/v1/signIn");
            HttpURLConnection conn = (HttpURLConnection) url.openConnection();
            conn.setRequestMethod("POST");
            conn.setRequestProperty("Content-Type", "application/json");
            conn.setDoOutput(true);

            String payload = "{\"userEmail\":\"pepe-Slate@github.com\",\"userPassword\":\"drink-party1!\"}";
            OutputStream os = conn.getOutputStream();
            os.write(payload.getBytes());
            os.flush();

            BufferedReader br = new BufferedReader(new InputStreamReader((conn.getInputStream())));
            String output;
            while ((output = br.readLine()) != null) {
                System.out.println(output);
            }

            conn.disconnect();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

```kotlin
import java.net.HttpURLConnection
import java.net.URL

fun main(args: Array<String>) {
    val url = URL("https://goose-auth.synology.me/v1/signIn")
    val conn = url.openConnection() as HttpURLConnection
    conn.requestMethod = "POST"
    conn.setRequestProperty("Content-Type", "application/json")
    conn.doOutput = true

    val payload = "{\"userEmail\":\"pepe-Slate@github.com\",\"userPassword\":\"drink-party1!\"}"
    val os = conn.outputStream
    os.write(payload.toByteArray())
    os.flush()

    val br = conn.inputStream.bufferedReader()
    var output: String?
    while (br.readLine().also { output = it } != null) {
        println(output)
    }

    conn.disconnect()
}
```

```python
import requests
import json

url = "https://goose-auth.synology.me/v1/signIn"
payload = {
    "userEmail": "pepe-Slate@github.com",
    "userPassword": "drink-party1!"
}
headers = {
    "Content-Type": "application/json"
}
response = requests.post(url, data=json.dumps(payload), headers=headers)

print(response.text)
```

```javascript
const https = require('https');

const options = {
    hostname: 'goose-auth.synology.me',
    port: 443,
    path: '/v1/signIn',
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    }
};

const payload = JSON.stringify({
    "userEmail": "pepe-Slate@github.com",
    "userPassword": "drink-party1!"
});

const req = https.request(options, res => {
    console.log(`statusCode: ${res.statusCode}`);

    res.on('data', d => {
        process.stdout.write(d);
    });
});

req.on('error', error => {
    console.error(error);
});

req.write(payload);
req.end();
```

> SignIn Request body:

```json
{
  "userEmail": "pepe-Slate@github.com",
  "userPassword": "drink-party1!"
}
```

> SignIn Response body:

```json
{
  "success": true,
  "code": 0,
  "message": "성공하였습니다.",
  "data": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiI1Iiwicm9sZXMiOlsiUk9MRV9VU0VSIl0sImlhdCI6MTY3Nzc0NzI2MSwiZXhwIjoxNjc3NzUwODYxfQ.secdNRBHInHkWU720t5s6iF9D0uysnSF1WRIKYoXbWU"
}
```

`/v1/signUp` 호출 후  
userEmail, userPassword를 입력하여 토큰을 발급 받습니다.  
해당 토큰을 아래와 같이 header에 입력 할 수 있습니다.  

`X-AUTH-TOKEN: some-jwt-token` 

### HTTP Request

`POST https://goose-auth.synology.me/v1/SignIn`

### Request body

key | Required | Description
--------- | ------- | -----------
userEmail | true | 회원가입 시 입력했던 userEmail
userPassword | true | 회원가입 시 입력했던 userPassword

# Goose-Auth API

API를 호출하기 위해선 jwt token이 있어야 합니다.  
[Bitwarden](https://bitwarden.com/)을 클론코딩한 API 입니다.  
정보를 저장, 조회, 수정, 삭제가 가능합니다.

## Add Items

> To Add Items, use this code:

```shell
curl -X POST \
  https://goose-auth.synology.me/v1/gooseAuth/addItems \
  -H 'Content-Type: application/json' \
  -H 'X-AUTH-TOKEN: some-jwt-token' \
  -d '{
    "name":"duck",
    "userName":"duck@goose.com",
    "userPassword":"Quarkquark12!",
    "folder":"goose",
    "notes":"I hate goose",
    "uri":[
        "https://www.youtube.com/watch?v=1P5yyeeYF9o",
        "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
    ]
}'
```

```java
import java.net.*;
import java.io.*;
import java.util.*;
import org.json.*;

public class HttpRequest {
    public static void main(String[] args) {
        URL url = new URL("https://goose-auth.synology.me/v1/gooseAuth/addItems");
        HttpURLConnection con = (HttpURLConnection) url.openConnection();
        con.setRequestMethod("POST");

        // Set headers
        con.setRequestProperty("Content-Type", "application/json");
        con.setRequestProperty("X-AUTH-TOKEN", "some-jwt-token");

        // Set request body
        JSONObject requestBody = new JSONObject();
        requestBody.put("name", "duck");
        requestBody.put("userName", "duck@goose.com");
        requestBody.put("userPassword", "Quarkquark12!");
        requestBody.put("folder", "goose");
        requestBody.put("notes", "I hate goose");
        JSONArray uriArray = new JSONArray();
        uriArray.put("https://www.youtube.com/watch?v=1P5yyeeYF9o");
        uriArray.put("https://www.youtube.com/watch?v=dQw4w9WgXcQ");
        requestBody.put("uri", uriArray);

        // Send the POST request
        con.setDoOutput(true);
        OutputStreamWriter wr = new OutputStreamWriter(con.getOutputStream());
        wr.write(requestBody.toString());
        wr.flush();

        // Read the response
        BufferedReader in = new BufferedReader(new InputStreamReader(con.getInputStream()));
        String inputLine;
        StringBuffer response = new StringBuffer();
        while ((inputLine = in.readLine()) != null) {
            response.append(inputLine);
        }
        in.close();

        // Print the response
        System.out.println(response.toString());
    }
}
```

```kotlin
import java.io.BufferedWriter
import java.io.OutputStreamWriter
import java.net.URL

fun main() {
    val url = URL("https://goose-auth.synology.me/v1/signUp")
    val connection = url.openConnection() as HttpURLConnection
    connection.requestMethod = "POST"
    connection.setRequestProperty("Content-Type", "application/json")
    connection.setRequestProperty("X-AUTH-TOKEN", "some-jwt-token")
    connection.doOutput = true

    val requestBody = """
        {
            "userEmail": "pepe-Slate@github.com",
            "userPassword": "drink-party1!",
            "userNickname": "pepe"
        }
    """.trimIndent()

    val writer = BufferedWriter(OutputStreamWriter(connection.outputStream))
    writer.write(requestBody)
    writer.flush()
    writer.close()

    val responseCode = connection.responseCode
    val responseBody = connection.inputStream.bufferedReader().use { it.readText() }

    println("Response code: $responseCode")
    println("Response body: $responseBody")
}
```

```python
import requests
import json

url = "https://goose-auth.synology.me/v1/gooseAuth/addItems"
payload = {
    "name": "duck",
    "userName": "duck@goose.com",
    "userPassword": "Quarkquark12!",
    "folder": "goose",
    "notes": "I hate goose",
    "uri": [
        "https://www.youtube.com/watch?v=1P5yyeeYF9o",
        "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
    ]
}
headers = {
    "Content-Type": "application/json",
    "X-AUTH-TOKEN": "some-jwt-token"
}
response = requests.post(url, data=json.dumps(payload), headers=headers)
print(response.content)
```

```javascript
const https = require('https');

const options = {
    hostname: 'goose-auth.synology.me',
    path: '/v1/gooseAuth/addItems',
    method: 'POST',
    headers: {
        'Content-Type': 'application/json',
        'X-AUTH-TOKEN': 'some-jwt-token'
    }
};

const req = https.request(options, (res) => {
    console.log(`statusCode: ${res.statusCode}`);

    res.on('data', (d) => {
        process.stdout.write(d);
    });
});

req.on('error', (error) => {
    console.error(error);
});

const payload = JSON.stringify({
    name: 'duck',
    userName: 'duck@goose.com',
    userPassword: 'Quarkquark12!',
    folder: 'goose',
    notes: 'I hate goose',
    uri: [
        'https://www.youtube.com/watch?v=1P5yyeeYF9o',
        'https://www.youtube.com/watch?v=dQw4w9WgXcQ'
    ]
});

req.write(payload);
req.end();
```

> addItems Request body:

```json
{
  "name":"duck",
  "userName":"duck@goose.com",
  "userPassword":"Quarkquark12!",
  "folder":"goose",
  "notes":"I hate goose",
  "uri":[
    "https://www.youtube.com/watch?v=1P5yyeeYF9o",
    "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
  ]
}
```

> addItems Response body:

```json
{
  "success": true,
  "code": 0,
  "message": "성공하였습니다.",
  "data": {
    "itemIdentity": 22,
    "name": "duck",
    "userName": "duck@goose.com",
    "userPassword": "Quarkquark12!",
    "folder": "goose",
    "notes": "I hate goose",
    "uri": [
      {
        "uriIdentity": 55,
        "uri": "https://www.youtube.com/watch?v=1P5yyeeYF9o"
      },
      {
        "uriIdentity": 56,
        "uri": "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
      }
    ]
  }
}
```

원하는 정보를 저장 할 수 있습니다.

### HTTP Request

`POST https://goose-auth.synology.me/v1/gooseAuth/addItems`

### headers

`Content-Type: application/json`
`X-AUTH-TOKEN: some-jwt-token`

### Request body

key | Required | Description
--------- | ------- | -----------
name  | true | 정보 이름
userName  | false | 특정 로그인의 계정명
userPassword  | false | 특정 로그인의 패스워드
folder  | false | 저장 위치 지정
notes  | false | 정보에 대한 설명
uri  | false | 접속장소

## Get all items

> To Get all items, use this code:

```shell
curl -H "X-AUTH-TOKEN: some-jwt-token" https://goose-auth.synology.me/v1/gooseAuth/items
```

```java
import java.net.HttpURLConnection;
import java.net.URL;
import java.io.BufferedReader;
import java.io.InputStreamReader;

public class Main {
    public static void main(String[] args) {
        String url = "https://goose-auth.synology.me/v1/gooseAuth/items";
        URL obj = new URL(url);
        HttpURLConnection con = (HttpURLConnection) obj.openConnection();
        con.setRequestMethod("GET");
        con.setRequestProperty("X-AUTH-TOKEN", "some-jwt-token");

        int responseCode = con.getResponseCode();
        BufferedReader in = new BufferedReader(new InputStreamReader(con.getInputStream()));
        String inputLine;
        StringBuffer response = new StringBuffer();

        while ((inputLine = in.readLine()) != null) {
            response.append(inputLine);
        }
        in.close();

        System.out.println("Response code: " + responseCode);
        System.out.println("Response body: " + response.toString());
    }
}
```

```kotlin
import java.net.URL
import java.io.BufferedReader
import java.io.InputStreamReader
import java.net.HttpURLConnection

fun main() {
    val url = URL("https://goose-auth.synology.me/v1/gooseAuth/items")
    val connection = url.openConnection() as HttpURLConnection
    connection.setRequestProperty("X-AUTH-TOKEN", "some-jwt-token")
    connection.requestMethod = "GET"

    val responseCode = connection.responseCode
    val responseBody = connection.inputStream.bufferedReader().use { it.readText() }

    println("Response code: $responseCode")
    println("Response body: $responseBody")
}
```

```python
import urllib.request
import json

url = 'https://goose-auth.synology.me/v1/gooseAuth/items'
req = urllib.request.Request(url, headers={'X-AUTH-TOKEN': 'some-jwt-token'})

with urllib.request.urlopen(req) as response:
    response_body = response.read().decode('utf-8')
    print("Response code:", response.status)
    print("Response body:", response_body)
```

```javascript
const https = require('https');

const options = {
    hostname: 'goose-auth.synology.me',
    port: 443,
    path: '/v1/gooseAuth/items',
    method: 'GET',
    headers: {
        'X-AUTH-TOKEN': 'some-jwt-token'
    }
};

const req = https.request(options, (res) => {
    let responseBody = '';
    res.on('data', (chunk) => {
        responseBody += chunk;
    });
    res.on('end', () => {
        console.log('Response code:', res.statusCode);
        console.log('Response body:', responseBody);
    });
});

req.on('error', (e) => {
    console.error(e);
});

req.end();
```

> items Response body:

```json
{
  "success": true,
  "code": 0,
  "message": "성공하였습니다.",
  "list": [
    {
      "itemIdentity": 22,
      "name": "duck",
      "userName": "duck@goose.com"
    }
  ]
}
```

모든 정보를 가져올 수 있습니다.

### HTTP Request

`GET https://goose-auth.synology.me/v1/gooseAuth/items`

### headers

`Content-Type: application/json`
`X-AUTH-TOKEN: some-jwt-token`

## Get item

> To Get item, use this code:

```shell
curl -H "X-AUTH-TOKEN: some-jwt-token" https://goose-auth.synology.me/v1/gooseAuth/items/22
```

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.net.HttpURLConnection;
import java.net.URL;

public class ApiTest {
    public static void main(String[] args) {
        String url = "https://goose-auth.synology.me/v1/gooseAuth/items/22";
        URL obj = new URL(url);
        HttpURLConnection con = (HttpURLConnection) obj.openConnection();
        con.setRequestMethod("GET");
        con.setRequestProperty("X-AUTH-TOKEN", "some-jwt-token");

        int responseCode = con.getResponseCode();
        System.out.println("\nSending 'GET' request to URL : " + url);
        System.out.println("Response Code : " + responseCode);

        BufferedReader in = new BufferedReader(
                new InputStreamReader(con.getInputStream()));
        String inputLine;
        StringBuffer response = new StringBuffer();

        while ((inputLine = in.readLine()) != null) {
            response.append(inputLine);
        }
        in.close();

        System.out.println(response.toString());
    }
}
```

```kotlin
import java.net.HttpURLConnection
import java.net.URL

fun main() {
  val url = URL("https://goose-auth.synology.me/v1/gooseAuth/items/22")
  val con = url.openConnection() as HttpURLConnection
  con.requestMethod = "GET"
  con.setRequestProperty("X-AUTH-TOKEN", "some-jwt-token")

  val responseCode = con.responseCode
  println("\nSending 'GET' request to URL : $url")
  println("Response Code : $responseCode")

  val input = BufferedReader(InputStreamReader(con.inputStream))
  var inputLine: String?
  val response = StringBuffer()

  while (input.readLine().also { inputLine = it } != null) {
    response.append(inputLine)
  }
  input.close()

  println(response.toString())
}
```

```python
import requests

headers = {
    'X-AUTH-TOKEN': 'some-jwt-token'
}

response = requests.get('https://goose-auth.synology.me/v1/gooseAuth/items/22', headers=headers)
print(response.text)
```

```javascript
const https = require('https');

const options = {
  hostname: 'goose-auth.synology.me',
  path: '/v1/gooseAuth/items/22',
  method: 'GET',
  headers: {
    'X-AUTH-TOKEN': 'some-jwt-token'
  }
};

const req = https.request(options, res => {
  console.log(`statusCode: ${res.statusCode}`);

  res.on('data', d => {
    process.stdout.write(d);
  });
});

req.on('error', error => {
  console.error(error);
});

req.end();
```

> /items/{itemIdentity} Response body:

```json
{
  "success": true,
  "code": 0,
  "message": "성공하였습니다.",
  "data": {
    "itemIdentity": 22,
    "name": "duck",
    "userName": "duck@goose.com",
    "userPassword": "Quarkquark12!",
    "folder": "goose",
    "notes": "I hate goose",
    "uris": [
      {
        "uriIdentity": 55,
        "uri": "https://www.youtube.com/watch?v=1P5yyeeYF9o"
      },
      {
        "uriIdentity": 56,
        "uri": "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
      }
    ]
  }
}
```

특정 정보를 가져올 수 있습니다.

### HTTP Request

`GET https://goose-auth.synology.me/v1/gooseAuth/items/{itemIdentity}`

### headers

`Content-Type: application/json`
`X-AUTH-TOKEN: some-jwt-token`

### URL Parameters

Parameter | Description
--------- | -----------
itemIdentity | addItems id

## Update Item

> To Update Item, use this code:

```shell
curl -X PUT \
  https://goose-auth.synology.me/v1/gooseAuth/items/22 \
  -H 'Content-Type: application/json' \
  -H 'X-AUTH-TOKEN: some-jwt-token' \
  -d '{
    "name": "goose",
    "userName": "duck@github.com",
    "userPassword": "as345gh!@#",
    "folder": "temp folder",
    "notes": "temp",
    "uris": [
        {
            "uriIdentity": 55,
            "uri": "https://youtu.be/zd7c5tQCs1I"
        },
        {
            "uriIdentity": 56,
            "uri": "https://youtu.be/Svj1bZz2mXw"
        }
    ]
}'
```

```java
import java.net.HttpURLConnection;
import java.net.URL;
import java.io.OutputStreamWriter;
import java.io.BufferedReader;
import java.io.InputStreamReader;

public class HttpPutExample {
    public static void main(String[] args) {
        try {
            URL url = new URL("https://goose-auth.synology.me/v1/gooseAuth/items/22");
            HttpURLConnection con = (HttpURLConnection) url.openConnection();
            con.setRequestMethod("PUT");
            con.setRequestProperty("Content-Type", "application/json");
            con.setRequestProperty("X-AUTH-TOKEN", "some-jwt-token");
            con.setDoOutput(true);

            String data = "{\"name\": \"goose\", \"userName\": \"duck@github.com\", \"userPassword\": \"as345gh!@#\", \"folder\": \"temp folder\", \"notes\": \"temp\", \"uris\": [{\"uriIdentity\": 55, \"uri\": \"https://youtu.be/zd7c5tQCs1I\"}, {\"uriIdentity\": 56, \"uri\": \"https://youtu.be/Svj1bZz2mXw\"}]}";
            OutputStreamWriter wr = new OutputStreamWriter(con.getOutputStream());
            wr.write(data);
            wr.flush();

            int responseCode = con.getResponseCode();
            BufferedReader in = new BufferedReader(new InputStreamReader(con.getInputStream()));
            String inputLine;
            StringBuffer response = new StringBuffer();
            while ((inputLine = in.readLine()) != null) {
                response.append(inputLine);
            }
            in.close();

            System.out.println(response.toString());
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}
```

```kotlin
import java.net.HttpURLConnection
import java.net.URL
import java.io.BufferedReader
import java.io.InputStreamReader

fun main() {
    val url = URL("https://goose-auth.synology.me/v1/gooseAuth/items/22")
    val connection = url.openConnection() as HttpURLConnection
    connection.requestMethod = "PUT"
    connection.setRequestProperty("Content-Type", "application/json")
    connection.setRequestProperty("X-AUTH-TOKEN", "some-jwt-token")
    connection.doOutput = true

    val requestBody = """
        {
            "name": "goose",
            "userName": "duck@github.com",
            "userPassword": "as345gh!@#",
            "folder": "temp folder",
            "notes": "temp",
            "uris": [
                {
                    "uriIdentity": 55,
                    "uri": "https://youtu.be/zd7c5tQCs1I"
                },
                {
                    "uriIdentity": 56,
                    "uri": "https://youtu.be/Svj1bZz2mXw"
                }
            ]
        }
    """.trimIndent()

    connection.outputStream.write(requestBody.toByteArray(Charsets.UTF_8))
    connection.outputStream.flush()

    val responseCode = connection.responseCode
    if (responseCode == HttpURLConnection.HTTP_OK) {
        val responseReader = BufferedReader(InputStreamReader(connection.inputStream))
        val response = StringBuilder()
        var line: String? = null
        while ({ line = responseReader.readLine(); line }() != null) {
            response.append(line)
        }
        responseReader.close()
        println(response.toString())
    } else {
        println("Error: $responseCode")
    }

    connection.disconnect()
}
```

```python
import json
import urllib.request

url = "https://goose-auth.synology.me/v1/gooseAuth/items/22"
headers = {
    "X-AUTH-TOKEN": "some-jwt-token",
    "Content-Type": "application/json"
}
data = {
    "name": "goose",
    "userName": "duck@github.com",
    "userPassword": "as345gh!@#",
    "folder": "temp folder",
    "notes": "temp",
    "uris": [
        {
            "uriIdentity": 55,
            "uri": "https://youtu.be/zd7c5tQCs1I"
        },
        {
            "uriIdentity": 56,
            "uri": "https://youtu.be/Svj1bZz2mXw"
        }
    ]
}
data = json.dumps(data).encode("utf-8")

req = urllib.request.Request(url, data=data, headers=headers, method="PUT")
response = urllib.request.urlopen(req)
response_code = response.getcode()
```

```javascript
const https = require('https');

const data = JSON.stringify({
  "name": "goose",
  "userName": "duck@github.com",
  "userPassword": "as345gh!@#",
  "folder": "temp folder",
  "notes": "temp",
  "uris": [
    {
      "uriIdentity": 55,
      "uri": "https://youtu.be/zd7c5tQCs1I"
    },
    {
      "uriIdentity": 56,
      "uri": "https://youtu.be/Svj1bZz2mXw"
    }
  ]
});

const options = {
  hostname: 'goose-auth.synology.me',
  port: 443,
  path: '/v1/gooseAuth/items/22',
  method: 'PUT',
  headers: {
    'Content-Type': 'application/json',
    'X-AUTH-TOKEN': 'some-jwt-token',
    'Content-Length': data.length
  }
};

const req = https.request(options, res => {
  console.log(`statusCode: ${res.statusCode}`);

  res.on('data', d => {
    process.stdout.write(d);
  });
});

req.on('error', error => {
  console.error(error);
});

req.write(data);
req.end();
```

> Update Item Request body:

```json
{
  "name": "goose",
  "userName": "duck@github.com",
  "userPassword": "as345gh!@#",
  "folder": "temp folder",
  "notes": "temp",
  "uris": [
    {
      "uriIdentity": 55,
      "uri": "https://youtu.be/zd7c5tQCs1I"
    },
    {
      "uriIdentity": 56,
      "uri": "https://youtu.be/Svj1bZz2mXw"
    }
  ]
}
```

> Update Item Response body:

```json
{
  "success": true,
  "code": 0,
  "message": "성공하였습니다.",
  "data": {
    "itemIdentity": 22,
    "name": "goose",
    "userName": "duck@github.com",
    "userPassword": "as345gh!@#",
    "folder": "temp folder",
    "notes": "temp",
    "uris": [
      {
        "uriIdentity": 55,
        "uri": "https://youtu.be/zd7c5tQCs1I"
      },
      {
        "uriIdentity": 56,
        "uri": "https://youtu.be/Svj1bZz2mXw"
      }
    ]
  }
}
```

원하는 정보를 수정 할 수 있습니다.

### HTTP Request

`PUT https://goose-auth.synology.me/v1/gooseAuth/items/{itemIdentity}`

### headers

`Content-Type: application/json`
`X-AUTH-TOKEN: some-jwt-token`

### Request body

key | Required | Description
--------- | ------- | -----------
name  | true | 정보 이름
userName  | false | 특정 로그인의 계정명
userPassword  | false | 특정 로그인의 패스워드
folder  | false | 저장 위치 지정
notes  | false | 정보에 대한 설명
uris  | false | 접속장소

### URL Parameters

Parameter | Description
--------- | -----------
itemIdentity | addItems id

## Add item url

> To Add item url, use this code:

```shell
curl --request POST \
     --url https://goose-auth.synology.me/v1/gooseAuth/items/22 \
     --header 'Content-Type: application/json' \
     --header 'X-AUTH-TOKEN: some-jwt-token' \
     --data '{ "uri": ["https://youtu.be/ZZ5LpwO-An4", "https://youtu.be/gy1B3agGNxw"] }'
```

```java
import java.io.IOException;
import java.net.HttpURLConnection;
import java.net.URL;

public class Main {
  public static void main(String[] args) {
    URL url = new URL("https://goose-auth.synology.me/v1/gooseAuth/items/22");
    HttpURLConnection con = (HttpURLConnection) url.openConnection();
    con.setRequestMethod("POST");
    con.setRequestProperty("Content-Type", "application/json");
    con.setRequestProperty("X-AUTH-TOKEN", "some-jwt-token");
    con.setDoOutput(true);
    String requestBody = "{ \"uri\": [\"https://youtu.be/ZZ5LpwO-An4\", \"https://youtu.be/gy1B3agGNxw\"] }";
    con.getOutputStream().write(requestBody.getBytes());
    int responseCode = con.getResponseCode();
    System.out.println("Response code: " + responseCode);
  }
}
```

```kotlin
import java.net.HttpURLConnection
import java.net.URL

fun main() {
  val url = URL("https://goose-auth.synology.me/v1/gooseAuth/items/22")
  val con = url.openConnection() as HttpURLConnection
  con.requestMethod = "POST"
  con.setRequestProperty("Content-Type", "application/json")
  con.setRequestProperty("X-AUTH-TOKEN", "some-jwt-token")
  con.doOutput = true
  val requestBody = "{ \"uri\": [\"https://youtu.be/ZZ5LpwO-An4\", \"https://youtu.be/gy1B3agGNxw\"] }"
  con.outputStream.write(requestBody.toByteArray())
  val responseCode = con.responseCode
  println("Response code: $responseCode")
}
```

```python
import urllib.request
import json

url = 'https://goose-auth.synology.me/v1/gooseAuth/items/22'
data = json.dumps({"uri": ["https://youtu.be/ZZ5LpwO-An4", "https://youtu.be/gy1B3agGNxw"]}).encode('utf-8')
headers = {
    'Content-Type': 'application/json',
    'X-AUTH-TOKEN': 'some-jwt-token'
}
req = urllib.request.Request(url, data=data, headers=headers, method='POST')
with urllib.request.urlopen(req) as response:
    print(response.status)
```

```javascript
const xhr = new XMLHttpRequest();

// 요청 완료 시 콜백 함수 지정
xhr.onreadystatechange = function() {
  if (xhr.readyState === XMLHttpRequest.DONE) {
    console.log(xhr.responseText);
  }
}

// HTTP 요청 설정
xhr.open('POST', 'https://goose-auth.synology.me/v1/gooseAuth/items/22');
xhr.setRequestHeader('X-AUTH-TOKEN', 'some-jwt-token');
xhr.setRequestHeader('Content-Type', 'application/json');
const requestBody = {
  "uri": [
    "https://youtu.be/ZZ5LpwO-An4",
    "https://youtu.be/gy1B3agGNxw"
  ]
};
xhr.send(JSON.stringify(requestBody));
```

> Add item url Request body:

```json
{
  "uri": [
    "https://youtu.be/ZZ5LpwO-An4",
    "https://youtu.be/gy1B3agGNxw"
  ]
}
```

> Add item url Response body:

```json
{
  "success": true,
  "code": 0,
  "message": "성공하였습니다.",
  "data": {
    "itemIdentity": 22,
    "name": "goose",
    "userName": "duck@github.com",
    "userPassword": "as345gh!@#",
    "folder": "temp folder",
    "notes": "temp",
    "uris": [
      {
        "uriIdentity": 55,
        "uri": "https://youtu.be/zd7c5tQCs1I"
      },
      {
        "uriIdentity": 56,
        "uri": "https://youtu.be/Svj1bZz2mXw"
      },
      {
        "uriIdentity": 57,
        "uri": "https://youtu.be/ZZ5LpwO-An4"
      },
      {
        "uriIdentity": 58,
        "uri": "https://youtu.be/gy1B3agGNxw"
      }
    ]
  }
}
```

원하는 uri를 추가 할 수 있습니다.

### HTTP Request

`POST https://goose-auth.synology.me/v1/gooseAuth/items/{itemIdentity}`

### headers

`Content-Type: application/json`
`X-AUTH-TOKEN: some-jwt-token`

### Request body

key | Required | Description
--------- | ------- | -----------
uris  | true | 접속장소

### URL Parameters

Parameter | Description
--------- | -----------
itemIdentity | addItems id

## Delete item uris

> To Delete item uris url, use this code:

```shell
curl -X DELETE \
  'https://goose-auth.synology.me/v1/gooseAuth/items/22?uriIdentity=55&uriIdentity=56' \
  -H 'Content-Type: application/json' \
  -H 'X-AUTH-TOKEN: some-jwt-token'
```

```java
import java.net.HttpURLConnection;
import java.net.URL;

public class DeleteRequestExample {
  public static void main(String[] args) {
    try {
      URL url = new URL("https://goose-auth.synology.me/v1/gooseAuth/items/22?uriIdentity=55&uriIdentity=56");
      HttpURLConnection conn = (HttpURLConnection) url.openConnection();
      conn.setRequestMethod("DELETE");
      conn.setRequestProperty("Content-Type", "application/json");
      conn.setRequestProperty("X-AUTH-TOKEN", "some-jwt-token");

      if (conn.getResponseCode() != 204) {
        throw new RuntimeException("Failed : HTTP error code : " + conn.getResponseCode());
      }

      conn.disconnect();

    } catch (Exception e) {
      e.printStackTrace();
    }
  }
}
```

```kotlin
import java.net.URL
import java.net.HttpURLConnection

fun main() {
  try {
    val url = URL("https://goose-auth.synology.me/v1/gooseAuth/items/22?uriIdentity=55&uriIdentity=56")
    val conn = url.openConnection() as HttpURLConnection
    conn.requestMethod = "DELETE"
    conn.setRequestProperty("Content-Type", "application/json")
    conn.setRequestProperty("X-AUTH-TOKEN", "some-jwt-token")

    if (conn.responseCode != 204) {
      throw RuntimeException("Failed : HTTP error code : " + conn.responseCode)
    }

    conn.disconnect()
  } catch (e: Exception) {
    e.printStackTrace()
  }
}
```

```python
import urllib.request

url = 'https://goose-auth.synology.me/v1/gooseAuth/items/22?uriIdentity=55&uriIdentity=56'
req = urllib.request.Request(url, method='DELETE')
req.add_header('Content-Type', 'application/json')
req.add_header('X-AUTH-TOKEN', 'some-jwt-token')

with urllib.request.urlopen(req) as f:
    pass
```

```javascript
const https = require('https');

const options = {
  hostname: 'goose-auth.synology.me',
  path: '/v1/gooseAuth/items/22?uriIdentity=55&uriIdentity=56',
  method: 'DELETE',
  headers: {
    'Content-Type': 'application/json',
    'X-AUTH-TOKEN': 'some-jwt-token'
  }
};

const req = https.request(options, res => {
  console.log(`statusCode: ${res.statusCode}`);

  res.on('data', d => {
    process.stdout.write(d);
  });
});

req.on('error', error => {
  console.error(error);
});

req.end();
```

> Delete item uris Request URL:

[https://goose-auth.synology.me/v1/gooseAuth/items/22?uriIdentity=55&uriIdentity=56
](https://goose-auth.synology.me/v1/gooseAuth/items/22?uriIdentity=55&uriIdentity=56)

> Delete item uris url Response body:

```json
{
  "success": true,
  "code": 0,
  "message": "성공하였습니다.",
  "data": {
    "itemIdentity": 22,
    "name": "goose",
    "userName": "duck@github.com",
    "userPassword": "as345gh!@#",
    "folder": "temp folder",
    "notes": "temp",
    "uris": [
      {
        "uriIdentity": 57,
        "uri": "https://youtu.be/ZZ5LpwO-An4"
      },
      {
        "uriIdentity": 58,
        "uri": "https://youtu.be/gy1B3agGNxw"
      }
    ]
  }
}
```

원하는 uri 정보를 삭제 할 수 있습니다.

### HTTP Request

`DELETE https://goose-auth.synology.me/v1/gooseAuth/items/{itemIdentity}`

### headers

`Content-Type: application/json`
`X-AUTH-TOKEN: some-jwt-token`

### Query Parameters

key | Required | Description
--------- | ------- | -----------
uriIdentity  | true | URI id

### URL Parameters

Parameter | Description
--------- | -----------
itemIdentity | addItems id

