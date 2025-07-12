#### set_style

> 设置图表的显示背景为白色网格，括号内的背景样式可以替代为
>
> **`"darkgrid"`**: 默认风格，深灰色背景，白色网格线。
>
> **`"white"`**: 白色背景，没有网格线。
>
> **`"dark"`**: 深灰色背景，没有网格线。
>
> **`"ticks"`**: 类似 `"white"` 风格，但会在轴上添加刻度线。

```python
sns.set_style("whitegrid")
```

#### set_palette

> 设置图表的颜色方案，husl是一种对人类感知更均匀的方式来表示颜色。

```python
sns.set_palette("husl")
```

#### lineplot()

> 其中包含多个参数，参数一**`x=t`**: 表示X轴的数据，参数二**`y=flow`**:表示Y轴的数据，参数三**`marker='o'`**: 表示数据点的标记样式，参数四**`label='主路3实际车流量'`**: 为这条折线图设置**图例标签**。参数五**`linewidth=2`**: 设置折线的**宽度**。参数六**`linestyle='--'`**: 设置折线的**样式**。

```python
sns.lineplot(x=t, y=flow, marker='o', label='主路3实际车流量', linewidth=2)
```
