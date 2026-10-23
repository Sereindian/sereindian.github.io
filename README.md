# SereindianP · Producer Profile

用于偶像大师名片背面二维码的个人介绍网站，展示担当偶像、游戏好友码、音乐偏好与社交联系方式。

[在线访问](https://sereindian.github.io/) · [问题反馈](https://github.com/Sereindian/sereindian.github.io/issues) · [旧站归档](https://github.com/Sereindian/sereindian.github.io/tree/archive-old-site)

## 功能

- **按企划浏览担当**：提供 765PRO ALLSTARS、Cinderella Girls、Million Live!、SideM、Shiny Colors、Gakuen 六个入口，支持键盘切换。
- **主题切换**：混色、水色、玫瑰三种配色与深浅色模式，使用浏览器本地存储保存外观偏好。
- **好友码与联系方式**：复制游戏 ID、QQ 号，展示加好友二维码，并跳转至社交主页。
- **音乐推荐**：展示歌曲封面，直接打开对应的 Apple Music 歌曲或专辑。
- **名片分享**：复制完整扩列介绍，或下载 `.vcf` 电子名片。
- **移动端适配**：响应式布局、六企划胶囊导航，以及遵循减少动态效果偏好的动画设置。

## 技术栈

网站使用 HTML、CSS 和原生 JavaScript 实现，无需 npm 安装、构建命令或后端服务。

| 组件 | 用途 |
| --- | --- |
| Tailwind CSS（CDN） | 页面布局与样式工具类 |
| Font Awesome 6.5.1（CDN） | 通用界面与社交平台图标 |
| Noto Sans SC / Noto Serif JP | 中文正文与日文衬线文字 |
| Shippori Mincho | 担当偶像卡片的日文介绍 |
| JetBrains Mono | ID、编号等内容的等宽排版 |
| GitHub Pages | 静态网站发布 |

字体通过 `fonts.loli.net` / `gstatic.loli.net` 镜像加载，采用异步样式表与 `noscript` 回退。样式、图标及字体包含外部 CDN 请求，本地预览时需要网络连接。

## 目录结构

```text
.
├── index.html          # 页面结构、样式、静态资料与交互逻辑
├── my-avatar.jpg       # 页面头像原图
├── favicon-round.svg   # 内嵌头像的透明圆形标签页图标
├── icon/               # 六个企划的 SVG 标识
├── cover/              # 三首推荐歌曲的封面
└── README.md           # 项目说明
```

## 本地运行

需要 Git 和 Python 3。

```sh
git clone https://github.com/Sereindian/sereindian.github.io.git
cd sereindian.github.io
python -m http.server 4173 --bind 127.0.0.1
```

在浏览器中打开 [http://127.0.0.1:4173/](http://127.0.0.1:4173/)。按 `Ctrl+C` 停止预览服务。

## 内容维护

主要内容集中在 [index.html](index.html)，图片使用仓库内的相对路径引用。

| 修改内容 | 对应位置 |
| --- | --- |
| 昵称、担当简述、QQ、游戏 ID | `defaultProfile` 与对应的页面静态文字 |
| 担当偶像与所属企划 | `franchiseTabs`、`panel-*` 和 `.idol-showcase-card` |
| 日文介绍 | `.idol-introduction`，每张卡片包含两句文字 |
| 头像 | [my-avatar.jpg](my-avatar.jpg) 与 `defaultProfile.avatarUrl` |
| 标签页图标 | [favicon-round.svg](favicon-round.svg) 与 `<link rel="icon">` |
| 企划标识 | `icon/` 文件及页面中的 `<img>` 引用 |
| 歌曲封面与跳转链接 | `cover/`、`trackRow0` 至 `trackRow2` |
| 底部专辑链接 | `appleMusicLink`，该按钮不展示封面 |
| 社交链接 | 页面底部各平台入口的 `href` |
| 完整扩列介绍 | `copyFullMeishiSummary()` |
| 电子名片导出 | `downloadVCard()` |
| 配色与介绍字号 | CSS 主题变量、`data-theme-accent` 与 `.idol-introduction` |

维护时需同步以下关联内容：

- `favicon-round.svg` 内嵌了头像数据。更换 `my-avatar.jpg` 后，需要另行更新圆形图标。
- QQ 二维码是静态 SVG，位于 `qqContactQr`。修改 QQ 加好友链接时，需要重新生成并替换二维码。
- Shippori Mincho 字体请求使用 `text` 字符子集。修改日文介绍时，需要同步更新两处字体链接的字符子集，或移除 `text` 参数以加载完整字体。
- 企划和担当发生变化时，同步更新顶部徽章、导航、卡片与完整扩列介绍文本。

提交前，建议在手机和桌面宽度下检查布局、主题、图片、复制按钮及外部链接。

## 部署

网站通过 GitHub Pages 从 `main` 分支根目录发布。

1. 修改文件并在本地预览。
2. 提交并推送到 `main`。
3. 在仓库 [Actions](https://github.com/Sereindian/sereindian.github.io/actions) 中查看 `pages build and deployment` 的执行结果。
4. 部署成功后访问 [在线网站](https://sereindian.github.io/) 确认效果。

若复用到自己的仓库，在 **Settings → Pages** 中选择从分支发布，并设置实际使用的分支与 `/ (root)` 目录。使用子路径部署时，保留图片的相对路径。

## 旧站归档

旧版个人主页保存在 [archive-old-site](https://github.com/Sereindian/sereindian.github.io/tree/archive-old-site) 分支。当前站点的日常更新提交至 `main`，归档分支保留旧站内容。

## 反馈与素材说明

可通过 [GitHub Issues](https://github.com/Sereindian/sereindian.github.io/issues) 反馈页面问题或提出改进建议。

本仓库尚未指定统一的开源许可证。角色、企划标识、头像及音乐封面等素材的权利归各自权利人所有，第三方字体与图标遵循其各自的授权条款。
