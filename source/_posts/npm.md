---
title: npm
date: 2017-02-21 16:55:36
tags: npm
commit: false
categories: 工具
---
### 自己手动rm -rm /User/xxx/.npm下的 cache包 会导致 npm无法使用：
- ENOENT: no such file or directory, uv_cwd

解决：npm cache clean -f 强制清除