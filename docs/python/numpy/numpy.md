#### zeros_like()

> 用于创建一个与已知变量类型相同，形状相同的并且指定元素类型的新变量，且所有元素值初始化为0
>
> 如下即创建一个与t变量类型相同，形状相同的并且所有元素全是浮点数的数值全为0的新变量f2

```python
f2 = np.zeros_like(t, dtype=float)
```

#### 布尔索引在分段函数中的应用

> 常用于表示分段函数，将特定的变量对应的范围对应于特定的函数，例：

```python
f2[t <= t_breakpoint] = c * t[t <= t_breakpoint] + d
```

#### sum()

> 用于计算输入数组中所有元素的总和，如下是在求残差平方和的应用

```python
error = np.sum((f3_pred - flow) ** 2)
```

#### abs()

> 用于计算传入参数的绝对值

#### sqrt() mean()

> Sqrt()函数计算输入值的平方根
>
> Mean()函数计算输入数组中所有元素的平均值
>
> 以上两种函数常用于求解均方根误差

```python
rmse = np.sqrt(np.mean((f3_pred - flow) ** 2))
```

