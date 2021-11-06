# 타임리프 - 기본기능
- 공식 사이트 : https://www.thymeleaf.org/

## 타임리프 특징
- 서버 사이트 HTML 렌더링 (SSR)
  - 타임리프는 백엔드 서버에서 HTML을 동적으로 렌더링 하는 용도로 사용
- 네츄럴 템플릿
  - 타임리프는 순수 HTML을 최대한 유지하는 특징을 가짐
  - 타임리프로 작성한 파일은 웹 브라우저에서 파일을 직접 열어도 내용을 확인할 수 있으며, 서버를 통해 뷰템플릿을 거치면 동적으로 변경된 결과 확인 가능
  - JSP로 작성된 파일은 웹브라우저에서 열어보면 JSP코드 + HTML이 뒤죽박죽 섞여서 정상적인 HTML결과를 확인할 수 없음, 오직 서버를 통해 JSP가 렌더링되고 HTML응답 결과를 받아야 확인가능
  - 타임리프로 작성한 파일은 웹브라우저에서 열어보면 정상적인 HTML 결과를 확인할 수 있음 (물론 동적 결과 렌더링 X)
  - **순수 HTML을 그대로 유지하면서 뷰 템플릿도 사용할 수 있는 타임리프의 특징 == 네츄럴 템플릿(natural templates)**
- 스프링 통합 지원
  - 타임리프는 스프링과 자연스럽게 통합 되며, 스프링의 다양한 기능을 편리하게 사용할 수 있게 지원함  

## 타임리프 기본 기능
### 타임리프 사용 선언
```html
<html xmlns:th="http://www.thymeleaf.org"></html>
```

### 기본 표현식
#### 텍스트 - text, utext
html 콘텐츠에 데이터 출력 시
```html
<span th:text="${data}">
```
html 태그 속성이 아닌, 콘텐츠 영역안에서 직접 데이터 출력 시
```html
[[${data}]]
```
> **BasicController**
```java
@GetMapping("/text-basic")
    public String textBasic(Model model){
        model.addAttribute("data", "Hello <b>Spring!</b>");
        return "basic/text-basic";
    }
 ```
 >**text-basic.html**
 ```html
 <!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<h1>컨텐츠에 데이터 출력하기</h1>
<ul>
    <li>th:text 사용 <span th:text="${data}"></span></li>
    <li>컨텐츠 안에서 직접 출력하기 = [[${data}]]</li>
</ul>
</body>
</html>
 ```

    
