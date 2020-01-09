晟东评估板v1.0例程调试教程
----

# 1. 工具准备
  和在GD32VF103V上的调试环境移植

# 2. 配置修改

## 2.1 系统时钟频率
  GD32VF103V默认使用8M的外部时钟频率，晟东评估板的外部时钟频率设计为25M.

### 2.1.1 配置预处理器
右键项目 -> Properties -> C/C++ Build -> Settings -> GNU RISC-V Cross C Compiler，在Preprocessor中添加两项
- USE_STDPERIPH_DRIVER
- GD32VF103V_EVAL

   ![avator](https://github.com/VincentLee-EN/img/blob/master/RunDemoOnEval_v1.0/prepeocessor.png)