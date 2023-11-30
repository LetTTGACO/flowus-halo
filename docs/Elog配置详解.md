---
urlname: elog-config
title: Elog配置详解
updated: '2023-11-30 17:50:29'
date: '2023-11-29 17:28:56'
categories:
  - 配置详情
  - 快速开始
tags:
  - Elog
public: 'true'
excerpt: 未开启自动生成
publish: 'true'
---
# 前言
参考 [Elog 文档](https://elog.1874.cool/)，仓库中有两个 elog 配置文件：
1. `elog.config.js`：同步到 Halo 时的配置文件，用于同步 FlowUs 文档到 Halo
	```javascript
	module.exports = {
	  write: {
	    platform: 'flowus',
	    flowus: {
	      tablePageId: process.env.FLOWUS_TABLE_PAGE_ID,
	    }
	  },
	  deploy: {
	    platform: 'halo',
	    halo: {
	      endpoint: process.env.HALO_ENDPOINT,
	      token: process.env.HALO_TOKEN,
	      policyName: process.env.HALO_POLICY_NAME,
	      rowType: 'html',
	      needUploadImage: true,
	    }
	  },
	  image: {
	    enable: false,
	  }
	}
	
	```
1. `elog.config.local.js`：同步到本地时的配置文件，用于备份 FlowUs 文档到本地
	```javascript
	module.exports = {
	  write: {
	    platform: 'flowus',
	    flowus: {
	      tablePageId: process.env.FLOWUS_TABLE_PAGE_ID,
	    },
	  },
	  deploy: {
	    platform: 'local',
	    local: {
	      outputDir: './docs',
	      filename: 'title',
	      format: 'markdown',
	      frontMatter: {
	        enable: true,
	        exclude: ['cover']
	      }
	    }
	  },
	  image: {
	    enable: true,
	    platform: 'local',
	    local: {
	      outputDir: './images',
	      pathFollowDoc: true,
	    }
	  }
	}
	
	```
# elog.config.js
## FlowUs 配置
```javascript
write: {
  platform: 'flowus',
  flowus: {
    tablePageId: process.env.FLOWUS_TABLE_PAGE_ID,
  }
}
```
- `tablePageId`为FlowUs 数据表格页面 ID，可从[此处](https://elog.1874.cool/notion/gvnxobqogetukays#tablepageid)获取


## Halo 配置
```javascript
deploy: {
  platform: 'halo',
  halo: {
    endpoint: process.env.HALO_ENDPOINT,
    token: process.env.HALO_TOKEN,
    policyName: process.env.HALO_POLICY_NAME,
    needUploadImage: true,
  }
}
```
- `endpoint`表示 Halo 站点地址

- `token`表示 Halo 个人令牌

- `policyName`表示附件的存储策略

- `needUploadImage`表示文档将会把扫描到的图片上传到 Halo中去

## 图床配置
```javascript
image: {
  enable: false
}
```
不使用图床。不推荐图床和`needUploadImage`一起打开，要么用在线图床图片，要么上传到 Halo 中
# elog.config.local.js
## 本地配置
```javascript
deploy: {
  platform: 'local',
  local: {
    outputDir: './docs',
    filename: 'title',
    format: 'markdown',
    frontMatter: {
      enable: true
    }
  }
}
```
- `outputDir`为导出文件夹，文档将被导出到此目录下

- `filename`为文件命名方式，`title` 表示按照文档标题命名

- `format`表示文档将被格式化为 markdown 形式的文档

- `frontMatter.enable`表示将生成带有 FrontMatter 的 markdown 文档

## 图床配置
```javascript
image: {
  enable: true,
  platform: 'local',
  local: {
    outputDir: './images',
    pathFollowDoc: true,
  }
}
```
- `outputDir`为导出文件夹，图片将被导出到此目录下

- `pathFollowDoc`表示文档图片路径将跟随文档路径计算

## 更多 Elog 配置详情，请阅读 [Elog 文档](https://elog.1874.cool/)
