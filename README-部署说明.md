---
AIGC:
    Label: "1"
    ContentProducer: 001191440300708461136T1XGW3
    ProduceID: da44ed0679f3a766ed9442efd95a55ae_b9c7d2e6e58511f184bd52540072b1e8
    ReservedCode1: mSHmH8VYYqb/bS3Lzv/WX8WJB7JjLqGb2oVGnFOwI5sr46xu0EKE2YV7EdvAd2vVscgMc+GhYIkFyG6JvQ2f6y4y9HhvC5z+lmzj0bMfgTND8y5SQDqU+Wwn/Eizdpkz2jEILLAg5YZqnjlX4/cBgulzJx3eN+1B6yJvTsV8m5Ja9IpKNMHE6aQVkkI=
    ContentPropagator: 001191440300708461136T1XGW3
    PropagateID: da44ed0679f3a766ed9442efd95a55ae_b9c7d2e6e58511f184bd52540072b1e8
    ReservedCode2: mSHmH8VYYqb/bS3Lzv/WX8WJB7JjLqGb2oVGnFOwI5sr46xu0EKE2YV7EdvAd2vVscgMc+GhYIkFyG6JvQ2f6y4y9HhvC5z+lmzj0bMfgTND8y5SQDqU+Wwn/Eizdpkz2jEILLAg5YZqnjlX4/cBgulzJx3eN+1B6yJvTsV8m5Ja9IpKNMHE6aQVkkI=
---

# 新站（kalokfung29-arch.github.io）修復包 · 部署說明

本目錄是修復後的新站完整靜態檔案，玩法清單與舊站一致（8 個首頁玩法 + 免費玩面板 + 賭博合集 8 款 + 商店/安全模式/成年模式）。

## 本次變更
1. 補回 **大富翁**（`goMonopoly` / `mpScreen`）與 **中國象棋盲棋**（`goXqBlind`）入口與全部對應邏輯。
2. 新增 **`xiangqi-blind.html`** 盲棋獨立頁（原新站點擊盲棋會 404）。
3. 補回 **免費玩面板與轉盤抽獎**（`freeHub` / `freeSheet`）。
4. 補回 **`manifest.json` / `manifest.webmanifest` / `favicon.ico` / 各尺寸圖示**（修復「加到主畫面」與頁籤圖示 404）。
5. 下載區改版（新站不再自帶 APK，避開 GitHub Pages 單檔 25 MB 上限）：
   - 分享版：`https://tetrisjames.surge.sh/TETRIS-SHARE-5.2.apk`（直接下載）
   - 完整版：`https://tetrisjames.surge.sh/TETRIS-FULL-5.2.apk`（新視窗）
   - 管理端：`https://tetrisjames.surge.sh/TETRIS-ADMIN-2.9.apk`（新視窗）
6. `APP_VERSION` 更新為 `2026.11.21.5.2`；頁面底部「新站入口」提示改指向舊站 tetrisjames.surge.sh。

## 部署方式（任選一種，需 GitHub 憑證）

### A. 網頁上傳（最簡單）
1. 瀏覽器登入 GitHub → 打開倉庫 `kalokfung29-arch/kalokfung29-arch.github.io`（分支 `main`）。
2. 對 `index.html` 點「Add file → Upload files」，上傳本目錄 `index.html` 覆蓋；同樣上傳 `xiangqi-blind.html` 與其它資源（圖示、manifest、robots、sitemap）。
3. Commit 後等待 1–2 分鐘，強制重新整理（Ctrl+F5）驗證。

### B. 命令列（需 PAT）
```bash
git clone https://<PAT>@github.com/kalokfung29-arch/kalokfung29-arch.github.io.git newsite
copy 本目錄\*  newsite\        # 覆蓋 index.html 等
cd newsite && git add -A && git commit -m "web: 補齊大富翁/盲棋/免費玩與 manifest，下載改指向 5.2" && git push
```

## 驗收清單
- 首頁應有 8 個玩法按鈕（含「大富翁」「中國象棋盲棋」）。
- 點「中國象棋盲棋」應跳到 `xiangqi-blind.html`，標題「中國象棋 · 盲棋（暗棋）」，不應 404。
- 點「免費玩」應彈出面板並可玩轉盤抽獎。
- 「加入主畫面」不再因 manifest 404 失敗。

## 已知外部問題
Supabase 專案（`atjskewhkbptnnmubdsb.supabase.co`）對頁面內 anon key 一律回 401，導致雲端版本推送、VIP/成年模式狀態、排行榜雲同步、訂單拉取失效。需在 Supabase 後台換發/修復 key 後，同步替換頁面內 `SB_KEY` 常數。
*（内容由AI生成，仅供参考）*
