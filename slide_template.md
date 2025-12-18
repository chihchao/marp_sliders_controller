---
marp: true
theme: default
paginate: true
header: "🚀 My Awesome Presentation"
footer: "© 2025 Your Name | yourwebsite.com"
backgroundColor: "#ffffff"
style: |
  section {
    font-family: 'Noto Sans TC', sans-serif;
    font-size: 28px;
  }
  h1 {
    color: #1a73e8;
  }
  h2 {
    border-bottom: 2px solid #1a73e8;
    padding-bottom: 10px;
  }
---

<!--
_class: lead
backgroundColor: #ffffff
color: #1a1a1a
header: ""
footer: ""
paginate: false
-->

# 簡報標題：Marp Markdown 模板
### 副標題：快速打造專業簡報  
報告人：您的名字

---

## 為什麼選擇 Marp?

- 純文本編輯：專注內容，不被格式干擾
- Git 友好：簡報可像程式碼一樣版本控管
- 跨平台輸出：匯出 PDF、HTML、PPTX 或圖片
- 自訂性強：直接用 CSS 調整樣式

<!-- 這是講稿 page 2 -->

---

## 基本語法範例

- **粗體** 與 _斜體_
- [超連結範例](https://marp.app)
- 行內代碼：`npm install @marp-team/marp-cli`
- 引用：
  > 這是一個引用區塊，適合用來放置名言佳句或重點摘要。

<!-- 這是講稿 page 3 -->

---

## 雙欄配置 (HTML/CSS)

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
  <div>
    <strong>左側欄位</strong><br>
    - 列出優點 A<br>
    - 列出優點 B<br>
    - 列出優點 C
  </div>
  <div>
    <strong>右側欄位</strong><br>
    - 詳細說明 1<br>
    - 詳細說明 2<br>
    - 詳細說明 3
  </div>
</div>

---

## 圖片展示

![圖片描述](https://dummyimage.com/800x450/1a73e8/ffffff&text=Sample+Image){ width="600" }

- 可用 `w:600` 或 `width="600"` 調整寬度
- 圖片位址可換成本機或線上資源

---

## 程式碼高亮

```js
// 這是一個簡單的 JS 函數
function greet(name) {
  console.log(`Hello, ${name}!`);
  return true;
}

greet('Marp User');
```

---

## 數學公式 (KaTeX)

- 行內公式：$E = mc^2$
- 獨立公式塊：

$$
I = \int_{a}^{b} f(x) \, dx
$$

---

<!-- _class: lead -->

# Q&A
感謝您的聆聽！  
[返回首頁](#) | [聯繫我們](mailto:you@example.com)


