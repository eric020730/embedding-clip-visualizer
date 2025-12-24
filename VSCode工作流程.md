# VS Code + Vercel 完整工作流程

## 🛠️ 準備工作

### 1. 安裝必要軟體

#### 下載並安裝：
- **VS Code**: https://code.visualstudio.com/
- **Git**: https://git-scm.com/downloads
- **Node.js**: https://nodejs.org/ (選擇 LTS 版本)

#### 驗證安裝
打開終端機（Terminal）執行：
```bash
git --version
node --version
npm --version
```

如果都顯示版本號，代表安裝成功！

---

## 📁 步驟 1: 在 VS Code 中開啟專案

### 方法 A: 從下載的檔案開始
1. 下載所有檔案到一個資料夾，例如 `embedding-visualizer`
2. 打開 VS Code
3. 點擊 `File` → `Open Folder...`
4. 選擇你的專案資料夾
5. 點擊 `選擇資料夾`

### 方法 B: 創建新專案
1. 在桌面或任何位置創建新資料夾 `embedding-visualizer`
2. 在 VS Code 中打開這個資料夾
3. 將下載的所有檔案複製到這個資料夾

### 確認檔案結構
在 VS Code 左側應該看到：
```
embedding-visualizer/
├── index.html
├── package.json
├── vercel.json
├── README.md
├── .gitignore
└── Vercel部署指南.md
```

---

## 🔧 步驟 2: 在 VS Code 中編輯

### 打開終端機
- 快捷鍵：`` Ctrl + ` `` (backtick 鍵)
- 或點擊：`Terminal` → `New Terminal`

### 開啟檔案編輯
1. 點擊左側 `index.html` 開始編輯
2. VS Code 會提供：
   - 語法高亮
   - 自動完成
   - 即時錯誤提示

### 推薦安裝的 VS Code 擴充功能
在左側點擊擴充功能圖示（或按 `Ctrl+Shift+X`）搜尋並安裝：
- **Live Server** - 本地預覽網頁
- **Prettier** - 程式碼格式化
- **GitLens** - Git 增強功能
- **Error Lens** - 即時錯誤顯示

---

## 👀 步驟 3: 本地預覽（測試修改）

### 方法 1: 使用 Live Server（推薦）
1. 安裝 Live Server 擴充功能
2. 在 `index.html` 上按右鍵
3. 選擇 `Open with Live Server`
4. 瀏覽器會自動開啟 http://localhost:5500
5. **每次存檔都會自動重新整理！**

### 方法 2: 直接開啟檔案
1. 在 VS Code 中對 `index.html` 按右鍵
2. 選擇 `Reveal in File Explorer`
3. 雙擊 `index.html` 用瀏覽器開啟

---

## 📤 步驟 4: 部署到 Vercel

### 初次部署

#### 4.1 初始化 Git
在 VS Code 終端機中執行：
```bash
git init
git add .
git commit -m "Initial commit: Embedding & CLIP visualizer"
```

#### 4.2 創建 GitHub Repository
1. 到 https://github.com/new
2. Repository name: `embedding-clip-visualizer`
3. 選擇 Public
4. **不要**勾選任何初始化選項
5. 點擊 `Create repository`

#### 4.3 推送到 GitHub
複製 GitHub 顯示的指令，在 VS Code 終端機執行：
```bash
git remote add origin https://github.com/你的用戶名/embedding-clip-visualizer.git
git branch -M main
git push -u origin main
```

如果要求輸入密碼，使用 **Personal Access Token**：
- 到 GitHub Settings → Developer settings → Personal access tokens
- Generate new token (classic)
- 選擇 `repo` 權限
- 複製 token 當作密碼使用

#### 4.4 連接 Vercel
1. 到 https://vercel.com/
2. 用 GitHub 帳號登入
3. 點擊 `Add New...` → `Project`
4. 選擇 `embedding-clip-visualizer`
5. **直接點擊 Deploy**
6. 等待 30 秒 → 完成！🎉

---

## 🔄 步驟 5: 更新流程（之後每次修改）

### 簡單的更新流程
每次在 VS Code 修改完成後：

```bash
# 1. 查看修改了什麼
git status

