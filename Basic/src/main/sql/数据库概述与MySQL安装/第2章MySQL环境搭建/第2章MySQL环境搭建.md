# 第2章MySQL环境搭建
## 1. MySQL的卸载
### 步骤1：停止MySQL服务
在卸载之前，先停止MySQL8.0的服务。按键盘上的<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Delete</kbd>组合键，打开“任务管理器”对话框，可以在“服务”列表找到“MySQL8.0”的服务，如果现在“正在运行”状态，可以右键单击服务，选择“停止”选项停止MySQL8.0的服务，如图所示：  
![img.png](img.png)  
### 步骤2：软件的卸载
#### 方式1：通过控制面板方式
卸载MySQL8.0的程序可以和其他桌面应用程序一样直接在“控制面板”选择“卸载程序”，并在程序列表中找到MySQL8.0服务器程序，直接双击卸载即可，如图所示。这种方式删除，数据目录下的数据不会跟着删除：  
![img_1.png](img_1.png)  

#### 方式2：通过360或电脑管家等软件卸载
略

#### 方式3：通过安装包提供的卸载功能卸载
你也可以通过安装向导程序进行MySQL8.0服务器程序的卸载。
1. 再次双击下载的mysql-installer-community-8.0.26.0.msi文件，打开安装向导。安装向导会自动检测已
安装的MySQL服务器程序。
2. 选择要卸载的MySQL服务器程序，单击“Remove”（移除），即可进行卸载。  
![img_2.png](img_2.png)
3. 单击“Next”（下一步）按钮，确认卸载。  
![img_3.png](img_3.png)  
4. 弹出是否同时移除数据目录选择窗口。如果想要同时删除MySQL服务器中的数据，则勾选“Remove the data directory”，如图所示。  
![img_4.png](img_4.png)  
5. 执行卸载。单击“Execute”（执行）按钮进行卸载。 
![img_5.png](img_5.png)
6. 完成卸载。单击“Finish”（完成）按钮即可。如果想要同时卸载MySQL8.0的安装向导程序，勾选“Yes，Uninstall MySQL Installer”即可，如图所示。  
![img_6.png](img_6.png)

### 步骤3：残余文件的清理
如果再次安装不成功，可以卸载后对残余文件进行清理后再安装。
1. 服务目录：mysql服务的安装目录
2. 数据目录：默认在C:\ProgramData\MySQL  

如果自己单独指定过数据目录，就找到自己的数据目录进行删除即可。

> 注意：请在卸载前做好数据备份  
> 在操作完以后，需要重启计算机，然后进行安装即可。如果仍然安装失败，需要继续操作如下步骤4。

### 步骤4：清理注册表（选做）
如果前几步做了，再次安装还是失败，那么可以清理注册表。如何打开注册表编辑器：在系统的搜索框中输入`regedit`
```
HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Eventlog\Application\MySQL服务 目录删除
HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\MySQL服务 目录删除
HKEY_LOCAL_MACHINE\SYSTEM\ControlSet002\Services\Eventlog\Application\MySQL服务 目录删除
HKEY_LOCAL_MACHINE\SYSTEM\ControlSet002\Services\MySQL服务 目录删除
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Eventlog\Application\MySQL服务目录删除
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MySQL服务删除
```
> 注册表中的ControlSet001,ControlSet002,不一定是001和002,可能是ControlSet005、006之类

### 步骤5：删除环境变量配置
找到path环境变量，将其中关于mysql的环境变量删除，切记不要全部删除。  

例如：删除 D:\develop_tools\mysql\MySQLServer8.0.26\bin; 这个部分

![img_7.png](img_7.png)

## 2. MySQL的下载、安装、配置
### 2.1 MySQL的4大版本
> MySQL Community Server 社区版本，开源免费，自由下载，但不提供官方技术支持，适用于大多数普通用户。  
> MySQL Enterprise Edition 企业版本，需付费，不能在线下载，可以试用30天。提供了更多的功能和更完备的技术支持，更适合于对数据库的功能和可靠性要求较高的企业客户。  
> MySQL Cluster 集群版，开源免费。用于架设集群服务器，可将几个MySQL Server封装成一个Server。需要在社区版或企业版的基础上使用。  
> MySQL Cluster CGE 高级集群版，需付费。  

目前最新版本为 8.0.27 ，发布时间 2021年10月 。此前，8.0.0 在 2016.9.12日就发布了。  

