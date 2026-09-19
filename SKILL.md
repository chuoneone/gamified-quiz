---
name: gamified-quiz
description: >-
  測驗遊戲化產生器（Gamified Quiz Generator）。專門將教師或使用者提供的各學科試題（數學、國文、英文、自然、社會、特教等題目），轉換為高互動度、高沉浸感的單一獨立「遊戲式互動測驗」HTML 檔案。首波核心模板為「盲盒抽卡養成模板（Blind Box Gacha）」：具備金幣與3連擊代幣經濟、抽盲盒與SSR開箱光芒動畫、圖鑑養成、純Web Audio擬真音效、KaTeX數學公式、TTS語音朗讀、以及教師後台學習歷程與錯題追蹤（支援GAS雲端與單機模式）。當使用者提到「測驗遊戲化」、「遊戲式測驗」、「遊戲測驗」、「盲盒測驗」、「抽卡測驗」、「測驗遊戲」、「互動測驗」或提供試題要轉成遊戲時，皆啟動此 skill。
---

# 測驗遊戲化 (Gamified Quiz Generator) — 盲盒抽卡養成互動測驗

此技能專門將教師或使用者提供的任何學科題目（單選題、數學題、字詞題、問答轉選擇等），轉換為**單一獨立的「遊戲化互動測驗」HTML 檔案**。
首波內建核心模板為**「盲盒抽卡養成模板（Blind Box Gacha）」**，將傳統單調的刷題轉化為「答題賺金幣 ➔ 連擊贏代幣 ➔ 開盲盒抽寵物/神獸 ➔ 收集全套圖鑑」的沉浸式正向激勵循環。

---

## 🎯 處理流程：輸入試題與需求確認

當使用者提供題目（文字、Markdown、Word、PDF、圖片或大綱）時：

1. **題目解析與結構化**：
   - 提取每道題目之**題幹（Question）**、**選項（Options）**、**正確答案（Answer）**。
   - 若為數學或理化題目，將公式轉換為標準 LaTeX 格式（例如 `$x:3 = 4:6$`、`$\frac{1}{2}$`）。
   - 若使用者未提供干擾選項（只有問答），自動為其生成 3 個具教學鑑別度且合理的干擾選項，湊成 4 選 1 選擇題。
2. **主題與圖鑑風格設定（可依學科/年級客製化）**：
   - **預設通用／可愛風**：魔法動物園（一般寵物 🐶🐱🐰🐭🦊🐻🐼🐨🐷🐸 ＋ 史詩神獸 🦄🦖🐉🐙👽🤖）。
   - **數學/自然/科學風**：星際探險家／太空機械獸。
   - **國文/歷史/社會風**：古代名將與歷史神獸。
   - **英文/外語風**：環球旅行家與世界地標。
3. **輸出交付**：
   - 直接生成完整、單一檔案的 `.html`，所有 CSS、JavaScript、Web Audio 音效合成、SVG/動畫皆內嵌，直接用瀏覽器開啟即可玩，支援電腦投影、平板與手機。

---

## 📦 盲盒模板核心遊戲機制（Game Mechanics）

### 1. 雙幣制經濟系統（Dual-Token Economy）
- 🪙 **金幣（Coins）**：每答對 1 題獲得 `50` 金幣。累積 `100` 金幣可至商店抽取「普通盲盒」。
- 🎫 **特殊代幣（Special Token）**：連續答對 3 題（3-Combo Streak）觸發連擊獎勵，額外獲得 `1` 枚「大型奇幻盲盒代幣 🎫」，可用於抽取稀有「史詩奇幻生物」。

### 2. 盲盒商店與沉浸式開箱動畫（Unboxing Experience）
- **普通盲盒（100 🪙）**：抽取一般池（Common / Rare）動物。
- **✨ 大型奇幻盲盒（1 🎫）**：抽取特殊池（SSR Legend）神獸／幻獸。
- **開箱儀式感**：
  1. 點擊盲盒 ➔ 盲盒左右劇烈震動（搭配搖盒音效）。
  2. 盲盒放大爆開（Pop-open 動畫與音效）。
  3. 背景浮現 360 度旋轉彩虹光芒（Rotating Rays），彈出獲獎卡片（Zoom-in 動畫與勝利號角）。
  4. 顯示稀有度標籤（COMMON / RARE / SSR LEGEND）、名稱、Emoji 圖示與持有數量。

