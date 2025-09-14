# Slide Style v2 規格文件

## 概述
本文檔記錄了 `w2.html` 投影片系統的 v2 版本樣式規格，基於 `w2_backup.html` 的設計理念進行優化。

## 設計原則
- **置中對齊**：所有投影片內容垂直置中顯示
- **適中字體**：使用較小但清晰的字體大小，提升閱讀舒適度
- **響應式設計**：支援桌面版和手機版的不同顯示需求
- **視覺一致性**：保持整體設計風格統一

## 色彩系統
```css
:root {
    --bg-color: #F4F2EF;        /* 背景色：淺米色 */
    --text-color: #5a5a5a;      /* 主要文字色：深灰色 */
    --accent-color: #78785b;    /* 強調色：橄欖綠 */
    --line-color: #d1d1c2;      /* 線條色：淺灰色 */
    --highlight-color: #8c867b; /* 高亮色：中灰色 */
    --font-family: 'Calibri', 'Noto Sans TC', sans-serif;
}
```

## 核心佈局

### 投影片容器
```css
.slide {
    flex: 0 0 100%;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;    /* 垂直置中 */
    align-items: center;        /* 水平置中 */
    padding: 40px 60px;        /* 固定 padding */
    text-align: center;
    position: relative;
    overflow-y: auto;
    box-sizing: border-box;
    font-size: 1.5rem;         /* 基礎字體大小 */
}
```

### 標題樣式
```css
.slide h1, .slide h2, .slide h3 {
    color: var(--highlight-color);
    font-weight: normal;
    margin-bottom: 20px;
}

.slide h1 { font-size: 4rem; }    /* 主標題 */
.slide h2 { font-size: 3rem; }    /* 次標題 */
.slide h3 { font-size: 2rem; }    /* 三級標題 */
```

### 文字內容
```css
.slide p, .slide li {
    font-size: 1.8rem;           /* 較大的文字大小 */
    line-height: 1.6;
    max-width: 800px;
}

.slide-subtitle {
    color: #888;
    font-size: 1.8rem;
    font-weight: 300;
    margin-top: -1rem;
}
```

## 特殊投影片樣式

### 圖表投影片 (.chart-slide)
```css
.slide.chart-slide {
    padding: 2vw;
    align-items: stretch;
}

.slide.chart-slide h3 {
    width: 100%;
    max-width: none;
    text-align: center;
}

.slide.chart-slide .iq-chart-container {
    width: 100%;
    max-width: none;
    margin: 10px 0;
}
```

### 影片投影片 (.video-slide)
```css
.slide.video-slide {
    padding: 2vw;
    align-items: stretch;
}

.slide.video-slide h2 {
    width: 100%;
    max-width: none;
    text-align: center;
}

.video-container {
    width: 80%;                  /* 80% 寬度 */
    max-width: 800px;           /* 最大 800px */
    height: auto;
    aspect-ratio: 16 / 9;       /* 16:9 長寬比 */
    margin-top: 20px;
    border: 1px solid var(--line-color);
}

.video-container iframe {
    width: 100%;
    height: 100%;
    border: none;
}
```

### 作業投影片 (.homework-slide)
```css
.homework-slide {
    display: flex;
    align-items: flex-start;
    justify-content: center;
    padding: 2vh 2vw;
    overflow-y: auto;
    text-align: left;            /* 左對齊 */
}

.homework-slide > div {
    width: 100%;
    max-width: 1000px;
    margin: 0;
}

.homework-slide h2 {
    font-size: clamp(1.1rem, 2.5vw, 1.4rem);
    margin-bottom: 1vh;
    text-align: center;
}

.homework-slide .homework-content {
    font-size: 0.9rem;
    line-height: 1.4;
    max-width: 100%;
    margin: 0;
}
```

### 字多版本容器 (.bunch-word-container)
```css
.bunch-word-container {
    display: flex;
    flex-direction: column;
    align-items: flex-start;         /* 左對齊 */
    justify-content: flex-start;     /* 從頂部開始 */
    padding: 1.5vh 2vw;
    overflow-y: auto;               /* 可滾動 */
    text-align: left;
    height: 100%;                   /* 填滿整個投影片 */
    box-sizing: border-box;
}

.bunch-word-container > div {
    width: 100%;
    max-width: 1200px;              /* 比 homework-slide 更寬 */
    margin: 0;
}

.bunch-word-container h2 {
    font-size: clamp(1.2rem, 2.8vw, 1.6rem);
    margin-bottom: 1.5vh;
    text-align: center;
    width: 100%;
    color: var(--highlight-color);
}

.bunch-word-container .homework-content {
    font-size: 1.425rem;            /* 放大 1.5 倍：0.95rem × 1.5 */
    line-height: 1.5;               /* 更好的行高 */
    max-width: 100%;
    margin: 0;
}

.bunch-word-container .homework-content h4 {
    font-size: 1.65rem;             /* 放大 1.5 倍：1.1rem × 1.5 */
    line-height: 1.4;
    margin-bottom: 1rem;
    color: var(--accent-color);
}

.bunch-word-container .homework-content p {
    font-size: 1.425rem;            /* 放大 1.5 倍：0.95rem × 1.5 */
    line-height: 1.5;
    margin-bottom: 1rem;
}

.bunch-word-container .homework-content pre {
    background-color: var(--bg-color);
    border: 1px solid var(--line-color);
    border-radius: 6px;             /* 更圓的邊角 */
    padding: 15px;                  /* 更大的內邊距 */
    margin: 1rem 0;
    overflow-x: auto;
    font-size: 1.2rem;              /* 放大 1.5 倍：0.8rem × 1.5 */
    line-height: 1.5;
}

.bunch-word-container .homework-content pre code {
    background: none;
    padding: 0;
    font-size: 1.2rem;              /* 放大 1.5 倍：0.8rem × 1.5 */
    color: #333;
    white-space: pre;
}
```

