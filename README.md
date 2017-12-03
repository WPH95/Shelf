# Shelf

shelf [货架]，inspire by docker 🐳。



## TODO

- [ ] Namespace
- [ ] Cgroup
- [ ] Mount

实验性功能

- [ ] OCI IMAGE SPEC
- [ ] DOCKER SPEC





一种精简的快速使用内核虚拟[容器]的 python 库

```

with shelf(ns=["pid"]) as s:
	s.run("ls")
	out = s.run("echo $$")
	print("pid is {}".format(out))

>> pid is 1
```





兼容 https://github.com/opencontainers/runtime-spec spec

但因为 shelf 的实现原因，



```
import json
CONFIG = """
{
    "version": "0.1.0",
    "platform": {
        "os": "linux",
        "arch": "amd64"
    },
    "process": {
        "terminal": true,
        "user": {
            "uid": 0,
            "gid": 0,
            "additionalGids": null
        },
        "args": [
            "sh"
        ],
        "env": [
            "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
            "TERM=xterm"
        ],
        "cwd": ""
    },
    "root": {
        "path": "rootfs",
        "readonly": true
    },
    "hostname": "shell",
    "mounts": [
        {
            "name": "proc",
            "path": "/proc"
        },
        ……
        {
            "name": "cgroup",
            "path": "/sys/fs/cgroup"
        }
    ],
    "linux": {
        "capabilities": [
            "CAP_AUDIT_WRITE",
            "CAP_KILL",
            "CAP_NET_BIND_SERVICE"
        ]
    }
}

"""


with shelf(oci=) as s:
	...



```





### 为什么造这个轮子？

的确 基于 docker 做类似下方的功能更使用感觉。

```
with docker.run("xxxx"):
	....

```

BTW 

毕业设计是基于 linux namespace 的 linux 虚拟化设计 

