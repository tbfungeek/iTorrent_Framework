1. 下载iTorrent_Framework 代码 https://github.com/XITRIX/iTorrent_Framework
2. 删除submodules下的libTorrent 执行 git clone --recurse-submodules https://github.com/arvidn/libtorrent.git 重新下载
否则会出现配置头文件找不到的问题
3. brew install boost-build boost openssl@1.1  安装必要的工具
4. 下载boost 这里用的是1_81_0 源代码 https://www.boost.org/users/download/#live 解压到/usr/local/boost_1_81_0
5. ./bootstrap.sh  ./b2 headers ./b2
日志头文件目录 /usr/local/boost_1_81_0, 
lib目录/usr/local/boost_1_81_0/stage/lib
https://futucocoa.github.io/2017-01-06-macOSBoostInstallGuide/

Bootstrapping is done. To build, run:
./b2
To generate header files, run:
./b2 headers
The configuration generated uses clang to build by default. If that is
unintended either use the --with-toolset option or adjust configuration, by
editing 'project-config.jam'.
Further information:
- Command line help:
    ./b2 --help
- Getting started guide:
    http://www.boost.org/more/getting_started/unix-variants.html
- B2 documentation:
    http://www.boost.org/build

The Boost C++ Libraries were successfully built!
The following directory should be added to compiler include paths:
    /usr/local/boost_1_81_0
The following directory should be added to linker library paths:
    /usr/local/boost_1_81_0/stage/lib

6. 修改环境变量~/.zshrc 中的 export BOOST_ROOT="/usr/local/boost_1_81_0"
    source ~/.zshrc
    echo $BOOST_ROOT 查看是否添加成功

7. 打开ITorrentFramework.xcodeproj 添加签名

8. ./make.sh 执行编译
9. 集成到项目中  https://blog.csdn.net/weixin_42232156/article/details/122011431
   在 Build Phases 里添加 Copy Files 
   接着把 Destination 改成 Frameworks, 并将拖入的 framework 包加入到 Name 目录下: 选择加号 在弹窗左上角选择 编译产物

参考文档

https://www.boost.org/users/download/#live
https://github.com/XITRIX/iTorrent_Framework
https://github.com/arvidn/libtorrent
https://github.com/arvidn/libtorrent/blob/RC_2_0/docs/building.rst#downloading-and-building