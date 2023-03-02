# Errors

### The goose-auth API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The goose-auth requested is hidden for administrators only.
404 | Not Found -- The specified goose-auth could not be found.
405 | Method Not Allowed -- You tried to access a goose-auth with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
410 | Gone -- The goose-auth requested has been removed from our servers.
418 | I'm a teapot.
429 | Too Many Requests -- You're requesting too many goose-auth! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

### 오류 response body 메시지와 코드

Error Code | HttpStatus | Meaning
---------- | ------- | ------- 
-9999 | 500 Internal Server Error | 알 수 없는 오류가 발생하였습니다.
-1000 | 404 Not Found | 존재하지 않는 회원입니다.
-1001 | 401 Unauthorized | 계정이 존재하지 않거나, 이메일 또는 비밀번호가 정확하지 않습니다.
-1002 | 401 Unauthorized | 해당 리소스에 접근하기 위한 권한이 없습니다.
-1003 | 403 Forbidden | 보유한 권한으로 접근할 수 없는 리소스 입니다.
-1004 | 500 Internal Server Error | 통신 중 오류가 발생하였습니다.
-1005 | 409 Conflict | 이미 가입한 회원입니다. 로그인을 해주십시오.
-1006 | 400 Bad Request | 요청 내용에 오류가 발생하였습니다.
-1007 | 404 Not Found | 요청 item 이 존재하지 않습니다.
-1008 | 400 Bad Request | 요청 parameter에 오류가 발생하였습니다.


### Error Response body message and codes 

Error Code | HttpStatus | Meaning
---------- | ------- | ------- 
-9999 | 500 Internal Server Error | An unknown error has occurred.
-1000 | 404 Not Found | This member not exist.
-1001 | 401 Unauthorized | Your account does not exist or your email or password is incorrect.
-1002 | 401 Unauthorized | You do not have permission to access this resource.
-1003 | 403 Forbidden | A resource that can not be accessed with the privileges it has.
-1004 | 500 Internal Server Error | An error occurred during communication.
-1005 | 409 Conflict | You are an existing member.
-1006 | 400 Bad Request | An error has occurred in your request body.
-1007 | 404 Not Found | This item does not exist.
-1008 | 400 Bad Request | An error has occurred in your request parameter.
