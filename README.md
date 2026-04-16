# LogiScan — 物流營運數據分析助手

> 由 Claude AI 驅動的物流報表一鍵分析工具，支援 CSV / Excel 上傳，自動輸出核心問題、異常預警與改善建議。

## 線上展示

部署後訪問：`https://<你的帳號>.github.io/<repository名稱>/`

---

## 功能

| 分析項目 | 說明 |
|---------|------|
| 數據總結 | 總筆數、日期範圍、店舖/路線/倉別數量 |
| 核心問題 Top 3 | 依類別與案件重要性排序 |
| 類別佔比分析 | 大/中/小類別數量與百分比 |
| 時效與品質評估 | 一次解決率（Y/N）、處理狀態、未結案異常件 |
| 異常預警偵測 | 高頻問題店舖、路線、倉別標記 |
| 改善建議 | 行動導向、依優先度（高/中/低）標示 |

---

## 快速開始

### 方法一：GitHub Pages 部署（推薦）

1. Fork 或上傳此專案到你的 GitHub Repository
2. 進入 Repository → **Settings** → **Pages**
3. Source 選擇 `Deploy from a branch`，Branch 選 `main`，Folder 選 `/ (root)`
4. 儲存後等待約 1 分鐘，即可透過 GitHub Pages URL 訪問

### 方法二：本機執行

```bash
# 使用任意靜態伺服器，例如：
npx serve .
# 或
python3 -m http.server 8080
```

開啟瀏覽器訪問 `http://localhost:8080`

---

## 使用方式

1. 在頁面中輸入你的 **Anthropic API Key**（格式：`sk-ant-...`）
   - API Key 僅儲存在瀏覽器本機（localStorage），不會傳送至任何第三方
   - 取得 API Key：https://console.anthropic.com/
2. 上傳 CSV 或 Excel 報表（支援 `.csv`、`.xlsx`、`.xls`）
3. 勾選需要的分析項目
4. 點擊「開始分析」

---

## 報表欄位建議

分析效果最佳的報表建議包含以下欄位（欄位名稱可自行調整，AI 會自動辨識）：

- `店名` / `店號`
- `路線` / `倉別`
- `大類別` / `中類別` / `小類別`
- `反應事項` / `處理結果`
- `一次性處理`（Y/N）
- `處理狀態`
- `日期` / `建立時間`

---

## 技術架構

```
logistics-analyzer/
├── index.html   # 主頁面
├── style.css    # 樣式表
├── app.js       # 應用邏輯
└── README.md    # 說明文件
```

- **前端**：純 HTML + CSS + JavaScript（無框架依賴）
- **AI 引擎**：Anthropic Claude API（`claude-sonnet-4-20250514`）
- **Excel 解析**：[SheetJS (xlsx)](https://sheetjs.com/)
- **部署**：任意靜態檔案伺服器 / GitHub Pages

---

## 注意事項

- 報表資料僅在本機瀏覽器中處理，前 8,000 字元會傳送至 Anthropic API 進行分析
- 請確保報表不含高度機敏個資，或在傳送前先行去識別化
- API 費用依 Anthropic 計費標準，每次分析約消耗 1,000–2,000 tokens

---

## License

MIT