此外，官方还提供了 MySQL Workbench （GUITOOL）一款专为MySQL设计的 图形界面管理工具。MySQLWorkbench又分为两个版本，分别是 社区版 （MySQL Workbench OSS）、 商用版 （MySQL WorkbenchSE）。

### 2.2 软件的下载
#### 1. 下载地址
官网：https://www.mysql.com

#### 2. 打开官网，点击DOWNLOADS
然后，点击 MySQL Community(GPL) Downloads

![img_8.png](img_8.png)

#### 3. 点击 MySQL Community Server
![img_9.png](img_9.png)

#### 4. 在General Availability(GA) Releases中选择适合的版本
Windows平台下提供两种安装文件：MySQL二进制分发版（.msi安装文件）和免安装版（.zip压缩文件）。一般来讲，应当使用二进制分发版，因为该版本提供了图形化的安装向导过程，比其他的分发版使用起来要简单，不再需要其他工具启动就可以运行MySQL。

这里在Windows 系统下推荐下载 MSI安装程序 ；点击 Go to Download Page 进行下载即可

![img_10.png](img_10.png)

![img_11.png](img_11.png)

* Windows下的MySQL8.0安装有两种安装程序
  + mysql-installer-web-community-8.0.26.0.msi 下载程序大小：2.4M；安装时需要联网安装组件。 
  + mysql-installer-community-8.0.26.0.msi 下载程序大小：450.7M；安装时离线安装即可。推荐。

* 如果安装MySQL5.7版本的话，选择 Archives ，接着选择MySQL5.7的相应版本即可。这里下载最近期的MySQL5.7.34版本。

![img_12.png](img_12.png)

![img_37.png](img_37.png)

### 2.3 MySQL8.0 版本的安装

MySQL下载完成后，找到下载文件，双击进行安装，具体操作步骤如下。

步骤1：双击下载的mysql-installer-community-8.0.26.0.msi文件，打开安装向导。

步骤2：打开“Choosing a Setup Type”（选择安装类型）窗口，在其中列出了5种安装类型，分别是Developer Default（默认安装类型）、Server only（仅作为服务器）、Client only（仅作为客户端）、Full（完全安装）、Custom（自定义安装）。这里选择“Custom（自定义安装）”类型按钮，单击“Next(下一步)”按钮。

![img_14.png](img_14.png)

步骤3：打开“Select Products” （选择产品）窗口，可以定制需要安装的产品清单。例如，选择“MySQL Server 8.0.26-X64”后，单击“→”添加按钮，即可选择安装MySQL服务器，如图所示。采用通用的方法，可以添加其他你需要安装的产品。

![img_15.png](img_15.png)

此时如果直接“Next”（下一步），则产品的安装路径是默认的。如果想要自定义安装目录，则可以选中对应的产品，然后在下面会出现“Advanced Options”（高级选项）的超链接。

![img_16.png](img_16.png)

单击“Advanced Options”（高级选项）则会弹出安装目录的选择窗口，如图所示，此时你可以分别设置MySQL的服务程序安装目录和数据存储目录。如果不设置，默认分别在C盘的Program Files目录和ProgramData目录（这是一个隐藏目录）。如果自定义安装目录，请避免“中文”目录。另外，建议服务目录和数据目录分开存放。

![img_17.png](img_17.png)

步骤4：在上一步选择好要安装的产品之后，单击“Next”（下一步）进入确认窗口，如图所示。单击“Execute”（执行）按钮开始安装。

![img_18.png](img_18.png)

步骤5：安装完成后在“Status”（状态）列表下将显示“Complete”（安装完成），如图所示。

![img_19.png](img_19.png)

### 2.4 配置MySQL8.0

MySQL安装之后，需要对服务器进行配置。具体的配置步骤如下。

步骤1：在上一个小节的最后一步，单击“Next”（下一步）按钮，就可以进入产品配置窗口。

![img_20.png](img_20.png)

步骤2：单击“Next”（下一步）按钮，进入MySQL服务器类型配置窗口，如图所示。端口号一般选择默认端口号3306。

![img_21.png](img_21.png)

其中，“Config Type”选项用于设置服务器的类型。单击该选项右侧的下三角按钮，即可查看3个选项，如图所示。

![img_22.png](img_22.png)

