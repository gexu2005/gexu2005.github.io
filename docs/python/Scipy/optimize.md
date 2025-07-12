#### minimize()

> `minimize()` 是 SciPy 库中 `scipy.optimize` 模块提供的一个**高阶函数**。它的主要任务是**寻找给定函数（称为“目标函数”或“成本函数”）的最小值**。
>
> 函数的第一个参数是你要调用的函数的函数名，该函数被称为目标优化函数，该函数要求有返回值，**minimize()函数传入不同的参数，求的返回值最小的结果，并将参数以 `OptimizeResult` 对象的形式返回**，第二个参数是要调用的函数所要传入的参数，即要求解的未知变量的初始值，（**一个好的初始猜测可以帮助算法更快地找到最优解。**）第三个参数是method参数，**`method`** 参数指定了 `minimize()` 函数内部将采用哪种**优化算法**来寻找最小值，其中`method='Nelder-Mead'` (单纯形法)适用于**目标函数不可导或梯度不连续的场景**（例如，包含 `if` 语句、`np.abs()` 等）。
>
> **`result.x`**: **最重要的属性！** 这就是优化算法找到的**最佳参数值**（一个 NumPy 数组）。这些参数是使 `objective` 函数最小化的输入。
>
> `result.fun`: 目标函数在 `result.x` 处的最小值。
>
> `result.nit`: 迭代次数。
>
> `result.success`: 一个布尔值，指示优化是否成功收敛。
>
> `result.message`: 描述优化结果的文本信息。

```python
result = minimize(objective, initial_params, method='Nelder-Mead')
```

