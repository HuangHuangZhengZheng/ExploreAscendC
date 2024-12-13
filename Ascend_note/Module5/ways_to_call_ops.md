# 算子的调用方式

## 5.1 概述


## 5.2 kernel直调
调用在kernel侧算子工程 `main.cpp` 中

- cpu算子调用方式
![alt text](image.png)    
  - blkdim: aicore的数量
- npu算子调用方式
  - ![alt text](image-1.png)

kernel side同样可以传入tiling但是不重要？因为只关注快速验证
```shell
bash run.sh -r ... -v ...
```
## 5.3 Ascend CL调用算子
![alt text](image-2.png)
计算图更加重视shape

### 单算子API调用
![alt text](image-3.png)
两段式调用，先计算workspace，再调用算子

关键实现
![alt text](image-4.png)

cmakelist.txt
![alt text](image-5.png)



### 单算子模型执行
`AclofflineModel` 文件夹下有源码

转换为.om文件
![alt text](image-6.png)

代码编写关键信息
![alt text](image-7.png)

## 5.4 PyTorch调用算子
真要写就是写 `op_plugin` 里面的东西

![alt text](image-8.png)
![alt text](image-9.png)
![alt text](image-10.png)

![alt text](image-11.png)
