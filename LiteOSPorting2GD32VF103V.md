# LiteOS移植教程
----

## 一、 工具准备

- Win10电脑 

- GD32VF103V开发板

- GD32VF103V的LiteOS裸机工程
  - 下载方式一
    安装 Git for Windows，执行以下命令：
    > git clone -b iot_link https://github.com/LiteOS/LiteOS_Lab
  - 下载方式二
    百度云：
    > 地址：https://pan.baidu.com/s/19pDRt-gwtITC92bNaM5qTw
    > 提取码： pzq0

- RISCV-GCC工具链
  下载安装教程：
  > https://blog.csdn.net/qq_35553265/article/details/91324754

- windows10配置make命令
  教程
  > https://blog.csdn.net/weixin_39506322/article/details/91978490

  注：安装MinGW的时候选择Basic setup下选择mingw32-base包就可以了。
  

## 二、 移植

### 1. 编译裸机工程
到GD32VF103V的LiteOS裸机工程下的GCC目录下，执行以下命令编译工程：
> make GD

- 采用 git clone方法下载的裸机工程，目录结构如下：
![avator](https://github.com/VincentLee-EN/img/blob/master/make.png)

- 采用百度云下载的裸机工程，目录如下
![avator](https://github.com/VincentLee-EN/img/blob/master/make2.png)

如果能看到下图所示结果，说明编译成功。
![avator](https://github.com/VincentLee-EN/img/blob/master/make_result.png)

### 2. 准备并验证移植环境

按照[Nuclei Studio IDE快速上手手册](https://riscv-mcu.github.io/Webpages/IDE_QuickStart/#8b-3)完成1-7步。

### 3. 将编译文件下载到裸机工程中
1. 右键上一步创建的Running_LED->Run as->Run Configurations

![avator](https://github.com/VincentLee-EN/img/blob/master/run_config.png)

2. 选择前面编译好的elf文件，禁用auto build，应用后运行
![avator](https://github.com/VincentLee-EN/img/blob/master/download2GD.png)

### 4. 验证
1. 开发板四盏灯亮
![avator](https://github.com/VincentLee-EN/img/blob/master/light_on.jpg)

2. 串口输出信息如下
![avator](https://github.com/VincentLee-EN/img/blob/master/output_1.png)

读者可以试试触屏点灭LCD屏上的灯，串口正常情况下会输出对应信息。

# 三、结束
If you follow the tutorial to this step，congratulations! Nice work!