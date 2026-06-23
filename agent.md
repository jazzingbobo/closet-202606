# Closet 首頁維護規格

## 專案概要

本專案為 Bootstrap 5 靜態首頁切版，依照 UIUX 設計稿製作。頁面由上到下包含選單、5 張輪播圖、關於我們左圖右文、2 塊產品介紹 card、頁尾聯絡資訊、社群連結、公司資訊與版權宣告。

目前不使用任何 CDN，CSS、JS、圖片皆由本地端檔案載入，方便離線預覽與後續維護。

## 主要檔案

- `index.html`：首頁 HTML 結構。
- `css/bootstrap.min.css`：Bootstrap 5 樣式主檔。
- `css/style.css`：自訂樣式，包含首頁版面、色彩、間距、RWD、footer、產品卡等設定。
- `js/bootstrap.bundle.min.js`：Bootstrap 5 JS，已包含 Popper，供 navbar collapse、carousel 等元件使用。
- `images/logo.png`：導覽列 logo。
- `images/img-1.jpg` 至 `images/img-5.jpg`：輪播、關於我們與產品卡使用圖片。

## 頁面結構

`index.html` 目前主要區塊如下：

1. `nav.site-navbar`
   - 主選單區。
   - 包含 logo、首頁、關於我、聯絡我們、登入。
   - 手機版使用 Bootstrap navbar collapse。

2. `header#mainCarousel`
   - Bootstrap carousel。
   - 目前共有 5 張圖片，對應 `images/img-1.jpg` 到 `images/img-5.jpg`。
   - 使用 `data-bs-ride="carousel"` 自動播放。

3. `section#about`
   - 關於我們區塊。
   - 桌機版為左圖右文，手機版依 Bootstrap grid 自動上下排列。

4. `section#products`
   - 產品介紹區塊。
   - 目前有 2 張 Bootstrap card。
   - 按鈕文字為「瞭解更多」。

5. `.back-to-top`
   - 固定式回到頁首按鈕。
   - 連結到 `#top`。

6. `footer#contact`
   - 聯絡我們區塊。
   - 包含 Facebook、Messenger、Instagram 內嵌 SVG 圖示。
   - 包含客服專線、服務時間、版權宣告。

## 樣式維護

自訂樣式集中在 `css/style.css`，請優先修改此檔，不建議把樣式重新寫回 `index.html` 的 `<style>`。

目前主要 CSS 變數：

```css
:root {
  --brand-rose: #9f6261;
  --brand-paper: #fff39b;
  --brand-aqua: #20d6d2;
  --brand-ink: #222222;
}
```

常用 class 對應：

- `.site-navbar`：導覽列外觀。
- `.hero-carousel`：輪播圖尺寸與圖片裁切。
- `.section-space`：一般區塊上下留白。
- `.about-image`、`.about-copy`：關於我們區塊。
- `.product-area`、`.product-card`、`.btn-product`：產品介紹 card。
- `.site-footer`、`.social-links`、`.company-info`、`.copyright`：頁尾資訊。
- `.back-to-top`：回到頁首按鈕。

## Bootstrap 引用

HTML head 內載入順序如下：

```html
<link href="css/bootstrap.min.css" rel="stylesheet">
<link href="css/style.css" rel="stylesheet">
```

頁面底部載入：

```html
<script src="js/bootstrap.bundle.min.js"></script>
```

請保持 `style.css` 在 Bootstrap 後方載入，確保自訂樣式可以覆蓋 Bootstrap 預設值。

## 圖片替換規則

若要替換圖片，建議維持目前檔名，直接覆蓋 `images` 內檔案，可減少修改 HTML 的機會。

- 輪播圖：`img-1.jpg` 到 `img-5.jpg`
- Logo：`logo.png`
- 關於我們目前使用：`img-4.jpg`
- 產品卡目前使用：`img-2.jpg`、`img-3.jpg`

若更換為不同檔名，請同步更新 `index.html` 中的 `src`。

## 維護注意事項

- 本頁為純靜態頁，不需要啟動伺服器即可直接用瀏覽器開啟 `index.html`。
- 不要新增 CDN 引用，除非需求明確允許外部資源。
- 若新增其他頁面，建議沿用 `css/bootstrap.min.css`、`css/style.css`、`js/bootstrap.bundle.min.js`。
- 若新增多頁共用元件，建議維持相同 class 命名，例如 `site-navbar`、`site-footer`。
- 社群與公司資訊圖示目前為內嵌 SVG，不依賴 Bootstrap Icons。
- 修改 RWD 時，請同步檢查桌機、平板、手機寬度。

## 目前版本狀態

- Bootstrap：本地端 Bootstrap 5 檔案。
- 外部 CDN：無。
- 自訂 CSS：已抽離至 `css/style.css`。
- 首頁入口：`index.html`。