* Development Machine（开发机器） ：该选项代表典型个人用桌面工作站。此时机器上需要运行多个应用程序，那么MySQL服务器将占用最少的系统资源。
* Server Machine（服务器） ：该选项代表服务器，MySQL服务器可以同其他服务器应用程序一起运行，例如Web服务器等。MySQL服务器配置成适当比例的系统资源。
* Dedicated Machine（专用服务器） ：该选项代表只运行MySQL服务的服务器。MySQL服务器配置成使用所有可用系统资源。

步骤3：单击“Next”（下一步）按钮，打开设置授权方式窗口。其中，上面的选项是MySQL8.0提供的新的授权方式，采用SHA256基础的密码加密方法；下面的选项是传统授权方法（保留5.x版本兼容性）。

![img_23.png](img_23.png)

步骤4：单击“Next”（下一步）按钮，打开设置服务器root超级管理员的密码窗口，如图所示，需要输入两次同样的登录密码。也可以通过“Add User”添加其他用户，添加其他用户时，需要指定用户名、允许该用户名在哪台/哪些主机上登录，还可以指定用户角色等。此处暂不添加用户，用户管理在MySQL高级特性篇中讲解。

![img_24.png](img_24.png)

步骤5：单击“Next”（下一步）按钮，打开设置服务器名称窗口，如图所示。该服务名会出现在Windows服务列表中，也可以在命令行窗口中使用该服务名进行启动和停止服务。本书将服务名设置为“MySQL80”。如果希望开机自启动服务，也可以勾选“Start the MySQL Server at System Startup”选项（推荐）。

下面是选择以什么方式运行服务？可以选择“Standard System Account”(标准系统用户)或者“Custom User”(自定义用户)中的一个。这里推荐前者。

![img_25.png](img_25.png)

步骤6：单击“Next”（下一步）按钮，打开确认设置服务器窗口，单击“Execute”（执行）按钮。

![img_26.png](img_26.png)

步骤7：完成配置，如图所示。单击“Finish”（完成）按钮，即可完成服务器的配置。

![img_27.png](img_27.png)

步骤8：如果还有其他产品需要配置，可以选择其他产品，然后继续配置。如果没有，直接选择“Next”（下一步），直接完成整个安装和配置过程。

![img_28.png](img_28.png)

步骤9：结束安装和配置。

![img_29.png](img_29.png)

### 2.5 配置MySQL8.0 环境变量

如果不配置MySQL环境变量，就不能在命令行直接输入MySQL登录命令。下面说如何配置MySQL的环境变量：

> 步骤1：在桌面上右击【此电脑】图标，在弹出的快捷菜单中选择【属性】菜单命令。   
> 步骤2：打开【系统】窗口，单击【高级系统设置】链接。   
> 步骤3：打开【系统属性】对话框，选择【高级】选项卡，然后单击【环境变量】按钮。   
> 步骤4：打开【环境变量】对话框，在系统变量列表中选择path变量。   
> 步骤5：单击【编辑】按钮，在【编辑环境变量】对话框中，将MySQL应用程序的bin目录（C:\Program Files\MySQL\MySQL Server 8.0\bin）添加到变量值中，用分号将其与其他路径分隔开。   
> 步骤6：添加完成之后，单击【确定】按钮，这样就完成了配置path变量的操作，然后就可以直接输入MySQL命令来登录数据库了。

### 2.6 MySQL5.7 版本的安装、配置
* 安装

此版本的安装过程与上述过程除了版本号不同之外，其它环节都是相同的。所以这里省略了MySQL5.7.34版本的安装截图。

* 配置

配置环节与MySQL8.0版本确有细微不同。大部分情况下直接选择“Next”即可，不影响整理使用。这里配置MySQL5.7时，重点强调：与前面安装好的MySQL8.0不能使用相同的端口号。

### 2.7 安装失败问题

MySQL的安装和配置是一件非常简单的事，但是在操作过程中也可能出现问题，特别是初学者。

#### 问题1：无法打开MySQL8.0软件安装包或者安装过程中失败，如何解决？

在运行MySQL8.0软件安装包之前，用户需要确保系统中已经安装了.Net Framework相关软件，如果缺少此软件，将不能正常地安装MySQL8.0软件。

![img_30.png](img_30.png)

解决方案：到这个地址https://www.microsoft.com/en-us/download/details.aspx?id=42642下载Microsoft.NET Framework 4.5并安装后，再去安装MySQL。

