# 程式課教案產生器（lesson-plan-generator）

給國中資訊老師的 Claude Skill：輸入主題、年級、節數，產出一份可以直接帶進電腦教室的程式課教案。時間表分鐘數會對齊、範例程式可執行、每題練習都附解答。

線上介紹頁：https://kensong0518.github.io/lesson-plan-generator-skill/

## 安裝

**Claude Code（macOS / Linux）**

```bash
git clone https://github.com/kensong0518/lesson-plan-generator-skill.git
cp -r lesson-plan-generator-skill ~/.claude/skills/lesson-plan-generator
```

**Claude Code（Windows PowerShell）**

```powershell
git clone https://github.com/kensong0518/lesson-plan-generator-skill.git
Copy-Item -Recurse lesson-plan-generator-skill $HOME\.claude\skills\lesson-plan-generator
```

安裝後在 Claude Code 輸入 `/skills`，看到 `lesson-plan-generator` 就代表成功。

## 使用

在 Claude Code 中說：

- 「幫我做一份 for 迴圈的教案，七年級，1 節」
- 「用 Python 教 while 迴圈，八年級 2 節，做猜數字遊戲」

缺的資訊只會問一次，沒回答就用預設值（七年級、1 節、Python）。

## 功能

- 2–3 個可檢核的學習目標（「學生能……」）
- 分鐘時間表，加總剛好等於節數 × 45 分鐘，任何講解段落不超過 10 分鐘
- 可直接執行的示範程式，附中文註解與預期輸出
- 基礎／進階／挑戰三題練習，每題附解答與學生常見錯誤
- 課前準備清單
- 安全護欄：不使用國中生沒學過的語法、不出沒有解答的題目

## 範例

**輸入：** 主題「while 迴圈：猜數字遊戲」，八年級，2 節，Python

**輸出（節錄）：**

| 時段 | 分鐘 | 內容 |
|---|---|---|
| 暖身 | 5 | 老師心裡想一個 1～100 的數字，全班輪流猜 |
| 概念講解 | 10 | while 結構、和 for 的差別、無窮迴圈怎麼停 |
| … | … | … |
| 總結回饋 | 10 | 兩組上台玩彼此的遊戲，整理常見錯誤 |

完整輸出：[examples/while-loop-guess-number.md](examples/while-loop-guess-number.md)

## 檔案結構

```
lesson-plan-generator-skill/
├── SKILL.md                      ← 給 AI 讀
├── README.md                     ← 給人讀
├── assets/lesson-plan-template.md
├── examples/while-loop-guess-number.md
├── index.html                    ← 線上介紹頁（GitHub Pages）
├── CHANGELOG.md
└── LICENSE
```

## 授權

MIT
