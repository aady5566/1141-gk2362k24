# Slide Style Guide - 簡報設計風格指南

## 概述

這是一個專為學術簡報、數據視覺化和專業報告設計的現代化風格系統。該風格強調低飽和度色彩、優雅的排版和流暢的動畫效果，營造出專業而舒適的視覺體驗。

## 設計哲學

- **低飽和度美學**：使用溫和、不刺眼的色彩，適合長時間閱讀
- **優雅簡約**：避免過度設計，專注於內容呈現
- **響應式優先**：確保在各種裝置上都有良好的顯示效果
- **無障礙設計**：考慮視覺障礙用戶的使用體驗
- **Markdown 風格**：簡潔直接的內容呈現，減少視覺干擾
- **統一導航**：使用側邊欄提供一致的導航體驗，避免重複的按鈕元素

## 色彩系統

### 主色調
```css
:root {
    --bg-color: #F4F2EF;        /* 主背景色 - 溫暖的米白色 */
    --text-color: #5a5a5a;      /* 主文字色 - 深灰色 */
    --accent-color: #78785b;    /* 強調色 - 低飽和橄欖綠 */
    --line-color: #d1d1c2;      /* 邊框線色 - 淺灰色 */
    --font-family: 'Calibri', 'Noto Sans TC', sans-serif;  /* 字體 */
}
```

### 擴展色盤
```css
/* 低飽和度配色方案 */
--color-primary: rgba(120, 120, 91, 0.7);      /* 主色 */
--color-secondary: rgba(163, 163, 128, 0.7);   /* 次色 */
--color-accent: rgba(180, 120, 120, 0.7);      /* 強調色 */
--color-success: rgba(120, 150, 120, 0.7);     /* 成功色 */
--color-info: rgba(120, 140, 160, 0.7);        /* 資訊色 */
--color-warning: rgba(160, 140, 180, 0.7);     /* 警告色 */
```

## 排版系統

### 字體層級
```css
/* 主標題 - 用於投影片主標題 */
h1 {
    font-size: clamp(2rem, 6vw, 3.5rem);
    font-weight: 300;
    color: var(--text-color);
    margin-bottom: 1rem;
}

/* 次標題 - 用於投影片副標題 */
h2 {
    font-size: clamp(1.2rem, 3vw, 1.6rem);
    font-weight: 300;
    color: var(--accent-color);
    margin-bottom: 0.8rem;
}

/* 內容標題 - 用於投影片內容區塊標題 */
h3 {
    font-size: clamp(1.5rem, 4vw, 2.2rem);
    font-weight: 300;
    color: var(--text-color);
    margin-bottom: 4vh;
    border-bottom: 1px solid var(--line-color);
    padding-bottom: 1rem;
    width: 80%;
    max-width: 800px;
}

/* 小標題 - 用於內容區塊內的小標題 */
h4 {
    font-size: clamp(1.1rem, 2vw, 1.4rem);
    font-weight: 400;
    color: var(--accent-color);
    margin-bottom: 0.8rem;
    border-bottom: 1px solid var(--line-color);
    padding-bottom: 0.3rem;
}

/* 內文 */
p {
    color: #666;
    margin-bottom: 1rem;
    line-height: 1.6;
    font-size: clamp(0.9rem, 1.5vw, 1.1rem);
    max-width: 80ch; /* 限制段落寬度以提高可讀性 */
}

/* 投影片副標題 */
.slide-subtitle {
    color: #888;
    font-size: clamp(1rem, 2vw, 1.4rem);
    font-weight: 300;
    margin-top: -1rem;
}
```

### 響應式字體
- 使用 `clamp()` 函數實現流暢的字體縮放
- 最小字體：2rem，最大字體：3.5rem
- 根據視窗寬度動態調整（6vw）

## 投影片系統

### 基本結構
```css
/* 投影片容器 */
.slides-container {
    display: flex;
    width: 100%;
    height: 100%;
    transition: transform 0.6s cubic-bezier(0.65, 0, 0.35, 1);
}

/* 單一投影片 */
.slide {
    flex: 0 0 100%;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    padding: 5vw;
    text-align: center;
    position: relative;
    overflow-y: auto;
}

/* 第一頁（標題頁）置中顯示 */
.slide:first-child {
    justify-content: center;
    overflow-y: hidden; /* 第一頁不需要滾動 */
}
```

### 導航系統
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

## 組件樣式

