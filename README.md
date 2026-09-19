# 🎮 測驗遊戲化產生器 (Gamified Quiz Generator)

> 將枯燥的各學科練習題，一鍵轉換為高互動度、高沉浸感的單一檔案「遊戲化互動測驗」！

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Antigravity Skill](https://img.shields.io/badge/Antigravity-Skill-blue.svg)](https://github.com)

![盲盒測驗畫面預覽](preview.png)

---

## 🕹️ 內建 6 大精選遊戲化模板

本專案提供 6 種不同心理激勵機制的互動測驗模板，點擊可直接在線上體驗（皆使用數學「比與比例式」題庫）：

| 模板名稱 | 核心玩法 | 適合學科情境 | 線上試玩 |
| :--- | :--- | :--- | :---: |
| **🎁 盲盒抽卡養成** | 答題賺金幣 ➔ 連擊贏代幣 ➔ 開箱抽 SSR 神獸 ➔ 滿星圖鑑 | 全科平時測驗、課後複習作業 | [進入遊戲](index.html) |
| **⚔️ RPG 地牢打怪** | 答對發動攻擊 ➔ 連擊爆擊奧義 ➔ 扣血對決 ➔ 鐵匠鋪裝備升級 | 數學計算特訓、理化挑戰題 | [進入遊戲](template-rpg.html) |
| **🚀 星際太空防衛** | 雷射射擊擊碎敵機 ➔ 節奏快感 ➔ 能量護盾防禦 | 英文單字速記、九九乘法心算 | [進入遊戲](template-space.html) |
| **🏝️ 大富翁探索棋盤** | 答對擲骰前進 ➔ 踩寶箱/陷阱/機會命運 ➔ 環島通關 | 社會科歷史地理、單元總複習 | [進入遊戲](template-boardgame.html) |
| **🍣 夢幻美食餐車** | 小動物客人點單 ➔ 烹調上菜 ➔ 獲得 5 星好評與小店擴建 | 生活情境題、日常英語、特教自理 | [進入遊戲](template-diner.html) |
| **🧩 神秘密室逃脫** | 解碼古代符文 ➔ 破除火/水/木/雷四大元素封印 ➔ 開啟石門 | 國文長文閱讀理解、素養題組 | [進入遊戲](template-escape.html) |

---

## 🌟 共通核心技術特色

- 📦 **單一獨立 HTML 檔案**：純前端零伺服器依賴，任何裝置（電腦、平板、手機、大屏）開箱即用。
- 🔊 **純程式 Web Audio 音效**：內建答對、答錯、攻擊、雷射、開箱與勝利號角等合成音效，零外掛音檔。
- 🗣️ **TTS 智慧語音朗讀**：支援題幹與選項語音朗讀，自動將數學符號口語化。
- 📐 **KaTeX 數學公式支援**：標準 LaTeX 語法渲染清晰向量公式。
- 💾 **自動 LocalStorage 存檔**：離線或重整網頁進度不遺失，亦支援 Google Apps Script 雲端班級同步。

---

## 🚀 如何使用

### 1. 安裝 Skill
直接在你的 Antigravity / AI Agent 對話框中貼上以下指令：

> **請安裝這個skill︰https://github.com/chuoneone/gamified-quiz**

安裝完成後，AI 即可自動獲得「測驗遊戲化產生器」的所有能力！

---

### 2. 生成遊戲化測驗
隨時提供你的題目給 AI，並指定想使用的模板：
> 「*請幫我將這份試題做成 **RPG打怪** 遊戲測驗*」  
> 「*請幫我將這 20 個單字做成 **星際太空防衛戰** 測驗*」

AI 將自動為你生成完整的單一檔案互動測驗 HTML！

---

## 📁 專案目錄結構

```text
gamified-quiz/
├── .agents/skills/gamified-quiz/
│   └── SKILL.md                 # Antigravity 專案技能定義
├── index.html                   # 🎁 盲盒抽卡養成展示（附頂部 6 合 1 切換器）
├── template-rpg.html            # ⚔️ RPG 地牢打怪模板
├── template-space.html          # 🚀 星際太空防衛戰模板
├── template-boardgame.html      # 🏝️ 大富翁探索棋盤模板
├── template-diner.html          # 🍣 夢幻美食餐車經營模板
├── template-escape.html         # 🧩 神秘密室逃脫解謎模板
├── SKILL.md                     # 技能標準說明檔
├── README.md                    # 專案說明文件
└── preview.png                  # 預覽截圖
```

---

## 📄 License
MIT License
