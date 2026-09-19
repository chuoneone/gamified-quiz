# 🎮 測驗遊戲化產生器 (Gamified Quiz Generator)

> 將枯燥的各學科練習題，一鍵轉換為高互動度、高沉浸感的單一檔案「遊戲化互動測驗」！

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Antigravity Skill](https://img.shields.io/badge/Antigravity-Skill-blue.svg)](https://github.com)

---

## 🌟 核心特色（首波：盲盒抽卡養成模板）

- 📦 **單一獨立 HTML 檔案**：純前端零伺服器依賴，任何裝置（電腦、平板、手機、大屏）開箱即用。
- 🪙 **雙幣制激勵經濟**：答對獲取金幣抽「普通盲盒」，3 連擊（3-Combo）贏取特殊代幣抽「SSR 史詩神獸」。
- 🎁 **沉浸式開箱體驗**：點擊搖盒 ➔ 爆開 ➔ 360° 旋轉光芒 ➔ 稀有度標籤（Common / Rare / SSR）與滿星養成。
- 🔊 **純程式 Web Audio 音效**：內建答對、答錯、晃盒、爆盒與勝利號角等合成音效。
- 🗣️ **TTS 智慧語音朗讀**：支援題幹與選項語音朗讀，自動將數學符號口語化。
- 📐 **KaTeX 數學公式支援**：標準 LaTeX 語法渲染清晰向量公式。
- 👨‍🏫 **教師後台與錯題診斷**：密碼保護後台（預設 `0000`），即時統計答對率與學生錯題詳細回顧（支援 LocalStorage 離線持久化與 Google Apps Script 雲端同步）。

---

## 📁 專案目錄結構

```text
gamified-quiz/
├── .agents/
│   └── skills/
│       └── gamified-quiz/
│           └── SKILL.md          # Antigravity 專案技能定義
├── index.html                    # 遊戲展示首頁 (支援 GitHub Pages 直接遊玩)
├── SKILL.md                      # 技能標準說明檔
└── README.md                     # 專案說明文件
```

---

## 🚀 如何使用

### 方式 1：搭配 Antigravity AI 助理使用
1. 將本 Repo Clone 下來，或將 `.agents/skills/gamified-quiz` 加入你的工作區。
2. 直接向 AI 助理輸入你的題目（例如：「*請幫我將這 10 題數學/國文/英文題做成盲盒遊戲測驗*」）。
3. AI 將自動產出獨立的 HTML 遊戲檔案！

### 方式 2：直接使用瀏覽器開啟
* 雙擊開啟 `index.html` 即可直接在離線狀態下暢玩範例題庫！

---

## 🛠️ 開發與客製化

- **更換題庫**：修改 HTML 中的 `const questions = [...]` 陣列。
- **更換圖鑑與寵物**：修改 `const collectionDB = [...]` 陣列。
- **連接 Google 試算表**：填入你的 Google Apps Script Web App URL 到 `GAS_URL`。

---

## 📄 License
MIT License
