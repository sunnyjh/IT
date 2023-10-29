
### conda按照python包时提示错误：An HTTP error occurred when trying to retrieve this URL。需要将python包的镜像更新为国内镜像。

### 具体更新方法如下：
* 1.修改/home/.condarc文件来使用 TUNA 镜像源。如果没有/home/.condarc文件，可先执行 conda config --set show_channel_urls yes 生成该文件之后再修改。
* 2.往/home/.condarc里添加如下信息：
     
       channels:
         - defaults
       show_channel_urls: true
       default_channels:
         - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
         - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
         - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
       custom_channels:
         conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
         msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
         bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
         menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
         pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
         pytorch-lts: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
         simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
         deepmodeling: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/

* 3.运行 conda clean -i 清除索引缓存，保证用的是镜像站提供的索引。
* 4.运行 conda create -n myenv numpy 测试一下
* 5.添加conda额外库:（额外库都是第三方提供的，非anaconda官方的，建议没有特殊需要直接使用稳定的官方库。）

       #pytorch
       conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
       #安装时PyTorch，官网给的安装命令需要去掉最后的-c pytorch，才能使用清华源
       #conda-forge
       conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
       #msys2
       conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
       #bioconda
       conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/
       #menpo
       conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/menpo/
       #设置搜索时显示通道地址
       conda config --set show_channel_urls yes

* 6.中科大anaconda镜像

       conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/main/
       conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
       conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/
       conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/msys2/
       conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/bioconda/
       conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/menpo/
       conda config --set show_channel_urls yes

* 7.镜像回退
   国内源也是会挂的，之前清华就挂过，后来又活了，腾讯挂了就直接死了，一旦出现一直连接失败问题就可以换回来了

       换回默认源：conda config --remove-key channels

### 补充：Anaconda更新
  最近发现conda update conda很多包的版本会升级，出现anaconda=custom的版本号，但是conda update anaconda后很多包的版本又被降级了！我的理解是conda update conda升级的是conda下最新的版本，并使得anaconda成为了用户自己的定制版本，不在是anaconda官方的规定版本了。而conda update anaconda是将所有包升级到ananconda官方支持测试好的最稳定的新版本，所以会出现降级现象。

     #conda
     conda update conda
     #anaconda(升级anaconda前需要先升级conda)
     conda update anaconda
     #anaconda-navigator
     conda update anaconda-navigator
     #spyder
     conda update spyder
     #所有包
     conda update --all
     #尽量避免使用conda update --all命令，可能会出现部分包降级的问题


[参考链接](https://mirror.tuna.tsinghua.edu.cn/help/anaconda/) 
[anaconda更换清华源](https://blog.csdn.net/jasneik/article/details/114227716) 
