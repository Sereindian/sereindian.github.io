# Sereindian 的个人主页

访问：**https://sereindian.github.io/**

一个以文字排版为主的个人介绍页，包含德语座右铭和社交账号，适配电脑、平板和手机。

## 修改内容

网页全部位于 `index.html`，不需要安装依赖或运行构建命令。

- **昵称、自我介绍**：搜索 `在这里修改昵称和自我介绍`，修改相邻的标题和段落。
- **社交链接**：搜索 `social-list`。有效账号使用 `<a class="social-entry">`，修改 `href`、平台名称、账号说明和 `aria-label`。只填写自己的真实链接。
- **待添加账号**：QQ、微博、X 和 Instagram 使用 `.pending` 列表项中的 `<div class="social-entry">`。收到地址后，将这个 `div` 改成带真实 `href` 的 `a`，并移除 `pending` 类、修改“待添加”说明。
- **座右铭**：搜索 `class="german"` 修改德语引文；中文释义在相邻的 `<details class="translation">` 中，支持鼠标、触摸与键盘展开。
- **页面标题与搜索摘要**：修改 `<title>`、`description` 和对应的 `og:` 标签。
- **配色**：修改 CSS 顶部 `:root` 中的颜色变量。

当前 GitHub 与哔哩哔哩链接来自公开 GitHub 个人资料。
保留的平台为 GitHub、哔哩哔哩、QQ、微博、X 和 Instagram。未提供地址的账号保持不可点击，没有占位跳转。

德语引文使用尼采《查拉图斯特拉如是说》“论旧榜和新榜”第 23 节的原文，保留原版 `Ein Mal` 拼写。可在页面中的出处链接核对 1885 年版扫描本。

页面使用 Chivo 字体，并设置系统字体作为后备；字体加载失败时仍可正常阅读。动画遵循 `prefers-reduced-motion`。

## 发布

仓库的 **Settings → Pages** 已设置为从 `main` 分支的 `/ (root)` 发布。
在 GitHub 上修改 `index.html` 并提交到 `main`，GitHub Pages 会自动更新。
部署进度可在仓库的 **Actions → pages build and deployment** 查看。

## 本地预览

可以直接在浏览器打开 `index.html`，或在文件所在目录执行：

```sh
python -m http.server 4173 --bind 127.0.0.1
```

然后访问 http://127.0.0.1:4173/ 。
