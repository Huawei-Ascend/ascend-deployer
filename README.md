# 遖ｻ郤ｿ螳芽�ｷ･蜈ｷ雍譏

 遖ｻ郤ｿ螳芽�ｷ･蜈ｷ謠蝉ｾ帷ｳｻ扈滉ｾ晁ｵ悶｝ython萓晁ｵ冶�勘荳玖ｽｽ蟾･蜈ｷ逧�柱荳髞蠑丞ｮ芽｣�園譛我ｾ晁ｵ也噪閼壽悽

逶蜑咲ｻ郤ｿ螳芽�ｷ･蜈ｷ謾ｯ謖∝ゆｸ区桃菴懃ｳｻ扈

|謫堺ｽ懃ｳｻ扈 |迚域悽|cpu譫ｶ譫    |
|-------|-----|---------|
|centos |7.6  |aarch64  |
|centos |7.6  |x86_64   |
|centos |8.2  |aarch64  |
|centos |8.2  |x86_64   |
|ubuntu |18.04|aarch64  |
|ubuntu |18.04|x86_64   |

# 遖ｻ郤ｿ螳芽�ｷ･蜈ｷ謫堺ｽ懈欠蟇

## 蜊墓惻螳芽

- **豁･ 1**

蜷蜉ｨstart_download.bat謌冶�tart_download.sh荳玖ｽｽ萓晁ｵ冶ｽ莉

- **豁･ 2**

蟆�ANN霓莉ｶ蛹�ｽ莉ｶ蛹�叛蛻ｰresources逶蠖穂ｸ

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

- **豁･ 3**

菴ｿ逕ｨfilezilla遲牙ｷ･蜈ｷ�悟ｰ�紛荳逶蠖穂ｸ贋ｻ主芦蠕�ｮ芽｣�ｾ蜃荳

- **豁･ 4**
謇ｧ闌install.sh --help莉皮ｻ��霆蜿よ焚雍譏
```bash
./install.sh --help
```

- **豁･ 5**

霑占景nstall.sh螳芽�ｻ�ｻｶ謌匁潔蝨ｺ譎螳芽,萓句ゑｼ

```bash
./install.sh --install=driver      // 螳芽�river
./install.sh --install=npu         // 螳芽�river蜥掲irmware
./install.sh --install-scene=auto  // 閾蜉ｨ螳芽｣�園譛芽�謇ｾ蛻ｰ逧�ｽｯ莉ｶ蛹
```

## 謇ｹ驥丞ｮ芽

蝨ｨ蜊墓惻螳芽｣�鴬陦悟ｮ芽｣�ｹ句燕驟咲ｽｮinventor_file譁�ｻｶ謖�ｮ壼ｾ�ｮ芽｣�ｾ蜃繧荳玖ｽｽ蜥御ｸ贋ｼ荵区恪蜉｡蝎ｨ逧�ｿ�ｨ倶ｸ主黒譛ｺ逶ｸ蜷後

- **豁･ 1**

蝨ｨ譁�ｻｶinventory_file驟咲ｽｮ蠕�ｮ芽｣�噪蜈ｶ莉冶ｮｾ蜃逧�p蝨ｰ蝮縲∫畑謌ｷ蜷榊柱蟇�,蜿驟榊壻ｸｪ縲

萓句ゑｼ
```buildoutcfg
[ascend]
ip_address_1 ansible_ssh_user='root' ansible_ssh_pass='password1'
ip_address_2 ansible_ssh_user='root' ansible_ssh_pass='password2'
ip_address_3 ansible_ssh_user='root' ansible_ssh_pass='password3'

```

- **豁･ 2**

謇ｧ闌ansible ping豬玖ｯ募�莉冶ｮｾ蜃霑樣壽
```bash
export PATH=/usr/local/python3.7.5/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/python3.7.5/lib:$LD_LIBRARY_PATH
ansible all -i ./inventory_file -m ping
ip_address_1 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```
螯よ棡荵句燕豐｡譛牙ｮ芽�ｿ㌢nsible蜿莉･謇ｧ陦./install.sh --check
```bash
./install.sh --check
```
螯よ棡謇譛芽ｾ蜃驛ｽsuccess�瑚｡ｨ遉ｺ謇譛芽ｾ蜃驛ｽ閭ｽ譽蟶ｸ霑樊磁縲ょよ怏隶ｾ蜃螟ｱ雍･�瑚ｯｷ跏衍隘霎蜃逧�ｽ醍ｻ懆ｿ樊磁蜥茎shd譛榊苅譏蜷ｦ蠑蜷

