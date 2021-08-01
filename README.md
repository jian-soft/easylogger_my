## 移植自easylogger项目
源项目地址：https://github.com/armink/EasyLogger

所做的改动：
1）基于原项目Linux demo
2）将所有.c文件（包括linux demo的port.c文件）放到easylogger/src目录
3）将所有.h文件（包括elog.h elog_cfg.h）放到easylogger/inc目录
4）新的demo位于src/main.c

## build&run
Makefile是写好的，在Linux下直接敲make编译即可
```
make
./bin/easyloggerdemo
```

