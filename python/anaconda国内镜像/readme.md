
### conda按照python包时提示错误：An HTTP error occurred when trying to retrieve this URL。需要将python包的镜像更新为国内镜像。

### 具体更新方法如下：
* 1. 修改/home/.condarc文件来使用 TUNA 镜像源。如果没有/home/.condarc文件，可先执行 conda config --set show_channel_urls yes 生成该文件之后再修改。
* 2. 往/home/.condarc里添加如下信息：
     
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


### https://mirror.tuna.tsinghua.edu.cn/help/anaconda/ 