### 1. 側邊欄導航組件
```css
/* 側邊欄容器 */
#sidebar {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 1000;
    font-family: var(--font-family, 'Calibri', 'Noto Sans TC', sans-serif);
}

/* 側邊欄切換按鈕（漢堡選單） */
.sidebar-toggle {
    position: fixed;
    top: 1rem;
    left: 1rem;
    width: 30px;
    height: 30px;
    cursor: pointer;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    background: #4d4d3b;
    border-radius: 4px;
    padding: 6px;
    transition: all 0.3s ease;
    z-index: 1001;
}

.sidebar-toggle:hover {
    background: #3a3a2c;
    transform: translateY(-2px);
}

.sidebar-toggle span {
    display: block;
    width: 18px;
    height: 2px;
    background: #ffffff;
    border-radius: 1px;
    transition: all 0.3s ease;
}

/* 側邊欄選單 */
.sidebar-menu {
    position: fixed;
    top: 0;
    left: -300px;
    width: 280px;
    height: 100vh;
    background: var(--bg-color);  /* 使用主背景色 - 淺米色 */
    box-shadow: 2px 0 10px rgba(0,0,0,0.1);
    transition: left 0.3s ease;
    z-index: 1000;
    overflow-y: auto;
}

.sidebar-menu.active {
    left: 0;
}

/* 側邊欄標題區域 */
.sidebar-header {
    background: #4d4d3b;
    color: #ffffff;
    padding: 1rem;
    text-align: center;
    border-bottom: 1px solid var(--line-color);
}

.sidebar-header h3 {
    margin: 0;
    font-size: 1.1rem;
    font-weight: 400;
}

/* 側邊欄內容區域 */
.sidebar-content {
    padding: 1rem 0;
}

/* 側邊欄選項 */
.sidebar-item {
    display: block;
    padding: 0.8rem 1.5rem;
    color: var(--text-color);
    text-decoration: none;
    transition: all 0.3s ease;
    border-bottom: 1px solid var(--line-color);
}

.sidebar-item:hover {
    background: rgba(120, 120, 91, 0.1);  /* 低飽和度懸停效果 */
    color: #4d4d3b;
    transform: translateX(5px);
}

.sidebar-text {
    font-size: 0.9rem;
    font-weight: 400;
}

/* 遮罩層 */
.sidebar-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.3);
    z-index: 999;
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s ease;
}

.sidebar-overlay.active {
    opacity: 1;
    visibility: visible;
}

/* 手機版優化 */
@media (max-width: 767px) {
    .sidebar-toggle {
        top: 0.5rem;
        left: 0.5rem;
        width: 28px;
        height: 28px;
        padding: 5px;
    }

    .sidebar-toggle span {
        width: 16px;
        height: 2px;
    }

    .sidebar-menu {
        width: 260px;
    }

    .sidebar-item {
        padding: 0.7rem 1.2rem;
    }

    .sidebar-text {
        font-size: 0.85rem;
    }
}
```

### 2. 卡片容器（傳統樣式）
```css
.card-container {
    background: rgba(163, 163, 129, 0.1);
    border-radius: 1rem;
    padding: clamp(1rem, 2vw, 2rem);
    box-shadow: 0 4px 20px rgba(0,0,0,0.05);
    border: 1px solid var(--line-color);
    margin-bottom: 1rem;
    width: 100%;
    text-align: left;
}

.card-container h3 {
    color: var(--accent-color);
    border-bottom: 1px solid var(--line-color);
    padding-bottom: 0.5rem;
}
```

### 3. Markdown 風格內容佈局
```css
.content-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 2rem;
    width: 100%;
    max-width: 1000px;
}

@media (min-width: 768px) {
    .content-grid {
        grid-template-columns: repeat(2, 1fr);
    }
}

.content-section {
    text-align: left;
    padding: 0;
}

.content-section h4 {
    font-size: clamp(1.1rem, 2vw, 1.4rem);
    font-weight: 400;
    color: var(--accent-color);
    margin-bottom: 0.8rem;
    border-bottom: 1px solid var(--line-color);
    padding-bottom: 0.3rem;
}

.content-section p {
    margin-bottom: 0.5rem;
    line-height: 1.7;
}
```

### 4. 時間軸組件
```css
.timeline-container {
    width: 100%;
    max-width: 1200px;
    padding: 0 2rem;
    overflow-x: auto;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    position: relative;
    height: 50vh;
}

.timeline-track {
    display: flex;
    position: relative;
    align-items: flex-start;
    padding-top: 50px;
}

.timeline-track::before {
    content: '';
    position: absolute;
    top: 25px;
    left: 0;
    width: 100%;
    height: 2px;
    background-color: var(--line-color);
}

.timeline-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    padding: 0 20px;
    min-width: 150px;
    text-align: center;
}

.timeline-item::before {
    content: '';
    position: absolute;
    top: 25px;
    left: 50%;
    transform: translateX(-50%);
    width: 12px;
    height: 12px;
    background-color: var(--bg-color);
    border: 2px solid var(--accent-color);
    border-radius: 50%;
    z-index: 1;
}

.timeline-year {
    position: absolute;
    top: -5px;
    font-weight: bold;
    color: var(--accent-color);
    font-size: 1.1rem;
}

.timeline-content {
    margin-top: 50px;
}

.timeline-content .title {
    font-weight: bold;
    font-size: 1rem;
}

.timeline-content .subtitle {
    font-size: 0.9rem;
    color: #777;
}

.timeline-content ul {
    list-style: none;
    padding: 0;
    margin-top: 10px;
    font-size: 0.8rem;
    text-align: left;
}

.timeline-content ul li {
    margin-bottom: 5px;
}
```

