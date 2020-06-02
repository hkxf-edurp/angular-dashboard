# 樣式設計

建議樣式表全部放到 src/assets，再由 src/styles.scss 載入。

譬如，增加全域通用的導覽樣式。

1. 到 assets 增加 css 資料夾，在裡面加入 nav.scss

```
.
├── src
|   ├── assets
|   |   ├── css
|   |   |   └── nav.scss
```

2. 編輯內容

nav.scss

    ul.nav-item {
      padding: 0;
      li {
        display: inline-block;
        a {
          display: block;
          padding: 0.3em 1em;
          &:hover {
            background-color: #39c;
          }
          :link,&:hover,&:visited {
            color: white;
          }
        }
      }
    }


3. 由根樣式表載入 

src/styles.scss

    @import "./assets/css/nav.scss"

4. 使用樣式

src/app/app.component.html  

    <ul class="nav-item">
      <li><a routerLink="/">root</a></li>
      <li><a routerLink="/home">home</a></li>
      <li><a routerLink="/path-test">path-test</a></li>
      <li><a routerLink="/path-test/subpath">path-test/subpath</a></li>
    </ul>

