
# AudibleZ 安装教程（Windows 版）

Audiblez是一个使用Kokoro文本转语音模型的免费开源项目。最新版本增加了图形界面，更加直观，新手友好。

优点：语音自然流畅，多种口音可选。免费，开源，不需要联网。

缺点：安装略繁琐，对设备有一定要求。转换速度略慢，生成音频文件容量大，需要进一步压缩携带。


本文目标：一步步完成 AudibleZ 安装。

---

## 准备工具：安装chocolatey, ffmpeg, espeak-ng, python

### 第一步，安装chocolatey

Chocolatey是一款windows非常流行的软件下载与管理解决方案。鉴于audible需要非最新版本的python(<=12)，使用一款带版本控制的安装包管理软件是最优选择。

1. 点击左下角“开始”菜单，输入 `powershell`进行搜索
2. 右键点击“Windows PowerShell”，选择 **“以管理员身份运行”**
3. 粘贴下面这行命令，然后按下 Enter：

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; `
[System.Net.ServicePointManager]::SecurityProtocol = 3072; `
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

4. 安装完毕后，输入以下命令检查是否安装成功：

```powershell
choco --version
```

显示版本号如 `2.4.3` 即成功。(版本号可能比教程时更新，不用紧张只要能看到版本号就好)

---
### 第二步，使用chocolatey安装 ffmpeg 和 espeak-ng 

ffmpeg 是最流行的命令行音频处理软件，市面上80%的音频转化工具都是使用的ffmpeg内核。
espeak-ng 是一款免费开源的TTS语音合成器。

1. 在powershell（管理员身份运行）中粘贴下面这行命令安装ffmpeg，然后按下 Enter：

```powershell
choco install -y ffmpeg
```
安装完毕后，输入以下命令检查是否安装成功：

```powershell
ffmpeg -version
```
能看到版本号即成功。

2. 相同地，继续输入下一条命令来安装espeak-ng

```powershell
choco install -y espeak-ng
```
安装完毕后，输入以下命令检查是否安装成功：

```powershell
espeak-ng -version
```
能看到版本号即成功。


### 第三步：使用chocolatey安装 python

由于最新版本的python是v13，但audiblez适用于较老版本python(<=12),安装时需要**指定版本号**

1. 在powershell（管理员身份运行）中粘贴下面这行命令安装ffmpeg，然后按下 Enter：

```powershell
choco install python --version=3.12.9
```

安装完成后，使用以下命令确认是否成功：

```powershell
python --version
pip --version
```

你应该看到类似输出：

```
Python 3.12.9
pip 24.3.1
```
能看到版本号即成功。

---

## 安装 AudibleZ

由于Audiblez是本地AI音频处理软件，使用python安装Audiblez时会自动下载一百多个kokoro语音转换工具相关的依赖包，非常messy。强烈推荐在一个单独的虚拟环境（新建文件夹）中安装，将来需要删除时直接删掉整个文件夹，其他的软件依赖包不会收到影响

1. 创建专属文件夹
 打开Windows文件管理器，在你想要安装的地方新建文件夹audiblez。点击打开文件夹，右击空白处选择“在终端中打开（Open in Terminal）”

2. 在终端powershell中应该直接显示了当前文件夹的位置。比如我的终端此时显示的就是

 > PS D:\audiblez>

 D:\audiblez是我的audiblez路径。

3. 创建并激活虚拟环境
powershell中粘贴下面这行命令并回车，即可创建一个新的虚拟环境
```powershell
python -m venv venv
```
powershell中粘贴下面这行命令并回车，即可创激活并进入该虚拟环境
```powershell
.\venv\Scripts\activate
```
成功时命令行前会出现 `(venv)`，比如我的终端此刻显示的就是
> (venv) PS D:\audiblez>

4. 安装 AudibleZ
在命令行前显示有`(venv)`的情况下，输入下面命令并回车，即可在虚拟环境venv中安装audiblez
```powershell
pip install audiblez pillow wxpython
```
此时如果移开终端窗口，会发现audiblez文件夹中新出现一个叫“venv”的文件夹。audiblez相关依赖包全部安装在这个文件夹中，将来需要删除时一键删掉整个文件夹即可。

---

## 登录 AudibleZ

在命令行前显示有`(venv)`的情况下，输入下面命令并回车，即可打开audiblez图形界面
```powershell
audiblez-ui
```


>以后每次需要打开AudibleZ，请重复以下步骤：
>进入audiblez文件夹，右键单击“在终端中打开（Open in Terminal）”，在终端powershell中输入并回车
>
>.\venv\Scripts\activate
>
>在命令行前显示有`(venv)`的情况下，输入下面命令并回车，即可打开audiblez图形界面
>
>audiblez-ui
>
----

## 常见问题

待续……

<div style="height: 8rem;"></div>