### 5. 課程大綱組件
```css
.syllabus-container {
    display: flex;
    justify-content: space-around;
    width: 100%;
    max-width: 1000px;
    text-align: left;
    font-size: clamp(0.8rem, 1.8vw, 1rem);
}

.syllabus-column {
    width: 45%;
}

.syllabus-container ul {
    list-style: none;
    padding: 0;
}

.syllabus-container li {
    margin-bottom: 0.8em;
    padding-left: 1.5em;
    position: relative;
}

.syllabus-container li::before {
    content: "·";
    color: var(--accent-color);
    font-weight: bold;
    position: absolute;
    left: 0;
    font-size: 1.5em;
    line-height: 0.8em;
}

.assessment {
    margin-top: 3rem;
    font-size: 1.2rem;
    color: var(--accent-color);
}
```

### 6. 破冰活動組件
```css
.icebreaker-list {
    list-style: none;
    padding: 0;
    font-size: clamp(1.2rem, 3.5vw, 2rem);
    font-weight: 300;
    line-height: 2;
}

.icebreaker-list li {
    opacity: 0;
    transform: translateY(20px);
    animation: fadeIn 0.8s forwards;
}

.icebreaker-list li:nth-child(1) { animation-delay: 0.5s; }
.icebreaker-list li:nth-child(2) { animation-delay: 1s; }
.icebreaker-list li:nth-child(3) { animation-delay: 1.5s; }
```

### 7. 客製化投影片樣式

#### 圖表投影片 (chart-slide)
```css
/* 圖表投影片特殊樣式 - 加寬處理 */
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

/* 手機版圖表投影片優化 */
@media (max-width: 767px) {
    .slide.chart-slide {
        padding: 1vw;
        align-items: stretch;
    }

    .slide.chart-slide h3 {
        font-size: clamp(1.2rem, 4vw, 1.8rem);
        width: 100%;
        margin-bottom: 2vh;
    }

    .slide.chart-slide .iq-chart-container {
        margin: 5px 0;
        width: 100%;
    }

    .slide.chart-slide .slide-footer {
        font-size: 0.7rem;
        margin-top: 1vh;
    }
}

@media (max-width: 480px) {
    .slide.chart-slide {
        padding: 0.5vw;
    }

    .slide.chart-slide h3 {
        font-size: clamp(1rem, 5vw, 1.5rem);
        margin-bottom: 1vh;
    }
}
```

#### 影片投影片 (video-slide)
```css
/* 影片投影片特殊樣式 - 加寬處理 */
.slide.video-slide {
    padding: 2vw;
    align-items: stretch;
}

.slide.video-slide h2 {
    width: 100%;
    max-width: none;
    text-align: center;
}

.slide.video-slide .video-container {
    width: 100%;
    max-width: 1600px;
    margin: 20px auto;
    height: auto;
    aspect-ratio: 16 / 9;
}

/* 手機版影片投影片優化 */
@media (max-width: 767px) {
    .slide.video-slide {
        padding: 1vw;
        align-items: stretch;
    }

    .slide.video-slide h2 {
        font-size: clamp(1.2rem, 4vw, 1.8rem);
        width: 100%;
        margin-bottom: 2vh;
    }

    .slide.video-slide .video-container {
        margin: 10px 0;
        width: 100%;
        max-width: none;
    }
}

@media (max-width: 480px) {
    .slide.video-slide {
        padding: 0.5vw;
    }

    .slide.video-slide h2 {
        font-size: clamp(1rem, 5vw, 1.5rem);
        margin-bottom: 1vh;
    }
}
```

#### 作業投影片 (homework-slide)
```css
/* 作業專用 slide 樣式 - 針對字多的內容優化 */
.homework-slide {
    display: flex;
    align-items: flex-start;
    justify-content: center;
    padding: 2vh 2vw;
    overflow-y: auto;
    text-align: left;
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

/* 作業說明框樣式 */
.slide.homework-slide .homework-content p[style*="background-color: #e8e5dc"] {
    font-size: 1.1rem !important;
    line-height: 1.5;
}

.slide.homework-slide .homework-content p[style*="background-color: #e8e5dc"] strong {
    font-size: 1.2rem !important;
}

/* 作業 slide 中的 code 區塊樣式 */
.slide.homework-slide .homework-content pre {
    background-color: var(--bg-color);
    border: 1px solid var(--line-color);
    border-radius: 4px;
    padding: 10px;
    margin: 0.5rem 0;
    overflow-x: auto;
    font-size: 0.7rem;
    line-height: 1.4;
}

.slide.homework-slide .homework-content pre code {
    background: none;
    padding: 0;
    font-size: 0.7rem;
    color: #333;
    white-space: pre;
}

/* 手機版作業 slide 優化 */
@media (max-width: 767px) {
    .homework-slide {
        padding: 1vh 1vw;
        align-items: flex-start;
    }

    .homework-slide h2 {
        font-size: clamp(1rem, 2.5vw, 1.2rem);
        margin-bottom: 0.8vh;
    }

    .homework-slide .homework-content {
        font-size: 0.75rem;
        line-height: 1.3;
        padding: 0 0.3rem;
    }

    .slide.homework-slide .homework-content pre {
        background-color: var(--bg-color);
        border: 1px solid var(--line-color);
        font-size: 0.5rem;
        line-height: 1.2;
        padding: 8px;
        margin: 0.4rem 0;
    }

    .slide.homework-slide .homework-content pre code {
        font-size: 0.5rem;
    }

    .slide.homework-slide .homework-content p[style*="background-color: #e8e5dc"] {
        font-size: 0.9rem !important;
        line-height: 1.4;
        padding: 12px !important;
    }

    .slide.homework-slide .homework-content p[style*="background-color: #e8e5dc"] strong {
        font-size: 1rem !important;
    }
}
```

