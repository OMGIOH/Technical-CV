# GitHub Pages 个人网站部署教程

本教程将帮助你把 Technical CV 网站部署到 GitHub Pages，获得一个免费的在线网址（`https://你的用户名.github.io`）。

---

## 前置准备

1. 注册一个 GitHub 账号（https://github.com）
2. 下载并安装 Git（https://git-scm.com/downloads）
3. 安装完成后，在终端验证：`git --version`

---

## 方法一：用 GitHub Desktop（推荐，无需命令行）

### 第一步：安装 GitHub Desktop

1. 下载 GitHub Desktop（https://desktop.github.com/）
2. 安装后用你的 GitHub 账号登录

### 第二步：创建新仓库

1. 打开 GitHub Desktop，点击左上角 `File` → `New repository`
2. 填写信息：
   - **Name**：`你的用户名.github.io`（例如你的用户名是 `oliverhuang`，就填 `oliverhuang.github.io`）
   - **Local path**：选择一个你能找到的文件夹
   - **Initialize this repository with a README**：勾选
3. 点击 `Create repository`

> **重要**：仓库名必须是 `用户名.github.io` 这个格式，这是 GitHub Pages 的默认网址规则。

### 第三步：把网站文件复制进仓库

1. 打开你刚创建的仓库文件夹
2. 把 `Technical_CV` 文件夹里的**所有文件**复制到仓库根目录：
   ```
   你的用户名.github.io/
   ├── index.html
   ├── style.css
   ├── script.js
   ├── .gitattributes
   ├── game/
   │   ├── game.html
   │   ├── game.js
   │   ├── game.wasm
   │   ├── game.pck
   │   └── ...其他游戏文件
   └── 开发日志.md
   ```
3. 回到 GitHub Desktop，你会看到文件变化列表
4. 在左下角填写：
   - **Summary**：`Initial commit - Technical CV website`
5. 点击 `Commit to main`
6. 点击顶部 `Push origin` 把文件上传到 GitHub

### 第四步：开启 GitHub Pages

1. 打开浏览器，访问 `https://github.com/你的用户名/你的用户名.github.io`
2. 点击 `Settings`（设置）
3. 左侧菜单找到 `Pages`
4. 在 `Source` 下拉菜单选择 `Deploy from a branch`
5. 在 `Branch` 下选择 `main`，文件夹选 `/ (root)`
6. 点击 `Save`

### 第五步：等待并访问

1. 等待 1-5 分钟（首次部署可能稍慢）
2. 在 Pages 设置页面会显示你的网址：`https://你的用户名.github.io`
3. 打开网址即可看到你的个人简历网站

---

## 方法二：用命令行（适合有基础的用户）

### 第一步：在 GitHub 网站上创建仓库

1. 登录 GitHub，点击右上角 `+` → `New repository`
2. Repository name 填：`你的用户名.github.io`
3. 选择 `Public`
4. 勾选 `Add a README file`
5. 点击 `Create repository`

### 第二步：克隆仓库到本地

打开终端（PowerShell），执行：

```bash
cd d:\Document\HYF\实习
git clone https://github.com/你的用户名/你的用户名.github.io.git
```

### 第三步：复制文件并推送

```bash
# 把 Technical_CV 里的文件复制到仓库
Copy-Item "Technical_CV\*" "你的用户名.github.io\" -Recurse -Force

# 进入仓库目录
cd 你的用户名.github.io

# 添加所有文件
git add .

# 提交
git commit -m "Initial commit - Technical CV website"

# 推送到 GitHub
git push origin main
```

### 第四步：开启 GitHub Pages

同方法一的第四步。

---

## 常见问题

### Q: 游戏加载不出来？
A: 游戏文件较大（约 78MB），GitHub 对单文件有 100MB 限制。你的 `game.pck`（约 39MB）和 `game.wasm`（约 36MB）都在限制内，应该没问题。如果加载缓慢属正常现象。

### Q: 网站更新了怎么同步？
A: 修改本地文件后，在 GitHub Desktop 中再次 Commit 并 Push，GitHub Pages 会自动更新（约 1-2 分钟生效）。

### Q: 想用自定义域名？
A: 在仓库根目录创建一个 `CNAME` 文件（无扩展名），写入你的域名，然后在域名服务商处添加 CNAME 记录指向 `你的用户名.github.io`。

### Q: 推送时提示文件太大？
A: GitHub 单文件限制 100MB，仓库建议 1GB 以内。如果游戏文件继续增大，可考虑使用 Git LFS 或将游戏托管在其他平台。

### Q: 网站显示样式错乱？
A: 确保所有文件都正确上传，特别是 `style.css` 和 `game/` 文件夹下的所有文件。在 GitHub 仓库页面检查文件是否齐全。

---

## 后续更新流程

每次修改网站后，只需三步：
1. 修改本地文件
2. GitHub Desktop 中 Commit（填写更新说明）
3. Push origin

GitHub Pages 会自动重新部署，1-2 分钟后刷新网页即可看到更新。
