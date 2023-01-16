# Atcoder for Chinese 翻译仓库

[![Netlify Status](https://api.netlify.com/api/v1/badges/efdcea51-1343-4f00-a443-1fc5bb49722f/deploy-status)](https://app.netlify.com/sites/atcoder-for-chinese-translations/deploys)

## 基本信息

一个简易的存放文章的仓库，用于存放 Atcoder for Chinese 的翻译的仓库。

## 使用方法

### 如何贡献

Fork 之后直接在仓库中新建文章或修改文章。

仓库采用 GitHub Actions 自动部署。修改完文章后，待 GitHub Actions 执行完毕，就可以在 GitHub Pages 里面下载文章或获取文章列表 `list.json`。

文章的基本格式如下（请删去注释）：

```markdown
---
title: "文章标题（没有固定格式）"
tags: [ "标签 1", "标签 2", "..." ]
author: "原作者（转载 / 翻译请注意版权问题）"
created: "创作时间（格式比较随意，但需要保证能够被识别）"
---

<!-- 以上内容在发布时会被删除，并以 JSON 格式写入 list.json -->

<!-- 下面是正文 -->

...
```

如果还是不明白可以随便点开一篇看一下。

**下述的 `<比赛编号>` 和 `<题目编号>` 均指原题目链接中的 `https://atcoder.jp/contests/<比赛编号>/tasks/<题目编号>`，不按这个格式会无法识别。**

文章命名采用 `<比赛编号>.<题目编号>.<标识符>.md`，并且需要保证其中没有多余的 `.`。其中为避免冲突和保持风格统一，**标识符建议采用六位随机十六进制字符串（字母小写）或十六进制校验和前六位**。

### 如何使用

等待 GitHub Actions 成功执行后，会将仓库内容部署到 GitHub Pages。

访问 `<你的 GitHub Pages 网址，如 https://example.github.io>/translations/<比赛编号>.<题目编号>.<标识符>.md` 可以下载对应文章的 Markdown 源码；

访问 `<你的 GitHub Pages 网址，如 https://example.github.io>/translations/<比赛编号>.<题目编号>.<标识符>.html` 可以下载对应文章渲染后的 HTML 代码（不建议直接浏览，因为缺少部分 CSS）；

访问 `<你的 GitHub Pages 网址，如 https://example.github.io>/translations/list.json` 可以下载 `list.json` 文件。

`list.json` 文件包含了文章列表和所有文章的头部信息，格式如下：

```json
{
    "lastCommit": { "id": "...", "short": "...", "date": "..." }
    "data": {
        "比赛编号": {
            "题目编号": {
                "标识符": {
                    "title": "...",
                    "tags": [ "标签 1", "标签 2", "..." ],
                    "author": "...",
                    "created": "...",
                    "lastCommit": { "id": "...", "short": "...", "date": "..." }
                    /* 还有剩余的一些非必要但出现在文章头部的信息 */
                }
            }
        }
    }
}
```
