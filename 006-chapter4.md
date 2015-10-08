Markup Coding Guide - 4장. 웹 접근성 준수 방법
===

---

[목차로 이동](http://overtimeman.tistory.com/entry/Markup-Coding-Guide)

4. 웹 접근성 준수 방법
---

웹 접근성을 준수하여 마크업하는 방법을 설명한다.

### 4-1. 개요

웹 접근성(Web Accessibility)은 장애인과 비장애인, 운영체제와 브라우저 등 다양한 조건과 환경에 구애받지 않고 모두가 사이트를 이용할 수 있도록 보장하는 것을 말한다.  
모든 사용자들은 정보와 기능에 동등하게 접근하려면 사이트가 올바르게 설계되어 개발되고 편집되어 있어야 한다.  
여기서는 이미 보편화 된 방법에 대한 자세한 내용은 생략한다.

### 4-2. 의미있는 마크업(시멘틱 마크업)

웹 접근성을 준수하기 위해 의미에 맞게 작성된 마크업은 필수라 할 수 있다.  
마크업 시 다음과 같은 규칙을 참고하여 작성하도록 한다.

#### A. 일반 규칙

HTML 작성 시 내용의 의미에 맞는 태그를 사용하여 마크업한다.

#### B. 제목 엘리먼트

- 일반적으로 헤딩 엘리먼트(```<h1>```-```<h6>```)을 사용한다.
- 헤딩 엘리먼트를 사용할 수 없는 경우 ```<strong>``` 대신 ```<em>```을 사용한다.
- 엘리먼트르 생성할 수 없는 경우라면 내용이 될 엘리먼트에 ```aria-label``` 애트리뷰트를 추가한다.

> **[참고]** ```<strong>``` 엘리먼트와 ```<em>``` 엘리먼트의 차이
> 
> HTML5 이전
> : 둘 다 강조하는 내용을 뜻하며, ```<strong>```이 ```<em>```보다 강하다.
>
> HTML5
> : ```<strong>```은 중요성(importance)을 뜻하며, ```<em>```은 강조성(emphasis)을 뜻한다.
> 
> ```html
> <h1>당신이 오늘 해야할 작업</h1>
> <ul>
> 	<li><strong>오븐 끄기!</strong></li>
> 	<li>쓰레기 비우기</li>
> 	<li>빨래하기</li>
> </ul>
> <p>
> 	<em>고양이</em>는 귀여운 동물이다.
> </p>
> ```

#### C. 목록 엘리먼트

목록 엘리먼트 작성 시 목록의 성격에 따라 각기 다른 태그를 사용한다.

- 일반 목록
```html
<h1>메뉴판</h1>
<ul>
	<li>치킨 17,000원</li>
	<li>피자 13,000원</li>
	<li>햄버거 6,000원</li>
</ul>
```
- 순서 목록
```html
<h1>IP 확인방법</h1>
<ol>
	<li>'Windows+R'을 눌러 '실행'창을 엽니다.</li>
	<li>'cmd'를 입력하여 '명령 프롬프트'창을 엽니다.</li>
	<li>'ipconfig'을 입력하여 자신의 IP를 확인합니다.</li>
</ol>

<h1>IP 확인방법</h1>
<ul>
	<li>1. 'Windows+R'을 눌러 '실행'창을 엽니다.</li>
	<li>2. 'cmd'를 입력하여 '명령 프롬프트'창을 엽니다.</li>
	<li>3. 'ipconfig'을 입력하여 자신의 IP를 확인합니다.</li>
</ul>
```
- 정의 목록
```html
<dl>
	<dt>치킨이란?</dt>
	<dd>지방질이 적고 소화흡수가 좋은 단백질이 많으며, 값이 싸고 경제적, 근육 속에 지방이 섞여 있지 않아 맛이 담백하다. '치느님'이라고도 부른다.</dd>
</dl>
```

> **[참고]** 스크린 리더로 읽은 목록 엘리먼트(센스리더 3.0.7.0 기준)
> 
> - ```<ul>```과 ```<ol>```은 스크린 리더로 음성을 출력했을 경우 따로 구분지어 읽지 않는다.
> - 스크린 리더는 스타일의 list-style 속성 값에 따라 목록의 정보를 읽어주지만 W3C가 권장하는 표준이 아니다. 그러나 대부분의 해외 스크린 리더도 동일하므로 무분별한 스타일 list-style:none 사용은 자제하도록 한다.
> - ```<li>``` 내에 순서를 기입할 경우 번호의 중복을 막기 위해 일반 목록(```<ul>```) 태그를 사용한다.

#### D. 표 엘리먼트

HTML5가 아니라도 ```<table>``` 엘리먼트에는 ```summary``` 애트리뷰트를 사용하지 않는다.
헤딩 엘리먼트 등으로 ```<table>```에 대한 제목이 표기되어있을 경우 ```<caption>```으로 표의 제목을 적어줄 필요는 없다.

#### E. 폼 엘리먼트

```<fieldset>```에 대한 별도의 제목 엘리먼트가 제공되어 있을 경우 ```<legend>```로 표의 제목을 적어줄 필요는 없다.  
```<input>```과 같은 폼 입력 엘리먼트에 ```<label>```을 연결할 수 없는 상황이라면 굳이 숨김 처리된 ```<label>```을 제공할 필요는 없으며, ```title``` 애트리뷰트으로 대체한다.

### 4-3. 논리적인 순서의 마크업

마크업의 순서가 논리적이지 못하면 스타일로 화면을 정상적으로 구현하더라도 사용자가 선형화된 문서를 읽거나 키보드로 사용하는데 불편함이 생길 수 있다.  
마크업 시 다음과 같은 규칙을 참고하여 작성하도록 한다.

#### A. 일반 규칙
HTML 작성 시 코드는 내용의 순서를 따라가도록 마크업하며, 부득이하게 순서를 맞출 수 없는 상황이라면 제목이나 다른 방법으로 해당 영역의 의미를 알 수 있도록 한다.

```html
<!-- X -->
<h1>목록</h1>
<ul>
	<li>항목 1</li>
	<li>항목 2</li>
	<li>항목 3</li>
</ul>
<ul>
	<li>항목 2-1</li>
	<li>항목 2-2</li>
</ul>

<!-- △ -->
<h1>목록</h1>
<ul>
	<li>항목 1</li>
	<li>항목 2</li>
	<li>항목 3</li>
</ul>
<h2>목록 > 항목 2</h2>
<ul>
	<li>항목 2-1</li>
	<li>항목 2-2</li>
</ul>

<!-- O -->
<h1>목록</h1>
<ul>
	<li>항목 1</li>
	<li>
		항목 2
		<ul>
			<li>항목 2-1</li>
			<li>항목 2-2</li>
		</ul>
	</li>
	<li>항목 3</li>
</ul>
```

### 4-4. 대체 텍스트 제공

이미지의 내용을 ```<img>``` 또는 ```<area>``` 엘리먼트의 ```alt``` 애트리뷰트에 표기하여, 이미지를 볼 수 없는 환경에서도 내용을 확인할 수 있게 한다.

#### A. 일반 규칙
- 이미지 사용 시 항상 대체 텍스트를 제공하도록 한다.
```html
<img src=".." alt="내용">
```
- 의미가 없는, 또는 배경으로 img 엘리먼트를 사용할 경우 대체 텍스트는 빈 값으로 제공한다.
```html
<img src=".." alt="">
```
- 이미지의 alt 애트리뷰트 가이드는 W3C에서 제공하는 아래 URL을 확인한다.  
[http://www.w3.org/TR/html-alt-techniques/](http://www.w3.org/TR/html-alt-techniques/)

### 4-5. 스킵 네비게이션 제공

문서의 최상단에 서비스의 섹션별 바로가기를 제공하여 스크린 리더 사용 시 서비스 전체에 공통으로 사용되는 컨텐츠를 생략할 수 있도록 한다.

#### A. 일반 규칙

스킵 네비게이션은 body 엘리먼트 내부에서 스크린 리더가 가장 처음으로 읽을 수 있는 위치에 작성한다.

```html
...
<body>
<div id="wrap">
<div id="sknv">
	<a href="#content">본문 바로가기</a>
</div>
...
	<div id="content">
		...
	</div>
</body>
```

### 4-6. 키보드 접근성 보장

마우스를 사용할 수 없는 환경에서 웹을 이용할 수 있도록 제작하기 위해서는 키보드 접근성이 반드시 보장되어야 한다.  
그러므로 JavaScript 등을 이용한 마우스 이벤트 핸들러 사용 시 키보드 사용자를 위한 별도의 대응이 필요하다.

[이전](http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Chapter3) [다음](http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Chapter5) [목차](http://overtimeman.tistory.com/entry/Markup-Coding-Guide)  