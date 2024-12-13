# API 通用解读
来了，避免重复造轮子
## 4.1 Ascend C编程API概述
![alt text](image.png)
## 4.2 基础API
![alt text](image-1.png)


### 计算库API
#### 整个Tensor的计算
四则运算、按位与或，等不等

#### 前n个元素的计算
```cpp
Add(dst, src1, src2, n)
```

#### 高维度切分计算
通用参数
![alt text](image-2.png)

- repeat times:不要超过255
![alt text](image-3.png)

在这里1 block 对应 32 Byte

- Repeat stride:地址的步长，单位block
![alt text](image-4.png)

- Block size:每个block的大小
![alt text](image-5.png)


- mask
  - 连续模式
![alt text](image-6.png)

传入{1,1,1,8,8,8}指的是上面提到的参数binaryRepeatParams
  - 逐bit模式 -> mask比特作为索引去访问一次256Byte的读写单元
![alt text](image-7.png)

### 数据搬运API
![alt text](image-8.png)

对于 `DataCopyParams` 来说

![alt text](image-9.png)

### 内存管理API

![alt text](image-10.png)

避免直接使用cpp的new/delete
### 任务同步API
![alt text](image-11.png)

## 4.3 高阶API
![alt text](image-12.png)

***Sinh?***
![alt text](image-13.png)

![alt text](image-14.png)


[社区链接](https://www.hiascend.com/document/detail/zh/CANNCommunityEdition/800alpha001/devguide/opdevg/ascendcopdevg/atlas_ascendc_10_0028.html)


side note: 双目/单目算子
注意使用基础api！！！
