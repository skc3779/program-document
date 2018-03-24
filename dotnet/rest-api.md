## C# REST 프로그램

#### RestSharp - Simple .NET REST Client

> https://github.com/restsharp/RestSharp


#### ASP.NET Web API Tutorials:

* ASP.NET Web API Tutorials:
    > http://www.tutorialsteacher.com/webapi/web-api-tutorials


* ASP.NET Web API 및 Angular.js 단일 페이지 응용 프로그램 (SPA)을 작성 하는 실습 랩:   
    > https://docs.microsoft.com/ko-kr/aspnet/web-api/overview/getting-started-with-aspnet-web-api/build-a-single-page-application-spa-with-aspnet-web-api-and-angularjs#Exercise1
    

* ASP.NET 클라이언트 사이드 디버그 방법
    > https://blogs.msdn.microsoft.com/webdev/2016/11/21/client-side-debugging-of-asp-net-projects-in-google-chrome/

* Visual Studio를 사용하여 Razor 페이지 및 Entity Framework Core 시작(1/8)
    > https://docs.microsoft.com/ko-kr/aspnet/core/data/ef-rp/intro

* Entity Framework 개요
    > https://msdn.microsoft.com/ko-kr/library/bb399567(v=vs.110).aspx


#### EdmGen.exe 사용방법

* cmd.exe 실행

    ```
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration /c:"Server=192.168.0.131;Database=demo_school;User Id=sa;Password=_ekfrekfl99!!;" /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp
    ```

### EF Core

* EF Core & EF6 비교
    > https://docs.microsoft.com/ko-kr/ef/efcore-and-ef6/index

### .NET Framework에서 새 데이터베이스로 EF Core 시작

* 클래스로 데이터베이스 만들기
    https://docs.microsoft.com/ko-kr/ef/core/get-started/full-dotnet/new-db


### 모델 리버스 엔지니어링

```
Scaffold-DbContext "Server=(localdb)\MSSQLLocalDB;Database=demo_Blogs;Trusted_Connection=True" Microsoft.EntityFrameworkCore.SqlServer    
```

### Razor 페이지 프로젝트 만들기
> https://docs.microsoft.com/ko-kr/aspnet/core/mvc/views/razor#razor-syntax


### Swagger를 사용한 ASP.NET Core Web API 도움말 페이지
> https://docs.microsoft.com/ko-kr/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio    

* Swagger UI GitHub 리포지토리에서 dist 폴더의 콘텐츠를 가져옵니다
    > https://github.com/swagger-api/swagger-ui

* Swaggerhub 사이트
    > Join with github ID.    
    > https://app.swaggerhub.com

* scaffolding
    > Program.cs, Startup.cs 및 .csproj 파일이 포함된 프로젝트 디렉터리에서    
    ```
    $> dotnet aspnet-codegenerator razorpage -m Movie -dc MovieContext -udl -outDir Pages\Movies --referenceScriptLibraries
    ```
    > 다음 표에서는 ASP.NET Core 코드 생성기의 매개 변수를 자세히 설명합니다.
    ```
    -m	    모델의 이름입니다.
    -dc	    데이터 컨텍스트입니다.
    -udl	기본 레이아웃을 사용합니다.
    -outDir	뷰를 만들기 위한 상태 출력 폴더 경로입니다.
    --referenceScriptLibraries	편집 및 만들기 페이지에 _ValidationScriptsPartial을 추가합니다.
    ```

* ASP.NET Core를 사용하여 Razor 페이지 웹앱 만들기
    https://docs.microsoft.com/ko-kr/aspnet/core/tutorials/razor-pages/    

* Visual Studio Code
    https://code.visualstudio.com/shortcuts/keyboard-shortcuts-macos.pdf    

* Setting up Visual Studio Code
    * [mac](https://code.visualstudio.com/docs/setup/mac)
    * [linux](https://code.visualstudio.com/docs/setup/linux)
    * [windows](https://code.visualstudio.com/docs/setup/windows)

    
* EF 도구 추가 및 초기 마이그레이션 수행

도구 메뉴에서 NuGet 패키지 관리자 > 패키지 관리자 콘솔

```
Install-Package Microsoft.EntityFrameworkCore.Tools
Add-Migration Initial
Update-Database
```    

### .NET Core 가이드
> https://docs.microsoft.com/ko-kr/dotnet/core/


### 개인학습
2018-03-16 ASP.NET Core에서 종속성 주입
> https://docs.microsoft.com/ko-kr/aspnet/core/fundamentals/dependency-injection