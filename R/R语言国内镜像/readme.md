### 如果无法安装R包或者R包下载速度很慢，需更新R包的镜像为国内镜像
### 具体更新方法如下：

#### 长期使用
  CRAN (The Comprehensive R Archive Network) 镜像源配置文件之一是 .Rprofile (linux 下位于 ~/.Rprofile )。
  在文末添加如下语句：
        options("repos" = c(CRAN="https://mirrors.tuna.tsinghua.edu.cn/CRAN/"))
  打开 R 即可使用该 CRAN 镜像源安装 R 软件包。

    
