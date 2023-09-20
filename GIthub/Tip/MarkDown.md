#  마크다운 markdown 작성법

> "Markdown Guide ([https://www.markdownguide.org/](https://www.markdownguide.org/))" 

# [](https://ko.wikipedia.org/wiki/%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4)1. 마크다운 

## [](https://ko.wikipedia.org/wiki/%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4)1.1. 마크다운이란?

**마크다운**(Markdown)은 [일반 텍스트](https://ko.wikipedia.org/wiki/%ED%94%8C%EB%A0%88%EC%9D%B8_%ED%85%8D%EC%8A%A4%ED%8A%B8 "플레인 텍스트") 기반의 경량 [마크업 언어](https://ko.wikipedia.org/wiki/%EB%A7%88%ED%81%AC%EC%97%85_%EC%96%B8%EC%96%B4 "마크업 언어")다. 일반 텍스트로 서식이 있는 문서를 작성하는 데 사용되며, 일반 마크업 언어에 비해 문법이 쉽고 간단한 것이 특징이다. [HTML](https://ko.wikipedia.org/wiki/HTML "HTML")과 [리치 텍스트](https://ko.wikipedia.org/wiki/%EB%A6%AC%EC%B9%98_%ED%85%8D%EC%8A%A4%ED%8A%B8 "리치 텍스트")(RTF) 등 서식 문서로 쉽게 변환되기 때문에 [응용 소프트웨어](https://ko.wikipedia.org/wiki/%EC%9D%91%EC%9A%A9_%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4 "응용 소프트웨어")와 함께 배포되는 [README 파일](https://ko.wikipedia.org/wiki/%EB%A6%AC%EB%93%9C%EB%AF%B8 "리드미")이나 온라인 게시물 등에 많이 사용된다.

[존 그루버](https://ko.wikipedia.org/w/index.php?title=%EC%A1%B4_%EA%B7%B8%EB%A3%A8%EB%B2%84&action=edit&redlink=1 "존 그루버 (없는 문서)")는 2004년에 문법 면에서 [에런 스워츠](https://ko.wikipedia.org/wiki/%EC%97%90%EB%9F%B0_%EC%8A%A4%EC%9B%8C%EC%B8%A0 "에런 스워츠")와 중대한 협업을 통해 마크다운 언어를 만들었으며[[3]](https://ko.wikipedia.org/wiki/%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4#cite_note-markdown_swartz-3)[[5]](https://ko.wikipedia.org/wiki/%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4#cite_note-gruber-2004-release-5), 사람들이 읽기 쉽고 쓰기 쉬운 플레인 텍스트 포맷을 사용하여 쓸 수 있으면서 구조적으로 유효한 [XHTML](https://ko.wikipedia.org/wiki/XHTML "XHTML")(또는 HTML)로 선택적 변환이 가능하게 하는 것이 목표이다.[[6]](https://ko.wikipedia.org/wiki/%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4#cite_note-md-6)

## [](https://gist.github.com/ihoneymon/652be052a0727ad59601#12-%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4%EC%9D%98-%EC%9E%A5-%EB%8B%A8%EC%A0%90)1.2. 마크다운 장점

### 1.2.1. 장점

```
1. 간결하다.
2. 별도의 도구없이 작성가능하다.
3. 다양한 형태로 변환이 가능하다.
4. 텍스트(Text)로 저장되기 때문에 용량이 적어 보관이 용이하다.
5. 텍스트파일이기 때문에 버전관리시스템을 이용하여 변경이력을 관리할 수 있다.
6. 지원하는 프로그램과 플랫폼이 다양하다.
```

---

# [2. 마크다운 사용법(문법)](https://www.markdownguide.org/)

## [2.1. Heading](https://www.markdownguide.org/)


```
    H1
    =============    
```



# [](https://www.markdownguide.org/cheat-sheet/)H1

## [](https://www.markdownguide.org/cheat-sheet/)H2

### [](https://www.markdownguide.org/cheat-sheet/)H3

#### [](https://www.markdownguide.org/cheat-sheet/)H4

##### [](https://www.markdownguide.org/cheat-sheet/)H5

###### [](https://www.markdownguide.org/cheat-sheet/)H6


## [2.2. Bold](https://www.markdownguide.org/cheat-sheet/) 


```
	Bold체로 변경 :  **  //글자를 입력  ** 
```
 

 bold Text   : 기본 글씨체
 **bold Text** : **Bold 글씨체**

___
## [2.3. Italic](https://www.markdownguide.org/cheat-sheet/) 
```
	Italic체로 변경 :  *//글자를 입력* 
```
 

 Italic Text   : 기본 글씨체
 *Italic Text* : *Italic 글씨체*


## [2.4. BlockQuote](https://www.markdownguide.org/cheat-sheet/)

 `>` 블럭 인용문자 이용한다.

```
> This is a blockqute.
>	> This is a blockqute.
>	>	> This is a blockqute.
```

> This is a blockqute.
> 
> > This is a blockqute.
> > 
> > > This is a blockqute.

BlockQuote 안에서 다른 문법이 사용 가능하다. 

> ### H3
> 
> - List
>     
>     ```
>     code
>     ```
>      

## 2.5. List

### ● Ordered List(숫자)

[Ordered List](https://www.markdownguide.org/basic-syntax/#ordered-lists) 
```
1. First item  
2. Second item  
3. Third item
```

1. First item  
2. Second item  
3. Third item

**입력한 번호에서 내림차순으로 정의된다.**

```
5. 첫번째
6. 세번째
7. 두번째
```

1. First item
2. Second item  
3. Third item

### ● [Unordered List](https://www.markdownguide.org/basic-syntax/#unordered-lists) (글머리 기호: `*`, `+`, `-` 지원)

```
* First item
  * Second item
    * Third item

+ First item
  + Second item
    + Third item

- First item
  - Second item
    - Third item
```

* First item
  * Second item
    * Third item

+ First item
  + Second item
    + Third item

- First item
  - Second item
    - Third item

혼합 사용이 가능하다 그렇지만 겉보기는 똑같다. (Obsidian 기준) 

```
* First item
  - Second item
    + Third item
      + Fourth item
```

* First item
	- Second item
	    + Third item
		 * Fourth item

## [](https://gist.github.com/ihoneymon/652be052a0727ad59601#24-%EC%BD%94%EB%93%9C)2.6. Code

4개의 공백 또는 탭 한 번의 들여쓰기에서 없을 때 까지 지속


### 2.6.1. Code Blocks


```
단어는 역따옴표 (`)로 묶습니다.
```
To denote a word or phrase as code, enclose it in backticks (`` ` ``)`

```
하나 이상 포함된 단어는 (``) 두번의 역따옴표로 묶습니다.
```

```
줄은 (```) 세 번의 역따옴표로 묶습니다.
```

```
<html>
	<head>
	</head>
</html>
```

html
	head
	head
html

---
### 2.6.1.1. 사용 예시  

```
- ``` 을 이용하는 예시 입니다.
```

 
````
```kotlin
	fun main(){   
		Text("Hello, World");
	}
```
````

```kotlin
	fun main(){   
		Text("Hello, World");
	}
```


## 2.7. ## Horizontal Rules[](https://www.markdownguide.org/basic-syntax/#horizontal-rules) `<hr/>`

아래 줄은 모두 수평선을 만든다. 마크다운 문서를 미리보기로 출력할 때 _페이지 나누기_ 용도로 많이 사용한다.

```
* * *

***

*****

- - -

---------------------------------------
```

- 예시 

---

***

******

- - -

-----------------------------------

## [](https://gist.github.com/ihoneymon/652be052a0727ad59601#26-%EB%A7%81%ED%81%AC)2.8. [Link](https://www.markdownguide.org/basic-syntax/#links)

- ### Adding Titles

```
My favorite search engine is [Duck Duck Go](https://duckduckgo.com)

My favorite search engine is [Duck Duck Go](https://duckduckgo.com "The best search engine for privacy").
```
My favorite search engine is [Duck Duck Go](https://duckduckgo.com)

My favorite search engine is [Duck Duck Go](https://duckduckgo.com "The best search engine for privacy").
<br>
- ### Formatting Link
<br>
```
I love supporting the **[EFF](https://eff.org)**.
This is the *[Markdown Guide](https://www.markdownguide.org)*.
See the section on [`code`](#code).

```
<br>
I love supporting the **[EFF](https://eff.org)**.
This is the *[Markdown Guide](https://www.markdownguide.org)*.
See the section on [`code`](#code).
<br>

-  URLs and Email Addresses

```
* <https://www.markdownguide.org>
* <fake@example.com>
```
<https://www.markdownguide.org>
<fake@example.com>


## [](https://gist.github.com/ihoneymon/652be052a0727ad59601#28-%EC%9D%B4%EB%AF%B8%EC%A7%80)2.9. 이미지

```
![Alt text](/path/to/img.jpg)
![Alt text](/path/to/img.jpg "Optional title")
```

![pixa bay](https://cdn.pixabay.com/photo/2023/09/04/06/59/dog-8232158_1280.jpg)

 `<img width="" height=""></img>`를 사용해야 한다.


```
<img src="path" width="px" height="px" title="" alt="alt">
<img src="path" width="%" height="%" title="" alt="alt">
```

![pixa bay](https://cdn.pixabay.com/photo/2023/09/04/06/59/dog-8232158_1280.jpg)<br>
<img src="https://cdn.pixabay.com/photo/2023/09/04/06/59/dog-8232158_1280.jpg" width="450px" height="300px" title="예시용사진" alt="TestPicture"/>
<br>
## 강조 
```
*single asterisks*
_single underscores_
**double asterisks**
__double underscores__
~~cancelline~~
==Highlight==
<mark>Highlight<mark/>
```

- _single asterisks_
- _single underscores_
- **double asterisks**
- **double underscores**
- ~~cancelline~~
* ==Highlight==
* <mark>Highlight</mark>
<br>
## Subscript (아래 첨자)
```
H~2~O (안될 수 도 있음)
HTML 지원 시 
H<sub>2</sub>O
```
  
* H<sub>2</sub>O

---
<br>
* ## 윗 첨자 
```
H^2^O (안될 수 도 있음)
HTML 지원 시 
H<sup>2</sup>O
```

* X<sup>2</sup>P```