### 8. 外部投影片預覽（Google Slides 嵌入）
```css
/* 外部投影片預覽容器 */
.embed-wrapper {
    width: 100%;
    max-width: 1200px;
    height: 70vh;
    border: 1px solid var(--line-color);
    border-radius: 0.5rem;
    overflow: hidden;
    background: #fff;
    box-shadow: 0 4px 12px rgba(0,0,0,0.06);
}

.embed-wrapper iframe {
    width: 100%;
    height: 100%;
    border: 0;
}
```

## 響應式設計

### 手機版優化 (Mobile First)

#### 基本手機版樣式
```css
/* 手機版優化 - 適用於 max-width: 767px */
@media (max-width: 767px) {
    /* 投影片容器優化 */
    .slide {
        padding: 3vw;
        overflow-y: auto;  /* 允許垂直滾動，避免內容被裁切 */
        justify-content: flex-start;
    }

    /* 手機版第一頁也置中 */
    .slide:first-child {
        justify-content: center;
        overflow-y: hidden;
    }

    /* 導航按鈕優化 */
    .nav {
        width: 95%;
        left: 2.5%;
    }

    .nav-btn {
        padding: 12px 16px;  /* 增大點擊區域 */
        font-size: 14px;
    }

    /* 課程大綱手機版佈局 */
    .syllabus-container {
        flex-direction: column;  /* 改為單欄顯示 */
        gap: 2rem;
    }

    .syllabus-column {
        width: 100%;
    }

    /* 標題優化 */
    h3 {
        width: 95%;
        font-size: clamp(1.2rem, 4vw, 1.8rem);
    }

    /* 主頁面容器優化 */
    .container {
        padding: 1rem;  /* 減少內邊距 */
    }

    .header {
        margin-bottom: 2rem;  /* 減少標題下邊距 */
    }

    /* 卡片優化 */
    .week-card {
        padding: 1.2rem;  /* 減少卡片內邊距 */
    }

    .slide-link {
        padding: 0.6rem 0.8rem;  /* 調整按鈕內邊距 */
        font-size: 0.9rem;
    }
}
```

#### 手機版設計原則
1. **內容可滾動**：使用 `overflow-y: auto` 確保內容完整顯示
2. **第一頁置中**：標題頁使用 `justify-content: center` 和 `overflow-y: hidden`
3. **其他頁面從頂部開始**：長內容頁面使用 `justify-content: flex-start` 支援滾動
4. **增大觸控區域**：按鈕和連結使用較大的 padding
5. **單欄佈局**：複雜內容改為垂直排列
6. **減少間距**：適當縮小 padding 和 margin 以節省空間
7. **優化字體大小**：使用 clamp() 確保文字在小螢幕上可讀

#### 斷點系統
```css
/* 手機版優先 */
@media (max-width: 767px) {
    /* 手機版樣式 */
}

/* 平板版 */
@media (min-width: 768px) {
    /* 平板版樣式 */
}

/* 桌面版 */
@media (min-width: 1024px) {
    /* 桌面版樣式 */
}
```

## 佈局系統

### 網格系統
```css
.grid {
    display: grid;
    gap: 2rem;
    width: 100%;
}

.grid-2 {
    grid-template-columns: 1fr;
}

@media (min-width: 768px) {
    .grid-2 {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (min-width: 1024px) {
    .grid-3 {
        grid-template-columns: repeat(3, 1fr);
    }
}
```

### 圖表容器
```css
.chart-wrapper {
    position: relative;
    width: 100%;
    height: 100%;
    max-height: 65vh; /* 確保圖表在 slide 內有足夠空間 */
    padding: 1rem;
}
```

## 動畫效果

### 投影片切換動畫
```css
.slides-container {
    transition: transform 0.6s cubic-bezier(0.65, 0, 0.35, 1);
}
```

