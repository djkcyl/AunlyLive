---
title: live_auth v1.0.0
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
code_clipboard: true
highlight_theme: darkula
headingLevel: 2
generator: "@tarslib/widdershins v4.0.17"

---

# live_auth

> v1.0.0

Base URLs:

# Authentication

<a id="opIdlogin_for_access_token_auth_token_post"></a>

## POST Login For Access Token

POST /auth/token

> Body 请求参数

```yaml
grant_type: string
username: string
password: string
scope: string
client_id: string
client_secret: string

```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|object| 否 |none|
|» grant_type|body|string| 否 |none|
|» username|body|string| 是 |none|
|» password|body|string| 是 |none|
|» scope|body|string| 否 |none|
|» client_id|body|string| 否 |none|
|» client_secret|body|string| 否 |none|

> 返回示例

> 200 Response

```json
{
  "access_token": "string",
  "token_type": "string"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[Token](#schematoken)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

# Users

<a id="opIdcreate_new_user_users_create_post"></a>

## POST Create New User

POST /users/create

> Body 请求参数

```json
{
  "username": "string",
  "email": "user@example.com",
  "full_name": "string",
  "password": "string"
}
```

### 请求参数

|名称|位置|类型|必选|中文名|说明|
|---|---|---|---|---|---|
|body|body|[UserCreate](#schemausercreate)| 否 | UserCreate|none|

> 返回示例

> 200 Response

```json
{
  "username": "string",
  "email": "string",
  "full_name": "string",
  "permission_level": 0
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[User](#schemauser)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

<a id="opIdread_users_me_users_me_get"></a>

## GET Read Users Me

GET /users/me

> 返回示例

> 200 Response

```json
{
  "username": "string",
  "email": "string",
  "full_name": "string",
  "permission_level": 0
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[User](#schemauser)|

# Live Streaming

<a id="opIdcreate_live_token_route_live_create_token_post"></a>

## POST Create Live Token Route

POST /live/create_token

### 请求参数

|名称|位置|类型|必选|中文名|说明|
|---|---|---|---|---|---|
|stream|query|string| 是 ||none|
|level|query|integer| 否 ||none|

> 返回示例

> 200 Response

```json
{
  "username": "string",
  "stream": "string",
  "token": "string",
  "play_token": "string",
  "permissions_level": 0
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[LiveToken](#schemalivetoken)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

<a id="opIddestroy_live_token_route_live_destroy_token_delete"></a>

## DELETE Destroy Live Token Route

DELETE /live/destroy_token

### 请求参数

|名称|位置|类型|必选|中文名|说明|
|---|---|---|---|---|---|
|token|query|string| 是 ||none|

> 返回示例

> 200 Response

```json
"string"
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|string|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

<a id="opIdlist_live_tokens_live_list_tokens_get"></a>

## GET List Live Tokens

GET /live/list_tokens

> 返回示例

> 200 Response

```json
[
  {
    "username": "string",
    "stream": "string",
    "token": "string",
    "play_token": "string",
    "permissions_level": 0
  }
]
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|Inline|

### 返回数据结构

状态码 **200**

*Response List Live Tokens Live List Tokens Get*

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|Response List Live Tokens Live List Tokens Get|[[LiveToken](#schemalivetoken)]|false|none|Response List Live Tokens Live List Tokens Get|none|
|» LiveToken|[LiveToken](#schemalivetoken)|false|none|LiveToken|none|
|»» username|string|true|none|Username|none|
|»» stream|string|true|none|Stream|none|
|»» token|string|true|none|Token|none|
|»» play_token|string|true|none|Play Token|none|
|»» permissions_level|integer|true|none|Permissions Level|none|

# Callback

<a id="opIdon_publish_callback_on_publish_post"></a>

## POST On Publish

POST /callback/on_publish

> Body 请求参数

```json
{
  "server_id": "string",
  "action": "string",
  "client_id": "string",
  "ip": "string",
  "vhost": "string",
  "app": "string",
  "tcUrl": "string",
  "stream": "string",
  "param": "string",
  "stream_url": "string",
  "stream_id": "string"
}
```

### 请求参数

|名称|位置|类型|必选|中文名|说明|
|---|---|---|---|---|---|
|body|body|[LiveStreamCallback](#schemalivestreamcallback)| 否 | LiveStreamCallback|none|

> 返回示例

> 200 Response

```json
"string"
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|string|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

<a id="opIdon_play_callback_on_play_post"></a>

## POST On Play

POST /callback/on_play

> Body 请求参数

```json
{
  "server_id": "string",
  "action": "string",
  "client_id": "string",
  "ip": "string",
  "vhost": "string",
  "app": "string",
  "tcUrl": "string",
  "stream": "string",
  "param": "string",
  "stream_url": "string",
  "stream_id": "string"
}
```

### 请求参数

|名称|位置|类型|必选|中文名|说明|
|---|---|---|---|---|---|
|body|body|[LiveStreamCallback](#schemalivestreamcallback)| 否 | LiveStreamCallback|none|

> 返回示例

> 200 Response

```json
"string"
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|string|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

<a id="opIdon_dvr_callback_on_dvr_post"></a>

## POST On Dvr

POST /callback/on_dvr

> Body 请求参数

```json
{
  "action": "string",
  "client_id": "string",
  "ip": "string",
  "vhost": "string",
  "app": "string",
  "stream": "string",
  "param": "string",
  "cwd": "string",
  "file": "string",
  "server_id": "string",
  "stream_url": "string",
  "stream_id": "string"
}
```

### 请求参数

|名称|位置|类型|必选|中文名|说明|
|---|---|---|---|---|---|
|body|body|[DvrCallback](#schemadvrcallback)| 否 | DvrCallback|none|

> 返回示例

> 200 Response

```json
"string"
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|string|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

# Streams

<a id="opIdget_streams_streams_list_get"></a>

## GET Get Streams

GET /streams/list

> 返回示例

> 200 Response

```json
{
  "code": 0,
  "streams": [
    {
      "name": "string",
      "play_url": "string",
      "kbps": {},
      "video": {
        "codec": "string",
        "profile": "string",
        "level": "string",
        "width": 0,
        "height": 0
      },
      "audio": {
        "codec": "string",
        "sample_rate": 0,
        "channel": 0,
        "profile": "string"
      },
      "clients": 0
    }
  ]
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[LiveStreamResponse](#schemalivestreamresponse)|

# 数据模型

<h2 id="tocS_ValidationError">ValidationError</h2>

<a id="schemavalidationerror"></a>
<a id="schema_ValidationError"></a>
<a id="tocSvalidationerror"></a>
<a id="tocsvalidationerror"></a>

```json
{
  "loc": [
    "string"
  ],
  "msg": "string",
  "type": "string"
}

```

ValidationError

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|loc|[anyOf]|true|none|Location|none|

anyOf

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» *anonymous*|string|false|none||none|

or

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» *anonymous*|integer|false|none||none|

continued

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|msg|string|true|none|Message|none|
|type|string|true|none|Error Type|none|

<h2 id="tocS_UserCreate">UserCreate</h2>

<a id="schemausercreate"></a>
<a id="schema_UserCreate"></a>
<a id="tocSusercreate"></a>
<a id="tocsusercreate"></a>

```json
{
  "username": "string",
  "email": "user@example.com",
  "full_name": "string",
  "password": "string"
}

```

UserCreate

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|username|string|true|none|Username|none|
|email|string(email)|true|none|Email|none|
|full_name|string|true|none|Full Name|none|
|password|string|true|none|Password|none|

<h2 id="tocS_User">User</h2>

<a id="schemauser"></a>
<a id="schema_User"></a>
<a id="tocSuser"></a>
<a id="tocsuser"></a>

```json
{
  "username": "string",
  "email": "string",
  "full_name": "string",
  "permission_level": 0
}

```

User

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|username|string|true|none|Username|none|
|email|string|false|none|Email|none|
|full_name|string|false|none|Full Name|none|
|permission_level|integer|true|none|Permission Level|none|

<h2 id="tocS_Token">Token</h2>

<a id="schematoken"></a>
<a id="schema_Token"></a>
<a id="tocStoken"></a>
<a id="tocstoken"></a>

```json
{
  "access_token": "string",
  "token_type": "string"
}

```

Token

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|access_token|string|true|none|Access Token|none|
|token_type|string|true|none|Token Type|none|

<h2 id="tocS_StreamVideo">StreamVideo</h2>

<a id="schemastreamvideo"></a>
<a id="schema_StreamVideo"></a>
<a id="tocSstreamvideo"></a>
<a id="tocsstreamvideo"></a>

```json
{
  "codec": "string",
  "profile": "string",
  "level": "string",
  "width": 0,
  "height": 0
}

```

StreamVideo

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|codec|string|true|none|Codec|none|
|profile|string|true|none|Profile|none|
|level|string|true|none|Level|none|
|width|integer|true|none|Width|none|
|height|integer|true|none|Height|none|

<h2 id="tocS_StreamAudio">StreamAudio</h2>

<a id="schemastreamaudio"></a>
<a id="schema_StreamAudio"></a>
<a id="tocSstreamaudio"></a>
<a id="tocsstreamaudio"></a>

```json
{
  "codec": "string",
  "sample_rate": 0,
  "channel": 0,
  "profile": "string"
}

```

StreamAudio

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|codec|string|true|none|Codec|none|
|sample_rate|integer|true|none|Sample Rate|none|
|channel|integer|true|none|Channel|none|
|profile|string|true|none|Profile|none|

<h2 id="tocS_ResponseStream">ResponseStream</h2>

<a id="schemaresponsestream"></a>
<a id="schema_ResponseStream"></a>
<a id="tocSresponsestream"></a>
<a id="tocsresponsestream"></a>

```json
{
  "name": "string",
  "play_url": "string",
  "kbps": {},
  "video": {
    "codec": "string",
    "profile": "string",
    "level": "string",
    "width": 0,
    "height": 0
  },
  "audio": {
    "codec": "string",
    "sample_rate": 0,
    "channel": 0,
    "profile": "string"
  },
  "clients": 0
}

```

ResponseStream

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|name|string|true|none|Name|none|
|play_url|string|true|none|Play Url|none|
|kbps|object|true|none|Kbps|none|
|video|[StreamVideo](#schemastreamvideo)|true|none||none|
|audio|[StreamAudio](#schemastreamaudio)|true|none||none|
|clients|integer|true|none|Clients|none|

<h2 id="tocS_LiveToken">LiveToken</h2>

<a id="schemalivetoken"></a>
<a id="schema_LiveToken"></a>
<a id="tocSlivetoken"></a>
<a id="tocslivetoken"></a>

```json
{
  "username": "string",
  "stream": "string",
  "token": "string",
  "play_token": "string",
  "permissions_level": 0
}

```

LiveToken

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|username|string|true|none|Username|none|
|stream|string|true|none|Stream|none|
|token|string|true|none|Token|none|
|play_token|string|true|none|Play Token|none|
|permissions_level|integer|true|none|Permissions Level|none|

<h2 id="tocS_LiveStreamResponse">LiveStreamResponse</h2>

<a id="schemalivestreamresponse"></a>
<a id="schema_LiveStreamResponse"></a>
<a id="tocSlivestreamresponse"></a>
<a id="tocslivestreamresponse"></a>

```json
{
  "code": 0,
  "streams": [
    {
      "name": "string",
      "play_url": "string",
      "kbps": {},
      "video": {
        "codec": "string",
        "profile": "string",
        "level": "string",
        "width": 0,
        "height": 0
      },
      "audio": {
        "codec": "string",
        "sample_rate": 0,
        "channel": 0,
        "profile": "string"
      },
      "clients": 0
    }
  ]
}

```

LiveStreamResponse

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|code|integer|true|none|Code|none|
|streams|[[ResponseStream](#schemaresponsestream)]|true|none|Streams|none|

<h2 id="tocS_LiveStreamCallback">LiveStreamCallback</h2>

<a id="schemalivestreamcallback"></a>
<a id="schema_LiveStreamCallback"></a>
<a id="tocSlivestreamcallback"></a>
<a id="tocslivestreamcallback"></a>

```json
{
  "server_id": "string",
  "action": "string",
  "client_id": "string",
  "ip": "string",
  "vhost": "string",
  "app": "string",
  "tcUrl": "string",
  "stream": "string",
  "param": "string",
  "stream_url": "string",
  "stream_id": "string"
}

```

LiveStreamCallback

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|server_id|string|true|none|Server Id|none|
|action|string|true|none|Action|none|
|client_id|string|true|none|Client Id|none|
|ip|string|true|none|Ip|none|
|vhost|string|true|none|Vhost|none|
|app|string|true|none|App|none|
|tcUrl|string|true|none|Tcurl|none|
|stream|string|true|none|Stream|none|
|param|string|true|none|Param|none|
|stream_url|string|true|none|Stream Url|none|
|stream_id|string|true|none|Stream Id|none|

<h2 id="tocS_HTTPValidationError">HTTPValidationError</h2>

<a id="schemahttpvalidationerror"></a>
<a id="schema_HTTPValidationError"></a>
<a id="tocShttpvalidationerror"></a>
<a id="tocshttpvalidationerror"></a>

```json
{
  "detail": [
    {
      "loc": [
        "string"
      ],
      "msg": "string",
      "type": "string"
    }
  ]
}

```

HTTPValidationError

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|detail|[[ValidationError](#schemavalidationerror)]|false|none|Detail|none|

<h2 id="tocS_DvrCallback">DvrCallback</h2>

<a id="schemadvrcallback"></a>
<a id="schema_DvrCallback"></a>
<a id="tocSdvrcallback"></a>
<a id="tocsdvrcallback"></a>

```json
{
  "action": "string",
  "client_id": "string",
  "ip": "string",
  "vhost": "string",
  "app": "string",
  "stream": "string",
  "param": "string",
  "cwd": "string",
  "file": "string",
  "server_id": "string",
  "stream_url": "string",
  "stream_id": "string"
}

```

DvrCallback

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|action|string|true|none|Action|none|
|client_id|string|true|none|Client Id|none|
|ip|string|true|none|Ip|none|
|vhost|string|true|none|Vhost|none|
|app|string|true|none|App|none|
|stream|string|true|none|Stream|none|
|param|string|true|none|Param|none|
|cwd|string|true|none|Cwd|none|
|file|string|true|none|File|none|
|server_id|string|true|none|Server Id|none|
|stream_url|string|true|none|Stream Url|none|
|stream_id|string|true|none|Stream Id|none|

<h2 id="tocS_Body_login_for_access_token_auth_token_post">Body_login_for_access_token_auth_token_post</h2>

<a id="schemabody_login_for_access_token_auth_token_post"></a>
<a id="schema_Body_login_for_access_token_auth_token_post"></a>
<a id="tocSbody_login_for_access_token_auth_token_post"></a>
<a id="tocsbody_login_for_access_token_auth_token_post"></a>

```json
{
  "grant_type": "string",
  "username": "string",
  "password": "string",
  "scope": "",
  "client_id": "string",
  "client_secret": "string"
}

```

Body_login_for_access_token_auth_token_post

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|grant_type|string(string)|false|none|Grant Type|none|
|username|string(string)|true|none|Username|none|
|password|string(string)|true|none|Password|none|
|scope|string(string)|false|none|Scope|none|
|client_id|string(string)|false|none|Client Id|none|
|client_secret|string(string)|false|none|Client Secret|none|

