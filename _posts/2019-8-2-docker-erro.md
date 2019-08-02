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

