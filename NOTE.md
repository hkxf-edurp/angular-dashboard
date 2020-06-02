# Angular 快速筆記

## 零、準備

### 學習資源

angular.tw有完整中文教學，網路上查到任何 angular.io 的網址，把io替換成tw就能看中文內容。

例如:
https://angular.io/guide/http#intercepting-requests-and-responses

中文:
https://angular.tw/guide/http#intercepting-requests-and-responses


### 工具

#### VSCode

搜尋保哥的 Angular Extension Pack，全部安裝

#### GITHUB

裝GitHub Desktop，等專案建立之後執行 Add local repository，VSCode也需要安裝


## 一、專案初始化

### CMD

ng new app1

### VSCode

1. open folder [app1]
2. [Menubar] Terminal => New Terminal
3. enter: npm i
4. [NPM SCRIPTS] npm run start 

## 二、專案結構
```
.
├── src
|   ├── index.html 整體template
|   ├── main.ts 專案進入點
|   ├── style.scss 適用整體的樣式表
|   ├── app
│   │   ├── app.module.ts 基本模組，統整全專案的部件(components, service)
│   │   ├── app.component.ts 根元件
│   │   ├── app-routing.module.ts 路由設定模組
│   │   └── {在此加其他資料夾作專案結構}
│   └── assets (圖片等元素)
├── angular.json 工作區設定檔
└── package.json 
```

專案結構建議
```
.
├── app
|   ├── core (services、middleware...)
|   |   ├── api.service.ts
|   |   └── auth.service.ts
|   └── site
```

## 三、部件調整

### port調整

    [VSCode > Explorer] open angular.json, find node [serv > options], insert ["port": 4750,]

### 專案路徑

一般開發者會希望各專案路徑是分別掛在網域下的子目錄，方便整合多重專案在同一個伺服器內

    [VSCode > Explorer] open angular.json, find node [build > options], insert ["baseHref" : "/v1/",]

以上操作等於將專案整個往下縮一層，此專案不再處理根路徑，以免除部署後衝突，專案開發期間需要從瀏覽器網址列手動加 /v1/

### 部署

除了內建的dist之外，如果要加上其他部署位置，只要改 build 的參數。
譬如部署到 github pages (可於專案設定接受 docs 資料夾的內容)

    [Explorer] open package.json, find node [scripts], insert ["deploy-to-docs": "ng build --prod --output-path docs",]


### 工具列

/*最好加到 src/styles.scss*/

到 assets 增加 css 資料夾，在裡面加入 nav.scss

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

src/styles.scss

    @import "./assets/css/nav.scss"
  
src/app/app.component.html  

    <ul class="nav-item">
      <li><a routerLink="/">root</a></li>
      <li><a routerLink="/home">home</a></li>
      <li><a routerLink="/path-test">path-test</a></li>
      <li><a routerLink="/path-test/subpath">path-test/subpath</a></li>
    </ul>


## 四、登入控制


## 五、後端API整合

## 六、整合opensource資源
