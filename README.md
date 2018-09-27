# ansible_nginx_keepalived
ansible
├── ansible.cfg
├── hosts #主机配置文件，设置ansible控制的主机以及一些主机变量
├── playbooks
│   ├── init.retry
│   ├── init.yml #初始化受控主机，安装一些基础以及必要的软件包
│   ├── keepalived_nginx.retry
│   └── keepalived_nginx.yml #一键安装脚本，执行就可以一键安装keepalived+nginx环境了
└── roles 角色
    ├── HA #安装配置keepalived
    │   ├── default
    │   ├── files
    │   ├── handlers #触发器，配置文件发生变化重启服务
    │   │   └── main.yml
    │   ├── meta
    │   ├── tasks #任务
    │   │   └── main.yml
    │   ├── templates #模版文件
    │   │   ├── Backup_conf
    │   │   └── Master_conf
    │   └── vars #模版文件的相关变量
    │       └── main.yml
    ├── httpd #安装配置httpd
    │   ├── default
    │   ├── files #文件,因为httpd2.2和httpd2.4一些配置有差别，所以这里做了区分
    │   │   ├── httpd2.2.conf
    │   │   ├── httpd2.2.Virtual.conf
    │   │   ├── httpd2.4.conf
    │   │   └── httpd2.4.Virtual.conf
    │   ├── handlers #触发器
    │   │   └── main.yml
    │   ├── meta
    │   ├── tasks #任务，根据httpd版本不同做了区分
    │   │   ├── httpd-2.2.yml
    │   │   ├── httpd-2.4.yml
    │   │   └── main.yml
    │   ├── templates #模版
    │   │   └── index.html
    │   └── vars
    ├── init #初始化受控主机
    │   ├── default
    │   ├── files
    │   ├── handlers
    │   ├── meta
    │   ├── tasks #任务主要安装软件和设置epel源
    │   │   └── main.yml
    │   ├── templates
    │   └── vars
    └── LB #安装与配置nginx
        ├── default
        ├── files #精简过得nginx默认文件
        │   └── nginx_default.conf
        ├── handlers #触发器，配置文件发生改变重启服务
        │   └── main.yml
        ├── meta
        ├── tasks #任务
        │   └── main.yml
        ├── templates #模版
        │   └── nginx_lb.conf
        └── vars #模版文件用到的变量
            └── main.yml

34 directories, 26 files
