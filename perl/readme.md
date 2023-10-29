### 国内镜像安装perl模块
  CPAN (The Comprehensive Perl Archive Network) 镜像源的配置文件为 MyConfig.pm（一般位于 ~/.cpan/CPAN/MyConfig.pm），可使用包管理脚本 cpan 进行修改。
### 具体安装方法如下：

#### 1.初次使用
  如果 MyConfig.pm 配置文件不存在，在命令行中执行：

          # 自动生成 MyConfig.pm
          ## 对于 Perl 5.36 （或 CPAN 2.29）及以上，使用如下命令
          PERL_MM_USE_DEFAULT=1 perl -MCPAN -e 'CPAN::HandleConfig->edit("pushy_https", 0); CPAN::HandleConfig->edit("urllist", "unshift", "https://mirrors.tuna.tsinghua.edu.cn/CPAN/"); mkmyconfig'
          ## 对于较久版本，使用如下命令
          PERL_MM_USE_DEFAULT=1 perl -MCPAN -e 'CPAN::HandleConfig->edit("urllist", "unshift", "https://mirrors.tuna.tsinghua.edu.cn/CPAN/"); mkmyconfig'

         # 或不使用默认配置，手动确认各个配置选项
         perl -MCPAN -e 'mkmyconfig'

#### 2.已有配置
  在 CPAN Shell 中手动设置镜像
  在命令行中执行 cpan 进入 cpan shell

    cpan shell -- CPAN exploration and modules installation
    Enter 'h' for help.

    # 列出当前的镜像设置
    cpan[1]> o conf urllist

    # 将本站镜像加入镜像列表首位
    # 注：若已在列表中则可跳过本步直接退出，修改列表不会执行自动去重
    cpan[2]> o conf urllist unshift https://mirrors.tuna.tsinghua.edu.cn/CPAN/

    # 或将本站镜像加入镜像列表末尾
    # 注：本命令和上面的命令执行一个即可，修改列表不会执行自动去重
    cpan[3]> o conf urllist push https://mirrors.tuna.tsinghua.edu.cn/CPAN/

    # 或清空镜像列表，仅保留本站
    cpan[4]> o conf urllist https://mirrors.tuna.tsinghua.edu.cn/CPAN/

    # Perl 5.36 及以上用户需要关闭 pushy_https 以使用镜像站
    cpan[5]> o conf pushy_https 0

    # 保存修改后的配置至 MyConfig.pm
    cpan[6]> o conf commit

    # 退出 cpan shell
    cpan[7]> quit
* 1.啊
* 2.啊
* 3.啊


  


+ [CPAN](https://mirror.tuna.tsinghua.edu.cn/help/CPAN/)
