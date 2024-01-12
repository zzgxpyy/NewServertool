# 新服务器环境配置安装
```shell
yum update
yum install -y vim unzip nmap python3 git nodejs
#sudo yum install -y yum-utils
$ sudo yum-config-manager \
    --add-repo \
    https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo

$ sudo sed -i 's/download.docker.com/mirrors.aliyun.com\/docker-ce/g' /etc/yum.repos.d/docker-ce.repo

# 官方源
# $ sudo yum-config-manager \
#     --add-repo \
#     https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce docker-ce-cli containerd.io
sudo systemctl enable docker
sudo systemctl start docker
sed -i 's/#Port .*/Port 65522/g' /etc/ssh/sshd_config   
wget https://go.dev/dl/go1.20.2.linux-amd64.tar.gz
tar -C /usr/local -xzf go1.20.2.linux-amd64.tar.gz
rm -rf go1.18.1.linux-amd64.tar.gz      
echo 'export PATH=$PATH:/usr/local/go/bin' >> /etc/profile
echo 'export PATH=$PATH:/root/go/bin' >> /etc/profile
source /etc/profile
go install -v github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
mkdir tools
cd tools
git clone https://github.com/shmilylty/OneForAll
git clone https://github.com/zhzyker/vulmap.git
git clone https://github.com/maurosoria/dirsearch.git
git clone https://github.com/bit4woo/teemo
cd teemo;pip install -r requirements.txt;cd .. ##如果gevent安装不上可以去https://pypi.tuna.tsinghua.edu.cn/simple/gevent/进行下载安装
git clone https://github.com/rtcatc/Packer-Fuzzer
cd Packer-Fuzzer
pip3 install -r requirements.txt
cd ..
mkdir dismap
cd dismap
wget https://github.com/zhzyker/dismap/releases/download/v0.3/dismap-0.3-linux-amd64
cd ..
mkdir subfinder
cd subfinder/
wget https://github.com/projectdiscovery/subfinder/releases/download/v2.5.1/subfinder_2.5.1_linux_amd64.zip;unzip subfinder_2.5.1_linux_amd64.zip 
cd ..
git clone https://github.com/WhiteHSBG/JNDIExploit/;cd JNDIExploit;wget https://github.com/WhiteHSBG/JNDIExploit/releases/download/v1.4/JNDIExploit.v1.4.zip;unzip JNDIExploit.v1.4.zip;cd .. ##log4j利用工具
git clone https://github.com/wyzxxz/jndi_tool;cd jndi_tool;wget https://toolaffix.oss-cn-beijing.aliyuncs.com/jndi_tool.jar ##fastJson利用工具
cd ..
yum install sqlite-devel libxslt-devel libxml2-devel java-1.7.0-openjdk libpcap-devel nano openssl-devel zlib-devel libffi-devel gdbm-devel readline-devel wget gcc-c++ patch readline zlib bzip2 autoconf automake libtool bison iconv-devel libyaml-devel make postgresql-devel
curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall
chmod +x msfinstall
./msfinstall
rm -rf msfinstall
```

