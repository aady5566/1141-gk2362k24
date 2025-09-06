# Slide Style Guide - 簡報設計風格指南

## 概述

這是一個專為學術簡報、數據視覺化和專業報告設計的現代化風格系統。該風格強調低飽和度色彩、優雅的排版和流暢的動畫效果，營造出專業而舒適的視覺體驗。

## 設計哲學

- **低飽和度美學**：使用溫和、不刺眼的色彩，適合長時間閱讀
- **優雅簡約**：避免過度設計，專注於內容呈現
- **響應式優先**：確保在各種裝置上都有良好的顯示效果
- **無障礙設計**：考慮視覺障礙用戶的使用體驗
- **Markdown 風格**：簡潔直接的內容呈現，減少視覺干擾

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
    font-size: clamp(1.2rem, 3vw, 1.8rem);
    font-weight: 300;
    color: var(--accent-color);
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
    justify-content: center;
    align-items: center;
    padding: 5vw;
    text-align: center;
    position: relative;
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

### 1. 卡片容器（傳統樣式）
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

### 2. Markdown 風格內容佈局
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

### 3. 時間軸組件
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

### 4. 課程大綱組件
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

### 5. 破冰活動組件
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

### 1. 投影片導航系統
```javascript
document.addEventListener('DOMContentLoaded', () => {
    const slidesContainer = document.querySelector('.slides-container');
    const slides = document.querySelectorAll('.slide');
    const prevBtn = document.getElementById('prev');
    const nextBtn = document.getElementById('next');

    let currentSlide = 0;
    const totalSlides = slides.length;

    function showSlide(index) {
        if (index >= totalSlides) {
            currentSlide = 0;
        } else if (index < 0) {
            currentSlide = totalSlides - 1;
        } else {
            currentSlide = index;
        }

        const offset = -currentSlide * 100;
        slidesContainer.style.transform = `translateX(${offset}%)`;
    }

    nextBtn.addEventListener('click', () => {
        showSlide(currentSlide + 1);
    });

    prevBtn.addEventListener('click', () => {
        showSlide(currentSlide - 1);
    });

    document.addEventListener('keydown', (e) => {
        if (e.key === 'ArrowRight') {
            showSlide(currentSlide + 1);
        } else if (e.key === 'ArrowLeft') {
            showSlide(currentSlide - 1);
        }
    });

    // Initial setup
    showSlide(0);
});
```

### 2. Chart.js 配置
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

### 3. 滾動動畫觸發器
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

### 1. 基本 HTML 結構
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

### 2. 投影片類型

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

#### 圖表投影片
```html
<section class="slide">
    <h3>圖表標題</h3>
    <div class="chart-wrapper">
        <canvas id="chartId"></canvas>
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

## 最佳實踐

### 1. 色彩使用
- 主要內容使用 `--text-color`
- 標題和強調元素使用 `--accent-color`
- 背景使用 `--bg-color`
- 邊框和分隔線使用 `--line-color`

### 2. 間距規範
- 卡片間距：2rem
- 段落間距：1rem
- 標題下邊距：1rem
- 容器內邊距：2rem

### 3. 響應式設計
- 使用 `clamp()` 實現流暢縮放
- 移動端優先的設計方法
- 適當的斷點：768px, 1024px

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

## 檔案結構範例

```
project/
├── html/
│   ├── week1.html              # 課程簡介投影片
│   ├── ai-social-work.html     # AI 與社會工作投影片
│   ├── 2095-ai-forecast.html   # AI 預測投影片
│   └── slide_style.md          # 風格指南
└── assets/
    ├── images/                 # 圖片資源
    └── data/                   # 數據檔案
```

---

*此風格指南基於實際項目經驗總結，旨在提供一致且專業的視覺體驗。適用於學術簡報、教學材料和專業報告的製作。*