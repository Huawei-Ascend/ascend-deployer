# 离线安�工具�明

离线安�工具提供系统依赖�python依赖�动下载工具的和一�式安装所有依赖的脚本

�前�线安�工具支持�下操作系统

|操作系统 |版本|cpu架构    |
|-------|-----|---------|
|centos |7.6  |aarch64  |
|centos |7.6  |x86_64   |
|centos |8.2  |aarch64  |
|centos |8.2  |x86_64   |
|ubuntu |18.04|aarch64  |
|ubuntu |18.04|x86_64   |

# 离线安�工具操作指�

## 单机安�

- **步� 1**

�动start_download.bat或�start_download.sh下载依赖��

- **步� 2**

将CANN�件包�件包放到resources�录下

```
atlas-deployer
|- install.sh
|- ansible.cfg
|- playbooks
|- scenes
`- resources/
   |- centos_7.6_aarch64
   |- centos_7.6_x86_64
   |- ...
   |- aarch64
   |- x86_64
   |- A300-3000-npu-driver_xxx.run
   |- A300-3000-npu-firmware_xxx.run
   |- Ascend-cann-nnrt-xxx.run
   |- ...
   `- Ascend-cann-toolkit-xxx.run
```

- **步� 3**

使用filezilla等工具，将整��录上从到待安装��上

- **步� 4**
执�install.sh --help仔细阅�参数�明
```bash
./install.sh --help
```

- **步� 5**

运�install.sh安�组件或按场�安�,例�：

```bash
./install.sh --install=driver      // 安�driver
./install.sh --install=npu         // 安�driver和firmware
./install.sh --install-scene=auto  // �动安装所有能找到的软件包
```

## 批量安�

在单机安装执行安装之前配置inventor_file文件指定待安装���下载和上传之服务器的过程与单机相同�

- **步� 1**

在文件inventory_file配置待安装的其他设�的ip地址、用户名和密�,�配�个�

例�：
```buildoutcfg
[ascend]
ip_address_1 ansible_ssh_user='root' ansible_ssh_pass='password1'
ip_address_2 ansible_ssh_user='root' ansible_ssh_pass='password2'
ip_address_3 ansible_ssh_user='root' ansible_ssh_pass='password3'

```

- **步� 2**

执�ansible ping测试其他设�连通�
```bash
export PATH=/usr/local/python3.7.5/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/python3.7.5/lib:$LD_LIBRARY_PATH
ansible all -i ./inventory_file -m ping
ip_address_1 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```
如果之前没有安�过ansible�以执�./install.sh --check
```bash
./install.sh --check
```
如果�有��都success，表示所有��都能�常连接。�有设�失败，请�查���的网络连接和sshd服务�否开�

- **步� 4**
执�install.sh --help仔细阅�参数�明
```bash
./install.sh --help
```

- **步� 5**

执�install.sh�动批量安装�过程与单机安�基�相同，例如：
```bash
./install.sh --install=driver      // 安�driver
./install.sh --install=npu         // 安�driver和firmware
./install.sh --install-scene=auto  // �动安装所有能找到的软件包
```

# 离线安�工具�细说明
### 下载工具使用

windows下需安�python3，推荐使用python3.7版本以上

