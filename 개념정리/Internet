# Thymeleaf

---

> 미리 정의된 템플릿을 만들고 동적으로 HTML 페이지를 만들어서 클라이언트에 전달하는 방식
요청이 올 때마다 서버에서 새로운 HTML 페이지를 만들어주기 때문에 서버 사이드 렌더링 방식이라고 함
> 

JSP는 서버 사이드 렌더링을 하지 않으면 정상적인 화면 출력 결과를 볼 수 없지만 Thymeleaf 를 사용할 때 Thymeleaf 문법을 포함하고 있는 html 파일을 서버 사이드 렌더링을 하지 않고 브라우저에 띄워도 정상적인 화면을 볼 수 있다.

**Controller**

```java
package com.shop.controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
@RequestMapping("/thymeleaf")
public class ThymeleafExController {

    @GetMapping("/ex01")
    public String thymeleafExample01(Model model) {
        model.addAttribute("data", "타임리프 예제 입니다.");
        return "thymeleafEx/thymeleafEx01";
    }
}

```

- `@RequestMapping("/thymeleaf")` : 클라이언트의 요청에 대해서 어떤 컨트롤러가 처리할지 매핑하는 어노테이션이다. url에 `"/thymeleaf"` 경로로 오는 요청을 ThymeleafExController가 처리하도록 한다.
- `model.addAttribute("data", "타임리프 예제 입니다.")` : model 객체를 이용해 뷰에 전달할 데이터를 key, value 구조로 넣어준다.
- `return "thymeleafEx/thymeleafEx01"` : templates 폴더를 기준으로 뷰의 위치와 이름을 반환한다.
    
    → templates/thymeleafEx/thymeleafEx01.html
    

> **Model**
→ 컨트롤러에서 데이터를 생성해 View에 전달하는 역할을 한다.
→ key, value 구조로 값을 저장한다.
> 

**html**

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <p th:text="${data}">Hello Thymeleaf!</p>
</body>
</html>
```

- `<html xmlns:th="http://www.thymeleaf.org">` : Thymeleaf 문법을 사용하기 위해 추가한다.
- `<p th:text="${data}">Hello Thymeleaf!</p>` : ThymeleafExController의 model의 data라는 key값에 담아준 값을 출력한다. `th:text`는 thymeleaf의 문법이다.

→ 애플리케이션을 실행하면 “*Hello Thymeleaf!”* 대신 “*타임리프 예제 입니다.”* 가 출력된다.

## 1️⃣ th:text

**controller**

```java
@GetMapping("/ex02")
public String thymeleafExample02(Model model) {
    ItemDto itemDto = new ItemDto();

    itemDto.setItemDetail("상품 상세 설명");
    itemDto.setItemNm("테스트 상품1");
    itemDto.setPrice(10000);
    itemDto.setRegTime(LocalDateTime.now());

    model.addAttribute("itemDto", itemDto);
    return "thymeleafEx/thymeleafEx02";
}
```

ItemDto 객체를 생성 후 값을 할당한 다음에 model 객체를 사용하여 itemDto라는 속성으로 ItemDto 객체를 넘겨준다.

**html**

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org" lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <h1>상품 데이터 출력 예제</h1>
    <div>
        상품명 : <span th:text="${itemDto.itemNm}"/>
    </div>
    <div>
        상품 상세 설명 : <span th:text="${itemDto.itemDetail}"/>
    </div>
    <div>
        상품 등록일 : <span th:text="${itemDto.regTime}"/>
    </div>
    <div>
        상품 가격 : <span th:text="${itemDto.price}"/>
    </div>
</body>
</html>
```

위 controller에서 itemDto으로 model 객체가 넘어왔고 출력할 부분에 th:text속성을 사용하여 itemDto의 각 변수를 출력한다.

`th:text="${}"` **{ }**안에 컨트롤러에서 지정한 모델 속성을 입력한다.

## 2️⃣ th:each

**controller**

```java
@GetMapping("/ex03")
public String thymeleafExample03(Model model) {
    List<ItemDto> itemDtoList = new ArrayList<>();

    for(int i = 1; i<=10; i++) {
        ItemDto itemDto = new ItemDto();
        itemDto.setItemNm("상품명" + i);
        itemDto.setItemDetail("상품 상세 설명" + i);
        itemDto.setPrice(10000 + i);
        itemDto.setRegTime(LocalDateTime.now());

        itemDtoList.add(itemDto);
    }

    model.addAttribute("itemDtoList", itemDtoList);
    return "thymeleafEx/thymeleafEx03";
}
```

반복문을 통해 화면에 출력할 10개의 itemDto 객체를 만들어서 itemDtoList에 저장하고 model에 담아서 View에 전달한다.

**html**

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org" lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <h1>상품 리스트 출력 예제</h1>

    <table border="1">
        <thead>
            <tr>
                <td>순번</td>
                <td>상품명</td>
                <td>가격설명</td>
                <td>가격</td>
                <td>상품등록일</td>
            </tr>
        </thead>
        <tbody>
            <tr th:each="itemDto, status: ${itemDtoList}">
                <td th:text="${status.index}"></td>
                <td th:text="${itemDto.itemNm}"></td>
                <td th:text="${itemDto.itemDetail}"></td>
                <td th:text="${itemDto.price}"></td>
                <td th:text="${itemDto.regTime}"></td>
            </tr>
        </tbody>
    </table>
</body>
</html>
```

`th:each`을 이용하면 자바의 for문 처럼 반복문을 사용할 수 있다. 컨트롤러로부터 전달받은 itemDtoList에 있는 데이터를 하나씩 커내서 itemDto에 담는다. status에는 현재 반복에 대한 상태 데이터가 존재한다. 변수명은 status가 아닌 다른 것을 사용해도 된다.

`status.index`는 현재 데이터의 인덱스를 출력한다.

## 3️⃣ th:if, th:unless

**controller**

```java
@GetMapping("/ex04")
public String thymeleafExample04(Model model) {
    List<ItemDto> itemDtoList = new ArrayList<>();

    for(int i = 1; i<=10; i++) {
        ItemDto itemDto = new ItemDto();

        itemDto.setItemNm("상품명" + i);
        itemDto.setItemDetail("상품 상세 설명" + i);
        itemDto.setPrice(10000 + i);
        itemDto.setRegTime(LocalDateTime.now());

        itemDtoList.add(itemDto);
    }

    model.addAttribute("itemDtoList", itemDtoList);
    return "thymeleafEx/thymeleafEx04";
}
```

**html**

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org" lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <h1> 상품 리스트 출력 예제</h1>
    <table border="1">
        <thead>
            <tr>
                <td>순번</td>
                <td>상품명</td>
                <td>상품 상세 설명</td>
                <td>가격</td>
                <td>상품 등록일</td>
            </tr>
        </thead>
        <tbody>
        <tr th:each="itemDto, status: ${itemDtoList}">
            <td th:if="${status.even}" th:text="짝수"></td>
            <td th:unless="${status.even}" th:text="홀수"></td>
            <td th:text="${itemDto.itemNm}"></td>
            <td th:text="${itemDto.itemDetail}"></td>
            <td th:text="${itemDto.price}"></td>
            <td th:text="${itemDto.regTime}"></td>
        </tr>
        </tbody>
    </table>
</body>
</html>
```

`th:if="${status.even}"` : 인덱스가 짝수일 경우 status.even은 true가 되고 짝수를 출력한다.

`th:unless="${status.even}"`: 인덱스가 짝수가 아닐 경우 홀수를 출력한다.

th:if와 th:unless는 자바에서 if와 else와 비슷한 역할을 한다.
