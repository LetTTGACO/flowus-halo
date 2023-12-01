---
urlname: flowus-notice
title: FlowUs 写作注意事项
updated: '2023-12-01 13:40:05'
date: '2023-11-29 17:29:19'
autoExcerpt: 'true'
categories:
  - 配置详情
  - 快速开始
tags:
  - FlowUs
public: 'true'
publish: 'true'
---
# 写作注意事项
## 前言
在使用 Elog 同步 FlowUs 上的文档时，因为是将富文本向下转成 markdown，会有很多样式损失。这是由于 markdown 样式集合＜ FlowUs 样式集合。所以在 FlowUs 上书写时，得按照 markdown 支持的样式进行写作。

> 可以在[这里](/archives/flowus-example)看到 FlowUs 文档被导出为 markdown 时的样式损失程度

如果你不能接受样式损失，可能 markdown 并不适合你，隔壁 [NotionNext](https://github.com/tangly1024/NotionNext) 可能更适合你搭建文档站点。
## FlowUs 格式注意点
### 不要使用 markdown 不支持的样式/语法
例如字体颜色、多级折叠块、分栏、数据表、嵌入等。导出为 markdown 都不能正常展示。
### 适当使用 markdown 形式的超链接
在文档中使用 markdown 形式的超链接可以解决部分路由问题，例如链接 FlowUs 文档的超链接会被自动处理为非完整路径，或者手动链接到某个相对路由，可以使用以下方式解决
```javascript
// 使用[]() markdown 超链接语法
点击 [下一篇](/notion/deploy-platform) 继续配置部署平台
```
### 文档的维护交给写作平台
如果部署平台是 Halo/Confluence/WordPress 站点。那么你需要在写作平台，例如 FlowUs中维护文档，全面接管站点自带的编辑器。
### Elog 的更新是增量的
Elog 只会通过变动过的文档，并不会每次都全量更新
