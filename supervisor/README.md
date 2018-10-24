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
[root@squid Ansible-roles]# ansible-playbook install.yml  --tags "install_supervisor"
[root@squid Ansible-roles]# ansible-playbook addservice.yml --tags "supervisor_add_tomcat-8001-boss"


