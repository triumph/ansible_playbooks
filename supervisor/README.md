upervisor：是用Python开发的一个client/server服务，是Linux/Unix系统下的一个进程管理工具，不支持Windows系统。它可以很方便的监听、启动、停止、重启一个或多个进程。用Supervisor管理的进程，当一个进程意外被杀死，supervisort监听到进程死后，会自动将它重新拉起.但是只支持前台程序.

安装后默认的用户名和密码为  admin/baiyongjie

#### roles介绍
```
#role目录结构如下:
[root@squid data]# tree Ansible-roles/
Ansible-roles/
├── supervisor.yml
└── supervisor
    ├── files
    │   └── supervisor_install.sh
    └── tasks
        └── main.yml


```

#### 执行playbook
```
[root@squid Ansible-roles]# ansible-playbook supervisor.yml 

PLAY [install supervisor] **************************************************

TASK [supervisor : script] *************************************************
changed: [10.241.0.10]
changed: [10.241.0.11]

TASK [supervisor : debug] **************************************************
ok: [10.241.0.10] => {
    "msg": [
        "url: 10.241.0.10:9001", 
        "username: admin ", 
        "password: baiyongjie"
    ]
}
ok: [10.241.0.11] => {
    "msg": [
        "url: 10.241.0.11:9001", 
        "username: admin ", 
        "password: baiyongjie"
    ]
}

PLAY RECAP *****************************************************************
10.241.0.10                : ok=2    changed=1    unreachable=0    failed=0
10.241.0.11                : ok=2    changed=1    unreachable=0    failed=0

#执行tags,会失败是因为已经安装过了
[root@squid Ansible-roles]# ansible-playbook supervisor.yml --tags "install_supervisor"

PLAY [install supervisor] ************************************************************************************************************************

TASK [supervisor : script] ***********************************************************************************************************************
fatal: [10.241.0.10]: FAILED! => {"changed": true, "msg": "non-zero return code", "rc": 10, "stderr": "Shared connection to 10.241.0.10 closed.\r\n", "stderr_lines": ["Shared connection to 10.241.0.10 closed."], "stdout": "9001 port is used ...\r\nscript exit\r\n", "stdout_lines": ["9001 port is used ...", "script exit"]}
fatal: [10.241.0.11]: FAILED! => {"changed": true, "msg": "non-zero return code", "rc": 10, "stderr": "Shared connection to 10.241.0.11 closed.\r\n", "stderr_lines": ["Shared connection to 10.241.0.11 closed."], "stdout": "9001 port is used ...\r\nscript exit\r\n", "stdout_lines": ["9001 port is used ...", "script exit"]}
        to retry, use: --limit @/data/Ansible-roles/supervisor.retry

PLAY RECAP ***************************************************************************************************************************************
10.241.0.10                : ok=0    changed=0    unreachable=0    failed=1
10.241.0.11                : ok=0    changed=0    unreachable=0    failed=1
```
