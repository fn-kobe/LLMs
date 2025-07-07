



@[TOC](文章目录)
# 前言：技术简介
**亲爱的家人们，创作很不容易，若对您有帮助的话，请点赞收藏加关注哦，您的关注是我持续创作的动力，谢谢大家！有问题请私信或联系邮箱：fn_kobe@163.com**

**①Ollama**
定位：一个本地部署大语言模型（LLM）和相关工具的平台。
功能：帮助用户在本地环境中运行、测试和管理 AI 模型，而无需依赖云服务。
优势：数据本地化、隐私性较高，并能定制化部署。

**②Deepseekr1**
定位：国产AI大模型，干翻美股的AI新势力。
功能：侧重于深度搜索、数据分析或智能检索功能。
优势：通过深度学习技术，实现高效的信息搜索与分析）。

**③OpenWebUI**
定位：一个开源的网络用户界面，用于管理和交互操作。
功能：提供直观的网页界面，让用户可以通过浏览器对模型、工具或系统进行配置、监控和操作。
优势：界面友好、易于上手，降低了使用门槛和运维复杂度。

**④Hyper-V**
定位：微软提供的虚拟化平台。
功能：允许用户在单一物理服务器上创建和管理多个虚拟机。
优势：资源隔离、提高利用率、支持测试环境和生产环境的分离，为运行像 Ollama 这样需要特定环境支持的工具提供安全、稳定的虚拟平台。

**⑤总体来说**：
集成应用：将 Ollama 平台及其内部模型（例如 Deepseekr1）通过 OpenWebUI 提供友好的操作界面进行管理和使用；同时，通过 Hyper-V 构建虚拟化环境，为这些工具的部署、测试和生产运行提供稳定且隔离的基础设施支持。
适用场景：适合需要在本地部署、管理大语言模型和深度数据检索工具的场景，同时又希望借助虚拟化技术保障系统稳定性和安全性的用户。
# 一、笔者电脑配置
***笔者电脑配置如下：***
①OS：Win11
②内存：64G
③磁盘：1.5T
④CPU：14核 20线程
⑤GPU：RTX3060
***ps:内存尽量在16G以上***
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/4bf8a8ffd91c41d3a13c8523c91acffd.png)
# 二、安装Ollama
## 2.1、下载Ollama安装包
①登录[Ollama官网](https://ollama.com/)下载Ollama安装包，选择相应操作系统，***建议另存安装C盘以外地方***
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/fddadc20a8f34861bf2b1f2e49fd87f8.png)
## 2.2、安装Ollama
①Windows下安装Ollama简单，双击.exe运行安装
②打开win+r终端，输入cmd，命令行输入ollama，若出现下图所示则安装成功
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/4ed548d9663b4b748b9e8bb08431d8be.png)
## 2.3、配置Ollama模型路径（超级重要）
### 2.3.1、模型路径原配置
因为windows 的安装默认不支持修改程序安装目录，
①默认安装后的目录：C:\Users\username\AppData\Local\Programs\Ollama
②默认安装的模型目录：C:\Users\username\ .ollama
③默认的配置文件目录：C:\Users\username\AppData\Local\Ollama
### 2.3.2、更改模型路径原配置
由于Ollama的模型默认会在***C盘用户文件夹下的.ollama/models文件夹***中，避免C盘容量紧张，需要配置环境变量***OLLAMA_MODELS***，设置为指定的路径，如F:\LLM\ollama
     ①窗口搜索环境变量并打开
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/4700fcc8c49549d4a8a80e9b6d2b4e9b.png)
 ②依次执行并添加系统环境变量：***变量名：OLLAMA_MODELS    变量值：F:\LLM\ollama***（添加自己电脑的文件目录即可），最后一定要依次***点击确定***
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/92047dd858e44da093dd1bd8dcc6a315.png)
## 2.4、下载deepseek R1模型
### 2.4.1、deepseek模型选择
①进入[ollama](https://ollama.com/)官网，根据一下步骤
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/6d948e0016eb4d92aef90a2dc0a93199.png)
 
 ### 2.4.2、部署deepseek R1模型：7B
 **温馨提示**：模型的参数大小根据自己电脑的配置选择，部署的本地模型越大，使用的深度求索效果就越好。相应的配置表如下：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/fce06dbcac1e43e088c30366b84da592.png)

