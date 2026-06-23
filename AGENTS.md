# 智品防災網站規格與維護文件

## 文件資訊

- 專案名稱：智品防災靜態網站
- 主要頁面：`index.html`
- 文件用途：後續維護、交接、修改頁面與新增頁面的參考
- 最後整理日期：2026-06-22

## 專案說明

本網站依照 UI/UX 設計圖切版，使用 Bootstrap 5 作為基礎框架，搭配自訂 CSS 完成品牌視覺、輪播圖、關於我們、產品卡片與頁尾資訊。

目前網站為純靜態頁面，可直接用瀏覽器開啟 `index.html` 預覽。Bootstrap CSS、Bootstrap JS、圖片與自訂樣式皆使用本地端檔案，不依賴 CDN。

## 目前目錄結構

```text
website/
├── index.html
├── AGENTS.md
├── css/
│   ├── bootstrap.min.css
│   └── style.css
├── js/
│   └── bootstrap.bundle.min.js
├── images/
│   ├── LOGO_防災.png
│   ├── 形象01_1.png
│   ├── 形象02.png
│   ├── 形象03.png
│   ├── 形象04.png
│   ├── 形象05.png
│   ├── 商品_00.png
│   ├── 商品照_A01.jpg
│   ├── 商品照_A02.jpg
│   ├── 商品照_A03.jpg
│   ├── 商品照_A04.jpg
│   ├── 商品照_A05.jpg
│   ├── 商品照_A06.jpg
│   ├── 商品照_A07.jpg
│   ├── 商品照_A08.jpg
│   ├── 商品照_A09.jpg
│   └── Banner_A01.jpg
└── assets/
    └── images/
```

`assets/images/` 目前保留早期產生的暫存圖片。後續維護請優先使用 `images/`，不要再新增素材到 `assets/images/`。

## 技術規格

- HTML 語系：繁體中文，`lang="zh-Hant"`
- CSS 框架：Bootstrap 5
- Bootstrap CSS：`css/bootstrap.min.css`
- Bootstrap JS：`js/bootstrap.bundle.min.js`
- 自訂 CSS：`css/style.css`
- 圖片資料夾：`images/`
- CDN：不使用

`index.html` 的 CSS 載入順序需維持如下：

```html
<link href="css/bootstrap.min.css" rel="stylesheet">
<link rel="stylesheet" href="css/style.css">
```

Bootstrap 必須先載入，自訂 CSS 必須後載入，才可覆蓋 Bootstrap 預設樣式。

JS 載入位置維持在 `</body>` 前：

```html
<script src="js/bootstrap.bundle.min.js"></script>
```

Bootstrap 的 navbar 收合與 carousel 輪播需要 `bootstrap.bundle.min.js`，請勿移除。

## 頁面區塊結構

`index.html` 由上到下分為：

1. 導覽列：`nav.site-nav`
2. 輪播區：`header#home.hero-carousel`
3. 關於我們：`section#about.about-section`
4. 產品介紹：`section#products.product-section`
5. 頁尾資訊：`footer#contact.site-footer`
6. 回到頂端：`a.back-top`

## 導覽列規格

導覽列使用 Bootstrap navbar：

```html
<nav class="navbar navbar-expand-lg fixed-top site-nav">
```

目前選單項目：

- 首頁：`#home`
- 關於我們：`#about`
- 產品介紹：`#products`
- 會員登入：`#contact`

Logo 使用：

```text
images/LOGO_防災.png
```

樣式主要在 `css/style.css`：

- `.site-nav`
- `.brand-mark`
- `.brand-name`
- `.nav-pill`

## 輪播圖規格

輪播使用 Bootstrap carousel：

```html
<div id="mainCarousel" class="carousel slide carousel-fade" data-bs-ride="carousel">
```

目前共 5 張：

```text
images/形象01_1.png
images/形象02.png
images/形象03.png
images/形象04.png
images/形象05.png
```

若新增或刪除輪播圖，需要同步調整：

- `.carousel-indicators` 裡的 button 數量
- 每個 button 的 `data-bs-slide-to`
- `.carousel-inner` 裡的 `.carousel-item`
- 第一張保留 `active`，其他張不可有 `active`

輪播文字位於每張圖的 `.carousel-caption`。

## 關於我們規格

區塊 ID：

```html
<section id="about" class="about-section section-pad">
```

目前圖片：

```text
images/商品_00.png
```

版型為 Bootstrap grid：

- 左欄：圖片
- 右欄：標題、段落、按鈕

相關樣式：

