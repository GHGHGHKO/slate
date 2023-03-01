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

방문해주셔서 감사합니다. :)

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
  public static void main(String[] args) throws Exception {
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

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> `some-jwt-token` 토큰을 /v1/signIn response body의 jwt token으로 바꿔주세요.

API를 호출하기 위해선 jwt token이 있어야 합니다.  
`/v1/signIn` API를 호출하여 jwt token을 받을 수 있습니다.   
jwt token headers는 아래처럼 넣을 수 있습니다.

`X-AUTH-TOKEN: some-jwt-token`

<aside class="notice">
<code>some-jwt-token</code>을 jwt token으로 변경해야 합니다.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