### 淡入動畫
```css
@keyframes fadeIn {
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.icebreaker-list li {
    opacity: 0;
    transform: translateY(20px);
    animation: fadeIn 0.8s forwards;
}
```

### 滾動動畫
```css
.scroll-target {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.6s ease-out, transform 0.6s ease-out;
}

.scroll-target.visible {
    opacity: 1;
    transform: translateY(0);
}
```

## JavaScript 功能

### 1. 側邊欄導航系統
```javascript
// 側邊欄工具 JavaScript
document.addEventListener('DOMContentLoaded', function() {
    // 建立側邊欄 HTML 結構
    function createSidebar() {
        const sidebar = document.createElement('div');
        sidebar.id = 'sidebar';
        sidebar.innerHTML = `
            <div class="sidebar-toggle" id="sidebarToggle">
                <span></span>
                <span></span>
                <span></span>
            </div>
            <div class="sidebar-menu" id="sidebarMenu">
                <div class="sidebar-header">
                    <h3>工具選單</h3>
                </div>
                <div class="sidebar-content">
                    <a href="../index.html" class="sidebar-item">
                        <span class="sidebar-text">回首頁</span>
                    </a>
                    <a href="#" class="sidebar-item" id="languageToggle">
                        <span class="sidebar-text">切換語言</span>
                    </a>
                    <a href="random_grouping.html" class="sidebar-item" target="_blank">
                        <span class="sidebar-text">隨機分組</span>
                    </a>
                </div>
            </div>
        `;
        return sidebar;
    }

    // 初始化側邊欄
    function initSidebar() {
        // 檢查是否已經存在側邊欄
        if (document.getElementById('sidebar')) {
            return;
        }

        // 建立側邊欄
        const sidebar = createSidebar();
        document.body.appendChild(sidebar);

        // 建立遮罩層
        const overlay = document.createElement('div');
        overlay.className = 'sidebar-overlay';
        document.body.appendChild(overlay);

        // 綁定事件
        const toggle = document.getElementById('sidebarToggle');
        const menu = document.getElementById('sidebarMenu');
        const languageToggle = document.getElementById('languageToggle');

        // 切換側邊欄顯示/隱藏
        toggle.addEventListener('click', function(e) {
            e.stopPropagation();
            menu.classList.toggle('active');
            overlay.classList.toggle('active');
        });

        // 點擊遮罩層關閉側邊欄
        overlay.addEventListener('click', function() {
            menu.classList.remove('active');
            overlay.classList.remove('active');
        });

        // 語言切換功能
        if (languageToggle) {
            languageToggle.addEventListener('click', function(e) {
                e.preventDefault();
                const currentPath = window.location.pathname;

                // 判斷當前語言並切換
                if (currentPath.includes('_en.html') || currentPath.includes('/html_en/')) {
                    // 當前是英文版，切換到中文版
                    if (currentPath.includes('_en.html')) {
                        const chinesePath = currentPath.replace('_en.html', '.html');
                        window.location.href = chinesePath;
                    } else if (currentPath.includes('/html_en/')) {
                        window.location.href = '../index.html';
                    }
                } else {
                    // 當前是中文版，切換到英文版
                    if (currentPath.includes('.html') && !currentPath.includes('_en.html')) {
                        const englishPath = currentPath.replace('.html', '_en.html');
                        window.location.href = englishPath;
                    } else if (currentPath.endsWith('/index.html')) {
                        window.location.href = 'html_en/index_en.html';
                    }
                }
            });
        }

        // 點擊側邊欄項目後關閉側邊欄
        const sidebarItems = document.querySelectorAll('.sidebar-item');
        sidebarItems.forEach(item => {
            item.addEventListener('click', function() {
                if (this.getAttribute('target') === '_blank') {
                    return; // 隨機分組不關閉側邊欄
                }
                menu.classList.remove('active');
                overlay.classList.remove('active');
            });
        });
    }

    // 執行初始化
    initSidebar();
});
```

### 2. 投影片導航系統
```javascript
document.addEventListener('DOMContentLoaded', () => {
    const slidesContainer = document.querySelector('.slides-container');
    const allSlides = Array.from(document.querySelectorAll('.slide'));
    const visibleSlides = allSlides.filter(s => s.dataset.hidden !== 'true');
    const prevBtn = document.getElementById('prev');
    const nextBtn = document.getElementById('next');

    let currentIndex = 0; // index within visibleSlides

    function showSlideByIndex(index) {
        const total = visibleSlides.length;
        if (total === 0) return;

        if (index >= total) {
            currentIndex = 0;
        } else if (index < 0) {
            currentIndex = total - 1;
        } else {
            currentIndex = index;
        }

        const targetSlide = visibleSlides[currentIndex];
        const absoluteIndex = allSlides.indexOf(targetSlide);
        const offset = -absoluteIndex * 100;
        slidesContainer.style.transform = `translateX(${offset}%)`;
    }

    nextBtn.addEventListener('click', () => {
        showSlideByIndex(currentIndex + 1);
    });

    prevBtn.addEventListener('click', () => {
        showSlideByIndex(currentIndex - 1);
    });

    document.addEventListener('keydown', (e) => {
        if (e.key === 'ArrowRight') {
            showSlideByIndex(currentIndex + 1);
        } else if (e.key === 'ArrowLeft') {
            showSlideByIndex(currentIndex - 1);
        }
    });

    // Initial setup
    showSlideByIndex(0);
});
```

