# 大OS 報價系統 BIBLE（網站版）

聚陽成衣開發報價系統「大OS」（Quotation v3）操作說明的網頁版，整理自《大OS報價作業基本說明手冊 2026-05-04》與 Merge Options 教學影片。

## ⚠️ 機密與使用限制（務必先看）

- 本網站截圖含**客戶名稱、供應商、成本、報價、訂單數量**等公司機密資料。
- **限公司內部／私有（Private）repo 使用，嚴禁設為 Public（公開）。** 一旦公開即構成對外揭露客戶／成本資料，違反公司規範，且會被搜尋引擎與快取收錄、難以收回。
- 對外公開或跨組分享前，**需相關部門核准**並先完成去敏感化（遮蔽客戶名／成本／數量）。
- 內容為 AI 輔助整理，**僅供內部教育訓練參考**，正式作業以系統實際畫面與權責單位最新公告為準。

## 檔案結構

```
os-bible-site/
├─ index.html        # 網站主頁（單頁式，含目錄/搜尋/痛點互動表單）
├─ assets/           # 截圖（page_*.png）與影片影格（merge_*.jpg）
├─ .nojekyll         # 讓 GitHub Pages 直接出檔、不經 Jekyll 處理
├─ .gitignore
└─ README.md
```

## 本機預覽

直接用瀏覽器開 `index.html` 即可；或在本資料夾啟動簡易伺服器：

```bash
python -m http.server 8080
# 瀏覽器開 http://localhost:8080
```

## 部署到 GitHub Pages（私有 repo）

> 私有 repo 啟用 GitHub Pages 需 **GitHub Team / Enterprise** 方案；免費方案的 Pages 只能用於公開 repo（不適用本專案）。

1. 在公司 GitHub 建立一個 **Private** repository（例如 `os-bible`）。
2. 在本資料夾推送：
   ```bash
   git init
   git add .
   git commit -m "大OS BIBLE 網站初版"
   git branch -M main
   git remote add origin https://github.com/<你的組織>/os-bible.git
   git push -u origin main
   ```
3. 到 repo 的 **Settings → Pages**：Source 選 `Deploy from a branch`，Branch 選 `main` / `/(root)`，存檔。
4. 等幾分鐘，Pages 會給一個網址（私有 repo 僅授權成員可開）。

## 更新內容

內容與版型由產生器 `_build_os_bible.py`（在 `大OS_BIBLE` 資料夾）產出：

```bash
python _build_os_bible.py site
```

會重新輸出 `index.html` 並更新 `assets/`。改文字/痛點/章節都改該腳本對應段落再重跑即可。

---
資料日期：2026-05-04　|　整理：AI 輔助（需人工複核）
