# CSS 혐오하는 사람들을 위한 CSS 규칙

1. Selector 규칙을 최소한으로 줄이기

   가능하다면 최대한 하나의 class를 사용해서 selector 규칙을 만드는게 좋습니다. 

   ```css
    /* 안좋은 코드 */
    .navigation a {
      color: blue;
    }
   ```

   ```css
    /* 추천 코드 */
    .nav-link {
      color: blue;
    }
   ```
   
   만약 css style을 수정하고 싶다면 하나의 class를 더 추가하여 오버라이트를 하는것이 좋습니다.
   ```css
    /* 추천 코드 */
    .nav-link {
      color: blue;
      font-size: 2rem;
    }

    .nav-link-red {
      color: red;
    }
   ```
2. ID 또는 태그명을 selector 규칙으로 사용하지마세요.

   ID는 너무 구체적이고, 같은 ID를 여러 태그에 중복해서 사용할 수 없기때문에 좋지않습니다. 태그명은 가끔 써야될 때가 있지만 사용하는 것을 추천드리지 않습니다.
   ```css
    /* 안좋은 코드 */
    #banner {
      background-color: blue;
    }
    
    #banner h1 {
      color: white;
    }
   ```
   ```css
    /* 추천 코드 */
    .banner {
      background-color: blue;
    }
    
    .banner-title {
      color: white;
    }
   ```
3. 다른 selector 규칙에 영향을 받지 않도록 하는 것이 좋습니다.

   ```css
    /* 안좋은 코드 */
    .header ul li a {
      margin-right: 20px;
    }
   ```
   
   ```css
    /* 추천 코드 */
    .header-link {
      margin-right: 20px;
    }
   ```
4. 인라인 스타일 사용하지 마세요.
   ```html
    /* 안좋은 코드 */
    <span style="color: red; font-size: 14px;">Bad Code</span>
   ```
   
   ```html
    /* 추천 코드 */
    <span class="good-code">Good Code</span>
   ```
   ```css
    .good-code {
      color: red;
      font-size: 14px;
    }
   ```
5. !important 사용하지 마세요.
   
   !important는 가끔 Javascript 써드파티 라이브러리를 사용할때 라이브러리가 인라인 스타일을 사용해서 style을 바꿔야 할 경우에만 사용하는 것이 좋습니다.
   
6. class에 접두사를 사용하세요.
   ```css
     /* 안좋은 코드 */
     .btn {
      padding: .25em;
      background-color: blue;
      color: white;
     }
     .btn.red{
      background-color: red;
     }
   ```
   위와 같은 css 코드가 있습니다. 보기에 그렇게 나쁜코드는 아니지만 큰 프로젝트를 할 때 이런식의 코드는 좋지않습니다. 왜냐하면 다른 css 스타일과 중첩이 되어 원하지 않는 결과가 나타날수 있기때문입니다.
   
   예를들어
   ```css
     /* 안좋은 코드 */
     .btn {
      padding: .25em;
      background-color: blue;
      color: white;
     }
     .btn.red{
      background-color: red;
     }

     .top-navigation {
      font-size: 2rem;
      color: blue;
     }

     .top-navigation .red {
      color: red;
     }
   ```
   ```html
    <div class="top-navigation">
      <button class="btn red">Button</button>
    </div>
   ```
   
   위와 같은 HTML, CSS코드가 있을때 button 엘리먼트가 빨간색 바탕에 빨간색 글자로 된 button엘리먼트가 되어버릴 수 있습니다. 그래서 아래와 같이 class에 접두사를 붙여주는 것이 style을 더 명확하게 줄 수 있습니다.
   ```css
    .btn {
      padding: .25em;
      background-color: blue;
      color: white;
    }
    
    .btn-red {
      background-color: red;
    }
   ```

   