- **豁･ 4**
謇ｧ闌install.sh --help莉皮ｻ��霆蜿よ焚雍譏
```bash
./install.sh --help
```

- **豁･ 5**

謇ｧ闌install.sh蜷蜉ｨ謇ｹ驥丞ｮ芽｣�りｿ�ｨ倶ｸ主黒譛ｺ螳芽�渕譛逶ｸ蜷鯉ｼ御ｾ句ｦゑｼ
```bash
./install.sh --install=driver      // 螳芽�river
./install.sh --install=npu         // 螳芽�river蜥掲irmware
./install.sh --install-scene=auto  // 閾蜉ｨ螳芽｣�園譛芽�謇ｾ蛻ｰ逧�ｽｯ莉ｶ蛹
```

# 遖ｻ郤ｿ螳芽�ｷ･蜈ｷ隕扈�ｯｴ譏
### 荳玖ｽｽ蟾･蜈ｷ菴ｿ逕ｨ

windows荳矩怙螳芽�ython3�梧耳闕蝉ｽｿ逕ｨpython3.7迚域悽莉･荳

windows迚域悽荳玖ｽｽ霍蠕Ъpython3.7.5](https://www.python.org/ftp/python/3.7.5/python-3.7.5-amd64.exe)

蟾･蜈ｷ逶蠖慕ｻ捺桷蛯荳
```
|-- downloader
|-- playbooks
|-- start_download.bat
|-- start_download.sh
|-- install.sh
|-- resources
|-- ansble.cfg
```
蝨ｨwindows荳玖ｿ占｡茎tart_download.bat蜷蜉ｨ荳玖ｽｽ�悟惠linux荳玖ｿ占｡茎tart_download.sh蜷蜉ｨ荳玖ｽ

### 荳玖ｽｽ蟾･蜈ｷ驟咲ｽｮ

荳玖ｽｽ蟾･蜈ｷ豸牙所蛻ｰ逧��鄂ｮ譁�ｻｶ螯ゆｸ
```
downloader/config.ini
downloader/config/{os}_{version}_{arch}/source.list
downloader/config/{os}_{version}_{arch}/source.repo
```

- **Python貅宣�鄂**

python貅宣�鄂蝨ｨdownloader/config.ini荳�碁ｻ倩ｮ､菴ｿ逕ｨ蜊惹ｸｺ貅撰ｼ悟庄譬ｹ謐ｮ髴隕∵崛謐
```buildoutcfg
[pypi]
index_url=http://mirrors.huaweicloud.com/pypi/simple
```

- **Centos貅宣�鄂**

centos貅仙惠蟇ｹ莠守沿譛ｬ逧��鄂逶蠖穂ｸｭ
```
downloader/config/centos_{version}_{arch}/source.repo
```
萓句Ｄentos 7.6  aarch64隨荳逧�ｺ宣�鄂ｮ蝨ｨ蛯荳区枚莉ｶ荳 
```
downloader/config/centos_7.6_aarch64/source.repo
```
centos 7.6逧�ｺ宣�鄂ｮ譁�ｻｶ蜀�ｹ蛯荳:
```
[base]
baseurl=http://mirrors.huaweicloud.com/centos-altarch/7/os/aarch64

[epel]
baseurl=http://mirrors.huaweicloud.com/epel/7/aarch64
```
陦ｨ遉ｺ蜷梧慮蜷逕ｨ莠�ase貅仙柱epel貅撰ｼ御ｸ玖ｽｽcentos逧�ｾ晁ｵ匁弍莨壻ｻ手ｿ吩ｸ､荳貅蝉ｸｭ譟･陲蜥御ｸ玖ｽｽ縲るｻ倩ｮ､菴ｿ逕ｨ蜊惹ｸｺ貅撰ｼ梧ｹ謐髴隕∽ｿｮ謾ｹ
菫謾ｹ貅宣壼ｸｸ蜿髴隕∽ｿｮ謾ｹ蜈ｶ荳ｭhost驛ｨ蛻�ｼ悟叉mirrors.huaweicloud.com驛ｨ蛻�ょる怙菫謾ｹ蜷朱擇驛ｨ蛻�ｼ瑚ｯｷ遑ｮ菫晉炊隗centos逧�ｺ宣�鄂ｮ

_豕ｨ諢:_ centos逧�ｾ晁ｵ冶ｽｯ莉ｶ髴隕∝惠base蜥憩pel荳襍ｷ謇崎�蛹�仙ｮ梧紛縲ょよ棡髴蛻髯､貅撰ｼ悟剰�鬆謌蝉ｾ晁ｵ紋ｸ玖ｽｽ荳榊ｮ梧紛

centos 8.2逧�ｺ千ｻ捺桷荳7.2蟾蠑りｾ�､,萓句�entOS 8.2 aarch64荳区ｺ宣�鄂ｮ荳ｺ�
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
蛹�性4荳蟄先ｺ舌 菫謾ｹ閼蛻吩ｸ残entos7.6逶ｸ蜷


- **Ubuntu貅宣�鄂**

蟾ｲubuntu 18.04 aarch64荳ｺ萓句ｭ撰ｼ梧ｺ宣�鄂譁�ｻｶ荳ｺ�
```buildoutcfg
config/ubuntu_18.04_aarch64/source.list
```
蜀�ｹ蛯荳具ｼ
```buildoutcfg
deb http://mirrors.huaweicoud.com/ubuntu-ports/ bionic main multiverse restricted universe
deb http://mirrors.huaweicloud.com/ubuntu-ports/ bionic-updates main multiverse restricted universe
deb http://mirrors.huaweicloud.com/ubuntu-ports/ bionic-security main multiverse restricted universe
```
驟咲ｽｮ譁�ｻｶ譬ｼ蠑丞柱ubuntu逧/etc/apt.d/source.list蝓ｺ譛ｬ逶ｸ蜷後るｻ倩ｮ､菴ｿ逕ｨ蜊惹ｸｺ貅撰ｼ悟庄譬ｹ謐ｮ螳樣刔諠��菫謾ｹ

_豕ｨ諢柔: 菫謾ｹ貅先慮髫蟶ｸ蜿蟒ｺ鞴ｿ謾ｹurl縲 蠅槫刈謌門唖髯､貅仙剰�謇ｾ蜃ｺ萓晁ｵ紋ｸ玖ｽｽ螟ｱ雍･謌紋ｾ晁ｵ也沿譛ｬ荳榊源驟阪

### downloader莉狗ｻ
1.downloader荳玖ｽｽ菫晏ｭ倡噪逶ｮ蠖慕ｻ捺桷�  
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

2.荳玖ｽｽOS邉ｻ扈滉ｾ晁ｵ也ｻ�ｻｶ  
```shell script
# 貂�炊荳玖ｽｽ譁�ｻｶ蜿顔岼蠖
python os_dep_downloader.py clean
# 謇ｧ闌荳玖ｽ
python os_dep_downloader.py
```

3.莉｣逅��鄂ｮ  
```editorconfig
[proxy]
enable=true         # 譏蜷ｦ蠑蜷莉｣逅��鄂ｮ蜿よ焚
protocol=http
hostname=openproxy.huawei.com
port=8080
username=none       # 莉｣逅�ｴｦ蜿ｷ
userpassword=none   # 莉｣逅�ｯ�
```
### Driver,Frimware蜥靴ANN螻りｽｯ莉ｶ螳芽｣

Driver,Firmware,CANN螻りｽｯ莉ｶ髴隕∽ｽｿ逕ｨrun蛹� 蟆�嶌蜈ｳ霓ｯ莉ｶ蛹�叛鄂ｮ蝨ｨresources逶蠖穂ｸ句叉蜿ｯ�御ｾ句ｦゑｼ
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

# 螳牙�豕ｨ諢丈ｺ矩｡ｹ

1. 逕ｱ莠朱懆ｦ∽ｽｿ逕ｨdpkg� rpm遲牙桁邂｡逅�呻ｼ悟宵閭ｽ菴ｿ逕ｨroot雍ｦ蜿ｷ霑占

2. inventory譁�ｻｶ荳莨夐�鄂霑懃ｨ区惻蝎ｨ逧вoot逕ｨ謌ｷ蜷榊柱蟇��ｼ悟ｻｺ隶菴ｿ逕ｨansible逧ёault譛ｺ蛻ｶ霑幄悟刈蟇�ｼ御ｽｿ逕ｨ螳梧�荵句錘蟒ｺ韈ｫ句叉蛻髯､
   
   蜿り�枚譯[http://www.ansible.com.cn/docs/playbooks_vault.html](http://www.ansible.com.cn/docs/playbooks_vault.html)
