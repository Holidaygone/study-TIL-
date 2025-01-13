study-TIL-
=============


https://github.com/namjunemy/TIL 배울만한 사람


마크다운 작성법
-------------

* 큰 제목 : =============

* 작은 제목 : -------------

* 글머리 : #, ##, ###... 6개까지 지원

* BlockQuote : >, > 사용

* 순서 있는 목록 : 1. 2. 3. ...

* 순서 없는 목록 : *, +, - 지원

* 코드 1 - 들여쓰기 : 4개의 공백 또는 하나의 탭으로 들여쓰기를 만나면 변환되기 시작하여 
들여쓰지 않은 행을 만날때까지 변환이 계속된다.

* 코드 2 - 코드블럭 : &lt;pre&gt;&lt;code&gt;{code}&lt;/code&gt;&lt;/pre&gt; 이용방식

* 코드 3- 코드블럭코드 : ` ``` ` 를 앞 뒤로 붙이기
깃헙에서는 코드블럭코드() 시작점에 사용하는 언어를 선언하여 문법강조(Syntax highlighting)이 가능
예를 들어 ```java 이렇게 하는 것

* &lt;pre&gt; 같은 것을 문자 그대로 표시하기 위해서는 
    1. HTML 태그 이스케이프 사용
    + `<` → `&lt;` 
    + `>` → `&gt;`

    2. Markdown 인라인 코드 사용
    + 문서 중간에 태그를 짧게 인라인 코드로 기록할 때는 백틱(`)을 사용


* 수평선 : `* * *, *** 또는 ***** 또는 - - -, ---------` 이런 식으로 할 수 있다.

* 참조 링크
```
[link keyword][id]

[id]: URL "Optional Title here"

// code
Link: [Google][googlelink]

[googlelink]: https://google.com "Go google"
```

* 외부 링크
```
사용문법: [Title](link)
  적용예: [Google](https://google.com, "google link")
```

* 강조
```
*single asterisks*
_single underscores_
**double asterisks**
__double underscores__
~~cancelline~~
```
- *single asterisks*
- _single underscores_
- **double asterisks**
- __double underscores__
- ~~cancelline~~

* 줄바꿈 : 3칸 이상 띄어쓰기를 하면 줄이 바뀐다.