windows版本下载�径[python3.7.5](https://www.python.org/ftp/python/3.7.5/python-3.7.5-amd64.exe)

工具�录结构�下
```
|-- downloader
|-- playbooks
|-- start_download.bat
|-- start_download.sh
|-- install.sh
|-- resources
|-- ansble.cfg
```
在windows下运行start_download.bat�动下载，在linux下运行start_download.sh�动下�

### 下载工具配置

下载工具涉及到的配置文件如下
```
downloader/config.ini
downloader/config/{os}_{version}_{arch}/source.list
downloader/config/{os}_{version}_{arch}/source.repo
```

- **Python源配�**

python源配�在downloader/config.ini�，默认使用华为源，可根据�要替�
```buildoutcfg
[pypi]
index_url=http://mirrors.huaweicloud.com/pypi/simple
```

- **Centos源配�**

centos源在对于版本的配��录中
```
downloader/config/centos_{version}_{arch}/source.repo
```
例�centos 7.6  aarch64��的源配置在�下文件� 
```
downloader/config/centos_7.6_aarch64/source.repo
```
centos 7.6的源配置文件内��下:
```
[base]
baseurl=http://mirrors.huaweicloud.com/centos-altarch/7/os/aarch64

[epel]
baseurl=http://mirrors.huaweicloud.com/epel/7/aarch64
```
表示同时�用了base源和epel源，下载centos的依赖是会从这两�源中查�和下载。默认使用华为源，根��要修改�
�改源通常��要修改其中host部分，即mirrors.huaweicloud.com部分。�需�改后面部分，请确保理�centos的源配置

_注意:_ centos的依赖软件需要在base和epel�起才能包�完整。�果�删除源，�能�成依赖下载不完整�

centos 8.2的源结构�7.2�异较�,例�CentOS 8.2 aarch64下源配置为：
```buildoutcfg
[base]
baseurl=http://mirrors.huaweicloud.com/centos/8/BaseOS/aarch64/os

[powertool]
baseurl=http://mirrors.huaweicloud.com/centos/8/PowerTools/aarch64/os

[AppStream]
baseurl=http://mirrors.huaweicloud.com/centos/8/AppStream/aarch64/os/

[Everything]
baseurl=http://mirrors.huaweicloud.com/epel/8/Everything/aarch64
```
包含4�子源� �改�则与centos7.6相同


- **Ubuntu源配�**

已ubuntu 18.04 aarch64为例子，源配�文件为：
```buildoutcfg
config/ubuntu_18.04_aarch64/source.list
```
内��下�
```buildoutcfg
deb http://mirrors.huaweicoud.com/ubuntu-ports/ bionic main multiverse restricted universe
deb http://mirrors.huaweicloud.com/ubuntu-ports/ bionic-updates main multiverse restricted universe
deb http://mirrors.huaweicloud.com/ubuntu-ports/ bionic-security main multiverse restricted universe
```
配置文件格式和ubuntu�/etc/apt.d/source.list基本相同。默认使用华为源，可根据实际情况�改�

_注意_: �改源时�常�建��改url� 增加或删除源�能找出依赖下载失败或依赖版本不匹配�

### downloader介绍
1.downloader下载保存的目录结构：  
```
resources/
|-- centos_7.6_aarch64
|-- centos_7.6_x86_64
|-- centos_8.2_aarch64
|-- centos_8.2_x86_64
|-- ubuntu_18.04_aarch64
|-- ubuntu_18.04_x86_64
|-- aarch64
`-- x86_64
```

2.下载OS系统依赖组件  
```shell script
# 清理下载文件及目�
python os_dep_downloader.py clean
# 执�下�
python os_dep_downloader.py
```

3.代理配置  
```editorconfig
[proxy]
enable=true         # �否开�代理配置参数
protocol=http
hostname=openproxy.huawei.com
port=8080
username=none       # 代理账号
userpassword=none   # 代理密码
```
### Driver,Frimware和CANN层软件安�

Driver,Firmware,CANN层软件需要使用run包� 将相关软件包放置在resources�录下即可，例如：
```
atlas-deployer
|- install.sh
|- ansible.cfg
|- playbooks
|- scenes
`- resources/
   |- centos_7.6_aarch64
   |- centos_7.6_x86_64
   |- ...
   |- aarch64
   |- x86_64
   |- A300-3000-npu-driver_xxx.run
   |- A300-3000-npu-firmware_xxx.run
   |- Ascend-cann-nnrt-xxx.run
   |- ...
   `- Ascend-cann-toolkit-xxx.run
```

# 安全注意事项

1. 由于�要使用dpkg� rpm等包管理�，只能使用root账号运�

2. inventory文件�会配�远程机器的root用户名和密码，建�使用ansible的vault机制进�加密，使用完成之后建�立即删除
   
   参�文�[http://www.ansible.com.cn/docs/playbooks_vault.html](http://www.ansible.com.cn/docs/playbooks_vault.html)
