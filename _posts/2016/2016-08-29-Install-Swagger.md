---
layout:     post
title:      "ASP.NET Swagger 설치"
subtitle:   ""
date:       2016-08-29 16:42:00
author:     "ZePHomE"
header-img: "img/posts/jekyll-bg.jpg"
comments: false
tags: [ Swagger ]
---

[공식 홈페이지](http://swagger.io/)

Visual Studio에서 WEB API 프로젝트 생성 후 Nuget에서 [swashbuckle](https://github.com/domaindrivendev/Swashbuckle) 설치

> ASP.NET Core  
> [ASP.NET Web API Help Pages using Swagger](https://docs.microsoft.com/en-us/aspnet/core/tutorials/web-api-help-pages-using-swagger)  
> [참고사이트](http://www.talkingdotnet.com/add-swagger-to-asp-net-core-web-api/)

설치 후 http://도메인/swagger/ui로 접속하시면 생성하신 API 리스트가 자동으로 표시 되지만 아래 이미지의 빨간색 박스 부분은 표시가 되지 않습니다.

![swagger-capture](/img/posts/swagger_01.png)

### C# XML Comments를 이용하여 API Description과 Implementation Notes 표시
---

참고사이트
- [Github Issue](https://github.com/domaindrivendev/Swashbuckle/issues/258)
- [Github Readme](https://github.com/domaindrivendev/Swashbuckle#including-xml-comments)
- [MS Documentation](https://msdn.microsoft.com/en-us/library/b2s063f7(v=vs.110).aspx)

1. FormatXmlCommentProperties.cs
<script src="https://gist.github.com/zephome/e25bb00bc1677b687190942e4454b016.js"></script>

2. /App_Start/SwaggerConfig.cs
<script src="https://gist.github.com/zephome/901ae5a6f3cea1e2ce2ee8d26a9cfa3c.js"></script>

3. Visual Studio 프로젝트 속성 > 빌드 > 하단의 XML 문서 파일 체크 후 bin폴더의 프로젝트명.xml 경로 설정

4. XML Comments 생성 (액션 메서드에서 /// 입력하면 자동 완성)
<script src="https://gist.github.com/zephome/4df17d008034438b887085080c6c93e6.js"></script>

5. 프로젝트 빌드 후 http://도메인/swagger/ui 접속