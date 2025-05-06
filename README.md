# 和欣客運仿站實作教學說明

本專案仿製 [和欣客運官網](https://www.ebus.com.tw) 的首頁與登入畫面，透過 HTML、CSS 和 JavaScript 製作，並以教學方式說明開發流程與技術細節，幫助初學者快速上手前端切版與互動設計。

---

## 🧩 自己網站與目標網站的差異

| 項目         | 官網行為                            | 仿站實作                             |
|--------------|-------------------------------------|--------------------------------------|
| 導覽列連結   | 導向實際服務頁面                    | 全部被導向 `hacked.html`             |
| 登入行為     | 實際會員驗證與跳轉                  | 使用 alert 模擬登入並跳轉            |
| 驗證碼圖片   | 動態產生                             | 使用靜態圖片 `img/captcha.jpg`       |
| 響應式設計   | 完整支援手機版與桌面版              | 僅實作桌面版，CSS 為固定寬度排版     |

---

## 📁 專案結構

```
project/
├── index.html          # 主頁 HTML
├── style.css           # 所有樣式
├── img/
│   ├── header-logo.png # LOGO 圖片
│   ├── captcha.jpg     # 驗證碼圖
│   └── logo.jpg        # 頁腳 LOGO
```

---

## 🛠️ 實作步驟

### 1️⃣ 編寫 HTML 架構

```html
<header class="header">
  <div class="header-top container">
    <a class="logo" href="#"></a>
    <ul class="top-nav">
      <li><a href="#">常見問題</a></li>
      <li><a href="#">登入</a></li>
    </ul>
  </div>
</header>
```

---

### 2️⃣ 撰寫 CSS 樣式 (`style.css`)

#### 基礎 Reset & 字型設定

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: 'Segoe UI', 'Noto Sans TC', sans-serif;
  background: #f5f5f5;
  color: #333;
}
```

#### LOGO 與導覽列

```css
.logo {
  width: 220px;
  height: 60px;
  background-image: url('img/header-logo.png');
  background-size: contain;
  text-indent: -9999px;
}
.top-nav {
  display: flex;
  gap: 20px;
}
```

#### 選單與下拉選單 hover 顯示

```css
.menu > li:hover .sub_menu {
  display: block;
}
.sub_menu {
  display: none;
  position: absolute;
  background: white;
}
```

---

### 3️⃣ 建立登入表單區塊

#### HTML 表單結構

```html
<form id="loginForm">
  <input id="userName" placeholder="手機號碼">
  <input id="securityCode" placeholder="預設密碼">
  <input id="captchaCode" placeholder="驗證碼">
  <img src="img/captcha.jpg">
  <button id="login" type="button">登入</button>
</form>
```

#### JavaScript 登入行為（純前端模擬）

```javascript
document.getElementById('login').addEventListener('click', function () {
  const u = document.getElementById('userName').value;
  const p = document.getElementById('securityCode').value;
  const c = document.getElementById('captchaCode').value;

  if (u && p && c) {
    alert(`登入成功！\n帳號: ${u}`);
    window.location.href = 'hacked.html';
  } else {
    alert('請填寫所有欄位');
  }
});
```

---

## 📸 頁面預覽（以圖片或程式碼區塊示意）

### ▸ 登入表單範例

```html
<input placeholder="手機號碼">
<input placeholder="預設密碼">
<input placeholder="驗證碼">
<img src="img/captcha.jpg">
```

---

## 📌 備註

本專案僅為學術用途之仿站練習，不做商業用途。