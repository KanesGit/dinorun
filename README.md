# 🦕 恐龍跑酷

基於 Chrome 離線恐龍遊戲靈感，使用 **Godot 4.6** 開發並導出為網頁版的無盡跑酷遊戲。

**👉 [立即遊玩](https://kanesgit.github.io/project_t/)**

---

## 遊戲玩法

- 按**空白鍵**或**點擊**跳躍
- 躲避仙人掌和飛鳥
- 速度隨時間加快——看看你能跑多遠！

## 功能特色

- 像素風格恐龍，雙幀跑步動畫
- 程序生成音效（無需外部音頻文件）
- 頂部實時分數顯示 + 個人最高紀錄
- 暱稱輸入 + **前 10 名排行榜**（需後端伺服器支持）
- 支持桌面與移動端瀏覽器

## 操作方式

| 動作 | 按鍵 |
|------|------|
| 跳躍 | 空白鍵 / 滑鼠點擊 / 觸控 |
| 開始 / 重試 | 空白鍵 / 滑鼠點擊 / 觸控 |

## 技術棧

| 層級 | 技術 |
|------|------|
| 遊戲引擎 | Godot 4.6 |
| 開發語言 | GDScript |
| 導出格式 | HTML5 / WebAssembly |
| 排行榜後端 | Node.js + Express + SQLite |
| 部署平台 | GitHub Pages |

## 本地開發

### 運行遊戲
用 **Godot 4.x** 打開 `dino-runner/project.godot`，按 **F5** 即可運行。

### 啟動排行榜伺服器
```bash
cd dino-runner/server
npm install
npm start
```
伺服器運行於 `http://localhost:3000`

### 導出為網頁版
```bash
/path/to/Godot --headless --export-release "Web" build/web/index.html
```

## 項目結構

```
dino-runner/
├── main.gd              # 遊戲邏輯、UI、HTTP 請求
├── dino.gd              # 像素恐龍精靈 + 動畫
├── main.tscn            # 主場景
├── project.godot        # Godot 項目配置
├── export_presets.cfg   # Web 導出設置
└── server/
    ├── server.js        # Express API（提交分數 + 排行榜）
    └── package.json
```

## API 接口

| 方法 | 路徑 | 說明 |
|------|------|------|
| `POST` | `/api/score` | 提交分數 `{ name, score }` |
| `GET` | `/api/leaderboard` | 獲取前 10 名 |

---

使用 [Godot Engine](https://godotengine.org) 開發