①win + r打开终端，输入cmd，输入***ollama run deepseek-r1:7b***，安装过程比较漫长，约20分钟左右，成功会有如下提示：![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/5b70e94de64c4a89ae73fe43c9866955.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/2d13e9c8cd7c456fadea3d417f84ab93.png)

### 2.4.3、模型问答测试
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/919f822ebbd94063a75cf9932987703d.png)

***至此：deepseek R1:7B本地部署已完成***

①由于***终端问答测试不美观***，需要安装OpenWebUI在Web端测试
# 三、安装OpenWebUI
## 3.1、安装Docker
### 3.1.1、下载Docker
[下载地址](https://docs.docker.com/desktop/setup/install/windows-install/)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/08d0814609c9414cab3a85f0523b071b.png)

### 3.1.2、启动微软Hyper-V
①依次操作：控制面板→查看方式-→程序→启用或关闭Windows功能→勾选Hyper-V→重启电脑后安装成功
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/3860af8fe0df4ee2ace90b66e5ffb4da.png)
***注意事项：***
①若没有Hyper-V选项，使用如下命令安装
```bash
pushd "%~dp0"

dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hv.txt

for /f %%i in ('findstr /i . hv.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"

del hv.txt

Dism /online /enable-feature /featurename:Microsoft-Hyper-V -All /LimitAccess /ALL

Pause

```
②将上述命令复制到Hyper-V.bat批处理文件中，然后以管理员身份运行，并重启电脑
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/6abcc8e58d314e0bbd3eaf5335dbdaa8.png)
### 3.1.3、安装Docker
①将3.1.1步骤中下载的.exe文件双击执行
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/e4bfce7d1288422e9a321a861ee239c3.png)

②打开并测试Docker，一般用命令行操作
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/8c50b5d55c8a4e5aa8f930b9253d4f4b.png)
### 3.1.4、Docker切换国内镜像源
①操作如下：设置→Docker Engine→复制添加→Apply&restart
![`在这里插入图片描述`](https://i-blog.csdnimg.cn/direct/fed01b5e1a604c6da1c781c11979316f.png)

```bash
{
  "registry-mirrors": [
    "https://82m9ar63.mirror.aliyuncs.com",
    "http://hub-mirror.c.163.com",
    "https://docker.mirrors.ustc.edu.cn"
  ],
  "builder": {
    "gc": {
      "defaultKeepStorage": "20GB",
      "enabled": true
    }
  },
  "experimental": false,
  "features": {
    "buildkit": true
  }
}

```
## 3.2、安装OpenWebUI
[安装地址](https://github.com/open-webui/open-webui)
①进入github地址，下拉找到如图命令
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/4e07e332076e4c05b10e83857223c6ef.png)
②***win+r后，cmd打开终端，输入命令***：docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
***ps:安装比较漫长，请耐心等待***
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/16bc08e98245406d9f0ead875e92f260.png)

## 3.3、Web访问测试
**①访问地址**：[http://localhost:3000/](http://localhost:3000/)。  前提是***终端后台启动Docker DeskTop和deepseek R1：7B***，启动方式如下：
deepseek-r1:7b：win+r后，输入cmd，再输入命令：ollama run deepseek-r1:7b
Docker DeskTop：双击快捷方式启动即可
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/ef0fb845336444e580277e683663918f.png)

***②提问测试***
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/0e8c6e9f053b4e61b8f085b90ca81396.png)

# 四、总结与感谢
①利用Hyper-V创建虚拟化环境，通过Ollama高效管理和部署deepseek R1大语言模型，并结合OpenWebUI提供直观的交互界面，这些技术的结合能够实现高效、灵活的自然语言处理应用开发与测试，适用于多种场景的智能化解决方案。

***②以上内容和步骤亲测有效，若有问题请私信我，创作不易，亲爱的家人们多多支持哦！***