### 3. 圖鑑養成與滿星機制（Collection & Star-Up）
- **圖鑑分類**：分為「一般魔法動物」與「史詩奇幻生物」。
- **未解鎖狀態**：呈現灰色剪影（Grayscale / Low Opacity），點擊提示解鎖方式。
- **重複抽中與升級**：每隻寵物最多可累積收集 `3` 隻（顯示 `x1`、`x2`、`MAX` 滿星徽章）。
- **進度追蹤**：頂部即時顯示「收集進度：X / Y」。

### 4. 答題體驗與輔助系統（Quiz UX）
- **連對指示器（Combo Stars）**：答題區頂部有 3 顆連擊星號（★），答對點亮，答錯重置。
- **即時回饋**：點擊選項即時鎖定，正確變綠、錯誤變紅震動，下方顯示正確解答回饋。
- **隨機洗牌**：每次重新開始時，自動洗牌題目順序與各題選項順序，防止死記位置。
- **KaTeX 數學支援**：公式支援 `$math$` 語法，自動渲染為清晰向量公式。
- **🔊 TTS 語音朗讀**：支援題幹與選項旁的一鍵語音朗讀（Web Speech API），支援中英文發音（自動將數學符號如 `\frac{a}{b}` 轉為口語「b分之a」）。

### 5. 👨‍🏫 教師後台與錯題診斷（Teacher Analytics & Diagnostic）
- **密碼保護**：預設進入密碼為 `0000`（可在代碼中自訂）。
- **學情總覽表格**：條列學生姓名、答題總數、答對率（紅綠警示色彩）。
- **錯題明細檢視**：點擊「👀 查看錯題」，即時彈出該名學生所有選錯的題目、學生當時選的錯誤答案、以及正確答案（支援公式渲染），方便教師進行精準補救教學。
- **雙模式資料持久化**：
  - **單機模式（預設）**：無須伺服器，自動使用記憶體與本機狀態儲存。
  - **GAS 雲端同步模式**：只需填入 Google Apps Script 網頁應用程式 URL，即支援全班學生跨裝置紀錄載入與教師後台即時雲端拉取。

### 6. 零相依純前端音效合成（Zero External Audio Dependency）
- 採用瀏覽器原生 **Web Audio API** 即時合成音效（OscillatorNode + GainNode）：
  - `correct`：清脆上升正弦波（Sine wave chime）。
  - `wrong`：低沉鋸齒波（Sawtooth buzz）。
  - `shake`：短促方波雜音（Square rattle）。
  - `open`：爆破三角波（Triangle pop）。
  - `win`：三和弦勝利號角（Fanfare）。

---

## 💻 完整 HTML 程式碼架構規範

