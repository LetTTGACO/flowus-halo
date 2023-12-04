---
urlname: flowus-halo
title: FlowUs + Halo + GitHub Actions 博客解决方案
updated: '2023-12-01 19:00:01'
date: '2023-11-29 17:28:00'
autoExcerpt: 'true'
categories:
  - 快速开始
tags:
  - FlowUs
public: 'true'
pinned: 'true'
excerpt: 开启自动生成
publish: 'true'
---
# 快速开始
## 站点工具汇总
- 写作平台：FlowUs

- 文档平台：[Halo](https://www.halo.run/)

- 文档同步：[Elog](https://github.com/LetTTGACO/elog)

## 站点搭建指南
### Fork模板仓库
[点击 Fork](https://github.com/elog-x/flowus-halo/fork) 该模板仓库到个人 Github 账号仓库下并 clone 到本地。
### 安装依赖
在项目根目录下运行命令安装依赖：
```shell
npm install
```
### 新建本地调试文件
在项目根目录中复制`.elog.example.env`文件并改名为`.elog.env`，此文件将用于本地同步文档时使用。
### 配置FlowUs
参考[示例数据表](https://flowus.cn/1874/share/e4e1e6dc-403b-45e6-b4cd-b3d8e6ae79b1)[格](https://flowus.cn/1874/share/e4e1e6dc-403b-45e6-b4cd-b3d8e6ae79b1)，选择或新建 FlowUs 数据表格，并按照[文档提示](https://elog.1874.cool/notion/gvnxobqogetukays#halo)配置 Halo 并获取`tablePageId endpoint token policyName`。并在本地`.elog.env`中写入。
```plaintext
# FlowUs
FLOWUS_TABLE_PAGE_ID=获取的数据表格页面ID

# Halo 站点信息
HALO_ENDPOINT=Halo 站点地址
HALO_TOKEN=获取的 Halo 个人令牌
HALO_POLICY_NAME=获取的存储策略
```
### 本地调试
仓库中有两个 elog 配置文件：
1. `elog.config.js`：同步到 Halo 时的配置文件，用于同步 FlowUs 文档到 Halo

1. `elog.config.local.js`：同步到本地时的配置文件，用于备份 FlowUs 文档到本地

在正式上传到 Halo 站点前，建议先运行本地同步命令，从 FlowUs 拉取文档到本地
```shell
npm run dev:local
```
拉取到本地测试没问题时，可运行同步到 Halo 命令
```shell
npm run dev:halo
```
### 配置 Halo 站点
配置你的Halo 站点直到满意为止，可适当安装一些主题、插件
- 代码高亮插件

- markdown 编辑器

### 提交代码到 github
halo 站点访问没问题直接提交所有文件到 Github 仓库即可
## 自动化同步&部署
### 检查 Github Actions 权限
![1700326915607-691643c8-d52c-4913-9464-cb96b6b1b854.png#averageHue=%23fefdfd&clientId=u0b0d2576-ef2a-4&from=paste&height=361&id=ue7d36a55&originHeight=1192&originWidth=1404&originalType=binary&ratio=2&rotation=0&showTitle=false&size=245762&status=done&style=none&taskId=ua488e237-33d1-4210-b26a-01ec5614d6d&title=&width=425](../images/ea903f5672495500ba7966b348453446.png)
### 配置环境变量
![1700329642998-9006a455-211b-49f8-a89b-c6774c3e0931.png#averageHue=%23fefcfb&clientId=u0b0d2576-ef2a-4&from=paste&height=400&id=u205bf5e5&originHeight=799&originWidth=1178&originalType=binary&ratio=2&rotation=0&showTitle=false&size=149338&status=done&style=none&taskId=ua1dc9507-f7c4-43da-b17d-077223bd25a&title=&width=589](../images/e9c14f115e7d8239d0126515b71c0b42.png)
### 自动化部署
当在 FlowUs 中改动文档后，手动/自动触发 Github Actions流水线，会重新从 FlowUs 增量拉取文档，并自动部署到 Halo 站点，如此就实现了自动化部署博客。  
整个流程的关键点就在于：如何手动/自动触发 Github Actions。  
在项目.`github/workflows/sync.yaml`中已经配置了外部 API 触发 Github Actions 事件，所以只需要调用 API 触发流水线即可。
#### 手动触发
为了方便，这里提供一个部署在 Vercel 的免费公用的[ServerlessAPI](https://github.com/elog-x/serverless-api)，按照文档配置好 URL 参数并浏览器访问即可触发流水线
```shell
https://serverless-api-elog.vercel.app/api/github?user=xxx&repo=xxx&event_type=deploy&token=xxx
```
#### 自动触发
FlowUs 目前还没有基于Webhooks的自动触发流程
## 参考示例
示例 Github 仓库：[https://github.com/LetTTGACO/flowus-halo](https://github.com/LetTTGACO/flowus-halo)  

示例 FlowUs 数据表格：[elog-halo](https://flowus.cn/1874/share/e4e1e6dc-403b-45e6-b4cd-b3d8e6ae79b1)


