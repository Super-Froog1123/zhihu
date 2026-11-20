# GitHub Pages 静态版

`index.html` 内嵌全部 JavaScript、CSS 和 Three.js，不依赖 CDN，也不需要 Node.js 或 Python 服务。`preview.html` 是独立场景预览，`.nojekyll` 用于静态文件发布。

保留原项目的 3D 办公室、角色动画、随机走动、取书、镜头操作、暂停与变速、对话界面、技能入口、知识资料管理与检索、知乎书签、文件预览和页面打开期间的定时任务。

GitHub Pages 无法运行原项目的 Python 后端，因此聊天改为明确标注的本地任务回执，支持历史、停止、重试和知识节选引用；分类使用本地关键词规则。它们不会实际调用 AI、浏览远程网页或执行云端任务。原项目的后端版不受影响。

对话及资料保存在当前浏览器中，清除网站数据会丢失记录；不跨设备同步。定时任务仅在页面打开时执行。浏览器需支持 WebGL 2。

## 发布

把本文件夹的内容复制到 GitHub Pages 的发布目录根部，确保入口名为 `index.html`，同时保留 `preview.html` 和 `.nojekyll`。也可通过已有的 Pages Actions 工作流上传整个 `github-pages/` 目录作为静态产物。所有页面使用相对链接，支持仓库子路径。

## 本地预览与更新

在项目根目录运行：

```sh
python3 -m http.server 8080 --directory github-pages
```

打开 `http://localhost:8080/`。建议使用 HTTP 服务预览，以保证存储与窗口通信行为一致。

修改原项目后重新导出（需已安装项目依赖）：

```sh
node scripts/build-pages.mjs
```

该脚本复用 `src/`，仅在导出时替换后端适配器和相关提示，不改动原有前端源码。

# zhihu
