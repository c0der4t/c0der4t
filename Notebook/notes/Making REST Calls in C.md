---
tags: ['C#']
title: Making REST Calls in C
created: '2021-05-05T13:25:01.349Z'
modified: '2021-05-05T14:57:45.951Z'
---

# Making REST Calls in C#

***
## Using

```
using System;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Text;
```
***
### Pretext

* You must set authentication headers, ONLY if authentication is applicable
* Basic Auth requires a base64 encoded string of format ```username:passowrd```
* You must supply the media/response type. Default is ```application/json```
* An endpoint has to be provided, ex : ```https://www.example.com/api/sales```
***
### Code Snippets

#### Instantiate a top level HttpClient. The client is designed to be re-uised by any method that wants to make calls
```c#
static HttpClient RESTClient = new HttpClient();
```

#### Example Method declaration
```
public static string GET(string Endpoint, string MediaType = "application/json", 
string AuthType = "Basic" , string AuthString = "username:password")
```

#### Setup Authentication for the Http Client

```
#region Authentication
    var BasedString = Convert.ToBase64String(Encoding.ASCII.GetBytes(AuthString));
    RESTClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Basic", BasedString);
#endregion
```

#### Specify the content format we are expecting the reply to be in, default is JSON
```
RESTClient.DefaultRequestHeaders.Accept.Add(new MediaTypeWithQualityHeaderValue(MediaType));
```
