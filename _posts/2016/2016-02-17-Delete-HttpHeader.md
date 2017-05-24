---
layout:     post
title:      "HTTP Header 정보 삭제"
subtitle:   ""
date:       2016-02-17 14:28:00
author:     "ZePHomE"
header-img: "img/posts/jekyll-bg.jpg"
comments: false
tags: [ ASP.NET, IIS ]
---

Fiddler, 크롬 개발자 도구를 사용하면 해당 사이트의 헤더 정보에 불필요한 정보를 삭제할 수 있습니다.  
삭제할 헤더 정보
- Server
- X-Powered-By
- X-AspNet-Version

```cs
// X-AspNet-Version (Web.config)
<HttpRuntime enableVersionHeader="false" />

// X-Powered-By
// IIS > 해당 사이트 > HTTP 응답 헤더 > X-Powered-By 삭제

// Server
Response.Remove("Server");    // 삭제
Response.Set("Server", "::ZePHomE BLOG::");  // 생성
```