# 2. 加入所有修改
git add .

# 3. 提交修改（寫清楚改了什麼）
git commit -m "更新：修改了 XXX 功能"

# 4. 推送到 GitHub
git push
```

**Vercel 會自動偵測並重新部署！**大約 30 秒後網站就更新了。

### VS Code 圖形界面操作（更簡單）
1. 點擊左側 Source Control 圖示（或按 `Ctrl+Shift+G`）
2. 看到所有修改的檔案
3. 在 "Message" 欄位輸入提交訊息
4. 點擊上方的 ✓ (Commit)
5. 點擊 `...` → `Push`

---

## 💡 實用技巧

### VS Code 快捷鍵
- `Ctrl + S` - 儲存檔案
- `Ctrl + /` - 註解/取消註解
- `Ctrl + F` - 搜尋
- `Ctrl + H` - 取代
- `Alt + ↑/↓` - 移動行
- `Shift + Alt + ↓` - 複製行
- `Ctrl + D` - 選擇下一個相同的字

### 常見修改點

#### 修改標題
```html
<h1 className="text-4xl font-bold text-white mb-2 text-center">
  你的新標題
</h1>
```

#### 修改資料點
搜尋 `embeddingData` 和 `clipData`：
```javascript
const embeddingData = [
  { id: 1, x: 100, y: 100, z: 100, label: '你的標籤', color: '#3B82F6' },
  // 加入更多資料點...
];
```

#### 修改顏色
搜尋顏色代碼並替換：
- `#3B82F6` (藍色) → 你想要的顏色
- `#EF4444` (紅色)
- `#10B981` (綠色)

### Git 常用指令速查

```bash
# 查看狀態
git status

# 查看修改內容
git diff

# 查看提交歷史
git log --oneline

# 撤銷最後一次 commit（保留修改）
git reset --soft HEAD~1

# 放棄本地所有修改
git checkout .

# 拉取最新版本
git pull
```

---

## 🐛 疑難排解

### 問題 1: git push 失敗
**錯誤**: `fatal: Authentication failed`

**解決**:
1. 使用 Personal Access Token 而非密碼
2. 或設定 SSH key: https://docs.github.com/en/authentication

### 問題 2: Vercel 部署失敗
**解決**:
1. 檢查 Vercel Dashboard 的 Deployment 日誌
2. 確認 `index.html` 檔案存在
3. 確認 `vercel.json` 格式正確

### 問題 3: 修改沒有更新到網站
**解決**:
1. 確認已經 push 到 GitHub
2. 檢查 Vercel Dashboard 是否有新的部署
3. 清除瀏覽器快取（Ctrl+Shift+R）

### 問題 4: Live Server 無法啟動
**解決**:
1. 確認已安裝 Live Server 擴充功能
2. 重新啟動 VS Code
3. 或直接雙擊 index.html 用瀏覽器開啟

---

## 📚 學習資源

- **VS Code 官方教學**: https://code.visualstudio.com/docs
- **Git 教學**: https://git-scm.com/book/zh-tw/v2
- **Vercel 文檔**: https://vercel.com/docs
- **HTML/CSS/JavaScript**: https://developer.mozilla.org/

---

## ✅ 檢查清單

完成以下步驟即可開始工作：

- [ ] 安裝 VS Code、Git、Node.js
- [ ] 在 VS Code 中開啟專案資料夾
- [ ] 安裝 Live Server 擴充功能
- [ ] 初始化 Git repository
- [ ] 創建 GitHub repository
- [ ] 推送程式碼到 GitHub
- [ ] 連接 Vercel 並首次部署
- [ ] 測試修改 → 推送 → 查看更新

---

## 🎉 現在你可以：

1. ✏️ 在 VS Code 中編輯 `index.html`
2. 👀 用 Live Server 即時預覽
3. 💾 存檔並 commit
4. 📤 Push 到 GitHub
5. ⚡ Vercel 自動部署
6. 🌐 訪問你的網站

**開始享受你的開發流程吧！** 🚀
