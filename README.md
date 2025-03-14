# AV Data Capture 日本电影元数据抓取工具（刮削器）


<a title="Hits" target="_blank" href="https://github.com/yoshiko2/AV_Data_Capture"><img src="https://hits.b3log.org/yoshiko2/AV_Data_Capture.svg"></a>
![](https://img.shields.io/badge/build-passing-brightgreen.svg?style=flat-square)
![](https://img.shields.io/github/downloads/yoshiko2/av_data_capture/total.svg?style=flat-square)<br>
![](https://img.shields.io/github/languages/code-size/yoshiko2/av_data_capture.svg?style=flat-square)
![](https://img.shields.io/github/issues/yoshiko2/av_data_capture.svg?style=flat-square)
![](https://img.shields.io/github/license/yoshiko2/av_data_capture.svg?style=flat-square)
![](https://img.shields.io/github/release/yoshiko2/av_data_capture.svg?style=flat-square)<br>
![](https://img.shields.io/github/forks/yoshiko2/av_data_capture.svg?style=flat-square)
![](https://img.shields.io/github/stars/yoshiko2/av_data_capture.svg?style=flat-square)
![](https://img.shields.io/github/watchers/yoshiko2/av_data_capture.svg?style=flat-square)

# 目录
* [免责声明](#免责声明)
* [注意](#注意)
* [你问我答 FAQ](#你问我答-faq)
* [效果图](#效果图)
* [如何使用](#如何使用)
* [下载](#下载)
* [简明教程](#简要教程)
* [模块安装](#1请安装模块在cmd终端逐条输入以下命令安装)
* [配置](#2配置configini)
* [运行软件](#4运行-av_data_capturepyexe)
* [异常处理（重要）](#5异常处理重要)
* [导入至媒体库](#7把jav_output文件夹导入到embykodi中根据封面选片子享受手冲乐趣)
* [写在后面](#8写在后面)

# 免责声明
1.本软件仅供**技术交流，学术交流**使用，本项目旨在学习Beautifulsoup, xpath, PyQuery<br>
2.本软件禁止用于任何非法用途<br>
3.使用者使用该软件产生的一切法律后果由使用者承担<br>
4.不可使用于商业和个人其他意图<br>

# 注意
**推荐用法: 使用该软件后，对于不能正常获取元数据的电影可以用 Everaver 来补救**<br>
暂不支持多P电影<br>

# 你问我答 FAQ
### F：这软件是干什么用的？
**Q**：配合本地影片管理软件EMBY,KODI管理本地影片，该软件起到分类与元数据抓取作用，利用元数据信息来分类，**注意：不提供任何影片下载地址**。
### F：什么是元数据？
**Q**：元数据包括了影片的：封面，导演，演员，简介，类型......
### F：软件收费吗？
**Q**：软件永久免费。除了 **作者** 钦点以外，给那些 **利用本软件牟利** 的人送上 **骨灰盒-全家族 | 崭新出厂**
### F：软件运行异常怎么办？
**Q**：认真看 [异常处理（重要）](#5异常处理重要)

# 效果图
**图片来自网络**，由于相关法律法规，具体效果请自行联想
![](https://i.loli.net/2019/07/04/5d1cf9bb1b08b86592.jpg)
![](https://i.loli.net/2019/07/04/5d1cf9bb2696937880.jpg)<br>

# 如何使用
### 下载
* release的程序可脱离**python环境**运行，可跳过 [模块安装](#1请安装模块在cmd终端逐条输入以下命令安装)<br>Release 下载地址(**仅限Windows**):<br>[![](https://img.shields.io/badge/%E4%B8%8B%E8%BD%BD-windows-blue.svg?style=for-the-badge&logo=windows)](https://github.com/yoshiko2/AV_Data_Capture/releases/download/0.11.5/Beta11.5.zip)<br>
* Linux,MacOS请下载源码包运行

* Windows Python环境:[点击前往](https://www.python.org/downloads/windows/) 选中executable installer下载
* MacOS Python环境：[点击前往](https://www.python.org/downloads/mac-osx/)
* Linux Python环境：Linux用户懂的吧，不解释下载地址
### 简要教程:<br>
**1.把软件拉到和电影的同一目录<br>2.设置ini文件的代理（路由器拥有自动代理功能的可以把proxy=后面内容去掉）<br>3.运行软件等待完成<br>4.把JAV_output导入至KODI,EMBY中。<br>详细请看以下教程**<br>

## 1.请安装模块,在CMD/终端逐条输入以下命令安装
```python
pip install requests
```
### 
```python
pip install pyquery
```
###
```python
pip install lxml
```
###
```python
pip install Beautifulsoup4
```
###
```python
pip install pillow
```
###

## 2.配置config.ini
config.ini
>[proxy]<br>
>proxy=127.0.0.1:1080<br>
>timeout=10<br>
>retry=3<br>
>
>[Name_Rule]<br>
>location_rule='JAV_output/'+actor+'/['+number+']-'+title<br>
>naming_rule=number+'-'+title<br>
>
>[update]<br>
>update_check=1<br>

### 1.网络设置
#### * 针对“某些地区”的代理设置
打开```config.ini```,在```[proxy]```下的```proxy```行设置本地代理地址和端口，支持Shadowxxxx/X,V2XXX本地代理端口:<br>
例子:```proxy=127.0.0.1:1080```<br>素人系列抓取建议使用日本代理<br>
**路由器拥有自动代理功能的可以把proxy=后面内容去掉**<br>
**本地代理软件开全局模式的同志同上**<br>
**如果遇到tineout错误，可以把文件的proxy=后面的地址和端口删除，并开启vpn全局模式，或者重启电脑，vpn，网卡**<br>
#### 连接超时重试设置
>[proxy]<br>
>timeout=10<br>

10为超时重试时间 单位：秒
#### 连接重试次数设置
>[proxy]<br>
>retry=3<br>

3即为重试次数

### (可选)设置自定义目录和影片重命名规则
**已有默认配置**<br>
##### 命名参数<br>
>title = 片名<br>
>actor = 演员<br>
>studio = 公司<br>
>director = 导演<br>
>release = 发售日<br>
>year = 发行年份<br>
>number = 番号<br>
>cover = 封面链接<br>
>tag = 类型<br>
>outline = 简介<br>
>runtime = 时长<br>
##### **例子**:<br>
>目录结构规则:location_rule='JAV_output/'+actor+'/'+number **不推荐修改目录结构规则，抓取数据时新建文件夹容易出错**<br>
>影片命名规则:naming_rule='['+number+']-'+title<br> **在EMBY,KODI等本地媒体库显示的标题**
### 3.更新开关
>[update]<br>update_check=1<br>
1为开，0为关
## 3.把软件拷贝和电影的统一目录下
## 4.运行 ```AV_Data_capture.py/.exe```
当文件名包含:<br>
中文，字幕，-c., -C., 处理元数据时会加上**中文字幕**标签
## 5.异常处理（重要）
### 请确保软件是完整地！确保ini文件内容是和下载提供ini文件内容的一致的！
### 关于软件打开就闪退
可以打开cmd命令提示符，把 ```AV_Data_capture.py/.exe```拖进cmd窗口回车运行，查看错误，出现的错误信息**依据以下条目解决**
### 关于 ```Updata_check``` 和 ```JSON``` 相关的错误
跳转 [网络设置](#1网络设置)
### 关于```FileNotFoundError: [WinError 3] 系统找不到指定的路径。: 'JAV_output''``` 
在软件所在文件夹下新建 JAV_output 文件夹，可能是你没有把软件拉到和电影的同一目录
### 关于连接拒绝的错误
请设置好[代理](#1针对某些地区的代理设置)<br>
### 关于Nonetype,xpath报错
同上<br>
### 关于番号提取失败或者异常
**目前可以提取元素的影片:JAVBUS上有元数据的电影，素人系列:300Maan,259luxu,siro等,FC2系列**<br>
>下一张图片来自Pockies的blog 原作者已授权<br>

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461gy1g1cxc31t41j20i804zdgo.jpg)

目前作者已经完善了番号提取机制，功能较为强大，可提取上述文件名的的番号，如果出现提取失败或者异常的情况，请用以下规则命名<br>
**妈蛋不要喂软件那么多野鸡片子，不让软件好好活了，操**
```
COSQ-004.mp4
```

针对 **野鸡番号** ，你需要把文件名命名为与抓取网站提供的番号一致（文件拓展名除外），然后把文件拖拽至core.exe/.py<br>
**野鸡番号**:比如 ```XXX-XXX-1```,  ```1301XX-MINA_YUKA``` 这种**野鸡**番号，在javbus等资料库存在的作品。<br>**重要**：除了 **影片文件名**  ```XXXX-XXX-C```，后面这种-C的是指电影有中文字幕！<br>
条件：文件名中间要有下划线或者减号"_","-"，没有多余的内容只有番号为最佳，可以让软件更好获取元数据
对于多影片重命名，可以用[ReNamer](http://www.den4b.com/products/renamer)来批量重命名<br>
### 关于PIL/image.py
暂时无解，可能是网络问题或者pillow模块打包问题，你可以用源码运行（要安装好第一步的模块）


## 6.软件会自动把元数据获取成功的电影移动到JAV_output文件夹中，根据演员分类，失败的电影移动到failed文件夹中。
## 7.把JAV_output文件夹导入到EMBY,KODI中，等待元数据刷新，完成
## 8.写在后面
怎么样，看着自己的日本电影被这样完美地管理，是不是感觉成就感爆棚呢?<br>
**tg官方电报群:[ 点击进群](https://t.me/AV_Data_Capture_Official)**<br>