## 列表樣式
```css
.slide ul {
    list-style-type: none;
    padding: 0;
    text-align: left;
}

.slide ul li {
    margin-bottom: 15px;
    position: relative;
    padding-left: 25px;
}

.slide ul li::before {
    content: '•';
    color: var(--accent-color);
    font-weight: bold;
    display: inline-block;
    width: 1em;
    margin-left: -1em;
    position: absolute;
    left: 0;
}
```

## 特殊元素

### 大數字顯示 (.chart73)
```css
.chart73 {
    font-size: 10rem;            /* 超大字體 */
    font-weight: bold;
    color: var(--highlight-color);
    margin: 20px 0;
    line-height: 1;
}
```

### 圓餅圖
```css
.pie-chart {
    width: 300px;
    height: 300px;
    border-radius: 50%;
    background: conic-gradient(
        #a39e93 0% 38.5%,
        #c1bcae 38.5% 77%,
        #dcd9d1 77% 100%
    );
    margin-bottom: 20px;
}

.legend {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    font-size: 1.2rem;
}

.legend-item {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
}

.legend-color {
    width: 20px;
    height: 20px;
    margin-right: 10px;
    border: 1px solid var(--text-color);
}
```

## 響應式設計

### 手機版 (max-width: 767px)
```css
@media (max-width: 767px) {
    .slide {
        padding: 3vw;
        overflow-y: auto;
        justify-content: flex-start;
    }

    .slide:first-child {
        justify-content: center;
        overflow-y: hidden;
    }

    h3 {
        width: 95%;
        font-size: clamp(1.2rem, 4vw, 1.8rem);
    }

    h2 {
        font-size: clamp(1rem, 3vw, 1.5rem);
        margin-bottom: 0.8rem;
    }

    .slide.video-slide .video-container {
        margin: 10px 0;
        width: 90%;              /* 手機版 90% 寬度 */
        max-width: 450px;        /* 最大 450px */
    }

    /* 字多版本響應式樣式 */
    .bunch-word-container {
        padding: 1vh 1vw;
    }

    .bunch-word-container h2 {
        font-size: clamp(1rem, 2.8vw, 1.3rem);
        margin-bottom: 1vh;
    }

    .bunch-word-container .homework-content {
        font-size: 1.2rem;              /* 放大 1.5 倍：0.8rem × 1.5 */
        line-height: 1.4;
        padding: 0 0.3rem;
    }

    .bunch-word-container .homework-content h4 {
        font-size: 1.35rem;             /* 放大 1.5 倍：0.9rem × 1.5 */
        line-height: 1.3;
        margin-bottom: 0.8rem;
    }

    .bunch-word-container .homework-content p {
        font-size: 1.2rem;              /* 放大 1.5 倍：0.8rem × 1.5 */
        line-height: 1.4;
        margin-bottom: 0.8rem;
    }

    .bunch-word-container .homework-content pre {
        font-size: 0.9rem;              /* 放大 1.5 倍：0.6rem × 1.5 */
        line-height: 1.3;
        padding: 10px;
        margin: 0.8rem 0;
    }

    .bunch-word-container .homework-content pre code {
        font-size: 0.9rem;              /* 放大 1.5 倍：0.6rem × 1.5 */
    }
}
```

## 導航控制
```css
.nav {
    position: fixed;
    top: 50%;
    transform: translateY(-50%);
    width: 98%;
    left: 1%;
    display: flex;
    justify-content: space-between;
    z-index: 100;
    pointer-events: none;
}

.nav-btn {
    pointer-events: all;
    background: none;
    border: 1px solid var(--line-color);
    color: var(--accent-color);
    font-size: 2rem;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    cursor: pointer;
    transition: background-color 0.3s, color 0.3s;
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: 0.4;
}

.nav-btn:hover {
    background-color: var(--accent-color);
    color: var(--bg-color);
    opacity: 1;
}
```

## 主要改進點

### 相較於 v1 版本的改進：
1. **置中對齊**：所有投影片內容垂直置中，提升視覺平衡
2. **字體優化**：使用更適中的字體大小，提升閱讀舒適度
3. **影片大小**：YouTube 影片調整為 80% 寬度，最大 800px
4. **響應式優化**：手機版影片調整為 90% 寬度，最大 450px
5. **樣式統一**：使用 `.slide` 前綴確保樣式正確應用
6. **視覺層次**：改善標題和內容的視覺層次關係
7. **字多版本容器**：新增 `.bunch-word-container` 樣式，專門處理內容較多的投影片
8. **字體放大優化**：`.bunch-word-container` 字體放大 1.5 倍，提升長文本可讀性

### 技術特點：
- 使用 CSS Grid 和 Flexbox 進行佈局
- 支援觸控和鍵盤導航
- 響應式設計，適配各種螢幕尺寸
- 模組化 CSS 結構，易於維護和擴展
- **字多版本容器**：`.bunch-word-container` 提供專門的長內容顯示解決方案
  - 從頂部開始顯示內容，避免置中對齊造成的內容截斷問題
  - 支援垂直滾動，確保所有內容都能完整查看
  - 優化的字體大小和行高，提升長文本的可讀性
  - 更寬的容器寬度（1200px），提供更多內容展示空間

## 使用方式
1. 將此樣式應用到新的投影片檔案
2. 確保 HTML 結構使用正確的 class 名稱
3. 根據需要調整色彩變數以符合品牌需求
4. 測試響應式效果確保在不同裝置上正常顯示

---
*最後更新：2025年1月*
*版本：v2.1*
*更新內容：字多版本容器字體放大 1.5 倍優化*
