> # CSS

## CSS의 개념

- Cascading Style Sheets

- 스타일을 지정하기 위한 언어
  
  -> 선택하고, 스타일을 지정한다 ('선택자')

- CSS 구문은 선택자를 통해 스타일 지정할 HTML 요소를 선택

- 중괄호 안에는 속성과 값, 하나의 쌍으로 이루어진 선언을 진행

- 각 쌍은 선택한 요소의 속성, 속성에 부여할 값을 의미
  
  - 속성(Property) : 어떤 스타일 기능을 변경할 지 결정
  
  - 값(Value) : 어떻게 스타일 기능을 변경할 지 결정

### CSS 정의 방법

- 인라인(inline)
  
  - 해당 태그에 직접 style 속성을 활용

- 내부참조(embedding)
  
  - `<head>` 태그 내에 `<style>` 에 지정

- 외부참조(link file)
  
  - 외부 css 파일을 `<head>` 내 `<link>` 태그로 가지고옴

### CSS with 개발자 도구

- styles : 해당 요소에 선언된 모든 css

- computed : 해당 요소에 최종 계산된 css (margin..)

---

## CSS Selectors

### 선택자(Selector)유형

- 기본 선택자
  
  - 전체 선택자, 요소 선택자
  
  - 클래스 선택자, 아이디 선택자, 속성 선택자

- 결합자(Combinators)
  
  - 자손 결합자, 자식 결합자
  - 일반 형제 결합자, 인접 형제 결합자

- 의사 클래스/요소(Pseudo Class)
  
  - 링크, 동적 의사 클래스
  
  - 구조적 의사 클래스, 기타 의사 클래스, 의사 엘리먼트, 속성 선택자

### CSS 선택자 정리

- 요소 선택자
  
  - HTML 태그를 직접 선택

- 클래스(class) 선택자
  
  - 마침표(.) 문자로 시작하며, 해당 클래스가 적용된 항목을 선택

- 아이디(id) 선택자
  
  - (#) 문자로 시작하며, 해당 아이디가 적용된 항목을 선택
  
  - 일반적으로 하나의 문서에 1번만 사용
  
  - 여러번 사용해도 동작하지만, 단일 id를 사용하는 것을 권장

### CSS 적용 우선순위(cascading order)

- CSS 우선순위
  1. 중요도 (Importance) - 사용시 주의!
     - `!important`
  2. 우선 순위 (Specificity)
     - 인라인 > id > class, 속성, pseudo-class > 요소, pseudo-element
  3. CSS 파일 로딩 순서

### CSS 상속

- 상속을 통해 부모 요소의 속성을 자식에게 상속한다.
  
  - 속성(Property) 중에는 상속이 되는 것과 되지 않는 것들이 있다.
  
  - 상속이 되는 것
    
    - Text관련 요소 : font, color, text-align..
    
    - opacity, visibility 등
  
  - 상속이 되지 않는 것
    
    - Box model 관련 요소 : width, height, margin, padding, border, box-sizing, display
    
    - position 관련 요소 : position, top/right/bottom/left, z-index 등..

---

## Selectors 심화

### 결합자(Combinators)

- 자손 결합자 vs 자식 결합자
  
  - 자손 결합자(공백)
    
    - selectorA 하위의 모든 selectorB 요소
  
  - 자식 결합자(>)
    
    - selectorA 바로 아래의 selectorB 요소

- 일반 형제 결합자 vs 인접 형제 결합자
  
  - 일반 형제 결합자(~)
    
    - selectorA의 형제 요소 중 뒤에 위치하는 selectorB 요소를 모두 선택
  
  - 인접 형제 결합자(+)
    
    - selecotrA의 형제 요소 중 바로 뒤에 위치하는 selecotrB 요소를 선택(1개만 선택)

---

## CSS 기본 스타일

### 크기 단위

- px (픽셀)
  
  - 모니터 해상도의 한 화소인 ‘픽셀’ 기준
  
  - 픽셀의 크기는 변하지 않기 때문에 고정적인 단위

- %
  
  - 백분율 단위
  
  - 가변적인 레이아웃에서 주로 사용

- em
  
  - (바로 위, 부모 요소에 대한) 상속의 영향을 받음
  
  - 배수 단위, 요소에 지정된 사이즈에 상대적인 사이즈를 가짐

- rem
  
  - (바로 위, 부모 요소에 대한) 상속의 영향을 받지 않음
  
  - 최상위 요소(html)의 사이즈를 기준으로 배수 단위를 가짐

### 크기 단위 (viewport)

- 웹 페이지를 방문한 유저에게 바로 보이게 되는 웹 컨텐츠의 영역 (디바이스 화면)

- 디바이스의 viewport를 기준으로 상대적인 사이즈가 결정됨

- vw, vh, vmin, vmax

- px는 브라우저의 크기를 변경해도 그대로

- vw는 브라우저의 크기에 따라 크기가 변함

### 색상 단위

- 색상 키워드 (`background-color: red;`)
  
  - 대소문자를 구분하지 않음
  
  - red, blue, black과 같은 특정 색을 직접 글자로 나타냄

- RGB 색상 (`background-color: rgb(0, 225, 0);`)
  
  - 16진수 표기법 혹은 함수형 표기법을 사용해서 특정 색을 표현하는 방식
  
  - `#` + 16진수 표기법
  
  - rgb() 함수형 표기법

- HSL 색상(`background-color: hsl(0, 100%, 50%);`)
  
  - 색상, 채도, 명도를 통해 특정 색을 표현하는 방식

- a는 alpha (투명도)

### CSS 문서 표현

- 텍스트
  
  - 서체(font-family), 서체 스타일(font-style, font-weight 등)
  
  - 자간(letter-spacing), 단어 간격(word-spacing), 행간(line-height) 등

- 컬러(color), 배경(background-image, background-color)

- 기타 HTML 태그별 스타일링
  
  - 목록(li), 표(table)

---

## CSS Box model

### CSS 원칙 I

- 모든 요소는 **네모(박스모델)** 이고

- 위에서부터 아래로, 왼쪽에서 오른쪽으로 **‘쌓여간다’**

- **좌측 상단에 배치**
  
  - 좌→우 쌓이는 것 : Inline 요소
  
  - 위→아래 쌓이는 것 : Block 요소



### Box model

- 모든 HTML 요소는 box 형태로 되어있음.

- 하나의 박스는 네 부분(영역)으로 이루어짐
  
  - margin : 외부 여백(배경색 지정x)
  
  - border : 테두리
  
  - padding : 내부 여백
  
  - content : 실제 내용 (글, 이미지 등)

- 컨텐츠와 테두리 사이 : 내부 여백



### Box model 구성(margin)

```css
.margin {
    margin-top: 10px;
    margin-right: 20px;
    margin-bottom: 30px;
    margin-left: 40px;
}
```



### Box model 구성(padding)

```css
.margin-padding {
    margin: 10px;
    padding: 30px;
}
```



### Box model 구성(border)

```css
.border {
    border-width: 2px;
    border-style: dashed;
    border-color: black;
}

.border {
    border: 2px dashed black;
}
```



### Box model 구성(margin/padding) - shorthand

- margin과 padding은 shorthand로 줄 수 있다.

- 갯수에 따른 적용 범위가 다르다.
  
  - `margin: 10px;` : 상하좌우 모두 10px
  
  - `margin: 10px 20px 30px 40px;` : 상 10px, 우 20px, 하 30px, 좌 40px
  
  - `margin: 10px 20px;` : 상하 10px, 좌우 20px
  
  - `margin: 10px 20px 30px;` : 상 10px, 좌우 20px, 하 30px