### 3. Chart.js 配置
```javascript
// 全域圖表設定
Chart.defaults.color = '#5a5a5a';
Chart.defaults.borderColor = '#d1d1c2';
Chart.defaults.font.family = "'Calibri', 'Noto Sans TC', sans-serif";
Chart.defaults.plugins.legend.position = 'bottom';
Chart.defaults.maintainAspectRatio = false;

// 顏色調色板
const colorPalette = {
    primary: 'rgba(120, 120, 91, 0.7)',
    secondary: 'rgba(163, 163, 128, 0.7)',
    accent: 'rgba(180, 120, 120, 0.7)',
    success: 'rgba(120, 150, 120, 0.7)',
    info: 'rgba(120, 140, 160, 0.7)',
    warning: 'rgba(160, 140, 180, 0.7)'
};
```

### 4. 滾動動畫觸發器
```javascript
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.classList.add('visible');
        }
    });
}, {
    threshold: 0.1
});

document.querySelectorAll('.scroll-target').forEach(el => {
    observer.observe(el);
});
```

## 使用指南

### 側邊欄導航系統
每個頁面都應包含側邊欄導航系統，提供統一的導航功能：

#### 1. 引入側邊欄 JavaScript
```html
<script src="sidebar_tools/sidebar.js"></script>
```

#### 2. 側邊欄功能
- **回首頁**：根據當前頁面自動導向正確的首頁
- **切換語言**：智能判斷當前語言並切換到對應版本
- **隨機分組**：連結到隨機分組工具（新開分頁）

#### 3. 路徑設定
- **根目錄頁面**：`<script src="sidebar_tools/sidebar.js"></script>`
- **子目錄頁面**：`<script src="../sidebar_tools/sidebar.js"></script>`

#### 4. 自動初始化
側邊欄會在頁面載入時自動初始化，無需額外設定。

### 基本 HTML 結構
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>您的標題</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/chartjs-adapter-date-fns/dist/chartjs-adapter-date-fns.bundle.min.js"></script>
    <style>
        /* 在這裡包含所有 CSS 樣式 */
    </style>
</head>
<body>
    <div class="slides-container">
        <section class="slide">
            <h1>投影片標題</h1>
            <p class="slide-subtitle">副標題或描述</p>
        </section>

        <section class="slide">
            <h3>內容標題</h3>
            <div class="content-grid">
                <div class="content-section">
                    <h4>小標題</h4>
                    <p>內容文字</p>
                </div>
            </div>
        </section>
    </div>

    <div class="nav">
        <button id="prev" class="nav-btn">&#8249;</button>
        <button id="next" class="nav-btn">&#8250;</button>
    </div>
</body>
</html>
```

### 投影片類型

#### 封面投影片
```html
<section class="slide">
    <h1>主標題</h1>
    <p class="slide-subtitle">副標題或描述</p>
</section>
```

#### 內容投影片
```html
<section class="slide">
    <h3>內容標題</h3>
    <p>內容文字</p>
</section>
```

#### 雙欄內容投影片
```html
<section class="slide">
    <h3>內容標題</h3>
    <div class="content-grid">
        <div class="content-section">
            <h4>左側標題</h4>
            <p>左側內容</p>
        </div>
        <div class="content-section">
            <h4>右側標題</h4>
            <p>右側內容</p>
        </div>
    </div>
</section>
```

#### 圖表投影片 (chart-slide)
```html
<section class="slide chart-slide">
    <h3>圖表標題</h3>
    <div class="chart-wrapper">
        <canvas id="chartId"></canvas>
    </div>
</section>
```

**特色：**
- 加寬處理，充分利用投影片空間
- 圖表容器最大寬度無限制
- 標題置中對齊
- 手機版優化，確保可讀性

#### 影片投影片 (video-slide)
```html
<section class="slide video-slide">
    <h2>影片標題</h2>
    <p>影片描述（可選）</p>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/VIDEO_ID"
                title="YouTube video player"
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                allowfullscreen>
        </iframe>
    </div>
</section>
```

**特色：**
- 影片容器最大寬度 1600px（約為標準的兩倍）
- 保持 16:9 寬高比
- 自動置中對齊
- 手機版完全響應式適配

#### 作業投影片 (homework-slide)
```html
<section class="slide homework-slide">
    <h2>週二作業</h2>
    <div class="homework-content">
        <h4>作業標題</h4>
        <p style="background-color: #e8e5dc; padding: 15px; border-radius: 5px;">
            <strong>重要說明：</strong>作業內容描述
        </p>
        <p><strong>範例（但不要直接照抄）：</strong></p>
        <pre><code>• 範例問題一
