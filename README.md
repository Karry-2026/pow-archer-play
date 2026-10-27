# POW! ARCHER · 在线试玩

这个仓库只做一件事：把游戏挂到 GitHub Pages 上，给一个能直接打开的链接。

**在线玩** → https://karry-2026.github.io/pow-archer-play/

---

## 当前线上版本

| 项 | 值 |
|---|---|
| 版本 | **v0.18**（2026-10-28） |
| 来源 | 主仓库 `pow-archer` 标签 `v0.14.1` |
| 文件 | `index.html`，6,230 行 / 264 KB |

怎么确认线上跑的是这一版：打开页面，控制台执行

```js
document.querySelector('meta[name=app-version]').content
```

返回 `v0.18` 就是最新的。这一版把开局改成六职业（各绑一把起手武器和一个超武）、加了进入加载页（点进去音乐已经在响）、回旋镖改成飞出去再追踪回到手上。

---

## 为什么单独开一个仓库

GitHub 免费账号的 Pages 只支持公开仓库。主仓库是私有的，放开发文档、开发日志、git 历史，不适合公开。

所以这里只放最终的 `index.html` 一个文件，主仓库继续私有。

需要说明的是：任何能在浏览器里跑的网页，代码本来就对访问者可见（浏览器必须下载才能执行）。这个仓库公开的部分，跟任何人打开网页后按 F12 看到的东西完全一样。私有仓库保护的是开发过程、文档和提交历史，不是这份 HTML 本身。

---

## 更新方式

改完主仓库的 `index.html` 之后，把它复制过来提交，Pages 会在一分钟左右自动更新。

```bash
cp ../pow-archer/index.html ./index.html
git add index.html README.md
git commit -m "vX.Y: 同步主仓库"
git push origin main
```

提交前先跑一次主仓库的回归用例。这个仓库没有测试，也没有构建步骤 —— 它就是最终产物本身。

---

## 本地跑

```bash
python -m http.server 8899
# 打开 http://127.0.0.1:8899/index.html
```

需要联网，因为 Three.js 从 CDN 加载。
