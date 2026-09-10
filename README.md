# 背单词 PWA 部署到 GitHub Pages

## 文件说明
- `index.html` — 应用本体（复习 / 词库 / 添加三个页面）
- `manifest.json` — PWA 配置，决定图标、名称、启动方式
- `sw.js` — Service Worker，负责离线缓存
- `icon-192.png` / `icon-512.png` — 应用图标

## 部署步骤

1. 新建一个 GitHub 仓库（公开或私有都行，私有仓库的 Pages 需要付费账号，建议公开）
2. 把这 5 个文件传上去（网页拖拽上传，或者 `git push`）
3. 进入仓库 Settings → Pages → Source 选择 `main` 分支、`/ (root)` 目录 → Save
4. 等 1-2 分钟，Pages 会给你一个 `https://你的用户名.github.io/仓库名/` 的网址
5. 用手机浏览器打开这个网址

## 添加到主屏幕

- **iPhone（Safari）**：打开网址 → 底部分享按钮 → 添加到主屏幕
- **Android（Chrome）**：打开网址 → 右上角菜单 → 安装应用 / 添加到主屏幕

添加后图标会是独立的"背单词"App，打开没有浏览器地址栏，断网也能正常复习和添加（数据存在手机本地）。

## 以后想加功能

单词的数据结构在 `index.html` 里的 `words` 数组，每个单词长这样：

```js
{
  id, word, meaning, sentences,   // 基础内容
  box, nextReview, reviewCount,   // 间隔重复相关
  createdAt, lastReviewed
}
```

想加发音、图片、标签、导出备份之类的功能，都可以在这个结构上扩展。需要的话随时回来找我加。

## 注意

- 数据存在浏览器的 `localStorage` 里，清除浏览器数据/App 数据会丢失，建议后续加一个导出 JSON 备份的功能
- 换手机或者清了缓存，数据不会跟着走——这是当前版本唯一的局限，之后可以加"账号同步"或"导入导出"来解决