• 範例問題二
• 範例問題三</code></pre>
        <p>其他說明文字</p>
    </div>
</section>
```

**特色：**
- 專門針對字多的內容優化
- 支援滾動顯示完整內容
- 作業說明框使用特殊樣式突出顯示
- 範例問題使用 code 區塊呈現，字體更小更緊湊
- 手機版進一步優化字體大小和間距
- 確保所有內容都能在螢幕上完整顯示

#### 手機版優化投影片
```html
<section class="slide">
    <h3>手機版優化標題</h3>
    <div class="content-grid">
        <div class="content-section">
            <h4>小標題</h4>
            <p>內容文字，在手機版會自動調整為單欄顯示</p>
        </div>
        <div class="content-section">
            <h4>另一個小標題</h4>
            <p>更多內容，確保在手機上可讀性良好</p>
        </div>
    </div>
</section>
```

#### 時間軸投影片
```html
<section class="slide">
    <h3>時間軸標題</h3>
    <div class="timeline-container">
        <div class="timeline-track">
            <div class="timeline-item">
                <div class="timeline-year">2023</div>
                <div class="timeline-content">
                    <div class="title">事件標題</div>
                    <div class="subtitle">事件描述</div>
                </div>
            </div>
        </div>
    </div>
</section>
```

#### 外部投影片預覽（Google Slides）
```html
<section class="slide">
    <h3>外部投影片預覽</h3>
    <div class="embed-wrapper">
        <iframe src="https://docs.google.com/presentation/d/SLIDE_ID/embed?start=false&loop=false&delayms=3000" allowfullscreen allow="autoplay"></iframe>
    </div>
</section>
```

小提示：
- 如需自動播放與循環，將 `start=true&loop=true`。
- 若不希望顯示外部來源連結，可不放置來源文字；或覆蓋一層透明連結以供點擊開新分頁（可選）。

```html
<!-- 透明覆蓋連結（可選） -->
<a href="https://docs.google.com/presentation/d/SLIDE_ID/edit" target="_blank" rel="noopener noreferrer"
   style="position:absolute; inset:0; z-index:5; text-indent:-9999px;">
   打開原始投影片
</a>
```

### 隱藏單一投影片
推薦使用 `data-hidden="true"` 來隱藏投影片，並保留版面寬度避免位移錯亂。

CSS：
```css
.slide[data-hidden="true"] {
    visibility: hidden;
    pointer-events: none;
}
```

HTML：
```html
<section class="slide" data-hidden="true">
    <h3>（隱藏中）</h3>
</section>
```

## 最佳實踐

### 1. 色彩使用
- 主要內容使用 `--text-color`
- 標題和強調元素使用 `--accent-color`
- 背景使用 `--bg-color`（淺米色，避免全白色）
- 邊框和分隔線使用 `--line-color`
- **避免全白色背景**：優先使用淺米色 `#F4F2EF` 營造溫暖視覺體驗
- 側邊欄和組件背景統一使用主背景色，保持視覺一致性

### 2. 間距規範
- 卡片間距：2rem
- 段落間距：1rem
- 標題下邊距：1rem
- 容器內邊距：2rem

### 3. 響應式設計
- 使用 `clamp()` 實現流暢縮放
- 移動端優先的設計方法
- 適當的斷點：767px (手機), 768px (平板), 1024px (桌面)
- 手機版必須考慮觸控操作和內容可讀性
- 投影片內容使用 `overflow-y: auto` 確保完整顯示
- 第一頁（標題頁）置中顯示，其他頁面支援滾動
- 長內容頁面從頂部開始顯示，避免內容被裁切

### 4. 無障礙設計
- 確保色彩對比度符合 WCAG 標準
- 提供鍵盤導航支持
- 使用語義化 HTML 標籤

### 5. Markdown 風格原則
- 避免過度使用卡片容器
- 直接呈現內容，減少視覺干擾
- 使用清晰的層次結構
- 保持簡潔的視覺設計

## 適用場景

- 學術簡報和教學材料
- 數據視覺化和圖表展示
- 專業報告和提案
- 產品介紹和展示
- 會議簡報和演講
- 課程簡介和課綱展示
- 時間軸和歷史展示

## 技術要求

- 現代瀏覽器支持
- CSS Grid 和 Flexbox 支持
- ES6+ JavaScript 支持
- Chart.js 3.x（如需要圖表功能）
- Chart.js Date Adapter（如需要時間軸圖表）
- 響應式設計支持（CSS Media Queries）
- 觸控設備支持（手機和平板）
- 滾動支持（overflow-y: auto）

## 多語言支援

### 檔案命名規範
- **中文版**：使用原始檔名（如 `w1.html`）
- **英文版**：使用 `_en` 後綴（如 `w1_en.html`）
- **首頁**：中文版為 `index.html`，英文版為 `index_en.html`