- `.about-section`
- `.about-img`
- `.section-pad`
- `.section-kicker`

## 產品介紹規格

區塊 ID：

```html
<section id="products" class="product-section section-pad">
```

目前首頁顯示 3 張產品 card：

```text
images/商品照_A01.jpg
images/商品照_A02.jpg
images/商品照_A05.jpg
```

可替換或新增的產品圖片：

```text
images/商品照_A03.jpg
images/商品照_A04.jpg
images/商品照_A06.jpg
images/商品照_A07.jpg
images/商品照_A08.jpg
images/商品照_A09.jpg
```

產品卡片使用 Bootstrap card：

```html
<article class="card product-card h-100">
```

新增產品卡片時，建議複製既有 `.col-md-6.col-lg-4` 區塊，再修改圖片、標題、說明與連結。

相關樣式：

- `.product-section`
- `.product-card`
- `.product-card .card-img-top`
- `.product-card .card-body`

## 頁尾規格

區塊 ID：

```html
<footer id="contact" class="site-footer">
```

內容包含：

- 公司 Logo
- 公司名稱
- 簡介
- 社群連結
- 公司資訊
- 版權宣告

社群連結目前使用文字標籤，不使用 icon font：

```text
FB / IG / LINE / YT
```

公司資訊目前使用 `.info-icon` 文字標籤：

```text
地址 / 電話 / 信箱 / 時間
```

相關樣式：

- `.site-footer`
- `.footer-logo`
- `.social-links`
- `.company-info`
- `.info-icon`
- `.copyright`

## CSS 維護規則

自訂樣式統一維護於：

```text
css/style.css
```

請勿直接修改：

```text
css/bootstrap.min.css
js/bootstrap.bundle.min.js
```

若需覆蓋 Bootstrap 樣式，請在 `css/style.css` 中新增或修改自訂 class。

CSS 目前主要分區：

- 全站變數：`:root`
- 基本設定：`html`、`body`
- 導覽列：`.site-nav`
- 輪播區：`.hero-carousel`
- 區塊共用：`.section-pad`
- 關於我們：`.about-section`
- 產品卡片：`.product-card`
- 頁尾：`.site-footer`
- 回頂端按鈕：`.back-top`
- RWD：`@media`

## 圖片維護規則

所有正式圖片請放在：

```text
images/
```

圖片替換時注意：

- 檔名需與 HTML 完全一致。
- 中文檔名可以使用，但避免多餘空白。
- 若替換圖片尺寸差異很大，需檢查 `object-fit: cover` 的裁切效果。
- Logo 建議使用透明背景 PNG。
- Banner 建議使用橫式圖片。
- 產品圖建議維持接近正方形或 4:3。

## 新增頁面規則

若新增 `about.html`、`products.html` 或其他頁面：

1. 複製 `index.html` 的 `<head>` 設定。
2. 保留 Bootstrap 與 `css/style.css` 的引用順序。
3. 保留相同 navbar/footer，維持全站一致。
4. 圖片仍放在 `images/`。
5. 新頁面樣式先寫在 `css/style.css`。
6. 若頁面數量增加很多，再考慮拆分 `css/about.css`、`css/products.css`。

## 常見修改位置

- 網站標題：`<title>智品防災</title>`
- 導覽列文字：`.navbar-nav`
- Logo 圖片：`.brand-mark` 與 `.footer-logo`
- 輪播圖片：`.carousel-item img`
- 輪播標題：`.carousel-caption`
- 關於我們文字：`section#about`
- 產品資料：`.product-card`
- 社群連結：`.social-links`
- 公司資訊：`.company-info`
- 版權文字：`.copyright`

## 維護檢查清單

每次修改後建議確認：

- `index.html` 沒有 CDN 連結。
- Bootstrap CSS 指向 `css/bootstrap.min.css`。
- Bootstrap JS 指向 `js/bootstrap.bundle.min.js`。
- 自訂 CSS 指向 `css/style.css`。
- 圖片路徑都指向 `images/`。
- 輪播可正常切換。
- 手機版 navbar 可正常展開與收合。
- 產品卡片在桌機為 3 欄，手機為單欄。
- 頁尾資訊沒有文字重疊。

## 不建議事項

- 不建議直接改 Bootstrap 原始檔。
- 不建議重新引入 CDN。
- 不建議把正式圖片放回 `assets/images/`。
- 不建議在 HTML 裡寫大量 inline style。
- 不建議移除 Bootstrap bundle，否則輪播與 navbar 會失效。
