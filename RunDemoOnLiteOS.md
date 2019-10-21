# LiteOS运行Demo教程
----

## 一、运行裸机工程自带demo
LiteOS启动时默认运行裸机工程下的oc_oceanlink_demo，该例程会去连接云端，但是由于"GD32VF103V_EVAL"开发板无通讯组件（初步怀疑），所以调试串口会输出"config err"（参见[LiteOS移植教程](https://github.com/VincentLee-EN/Wisinfo-Share/blob/master/LiteOSPorting2GD32VF103V.md)的最后一张[图](https://github.com/VincentLee-EN/img/blob/master/output_1.png)）。

![avator](https://github.com/VincentLee-EN/img/blob/master/10_21/default_demo.png) 

读者可能会想，既然这样，那禁用oc_oceanlink_demo，换个不连云的demo跑是不是就不报错了呢？别急，让我们一起动手看看。
官方一共提供了3个demo，下面我以hello_world_demo为例介绍如何更换demo并在LiteOS上运行。

1. 进入config.mk，修改LiteOS启动时默认运行的demo的名称

    ![avator](https://github.com/VincentLee-EN/img/blob/master/10_21/config_mk.png)
    
    ![avator](https://github.com/VincentLee-EN/img/blob/master/10_21/change_default_demo.png)

2. 进入main.c中添加头文件

    ![avator](https://github.com/VincentLee-EN/img/blob/master/10_21/main_c.png)

    ![avator](https://github.com/VincentLee-EN/img/blob/master/10_21/headfile.png)

    重新编译（make GD）工程，正常情况下会报一个错，我忘了在哪个文件下第几行报的错了，错误在于该报错文件没有#define hello_world_demo，模仿oc_oceanlink_demo的代码添加以下就好了（两行代码还是三行代码来着？？）。请读者根据报错信息自行修复错误~~

3. 重新编译并把生成的elf文件下载到开发板上，会发现原先的config err不见了！
    ![avator](https://github.com/VincentLee-EN/img/blob/master/10_21/hello_result.png)

## 二、运行github的demo
  1. 下载kernel demo到Demos目录下（解压后改名为kernel_demo,文件夹下应该有api和include两个子文件夹），并新建kernel_demo.mk
  ![avator](https://github.com/VincentLee-EN/img/blob/master/10_21/kernel_demo.png)
      > 链接：https://pan.baidu.com/s/1hAQXOp2abFMYdB_1-tQ6kg&shfl=sharepset \
      > 提取码：6v15 
  2. 修改kernel_demo.mk
      添加如下代码到文件中保存关闭：
      ```C
        kernel_demo_src = ${wildcard $(TOP_DIR)/targets/GD32VF103V_EVAL/Demos/kernel_demo/api/*.c}
        kernel_demo_inc = -I $(TOP_DIR)/targets/GD32VF103V_EVAL/Demos/kernel_demo/include

        C_SOURCES += $(kernel_demo_src)
        C_INCLUDES += $(kernel_demo_inc)
      ```

      ![avator](https://github.com/VincentLee-EN/img/blob/master/10_21/kernel_demo_mk.png)

    3. 在main.c中包含kernel_demo->include下相应的头文件，读者便可以参见[LiteOS开发指南](https://github.com/LiteOS/LiteOS/blob/master/doc/Huawei_LiteOS_Developer_Guide_zh.md)中给的编程示例进行学习。

## 三、结束语
如果读者有兴趣的话，还可以参见[LiteOS内核使用指南](https://liteos.github.io/tutorials/kernel/)去做实验玩转LiteOS内核，甚至自己设计实验！
