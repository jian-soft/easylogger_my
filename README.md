## 移植自easylogger项目
源项目地址：https://github.com/armink/EasyLogger

所做的改动：
1. 基于原项目Linux demo(所以本项目只适用于Linux系统)
2. 将所有.c文件（包括linux demo的port.c文件）放到easylogger/src目录
3. 将所有.h文件（包括elog.h elog_cfg.h）放到easylogger/inc目录
4. 新的demo位于src/main.c

## build&run
Makefile是写好的，在Linux下直接敲make编译即可
```
make
./bin/easyloggerdemo
```

## 使用指南
将easylogger拷到自己项目后，还要修改三个部分。
1. elog_file_cfg.h： 修改ELOG_FILE_NAME为项目需要保存log的地址
2. elog_cfg.h： 定义LOG_TAG为自己的TAG，比如#define LOG_TAG "myprogram"
3. main.c中定义并调用easylogger_init
```
#define MY_ELOG_FMT (ELOG_FMT_LVL|ELOG_FMT_TAG|ELOG_FMT_TIME|ELOG_FMT_FUNC|ELOG_FMT_LINE)
void easylogger_init(void)
{
    /* initialize EasyLogger */
    elog_init();
    /* set EasyLogger log format */
    elog_set_fmt(ELOG_LVL_ASSERT, MY_ELOG_FMT);
    elog_set_fmt(ELOG_LVL_ERROR, MY_ELOG_FMT);
    elog_set_fmt(ELOG_LVL_WARN, MY_ELOG_FMT);
    elog_set_fmt(ELOG_LVL_INFO, MY_ELOG_FMT);
    elog_set_fmt(ELOG_LVL_DEBUG, MY_ELOG_FMT);
    elog_set_fmt(ELOG_LVL_VERBOSE, MY_ELOG_FMT);
    elog_start();
}
```
4. 在使用easylogger的地方，#include "elog.h"，然后使用log_i() log_w() log_e()这些接口
