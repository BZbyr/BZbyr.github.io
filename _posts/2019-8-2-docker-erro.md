---
layout:     post                            # 使用的布局（不需要改,js里有根据布局做判断）
title:      "Docker "exec format erro""           # 标题
subtitle:   " "  # 副标题
date:       2019-08-02 12:00:00             # 时间
author:     "BZbyr"                          # 作者
header-img: "img/tag-bg.jpg"       # 这篇文章标题背景图片
catalog: true                               # 是否归档
tags:                                       # 标签，可多个
    - docker
---
# docker "exec format error"

一个小细节，执行格式错误

```
# srk8s @ sr046 in ~[kube namespace: spark-cluster] [12:34:26]
$ kubectl logs spark-worker-controller-2btd5 -n spark-cluster
standard_init_linux.go:207: exec user process caused "exec format error"
```

这个错误原因基本上是因为执行的脚本里少句话：

```bash
#!/bin/bash
```

