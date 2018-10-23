# ansible_Update_LTJF
### 简介
本库为快速使用ansible部署LTJF项目
### 运行
```
ansible-playbook /root/ansible_playbooks/LTJF/update.yml -e "services_name=account services_version=12345" --syntax-check
ansible-playbook /root/ansible_playbooks/LTJF/update.yml -e "services_name=account services_version=12345" 
```
### 目录结构
```
root@iZbp11x4k98zgmepp7jezrZ:/root tree  .
LTJF/
├── Readme.md
├── roles
│   └── update
│       ├── files
│       ├── handlers
│       │   └── main.yml
│       ├── tasks
│       │   └── main.yml
│       ├── templates
│       └── vars
│           └── main.yml
└── update.yml

7 directories, 5 files

git clone git@github.com:donxan/ansible_playbooks.git