### 語言切換功能
每個首頁都應包含語言切換按鈕，使用統一的工具列樣式：

```html
<!-- 中文版首頁的語言切換 -->
<div class="top-toolbar">
    <a href="html_en/index_en.html" class="toolbar-link">English</a>
</div>

<!-- 英文版首頁的語言切換 -->
<div class="top-toolbar">
    <a href="../index.html" class="toolbar-link">中文</a>
</div>
```

```css
/* 左上角工具列樣式 */
.top-toolbar {
    position: fixed;
    top: 0.5rem;
    left: 0.5rem;
    z-index: 1000;
    display: flex;
    gap: 0.5rem;
    align-items: center;
}

.toolbar-link {
    display: inline-block;
    color: #ffffff;
    text-decoration: none;
    font-size: 0.63rem;
    padding: 0.21rem 0.42rem;
    border-radius: 0.25rem;
    background: #4d4d3b;
    transition: background-color 0.2s ease, color 0.2s ease;
}

.toolbar-link:hover {
    background: #3a3a2c;
    color: #ffffff;
}

/* 首頁容器調整 - 避免工具列遮擋內容 */
.container {
    padding-top: 3rem;
}

@media (min-width: 768px) {
    .container {
        padding-top: 3.2rem;
    }
}
```

### 回到首頁按鈕的多語言支援
- **中文版投影片**：`<a href="../index.html" class="home-link">首頁</a>`
- **英文版投影片**：`<a href="index_en.html" class="home-link">Home</a>`

### 按鈕樣式統一規範
所有按鈕（回到首頁、語言切換）都使用統一的樣式規範：

```css
/* 統一按鈕樣式 */
.unified-button {
    background: #4d4d3b;           /* 深色背景 */
    color: #ffffff;                /* 白色文字 */
    border: none;                  /* 無邊框 */
    font-size: 0.63rem;           /* 縮小 30% 的字體 */
    padding: 0.35rem 0.7rem;      /* 縮小 30% 的內邊距 */
    border-radius: 0.35rem;       /* 圓角 */
    transition: all 0.3s ease;    /* 平滑過渡 */
}

.unified-button:hover {
    background: #3a3a2c;          /* 深色懸停效果 */
    color: #ffffff;
    transform: translateY(-2px);  /* 輕微上移效果 */
}

/* 手機版進一步縮小 */
@media (max-width: 767px) {
    .unified-button {
        padding: 0.28rem 0.56rem;
        font-size: 0.56rem;
    }
}
```

### 翻譯注意事項
1. **HTML 屬性**：`lang` 屬性應設為對應語言（`zh-Hant` 或 `en`）
2. **標題翻譯**：頁面標題和投影片標題需完整翻譯
3. **圖表標籤**：Chart.js 圖表的所有標籤和工具提示都需翻譯
4. **技術術語**：保持專業術語的準確性
5. **文化適應**：適當調整表達方式以符合目標語言習慣
6. **投影片隱藏**：使用 `data-hidden="true"` 隱藏的投影片在兩個語言版本中應保持一致
7. **按鈕文字**：回到首頁按鈕使用對應語言（中文：「首頁」，英文：「Home」）
8. **講師姓名**：英文版使用羅馬拼音格式（如：YD (Yin-Dir, Hwang)）

## 檔案結構範例

```
project/
├── index.html                  # 中文版首頁
├── html/                       # 中文版投影片
│   ├── w1.html                 # 課程簡介投影片
│   ├── w1-2095-ai-forecast.html # AI 預測投影片
│   └── upcoming_gitignore/     # 被忽略的檔案
├── html_en/                    # 英文版投影片
│   ├── index_en.html           # 英文版首頁
│   ├── w1_en.html              # 課程簡介投影片（英文）
│   ├── w1-2095-ai-forecast_en.html # AI 預測投影片（英文）
│   └── upcoming_gitignore/     # 被忽略的檔案
├── .gitignore                  # Git 忽略檔案設定
└── slide_style.md              # 風格指南
```

### 實際專案結構
```
1141-gk2362k24/
├── index.html                  # 中文版首頁（課程內容）
├── html/
│   ├── w1.html                 # 第一週：課程簡介
│   └── w1-2095-ai-forecast.html # 第一週：2095 AI 預測
├── html_en/
│   ├── index_en.html           # 英文版首頁（Course Slides Collection）
│   ├── w1_en.html              # Week 1: Course Introduction
│   └── w1-2095-ai-forecast_en.html # Week 1: 2095 AI Forecast
├── .gitignore                  # 忽略 html/upcoming_gitignore/ 和 html_en/upcoming_gitignore/
└── slide_style.md              # 本風格指南
```

---

*此風格指南基於實際項目經驗總結，旨在提供一致且專業的視覺體驗。適用於學術簡報、教學材料和專業報告的製作。*