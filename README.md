# 名人新趨勢與合作夥伴追蹤

這是一個可部署到 GitHub Pages 的靜態 Web App。網站本身不需要伺服器；需要更新時可手動執行 GitHub Actions，抓取公開新聞來源，產生 `data/snapshot.json` 後部署。

## 功能

- 按需產生名人趨勢 snapshot
- 多名人切換
- 趨勢分群與 score
- 主體公司訊號與外部合作夥伴分流
- 外部合作夥伴 / 共同出現實體 table
- 提及次數、來源場合、首次出現標記
- 本地 snapshot Bot
- GitHub Actions 手動觸發更新與部署

## 目前追蹤對象

追蹤名單在 `config/celebrities.json`：

- Jensen Huang / 黃仁勳 — NVIDIA
- Lisa Su / 蘇姿丰 — AMD
- Masayoshi Son / 孫正義 — SoftBank

## 本機執行

```bash
node scripts/update-snapshot.mjs
node scripts/serve.mjs
```

然後打開：

```text
http://127.0.0.1:4173/
```

如果沒有網路，可以先產生 fallback 資料：

```bash
node scripts/update-snapshot.mjs --offline
```

## 部署

推到 GitHub 後，到 repo 的 Settings → Pages，把 Source 設為 GitHub Actions。之後可到 Actions 手動執行 `Request celebrity snapshot` 來更新資料並部署網站。

這個專案不會自動排程抓取；只有在你手動按 Run workflow 時才會更新。

## 重要檔案

```text
index.html                         # 頁面入口
assets/app.js                      # 前端互動與渲染
assets/styles.css                  # 樣式
config/celebrities.json            # 名人追蹤名單
scripts/update-snapshot.mjs        # 按需資料更新
scripts/serve.mjs                  # 本機靜態伺服器
data/snapshot.json                 # 最新 snapshot
data/history/*.json                # 歷史 snapshot
.github/workflows/daily-snapshot.yml
```
# 名人新趨勢與合作夥伴追蹤

這是一個可部署到 GitHub Pages 的靜態 Web App。網站本身不需要伺服器；需要更新時可手動執行 GitHub Actions，抓取公開新聞來源，產生 `data/snapshot.json` 後部署。

## 功能

- 按需產生名人趨勢 snapshot
- 多名人切換
- 趨勢分群與 score
- 合作夥伴 / 共同出現實體 table
- 提及次數、來源場合、首次出現標記
- 本地 snapshot Bot
- GitHub Actions 手動觸發更新與部署

## 目前追蹤對象

追蹤名單在 `config/celebrities.json`：

- Jensen Huang / 黃仁勳 — NVIDIA
- Lisa Su / 蘇姿丰 — AMD
- Masayoshi Son / 孫正義 — SoftBank

## 本機執行

```bash
node scripts/update-snapshot.mjs
node scripts/serve.mjs
```

然後打開：

```text
http://127.0.0.1:4173/
```

如果沒有網路，可以先產生 fallback 資料：

```bash
node scripts/update-snapshot.mjs --offline
```

## 部署

推到 GitHub 後，到 repo 的 Settings → Pages，把 Source 設為 GitHub Actions。之後可到 Actions 手動執行 `Request celebrity snapshot` 來更新資料並部署網站。

這個專案不會自動排程抓取；只有在你手動按 Run workflow 時才會更新。

## 重要檔案

```text
index.html                         # 頁面入口
assets/app.js                      # 前端互動與渲染
assets/styles.css                  # 樣式
config/celebrities.json            # 名人追蹤名單
scripts/update-snapshot.mjs        # 按需資料更新
scripts/serve.mjs                  # 本機靜態伺服器
data/snapshot.json                 # 最新 snapshot
data/history/*.json                # 歷史 snapshot
.github/workflows/daily-snapshot.yml
```
