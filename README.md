# SereindianP · Producer Profile

用于偶像大师名片背面二维码的个人介绍网站，展示担当偶像、游戏好友码、音乐偏好与社交联系方式。

[在线访问](https://sereindian.github.io/) · [问题反馈](https://github.com/Sereindian/sereindian.github.io/issues) · [旧站归档](https://github.com/Sereindian/sereindian.github.io/tree/archive-old-site)

## 功能

- **按企划浏览担当**：提供 765PRO ALLSTARS、Cinderella Girls、Million Live!、SideM、Shiny Colors、Gakuen 六个入口，支持键盘切换。
- **主题切换**：混色、水色、玫瑰三种配色；深浅色可跟随系统或按时间自动切换，也可通过图标手动切换，使用浏览器本地存储保存外观偏好。
- **好友码与联系方式**：复制游戏 ID、QQ 号，展示加好友二维码，并跳转至社交主页。
- **音乐推荐**：展示歌曲封面，直接打开对应的 Apple Music 歌曲或专辑。
- **名片分享**：复制完整扩列介绍，或下载 `.vcf` 电子名片。
- **手机与桌面双布局**：竖屏自动采用手机单栏，横向宽屏使用桌面双栏；缩放窗口或旋转设备时自动切换，同时遵循减少动态效果偏好。

## 响应式布局

同一个 `index.html` 按**浏览器视口宽度与方向**选择布局，无需选择设备或跳转到其他页面。这里的方向指页面可用区域的宽高关系，不依赖浏览器 User-Agent 或设备型号。

| 视口条件 | 布局 | 企划导航 |
| --- | --- | --- |
| 竖屏，或宽度小于 768px | 原有手机单栏，最大宽度 480px | 3 列 × 2 行 |
| 横屏且宽度为 768–1023px | 宽单栏，避免窄屏强行分栏 | 6 列 × 1 行 |
| 横屏且宽度不小于 1024px | 桌面双栏，最大宽度 1248px | 6 列 × 1 行 |

桌面左栏宽 320px，展示居中的头像与身份信息、渐变横幅、两列三行的企划徽章，以及 QQ 和五枚单行社交图标。左栏随页面正常滚动，不吸顶，也不设置内部滚动区域。

右栏展示担当档案、好友码、音乐与共同话题。三位担当采用首卡通栏、后两卡并排的排列；两位担当并排展示。桌面与手机端共用原版的浅色和深色主题，保留原有背景光晕、卡片透明度、边框与阴影，并随混色、水色、玫瑰配色切换。

旋转屏幕或调整窗口大小时，CSS 媒体查询与 `matchMedia` 同步更新布局和企划导航键盘操作，并将联系方式放回手机端原有的阅读顺序。头像、图标及封面均使用仓库相对路径。

## 深浅色模式

顶部下拉菜单提供“跟随系统”和“按时间”两个自动选项，默认为“跟随系统”，响应浏览器的 `prefers-color-scheme` 偏好及其变化。

- **按时间**：以访问者设备的当地时间为准，7:00（含）至 19:00（不含）为白天，其余为夜间。页面每分钟检查一次，重新回到页面时也会更新。
- **图标手动切换**：点击太阳或月亮按钮即可固定为白天或夜间，下拉框此时显示“手动模式”状态。自动规则不会覆盖手动选择；在下拉菜单重新选择自动模式即可恢复。

深浅色模式保存在 `localStorage` 的 `imas_theme_mode` 中，与配色偏好独立。页面在加载外部资源前应用模式；禁用本地存储时，选择仍在当前访问期间生效。

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
| 响应式断点与布局 | `responsiveLayoutStyles`、`.desktop-sidebar`、`.desktop-main` 与 `desktopLayoutQuery` |

维护时需同步以下关联内容：

- `favicon-round.svg` 内嵌了头像数据。更换 `my-avatar.jpg` 后，需要另行更新圆形图标。
- QQ 二维码是静态 SVG，位于 `qqContactQr`。修改 QQ 加好友链接时，需要重新生成并替换二维码。
- Shippori Mincho 字体请求使用 `text` 字符子集。修改日文介绍时，需要同步更新两处字体链接的字符子集，或移除 `text` 参数以加载完整字体。
- 企划和担当发生变化时，同步更新顶部徽章、导航、卡片与完整扩列介绍文本。

提交前，建议检查：

- 手机竖屏、宽屏竖屏、普通电脑横屏及较窄横屏下的布局、导航文字和横向溢出。
- 旋转或缩放后，企划选择、深浅色偏好及手机端内容顺序是否保持正常。
- 头像、企划图标与封面是否完整加载，以及二维码、复制、电子名片导出和外部链接是否可用。
- 深浅色模式、键盘切换企划及减少动态效果偏好。

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
