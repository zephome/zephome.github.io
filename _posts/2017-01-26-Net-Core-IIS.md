---
layout:     post
title:      ".NET Core IIS 게시 오류"
subtitle:   ""
date:       2017-01-26 11:53:00
author:     "ZePHomE"
header-img: "img/posts/jekyll-bg.jpg"
comments: false
tags: [ .Net Core, IIS ]
---

ASP.NET Core로 개발할때 로컬에서는 문제없이 디버깅되고 페이지도 잘보이지만 운영 or 개발 IIS 설정할때 오류가 항상 발생되더군요.

자료를 찾아보니 .NET Core는 기존과 다른 방식으로 발생되는 오류였습니다.

### 환경
---
* Visual Studio 2015 Update 3   
* ASP.NET Core


### 오류 내용
---
페이지 접속 시 에러 내용  
HTTP Error 502.5 - Process Failure  
Common causes of this issue:   
* The application process failed to start   
* The application process started but then stopped   
* The application process started but failed to listen on the configured port   


### 해결 방법
---
* 반드시 설치해야하는 프로그램  
  - [Windows Server hosting Bundle](https://docs.microsoft.com/en-us/aspnet/core/publishing/iis#install-the-net-core-windows-server-hosting-bundle)
  - [.NET Core Download LTS](https://www.microsoft.com/net/download/core)
* IIS 설정
  - 응용프로그램 풀에서 .NET Framework 버전을 관리코드 없음으로 선택
* Visual Studio
  - 기존 처럼 빌드가 아닌 게시를 이용하여 빌드 후 생성되는 폴더 (ex: ./Bin/Release/PublishOutput)를 IIS 경로로 설정
* 이벤트 뷰어에서 오류 내용 확인
* Publishing to IIS: https://docs.microsoft.com/en-us/aspnet/core/publishing/iis 에서 해당 오류 검색
* 저의 경우는 이벤트 오류에 에러 코드가 0x80070002로 표시
* 여러 해결 방법이 있지만 저의 경우
  - A 서버: 2번재 방법으로 해결 (환경 변수에 Path에서 dotnet 설치 경로 추가)
  - A, B 서버: 4번째 방법 서비스 재 시작 (net stop was /y, net start w3svc)