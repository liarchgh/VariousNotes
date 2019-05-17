# RaspberryPi

## Hardware

* [3代b+型E14版](https://item.jd.com/30028521882.html)
* [散热片两铜一铝](https://item.jd.com/11092679406.html)
* [九层外壳带风扇 透明](https://item.jd.com/29779894418.html)

All in [a store of jd](https://mall.jd.com/index-153636.html)

## Play

### [树莓派网络存储（NAS） OpenMediaVault 安装配置](http://shumeipai.nxez.com/2018/01/10/raspberry-pi-nas-openmediavault-installation.html)

NAS

### [树莓派远程桌面连接-使用Windows自带远程桌面连接工具](https://blog.csdn.net/qq813480700/article/details/72598000)

本来一开始要使用VcXsrv连接的，然而搞了半天没弄好

### [安装火狐浏览器](https://my.oschina.net/menghaoqi/blog/760817)

```text
    sudo apt-get install iceweasel
```

### [当前状态和数据（温度、CPU、内存、硬盘）](http://shumeipai.nxez.com/2014/10/04/get-raspberry-the-current-status-and-data.html)

```text
import os
import time

# global var
global CPU_temp
global CPU_usage

# RAM information
# Output is in kb
global RAM_stats
global RAM_total
global RAM_used
global RAM_free

# Disk informatio
global DISK_stats
global DISK_total
global DISK_used
global DISK_perc

# Return CPU temperature as a character string                                      
def getCPUtemperature():
    res = os.popen('vcgencmd measure_temp').readline()
    return(res.replace("temp=","").replace("'C\n",""))

# Return RAM information (unit=kb) in a list                                       
# Index 0: total RAM                                                               
# Index 1: used RAM                                                                 
# Index 2: free RAM                                                                 
def getRAMinfo():
    p = os.popen('free')
    i = 0
    while 1:
        i = i + 1
        line = p.readline()
        if i==2:
            return(line.split()[1:4])

# Return % of CPU used by user as a character string                                
def getCPUuse():
    return(str(os.popen("top -n1 | awk '/Cpu\(s\):/ {print $2}'").readline().strip()))

# Return information about disk space as a list (unit included)                     
# Index 0: total disk space                                                         
# Index 1: used disk space                                                         
# Index 2: remaining disk space                                                     
# Index 3: percentage of disk used                                                  
def getDiskSpace():
    p = os.popen("df -h /")
    i = 0
    while 1:
        i = i +1
        line = p.readline()
        if i==2:
            return(line.split()[1:5])


def getInfo():
    # global var
    global CPU_temp
    global CPU_usage

    # RAM information
    # Output is in kb
    global RAM_stats
    global RAM_total
    global RAM_used
    global RAM_free

    # Disk informatio
    global DISK_stats
    global DISK_total
    global DISK_used
    global DISK_perc

    # CPU informatiom
    CPU_temp = getCPUtemperature()
    CPU_usage = getCPUuse()

    # RAM information
    # Output is in kb, here I convert it in Mb for readability
    RAM_stats = getRAMinfo()
    RAM_total = round(int(RAM_stats[0]) / 1000,1)
    RAM_used = round(int(RAM_stats[1]) / 1000,1)
    RAM_free = round(int(RAM_stats[2]) / 1000,1)

    # Disk information
    DISK_stats = getDiskSpace()
    DISK_total = DISK_stats[0]
    DISK_used = DISK_stats[1]
    DISK_perc = DISK_stats[3]

if __name__ == '__main__':
    while True:
        # global var
        global CPU_temp
        global CPU_usage

        # RAM information
        # Output is in kb
        global RAM_stats
        global RAM_total
        global RAM_used
        global RAM_free

        # Disk informatio
        global DISK_stats
        global DISK_total
        global DISK_used
        global DISK_perc

        getInfo()

        print('================================')
        print(time.asctime(time.localtime(time.time())))
        print('--------------------------------')
        print('CPU Temperature = '+CPU_temp)
        print('CPU Use = '+CPU_usage)
        print('--------------------------------')
        print('RAM Total = '+str(RAM_total)+' MB')
        print('RAM Used = '+str(RAM_used)+' MB')
        print('RAM Free = '+str(RAM_free)+' MB')
        print('--------------------------------')
        print('DISK Total Space = '+str(DISK_total)+'B')
        print('DISK Used Space = '+str(DISK_used)+'B')
        print('DISK Used Percentage = '+str(DISK_perc))
        print('================================')
        time.sleep(1)
```

### Samba文件共享

[树莓派安装Samba](https://ails.top/archives/d7e3de59.html#打造SAMBA共享) [Windows访问Samba服务器](https://blog.csdn.net/linglongwunv/article/details/5212919)

### [终端连接wifi](https://blog.csdn.net/huayucong/article/details/51376279)

### [解锁root账户并允许ssh登录](http://www.shumeipaiba.com/wanpai/jiaocheng/2.html)

## Software

* [UFW防火墙](http://shumeipai.nxez.com/2014/06/09/simple-raspberry-pi-ufw-firewall-settings.html)

  [设置](https://linux.cn/article-8087-1.html)

  默认防火墙是开启的，一些涉及到网络的软件无法正常使用

## bashrc

### alias

```text
alias piinfo="python3 /home/pi/Tools/GetPiInformation.py"
```

## backup

* [制作指定大小Img镜像](http://www.cnblogs.com/haochuang/p/6066532.html)