另外，还要确保Windows Installer正常安装。windows上安装mysql8.0需要操作系统提前已安装好Microsoft Visual C++ 2015-2019。

![img_31.png](img_31.png)

![img_32.png](img_32.png)

解决方案同样是，提前到微软官网https://support.microsoft.com/en-us/topic/the-latest-supported-visual-c-downloads-2647da03-1eea-4433-9aff-95f26a218cc0， 下载相应的环境。

#### 问题2：卸载重装MySQL失败？

该问题通常是因为MySQL卸载时，没有完全清除相关信息导致的。

解决办法是，把以前的安装目录删除。如果之前安装并未单独指定过服务安装目录，则默认安装目录是“C:\Program Files\MySQL”，彻底删除该目录。同时删除MySQL的Data目录，如果之前安装并未单独指定过数据目录，则默认安装目录是“C:\ProgramData\MySQL”，该目录一般为隐藏目录。删除后，重新安装即可。

#### 问题3：如何在Windows系统删除之前的未卸载干净的MySQL服务列表？

操作方法如下，在系统“搜索框”中输入“cmd”，按“Enter”（回车）键确认，弹出命令提示符界面。然后输入“sc delete MySQL服务名”,按“Enter”（回车）键，就能彻底删除残余的MySQL服务了。

## 3. MySQL的登录

### 3.1 服务的启动与停止

MySQL安装完毕之后，需要启动服务器进程，不然客户端无法连接数据库。

在前面的配置过程中，已经将MySQL安装为Windows服务，并且勾选当Windows启动、停止时，MySQL也自动启动、停止。

#### 方式1：使用图形界面工具

* 步骤1：打开windows服务
  + 方式1：计算机（点击鼠标右键）→ 管理（点击）→ 服务和应用程序（点击）→ 服务（点击）
  + 方式2：控制面板（点击）→ 系统和安全（点击）→ 管理工具（点击）→ 服务（点击）
  + 方式3：任务栏（点击鼠标右键）→ 启动任务管理器（点击）→ 服务（点击）
  + 方式4：单击【开始】菜单，在搜索框中输入“services.msc”，按Enter键确认
* 步骤2：找到MySQL80（点击鼠标右键）→ 启动或停止（点击）  
![img_33.png](img_33.png)

#### 方式2： 使用命令行工具
```
# 启动 MySQL 服务命令：
net start MySQL服务名
# 停止 MySQL 服务命令：
net stop MySQL服务名
```

![img_34.png](img_34.png)

说明：
1. start和stop后面的服务名应与之前配置时指定的服务名一致。
2. 如果当你输入命令后，提示“拒绝服务”，请以 系统管理员身份 打开命令提示符界面重新尝试。

### 3.2 自带客户端的登录与退出

当MySQL服务启动完成后，便可以通过客户端来登录MySQL数据库。注意：确认服务是开启的。

#### 登录方式1：MySQL自带客户端

开始菜单 → 所有程序 → MySQL → MySQL 8.0 Command Line Client

![img_35.png](img_35.png)

> 说明：仅限于root用户

#### 登录方式2：windows命令行

* 格式：

```
mysql -h 主机名 -P 端口号 -u 用户名 -p密码
```

* 举例：
```
mysql -h localhost -P 3306 -u root -pabc123 # 这里设置的root用户的密码是abc123
```

![img_36.png](img_36.png)

注意：
1. -p与密码之间不能有空格，其他参数名与参数值之间可以有空格也可以没有空格。如：
```
mysql -hlocalhost -P3306 -uroot -pabc123
```

2. 密码建议在下一行输入，保证安全
```
mysql -h localhost -P 3306 -u root -p
Enter password:****
```

3. 客户端和服务器在同一台机器上，所以输入localhost或者IP地址127.0.0.1。同时，因为是连接本机： -hlocalhost就可以省略，如果端口号没有修改：-P3306也可以省略

简写成：
```
mysql -u root -p
Enter password:****
```

连接成功后，有关于MySQL Server服务版本的信息，还有第几次连接的id标识。

也可以在命令行通过以下方式获取MySQL Server服务版本的信息：
```
c:\> mysql -V
```
```
c:\> mysql --version
```

或登录后，通过以下方式查看当前版本信息：

```
mysql> select version();
```

#### 退出登录

```
exit
或
quit
```

## 4. MySQL演示使用

### 4.1 MySQL的使用演示

#### 1、查看所有的数据库

```
show databases;
```





































