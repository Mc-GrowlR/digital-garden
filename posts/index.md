# 介绍

**这是我的数字花园，基于开源项目MindStone构建**

MindStone demo： [MindStone](https://mindstone.tuancao.me/note/__index)

**注意：** 
1. 现在仅为测试用途，因此未将我的所有笔记开放，敬请谅解。
2. 项目demo亦为项目使用说明，介绍了项目的详细情况。

## 测试功能显示效果

**备注：**
1. 记录一下奇思妙想，看一看此项目能够表现出什么样的效果。
2. 针对一部分ob中的功能进行测试，比如双链，图片显示等

### 显示结果

1. 上传到图床中的照片在本地测试中未能正常显示，仅能显示出图片名称。
   - 因此 **建议（仅为建议）** 图片本地化，我也将改善我的库文件结构了。
2. 其余未测试。


# 项目构建教程（服务器实现）

完成（官方步骤）中的 0 1 2 步后：

在自己的云服务器上：

``` shell
screen -S garden
```

**备注：** [Linux终端命令神器--Screen命令详解。助力Linux使用和管理 - 腾讯云开发者社区-腾讯云](https://cloud.tencent.com/developer/article/1844735)

安装 `yarn` ：[Installation  Yarn](https://classic.yarnpkg.com/lang/en/docs/install/#mac-stable)，在这个网站中选择自己的 linux 发行版。

如果你是 `Ubuntu` 请用：[Ubuntu使用yarn报错：“ERROR There are no scenarios; must have at least one.”_ZTao-z的博客-CSDN博客](https://blog.csdn.net/think_A_lot/article/details/103276336)

**备注：** 我这台云服务器系统的版本是 `Ubuntu server 20.04`，直接用 apt 安装会报上方说明的错误。

登陆云服务器控制台放开 `3000` 端口。

进入项目根目录下输入：
``` shell
yarn && yarn run dev
```

在浏览器中输入你的服务器域名后面跟上 `:3000` 端口，就能看到构建完成的项目：

![[Pasted image 20230123090944.png]]

# 项目构建教程：(官方步骤)


我按照其中的步骤慢慢搭建起来我的数字花园，但是其原版的步骤过于简略，又是全英文操作，会使人感觉无从下手。

因此我记录了我搭建网站的步骤，并在其中进行了标注，希望能帮助到大家。

## 0. 前期准备

**您需准备好：**
1. github账号
2. 安装git
3. 配置好本地与github的私钥，本地git能够成功连接github
4. 其余我会安排在步骤中。

## 1. 下载仓库到本地

### 1.1 利用项目模板创建仓库

1. 登陆 github, 点击**项目地址：** [TuanManhCaodigital-garden Free Obisidian Publish alternative, for publishing your digital garden.](https://github.com/TuanManhCao/digital-garden)
   依次点击 `Use this template` -> `Create a new repository`
   ![[Pasted image 20230122214821.png]]

2. 点击之后出现如下界面，填写 `Repository name` (仓库名)
   -  **说明**： `Description` 是仓库的简明介绍，可选填。
   ![[Pasted image 20230122215110.png]]

3. 填写完 `Repository name` ，点击下方变为深绿的 `Create repository from template` 按钮。
   - **仓库创建中：**
     ![[Pasted image 20230122215432.png]] 
     - **创建成功：**
       ![[Pasted image 20230122215508.png]]
### 1.2 下载仓库
1. 点击右上角的 `code` 获取下载地址。
   - **注意**：此步骤需要配置好 `git` 私钥。
   -  ![[Pasted image 20230122215936.png]]
2. 下载项目文件
   1. 新建文件夹
   2. 自此文件夹目录下打开终端
   3. 运行 `git clone` 命令，例 ：`git clone 刚才获得的项目地址`
   4. 等待下载完成：
      ![[Pasted image 20230122220433.png]]

## 2. 选择笔记文件转移到项目中 （选作）

可以先跳过这步，等到笔记发布网站搭建起来之后再做。

**注意：**
1. 项目目录中的 `posts` 即为笔记文件夹，将想要发布的笔记放入其中。
2. `posts` 文件内的文件为项目 `demo` 文件可以删除，但 **必须保留**`index.md` 文件。
3. `./public/images` 目录存放笔记引用的图片。
4. 此项目实现的 ob 功能目前我尚未摸透，因此在发布笔记时，必须采用保守策略。
   - 可选几章笔记作为测试发布。
   - 善用 `git` ，此项目不会加载 `obsidian` 插件。

## 3. 利用 `Netlify` 发布自己的数字花园

### 3.1 注册账号

1. 点击网站连接：[Site Unreachable](https://www.netlify.com/blog/2020/11/30/how-to-deploy-next.js-sites-to-netlify/)，跳转到的界面为 demo 教程中的步骤，此时我们略过。
2. 点击右上角的 `Sign up`
   - ![[Pasted image 20230122222055.png]]
3. 选择 `github` 登陆
   - ![[Pasted image 20230122222134.png]]
4. 会有一个界面让你填写使用目的，填写个人就成。此处我没有截下来，抱歉。

### 3.2 导入站点

1. 选择导入来源
   - ![[Pasted image 20230122223007.png]]
2. 选择 `github`
   - ![[Pasted image 20230122223026.png]]
3. 选择仓库
   - 在这会看到我们一开始创建的仓库，点击。
   - ![[Pasted image 20230122223148.png]]
4. 创建站点。
   - 到第三步，拉到最下面点击 `Deploy site`。
   - ![[Pasted image 20230122223412.png]]
5. 站点导入成功
    - ![[Pasted image 20230122223453.png]]
### 3.3 设置自己的站点
共分三步
#### 3.3.1 构建站点
**点击图中框选的区域**，即可开始站点的构建，等到 `log` 显示 `100% complete` 即创建成功。
![[Pasted image 20230122225149.png]]

#### 3.3.2 设置站点域名

此处以阿里云域名为例。

1. 复制站点地址
   - 站点地址如图所示，但要注意复制时，只复制 `//` 之后的内容。
    -  ![[Pasted image 20230122224900.png]]
2. 登陆阿里云控制台，进入 `云解析DNS`。
3. 点击自己购买的域名添加记录：
   - 一次填写相关字段：
   - 记录值即为方才复制的站点地址。
   - ![[Pasted image 20230122224757.png]]
4. 点击第二步
    ![[Pasted image 20230122225212.png]]
5. 输入域名
   ![[Pasted image 20230122225303.png]]
6. 允许
   - 说明：这是说明我的域名已被占用，选择添加子域名并托管给这个网站。
   ![[Pasted image 20230122225438.png]]
7. 创建完成
   ![[Pasted image 20230122225614.png]]
#### 3.3.3 设置站点证书
在第二步完成的页面滚动到最下方。

![[Pasted image 20230122225718.png]]
点击框选内容。
成功：
![[Pasted image 20230122225758.png]]
## 4. 大工告成。

下面浏览你的数字花园吧！

实例：此为本文生成的 demo 演示。

![[Pasted image 20230122230559.png]]