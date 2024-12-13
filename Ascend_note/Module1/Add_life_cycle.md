# 一、Add算子前世今生

## 1.1 AI core架构抽象回顾

## 1.2 Ascend C的编程对象

### 存储
- 外部存储
```cpp
template <typename T> class GlobalTensor {
    void SetGlobalBuffer(__gm__ T* buffer, uint32_t buffer_size);
}

```
![alt text](image.png)

- 内部存储
![alt text](image-1.png)

### 逻辑位置 数据依赖
会具体说明

## 1.3 Vector算子开发流程——以Add算子为例
### 开发流程
![alt text](image-2.png)

- side note: `half` 半精度浮点
### 算子分析
![alt text](image-3.png)

### 核函数定义（kernel侧的实现）
![alt text](image-4.png)

### 编程范式
![alt text](image-5.png)
:yum: 有大框架了

#### SPMD
SIMD(Single-Instruction Multiple-Data)是核内的，SPMD(Single-Program Multiple-Data)是核间的

![alt text](image-6.png)

注意idx怎么获取的
#### 流水任务
![alt text](image-7.png)

和cpu优化一个道理
![alt text](image-8.png)
#### 矢量编程流水任务设计
有汇编那味了:yum:

![alt text](image-9.png)

伪代码实现
![alt text](image-10.png)

代码实现
- interface: （local tensor不在这里）
![alt text](image-11.png)

- **Init()**
![alt text](image-12.png)
- **Process()**
![alt text](image-13.png)


- DoubleBuffer()机制
![alt text](image-14.png)
参考代码实现里 `BUFFER_NUM` 的定义

- Conclusion
![alt text](image-15.png)


## 1.4 运行验证

### tree of content
![alt text](image-16.png)

算子调用示例sample
![alt text](image-17.png)
直接调用——kernel直调
![alt text](image-18.png)


side note: *Neo指代新手*
