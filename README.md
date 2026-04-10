# muggle-zoo-tools
muggle-zoo-tools
# Muggle Zoo Tools — `muggle-zoo-tools`

> **給下一個 AI 看的工作手冊。**  
> 這個 repo 放的是 Muggle Zoo 分享給讀者的小工具。直接讀這份 README，就能接手繼續做。

---

## Repo 基本資料

| 項目 | 內容 |
|------|-----|
| GitHub Repo | `mugglezoomi-web/muggle-zoo-tools` |
| GitHub Pages URL | `https://mugglezoomi-web.github.io/muggle-zoo-tools/` |
| 第一個工具直連 | `https://mugglezoomi-web.github.io/muggle-zoo-tools/dashboard.html` |
| 擁有者 | `mugglezoomi-web` 帳號（Muggle Zoo 前台）|
| 資料來源 | 由桌機 Python 腳本自動更新（見下方說明）|

---

## 現有檔案結構

```
muggle-zoo-tools/
├── README.md                  ← 你正在讀的這份
├── dashboard.html             ← 第一個工具：台股評估地圖
├── logo-chinese.png           ← 麻瓜婆婆動物園 中文 logo
├── logo-mugglezoo.png         ← Muggle Zoo 英文 logo
└── (未來)
    ├── tool-02.html
    └── index.html             ← 工具列表頁（待做）
```

> **注意**：GitHub Pages 預設找 `index.html`。目前直接用完整路徑  
> `https://mugglezoomi-web.github.io/muggle-zoo-tools/dashboard.html` 存取工具。

---

## 工具 01：台股評估地圖（dashboard.html）

### 功能說明

- 顯示台股個股的 **P/E vs P/B 散佈圖**，用四象限分類估值
- 市場概覽卡片（樣本數、低估企業數、平均 P/E、平均殖利率）
- P/E / P/B 分界線 slider（可即時調整）
- 個股明細表（按 P/E 升序）
- 支援手動貼入 JSON 更新資料

### 設計系統（Muggle Zoo Dark Theme）

```
背景色       #050d1a   (深夜藍)
卡片背景     #0d1a2e
金色主色     #f5c842   (accent、border、數字)
金色暗版     #c9a235
主文字       #e8dcc8
暗文字       #a09480
邊框色       #1a2a45
```

### 散佈圖四色分類

```
低估價值 Value    #22c55e  (亮綠)
高品質資產 Quality #60a5fa  (亮藍)
成長合理 Growth   #f97316  (橙)
高估成長 Premium  #ef4444  (紅)
```

### 字體

- 介面文字：`Noto Sans TC`
- 標題：`Noto Serif TC`（加粗）
- 數字/代號：`JetBrains Mono`

---

## 資料更新方式

### 自動更新（桌機 Python）

桌機有一支 Python 腳本自動更新資料：

- **腳本位置**：`C:\Users\mis23\OneDrive\桌面\my-stock-dashboard-TWSE-valuation\update_dashboard.py`
- **腳本功能**：找最新 `twse_*.json` → 把資料嵌入 `dashboard.html` → git commit + push
- **資料來源**：`twse_fetcher.py` 從台灣證交所 OpenAPI 抓取

### Python 設定（update_dashboard.py）

要讓腳本 push 到這個 repo（`mugglezoomi-web/muggle-zoo-tools`），需要：

1. 把這個 repo clone 到桌機：
   ```
   git clone https://github.com/mugglezoomi-web/muggle-zoo-tools.git
   ```
2. 修改腳本裡的 `DASHBOARD_HTML` 路徑：
   ```python
   DASHBOARD_HTML = Path(r"C:\Users\mis23\OneDrive\桌面\muggle-zoo-tools\dashboard.html")
   ```
3. 之後跑腳本，就會自動更新這個 repo 的 dashboard.html

### 手動更新（備用）

如果不想改腳本，也可以：
1. 在 `dashboard.html` 裡找到 `let DATA = [...]` 區塊
2. 把新的 JSON 資料貼入頁面上的「更新資料」欄位
3. 直接上傳到 GitHub repo

---

## 如何新增工具

每個工具獨立一個 HTML 檔案。新增時：

1. 用 `dashboard.html` 當模板，複製改造
2. 保持同樣的 design tokens（顏色/字體）
3. 在最上方加中文 logo（`logo-chinese.png`），置中，寬度用 `clamp(120px, 28vw, 180px)`
4. Footer 固定格式：
   ```
   Muggle Zoo 麻瓜婆婆動物園 · YouTube · Threads
   資料來源說明
   Content IP under Mi's Marketing
   ```
5. 未來做 `index.html` 工具列表頁時，把工具卡片加進去

---

## 重要連結

| 用途 | URL |
|------|-----|
| Muggle Zoo 主站 | `https://mugglezoomi-web.github.io/muggle.zoo/` |
| 電子報 repo | `mugglezoomi-web/muggle-zoo-newletter` |
| 投資工具後台 | `mis23ms` 帳號（獨立，不在這裡）|
| YouTube | `https://youtube.com/@muggle-zoo` |
| Threads | `https://www.threads.com/@muggle.zoo` |
| Mi's Marketing | `https://mismkt.com/zh/home/` |

---

## 待做清單

- [ ] `index.html` — 工具列表頁（卡片式，連到各工具）
- [ ] 桌機 Python 路徑更新，讓腳本直接 push 到這個 repo
- [ ] 第二個工具（內容待定）

---

*Content IP under Mi's Marketing*  
*Muggle Zoo 麻瓜婆婆動物園*
