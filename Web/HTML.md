### HTML

- html : 문서의 최상위(root) 요소
- head : 문서 메타데이터 요소
  - 문서 제목, 인코딩, 스타일, 외부 파일 로딩 등
  - 일반적으로 브라우저에 나타나지 않는 내용
  - 예시
    - <title>: 브라우저 상단 타이틀
    - <meta>: 문서 레벨 메타데이터 요소
    - <link>: 외부 리소스 연결 요소(CSS 파일, favicon 등)
    - <scrpit>: 스크립트 요소(JavaScrpit 파일/코드)
    - <style>: CSS 직접 작성
  - Open Graph Protocol
    - 메타 데이터를 표현하는 새로운 규약
    - HTML 문서의 메타 데이터를 통해 문서의 정보를 전달
    - 메타정보에 해당하는 제목, 설명 등을 쓸 수 있도록 정의
    - `<meta property="og:title" content="Google 뉴스">` : og는 카드뉴스 메인?
- body : 문서 본문 요소
  - 실제 화면 구성과 관련된 내용

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UFT-8">
    <title>Document</title>
</head>
<body>

</body>
</html>
```

### 요소(element)

- `<h1>contents</h1>` : HTML의 요소는 태그와 내용(contents)로 구성되어 있다
- HTML 요소는 시작 태그와 종료 태그 그리고 태그 사이에 위치한 내용으로 구성
  - 요소는 태그 컨텐츠(내용)를 감싸는 것으로 그 정보의 성격과 의미를 정의
  - 내용이 없는 태그들도 존재(닫는 태그가 없음)
    - br, hr, img, input, link, meta
- 요소는 중첩(nested)될 수 있음
  - 요소의 중첩을 통해 하나의 문서를 구조화
  - 여는 태그와 닫는 태그의 쌍을 잘 확인해야함
    - 오류를 반환하는 것이 아니고 그냥 레이아웃이 깨진 상태로 출력되기 때문에, 디버깅이 힘들어질 수 있음
- HTML 개발자 도구
  - elements : 해당 요소의 HTML태그

### 속성(attribute)

- `<a href=”<https://google.com>”></a>`
  - href : 속성명
  - [https~.com](http://https~.com) : 속성값
  - 속성 앞뒤로 공백주지 않고, 쌍따옴표를 사용한다.
- 속성을 통해 태그의 부가적인 정보를 설정할 수 있음
- 요소는 속성을 가질 수 있으며, 경로나 크기와 같은 추가적인 정보 제공
- 요소의 시작태그에 작성하여 보통 이름과 값이 하나의 쌍으로 존재
- 태그와 상관없이 사용 가능한 속성(HTML Global Attribute)들도 있음