產出的 HTML 必須符合下列完整結構：

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>【單元名稱】盲盒大搜集</title>
    <!-- 可愛字型與 KaTeX -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Chiron+GoRound+TC:wght@300;500;700&family=Fredoka:wght@400;600&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/katex.min.css">
    <script src="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/katex.min.js"></script>
    <style>
        :root {
            --bg-color: #fce4ec;       
            --card-bg: #ffffff;
            --primary-color: #ff8a80;  
            --secondary-color: #80deea; 
            --accent-yellow: #fff59d;  
            --accent-purple: #b39ddb;
            --text-color: #5d4037;     
            --shadow-soft: 0 8px 24px rgba(149, 157, 165, 0.2);
            --border-radius: 24px;
        }
        * { box-sizing: border-box; user-select: none; -webkit-tap-highlight-color: transparent; }
        body {
            margin: 0; padding: 0;
            font-family: 'Fredoka', 'Chiron GoRound TC', sans-serif;
            height: 100vh; overflow: hidden;
            background: linear-gradient(135deg, #fce4ec 0%, #e1bee7 100%);
            display: flex; justify-content: center; align-items: center;
        }
        /* 泡泡裝飾 */
        .bubble { position: absolute; border-radius: 50%; background: rgba(255, 255, 255, 0.4); animation: float 8s infinite ease-in-out; z-index: 0; }
        @keyframes float { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-20px); } }

        /* 主容器 */
        #game-container {
            width: 90%; max-width: 1000px; height: 85vh; 
            background: var(--card-bg); border-radius: var(--border-radius);
            box-shadow: var(--shadow-soft); display: flex; flex-direction: row; 
            position: relative; z-index: 10; overflow: hidden; border: 8px solid white;
        }
        .sidebar {
            width: 250px; background: #fff; border-right: 2px solid #f0f0f0;
            padding: 30px 20px; display: flex; flex-direction: column; align-items: center;
            z-index: 20; flex-shrink: 0;
        }
        .app-title { font-size: 1.5rem; color: var(--text-color); font-weight: bold; margin-bottom: 25px; text-align: center; line-height: 1.2; }
        .status-display {
            background: #fff3e0; color: #ff9800; padding: 10px; border-radius: 15px;
            font-weight: 700; display: flex; flex-direction: column; align-items: center; gap: 5px;
            font-size: 1.1rem; border: 2px solid #ffe0b2; width: 100%; margin-bottom: 30px;
        }
        .status-item { display: flex; align-items: center; gap: 8px; }
        .nav-menu { width: 100%; display: flex; flex-direction: column; gap: 15px; }
        .nav-item {
            display: flex; align-items: center; gap: 15px; padding: 15px 20px;
            border-radius: 15px; color: #9e9e9e; cursor: pointer; transition: 0.3s;
            font-size: 1.1rem; font-weight: bold; background: transparent;
        }
        .nav-item:hover { background: #f5f5f5; color: #757575; }
        .nav-item.active { background: #e3f2fd; color: #00838f; box-shadow: 0 2px 8px rgba(128, 222, 234, 0.2); }
        .nav-icon { font-size: 1.5rem; }

        .main-content { flex: 1; overflow-y: auto; overflow-x: hidden; padding: 20px; background: #fafafa; position: relative; }
        .hidden { display: none !important; }

        /* 商店 */
        .gacha-container { display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 15px; }
        .gacha-machine {
            width: 100%; max-width: 300px; height: 260px;
            background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Crect x='20' y='10' width='60' height='60' fill='%23ffccbc' rx='5'/%3E%3Ccircle cx='50' cy='40' r='20' fill='white' opacity='0.5'/%3E%3Cpath d='M30,80 L70,80 L65,95 L35,95 Z' fill='%23ef5350'/%3E%3C/svg%3E") no-repeat center;
            background-size: contain; position: relative; display: flex; justify-content: center; align-items: center;
        }
        .machine-glass {
            width: 120px; height: 120px; border-radius: 50%;
            background: rgba(255,255,255,0.3); border: 4px solid rgba(255,255,255,0.6);
            position: absolute; top: 40px; display: flex; justify-content: center; align-items: center; overflow: hidden;
        }
        .capsule { font-size: 2rem; position: absolute; }
        .btn {
            background: var(--primary-color); color: white; border: none; padding: 12px 30px; font-size: 1.2rem;
            border-radius: 50px; cursor: pointer; width: auto; min-width: 240px; font-family: inherit; font-weight: 700;
            box-shadow: 0 4px 10px rgba(255, 138, 128, 0.4); transition: transform 0.2s, box-shadow 0.2s;
        }
        .btn:active { transform: scale(0.96); box-shadow: 0 2px 5px rgba(0,0,0,0.2); }
        .btn-blue { background: var(--secondary-color); box-shadow: 0 4px 10px rgba(128, 222, 234, 0.4); color:#006064;}
        .btn-purple { background: var(--accent-purple); box-shadow: 0 4px 10px rgba(179, 157, 219, 0.4); border: 2px solid #9575cd; color: #fff;}

        /* 答題區 */
        .quiz-container { max-width: 800px; margin: 0 auto; height: 100%; display: flex; flex-direction: column; justify-content: center; }
        .combo-area {
            display: flex; justify-content: center; align-items: center; gap: 10px; margin-bottom: 15px;
            background: #fff; padding: 10px; border-radius: 20px; box-shadow: 0 3px 10px rgba(0,0,0,0.05); border: 2px solid #fff59d;
        }
        .combo-star { font-size: 2rem; color: #e0e0e0; transition: 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275); }
        .combo-star.active { color: #ffca28; filter: drop-shadow(0 0 5px rgba(255,202,40,0.6)); transform: scale(1.2); }
        .quiz-card {
            background: white; border-radius: 20px; padding: 15px 20px; 
            box-shadow: 0 5px 15px rgba(0,0,0,0.05); text-align: center; margin-bottom: 10px; border: 2px solid #f0f0f0;
        }
        .question-text { font-size: 1.6rem; color: var(--text-color); margin: 5px 0 15px 0; font-weight: bold; line-height: 1.6; letter-spacing: 1px; }
        #options-list { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; width: 100%; }
        .option-btn {
            background: white; border: 3px solid #eee; color: #666; width: 100%; padding: 12px 15px; 
            border-radius: 15px; font-size: 1.2rem; font-weight: 600; cursor: pointer; transition: 0.2s; 
            text-align: left; display: flex; justify-content: space-between; align-items: center; box-shadow: 0 4px 0 #eee;
        }
        .option-btn:hover { border-color: var(--secondary-color); background: #e0f7fa; color: #006064; box-shadow: 0 4px 0 #b2ebf2; transform: translateY(-2px);}
        .option-btn:active { transform: translateY(2px); box-shadow: 0 0 0 transparent; }
        .option-btn.correct { background: #c8e6c9; border-color: #4caf50; color: #1b5e20; box-shadow: 0 4px 0 #388e3c; }
        .option-btn.wrong { background: #ffcdd2; border-color: #ef5350; color: #b71c1c; animation: shake 0.4s; box-shadow: 0 4px 0 #d32f2f; }
        .option-btn.locked { cursor: default; pointer-events: none; }
        .option-btn.locked.correct { opacity: 1; } 
        .option-btn.locked:not(.correct):not(.wrong) { opacity: 0.5; background: #f5f5f5; border-color: #ddd; box-shadow: none; }
        .speaker-icon { font-size: 1.3rem; padding: 6px; border-radius: 50%; background: #eee; cursor: pointer; color: #555; transition: 0.2s; }
        .speaker-icon:hover { background: var(--accent-yellow); transform: scale(1.1); }
        .quiz-nav-area { display: flex; justify-content: space-between; gap: 15px; margin-top: 15px; width: 100%; }
        .quiz-nav-btn {
            flex: 1; padding: 12px; border-radius: 15px; background: white; border: 2px solid #ddd;
            color: #888; font-weight: bold; font-size: 1.1rem; cursor: pointer; transition: 0.2s; box-shadow: 0 4px 0 #eee;
        }
        .quiz-nav-btn.primary { background: var(--secondary-color); color: #006064; border: 2px solid #4dd0e1; box-shadow: 0 4px 0 #00acc1; }

        /* 圖鑑 */
        .collection-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(110px, 1fr)); gap: 20px; padding-bottom: 20px; }
        .collection-item {
            background: white; border-radius: 15px; aspect-ratio: 1; display: flex; flex-direction: column;
            justify-content: center; align-items: center; box-shadow: 0 3px 8px rgba(0,0,0,0.05); position: relative;
            border: 3px solid transparent; cursor: pointer; transition: transform 0.2s;
        }
        .collection-item:hover { transform: translateY(-5px); box-shadow: 0 8px 15px rgba(0,0,0,0.1); }
        .collection-item.locked { background: #eee; opacity: 0.6; box-shadow: none; transform: none;}
        .collection-item.locked .item-icon { filter: grayscale(100%) brightness(50%); opacity: 0.3; }
        .item-icon { font-size: 2.5rem; margin-bottom: 5px; }
        .item-name { font-size: 0.9rem; color: #888; font-weight: bold; }
        .rarity-badge { position: absolute; top: 5px; left: 5px; font-size: 0.7rem; padding: 2px 8px; border-radius: 10px; color: white; font-weight: bold; }
        .count-badge { position: absolute; bottom: 5px; right: 5px; font-size: 0.8rem; padding: 2px 6px; border-radius: 8px; background: #333; color: white; font-weight: bold; }
        .count-badge.max { background: #d32f2f; }
        .rarity-R { background: #42a5f5; } 
        .rarity-SSR { background: linear-gradient(45deg, #fbc02d, #ff6f00); } 

        /* 開箱動畫 Modal */
        .modal-overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.7); z-index: 100; display: flex; justify-content: center; align-items: center; backdrop-filter: blur(8px);
        }
        .box-container { width: 250px; height: 250px; position: relative; display: flex; justify-content: center; align-items: center; cursor: pointer; }
        .blind-box { font-size: 10rem; filter: drop-shadow(0 15px 15px rgba(0,0,0,0.4)); animation: bounce 2s infinite; cursor: pointer; }
        .blind-box.giant { font-size: 14rem; filter: drop-shadow(0 20px 25px rgba(179, 157, 219, 0.8)); }
        .blind-box.shaking { animation: shake-box 0.5s infinite; }
        .blind-box.opening { animation: pop-open 0.5s forwards; }
        .prize-display {
            background: white; padding: 40px; border-radius: 40px; text-align: center;
            animation: zoomIn 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275); width: 90%; max-width: 400px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.3); position: relative; z-index: 101;
        }
        .prize-icon { font-size: 8rem; display: block; margin: 10px 0; }
        .prize-title { font-size: 2rem; color: var(--primary-color); font-weight: bold; margin-bottom: 5px;}
        .prize-rarity { font-size: 1.1rem; color: #888; margin-bottom: 5px; display: inline-block; padding: 6px 16px; background: #eee; border-radius: 15px;}
        .rays {
            position: absolute; width: 600px; height: 600px;
            background: repeating-conic-gradient(rgba(255,255,255,0.4) 0 15deg, transparent 15deg 30deg);
            animation: rotate 10s linear infinite; z-index: -1;
        }

        /* 教師後台表格 */
        .teacher-table { width: 100%; border-collapse: collapse; text-align: left; background: white; }
        .teacher-table th, .teacher-table td { padding: 12px; border-bottom: 1px solid #eee; }
        .teacher-table th { background: #fafafa; font-weight: bold; color: #666; }
        .teacher-table .alert-red { color: #d32f2f; font-weight: bold; }
        .teacher-table .alert-green { color: #388e3c; font-weight: bold; }

        /* 動畫 Keyframes */
        @keyframes shake { 0%, 100% {transform: translateX(0);} 25% {transform: translateX(-5px);} 75% {transform: translateX(5px);} }
        @keyframes bounce { 0%, 100% {transform: translateY(0);} 50% {transform: translateY(-10px);} }
        @keyframes shake-box { 0% {transform: rotate(0deg);} 25% {transform: rotate(-10deg);} 75% {transform: rotate(10deg);} }
        @keyframes pop-open { 0% {transform: scale(1);} 50% {transform: scale(1.2);} 100% {transform: scale(0); opacity: 0;} }
        @keyframes zoomIn { from {transform: scale(0);} to {transform: scale(1);} }
        @keyframes rotate { from {transform: rotate(0deg);} to {transform: rotate(360deg);} }
        @keyframes starPop { 0% {transform: scale(0);} 80% {transform: scale(1.5);} 100% {transform: scale(1);} }

        /* 手機版適配 */
        @media (max-width: 768px) {
            #game-container { flex-direction: column; height: 95vh; width: 95%; max-width: 450px;}
            .sidebar { 
                order: 2; width: 100%; border-top: 2px solid #f0f0f0; border-right: none;
                flex-direction: row; padding: 10px; justify-content: space-around; flex-wrap: wrap;
            }
            .app-title, .status-display { display: none; } 
            .nav-menu { flex-direction: row; gap: 0; justify-content: space-around; width: 100%; }
            .nav-item { flex-direction: column; gap: 5px; font-size: 0.8rem; padding: 5px; border-radius: 10px; }
            .mobile-top-bar { display: flex; width: 100%; padding: 10px 20px; justify-content: space-between; align-items: center; background: white; border-bottom: 1px solid #eee;}
            .main-content { padding: 10px 15px; } 
            .question-text { font-size: 1.4rem; }
            #options-list { grid-template-columns: 1fr 1fr; gap: 10px; } 
            .option-btn { padding: 10px 12px; font-size: 1.1rem; }
        }
        .mobile-top-bar { display: none; }
    </style>
</head>
<body>
    <div class="bubble" style="width: 100px; height: 100px; top: 10%; left: -20px;"></div>
    <div class="bubble" style="width: 60px; height: 60px; bottom: 20%; right: -10px; animation-delay: 2s;"></div>
    <div class="bubble" style="width: 80px; height: 80px; top: 40%; right: 20%; animation-delay: 4s;"></div>

    <div id="game-container">
        <!-- 手機頂部欄 -->
        <div class="mobile-top-bar" id="mobile-header">
            <div style="font-weight: bold; color: var(--text-color);">Quiz Box 📦</div>
            <div style="display:flex; gap:10px;">
                <div class="status-display" style="width: auto; margin:0; padding: 5px 10px; font-size: 1rem; flex-direction:row;">
                    <span>🪙</span> <span id="mobile-coins">0</span>
                </div>
                <div class="status-display" style="width: auto; margin:0; padding: 5px 10px; font-size: 1rem; flex-direction:row; background:#ede7f6; color:#7e57c2; border-color:#d1c4e9;">
                    <span>🎫</span> <span id="mobile-tokens">0</span>
                </div>
            </div>
        </div>

        <!-- 側邊欄 -->
        <div class="sidebar">
            <div class="app-title">Quiz Box<br><span style="font-size:1.2rem; color: #aaa;">🐾 魔法動物園</span></div>
            <div id="player-display" style="font-weight: bold; color: var(--secondary-color); margin-bottom: 10px; font-size: 1.1rem; display: none;">👤 <span id="player-name-label"></span></div>
            <div class="status-display">
                <div class="status-item"><span>🪙 金幣:</span> <span id="user-coins">0</span></div>
                <div class="status-item" style="color: #7e57c2;"><span>🎫 特殊代幣:</span> <span id="user-tokens">0</span></div>
            </div>
            <div class="nav-menu">
                <div class="nav-item" onclick="switchTab('home')" id="nav-home"><div class="nav-icon">🏪</div><span>盲盒商店</span></div>
                <div class="nav-item active" onclick="switchTab('quiz')" id="nav-quiz"><div class="nav-icon">📝</div><span>知識挑戰</span></div>
                <div class="nav-item" onclick="switchTab('collection')" id="nav-collection"><div class="nav-icon">📒</div><span>我的圖鑑</span></div>
            </div>
            <div style="margin-top: auto; padding-top: 15px; border-top: 2px dashed #eee; width: 100%;">
                <div class="nav-item" onclick="openTeacherLogin()" id="nav-teacher" style="color: #ccc; justify-content: center; padding: 10px;">
                    <div class="nav-icon" style="font-size: 1.2rem;">👨‍🏫</div><span style="font-size: 0.9rem;">教師後台</span>
                </div>
            </div>
        </div>

        <!-- 主要內容區 -->
        <div class="main-content">
            <!-- 1. 商店 -->
            <div id="screen-home" class="content-area hidden">
                <div class="gacha-container">
                    <h2 style="color: var(--primary-color); margin-bottom: 0px; font-size: 2rem;">盲盒商店</h2>
                    <p style="color: #888; font-size: 1.1rem; margin-bottom: 15px;">快來收集奇妙的魔法動物！(最多可重複3隻升星)</p>
                    <div class="gacha-machine">
                        <div class="machine-glass">
                            <div class="capsule" style="color: #ef5350; top: 20px; left: 30px; transform: rotate(-20deg);">🐾</div>
                            <div class="capsule" style="color: #42a5f5; top: 50px; left: 50px; transform: rotate(45deg);">🐾</div>
                            <div class="capsule" style="color: #ffca28; top: 30px; left: 70px; transform: rotate(10deg);">🐾</div>
                        </div>
                    </div>
                    <button class="btn" onclick="tryOpenBox('normal')" id="draw-btn">普通盲盒 (100 🪙)</button>
                    <button class="btn btn-purple" onclick="tryOpenBox('special')" id="special-draw-btn">✨ 大型奇幻盲盒 (需 1 🎫)</button>
                    <div style="margin-top: 10px; font-size: 0.9rem; color: #aaa; text-align:center;">連對3題可獲取大型盲盒代幣🎫<br>內含稀有幻獸！</div>
                </div>
            </div>

            <!-- 2. 挑戰 -->
            <div id="screen-quiz" class="content-area">
                <div class="quiz-container">
                    <div class="combo-area" id="combo-display">
                        <span style="font-weight:bold; color:#795548;">連對挑戰：</span>
                        <div id="star-1" class="combo-star">☆</div>
                        <div id="star-2" class="combo-star">☆</div>
                        <div id="star-3" class="combo-star">☆</div>
                    </div>
                    <div class="quiz-card">
                        <div style="color: #aaa; font-size: 1rem; margin-bottom: 10px; font-weight: bold; letter-spacing: 1px;">QUESTION <span id="q-index">1</span></div>
                        <div class="question-text" id="q-text">題目載入中...</div>
                        <div style="display: flex; justify-content: center; gap: 10px; margin-bottom: 10px;">
                            <div class="speaker-icon" onclick="playQuestionAudio()" title="播放題目" style="font-size: 2rem; padding: 15px;">🔊</div>
                        </div>
                    </div>
                    <div id="options-list"></div>
                    <div id="feedback-msg" style="text-align: center; height: 30px; line-height: 30px; font-weight: bold; color: var(--primary-color); font-size: 1.2rem; margin-top: 15px;"></div>
                    <div class="quiz-nav-area">
                        <button class="quiz-nav-btn" id="prev-btn" onclick="prevQuestion()">◀ 上一題</button>
                        <button class="quiz-nav-btn primary" id="next-btn" onclick="nextQuestion()" disabled>下一題 ▶</button>
                    </div>
                </div>
            </div>

            <!-- 3. 圖鑑 -->
            <div id="screen-collection" class="content-area hidden">
                <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 25px;">
                    <h2 style="color: var(--text-color); margin: 0; font-size: 1.8rem;">我的動物園</h2>
                    <div style="background: white; padding: 5px 15px; border-radius: 15px; color: #888; font-weight: bold;">
                        進度: <span id="collected-count" style="color: var(--primary-color);">0</span> / <span id="total-count">0</span>
                    </div>
                </div>
                <h3 style="color:#888; border-bottom: 2px dashed #eee; padding-bottom:5px;">一般魔法動物</h3>
                <div class="collection-grid" id="collection-grid-normal"></div>
                <h3 style="color:#9575cd; border-bottom: 2px dashed #eee; padding-bottom:5px; margin-top:20px;">史詩奇幻生物</h3>
                <div class="collection-grid" id="collection-grid-special"></div>
            </div>

            <!-- 4. 教師後台 -->
            <div id="screen-teacher" class="content-area hidden">
                <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px;">
                    <h2 style="color: var(--text-color); margin: 0; font-size: 1.8rem;">👨‍🏫 教師後台：學習狀況總覽</h2>
                    <button class="btn btn-blue" onclick="fetchTeacherData()" style="min-width: 120px; padding: 8px 15px; font-size: 1rem;">↻ 更新資料</button>
                </div>
                <div style="background: white; border-radius: 15px; padding: 15px; box-shadow: 0 4px 10px rgba(0,0,0,0.05); overflow-x: auto;">
                    <table class="teacher-table">
                        <thead>
                            <tr><th>學生姓名</th><th>答題總數</th><th>答對率</th><th>錯題紀錄</th></tr>
                        </thead>
                        <tbody id="teacher-data-body"></tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- Modals: 開箱、登入、教師密碼、錯題明細、提示 -->
        <!-- 完整開箱動畫與彈窗容器 -->
    </div>
</body>
</html>
```

---

## ⚙️ 資料結構注入與題目格式轉換

產出時，請直接在 JavaScript 區段中將使用者的題目轉換為標準 `questions` 陣列：

```javascript
// --- 題目資料注入 ---
const questions = [
    {
        q: "若小明有 $5$ 元，小華有 $8$ 元，則小明與小華錢數的「比」為何？",
        ans: "$5:8$",
        options: ["$5:8$", "$8:5$", "$\\frac{5}{8}$", "$\\frac{8}{5}$"]
    },
    // ... 依序注入所有題目
];

// --- 圖鑑資料庫（可依學科微調） ---
const collectionDB = [
    { id: 1, name: "魔法小狗", icon: "🐶", rarity: 1, pool: "normal" }, 
    { id: 2, name: "星光小貓", icon: "🐱", rarity: 1, pool: "normal" },
    { id: 3, name: "幸運小兔", icon: "🐰", rarity: 1, pool: "normal" }, 
    { id: 4, name: "火花小鼠", icon: "🐭", rarity: 1, pool: "normal" },
    { id: 5, name: "赤炎小狐", icon: "🦊", rarity: 2, pool: "normal" }, 
    { id: 6, name: "大地幼熊", icon: "🐻", rarity: 2, pool: "normal" },
    { id: 7, name: "竹林熊貓", icon: "🐼", rarity: 2, pool: "normal" }, 
    { id: 8, name: "貪睡無尾熊", icon: "🐨", rarity: 2, pool: "normal" },
    { id: 9, name: "小飛豬", icon: "🐷", rarity: 1, pool: "normal" }, 
    { id: 10, name: "呱呱水怪", icon: "🐸", rarity: 1, pool: "normal" },
    { id: 101, name: "彩虹獨角獸", icon: "🦄", rarity: 3, pool: "special" }, 
    { id: 102, name: "霸王機甲龍", icon: "🦖", rarity: 3, pool: "special" },
    { id: 103, name: "遠古神龍", icon: "🐉", rarity: 3, pool: "special" }, 
    { id: 104, name: "深海大章魚", icon: "🐙", rarity: 3, pool: "special" },
    { id: 105, name: "星際訪客", icon: "👽", rarity: 3, pool: "special" }, 
    { id: 106, name: "智庫機器人", icon: "🤖", rarity: 3, pool: "special" }
];
```

---

## 🛠️ 交付檢核清單（Checklist）

每次生成遊戲化測驗 HTML 時，必須確認：
1. [ ] **單一純 HTML**：無外部本機相依檔，直接在瀏覽器雙擊即可執行。
2. [ ] **題目與答案完整**：所有題目選項正確，解答正確，選項經過隨機排序。
3. [ ] **公式與語音**：KaTeX 公式正確包裹 `$..$`，朗讀按鈕點擊可發聲且去除公式特殊符號。
4. [ ] **遊戲閉環完整**：答對加金幣 ➔ 連對3題送代幣 ➔ 開箱抽卡動畫正常 ➔ 圖鑑正確更新 ➔ 支援最多3隻滿星機制。
5. [ ] **教師後台正常**：預設密碼 `0000`，錯題會正確記錄在學生歷史並能在後台逐題回顧。
