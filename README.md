# Sereindian 的个人主页

访问：**https://sereindian.github.io/**

一个简洁的中文个人介绍页，展示自我介绍与社交账号，适配电脑和手机。

## 修改内容

网页全部位于 `index.html`，不需要安装依赖或运行构建命令。

- **昵称、自我介绍**：搜索 `在这里修改昵称和自我介绍`，修改相邻的标题和段落。
- **社交链接**：搜索 `social-list`。复制一个完整的 `<li>...</li>`，修改平台名称、账号说明、`href` 和 `aria-label`。只填写自己的真实链接。
- **页面标题与搜索摘要**：修改 `<title>`、`description` 和对应的 `og:` 标签。
- **配色**：修改 CSS 顶部 `:root` 中的颜色变量。

当前 GitHub 与哔哩哔哩链接来自公开 GitHub 个人资料。
微信、QQ、微博、小红书、抖音、X、Instagram 和 Telegram 目前是标有“待添加”的平台预留位，没有伪造地址。收到真实链接后，可将对应的 `li.platform-slot` 内容改为 `<a>` 链接；不要把账号、二维码或地址填入不相关的平台。

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
