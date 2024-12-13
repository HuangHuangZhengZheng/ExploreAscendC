# 二、Host侧实现


## 2.1 Host侧实现概述
![alt text](image.png)

in `op_host` directory...
Host的任务主要是
![alt text](image-1.png)


## 2.2 Tiling下发
即所谓切片:yum:
![alt text](image-2.png)

### 结构体
![alt text](image-3.png)
### 两侧Tiling实现
Host打包信息
![alt text](image-4.png)

Device侧解包
![alt text](image-5.png)
### 静态动态shape
- 静态shape：在编译时确定，在运行时不可变，注意 `total_len`, `block_len`, `tile_num` 等参数
![alt text](image-6.png)
- 动态shape：在运行时确定，在编译时不可变
![alt text](image-7.png)

- 对比：
- ![alt text](image-8.png)
- ![alt text](image-9.png)
- ![alt text](image-10.png)
- ![alt text](image-11.png)
静态常量->动态成员变量

## 2.3 Shape推导
![alt text](image-12.png)

![alt text](image-13.png)
这就不得不提到CMU 10-414传奇推导法了:yum:

## 2.4 原型注册
![alt text](image-14.png)
register basic info of op :thinking:

side note: `xxxx_out` 有可能有许多的结果和帮助

