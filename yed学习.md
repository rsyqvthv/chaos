# Layout Algorithms 布局算法
https://yed.yworks.com/support/manual/layout.html

## One-Click Layout
一键式布局

One-Click layout is an algorithm that automatically chooses and configures a layout style depending on the structure of the diagram to be arranged.

一键布局是一种根据要布置的图的结构自动选择和配置布局样式的算法。

## Hierarchical Layout 分层布局

分层是一种布局样式，
描绘有向图的优先关系。它是
非常适合许多应用领域，尤其是对于

–工作流程
- 软件工程
- 客户关系管理
- 配置管理
- 流程建模
- 数据库建模
- 生物信息学

使用分层布局样式突出指示方向的主要方向或流程图形。节点的循环依赖关系将自动检测并解决。节点将按层次排列层。
另外, 以这种方式选择每一层内节点的顺序线（或边）交叉的数量很少。


## Organic Layout 有机布局

“有机”是用于无向图的多功能布局样式。它可以清晰地表示复杂的网络特别适合诸如以下的应用领域

- 生物信息学
- 企业网络
- 知识表示
- 系统管理
- WWW可视化

有机布局器基于力导向布局范例。布置图时，节点被认为是具有相互排斥力的物理对象，例如质子或电子。节点之间的连接也如下物理类比，被认为是连接到成对节点的金属弹簧。
这些春天在端点之间产生排斥力或吸引力如果它们太短或太长。
布局器模拟这些物理力并重新排列节点的位置，使节点和边缘发出的力之和达到（局部）最低。

生成的布局通常会暴露出固有的对称和聚类图的结构，节点的均衡分布，和很少的边缘交叉。

布局器非常适合高度可视化连接的骨干区域，带有连接的外围环或星形结构。网络中这些结构上不同的区域通过查看由这个布局器。

## Orthogonal Layout (Classic) 正交布局(经典)

正交是用于无向图的多功能布局器。
它可以清晰地表示复杂的网络特别适合诸如以下的应用领域

- 软件工程
- 数据库架构
- 系统管理
- 知识表示

布局器非常适合中型稀疏图。它生成紧凑的图纸，没有节点重叠，很少的交叉和几弯。所有边缘将以正交样式进行布线，即仅使用垂直和水平线段。

## Orthogonal Layout (UML Style) 正交布局(UML 风格)

这种布局算法构成了正交布局方法。定向变体区分“定向”和“非定向”边缘，并尝试以这样一种方式路由边缘，即所有“定向”边缘都指向主布局方向。此外，还支持自动边缘分组。

定向正交布局非常适合安排UML类图。

## Orthogonal Layout (Compact) 正交布局(紧凑)

此布局算法是“正交”的专用变体布局方法。
它使用分治法来实现紧凑的正交布局尝试遵守指定的宽高比。
基本思想是计算可以布局的图分区根据优选的纵横比。

## Circular Layout 圆形布局
## Tree Layout 树木设计图
## Balloon Layout 气球布局
## Radial Layout 径向布局
## Selection (Partial Layout) 选择(部分布局)
## Series-Parallel Layout 串并联布局
## Component Arrangement 组件安排
## Random Layout 随机布局
## Hierarchic Swimlane Layout 层次式泳道布局
## Organic Swimlane Layout 有机泳道布局
## Tabular Layout 表格式布局
## Flowchart Layout 流程图布局
## BPMN Layout
## Family Tree Layout 家谱图
## Tree Map Layout 树木图版面设计
## Polyline Edge Router
## Orthogonal Edge Router 正交边缘路由器
## Orthogonal Channel Edge Router 正交通道边缘路由器
## Orthogonal Bus-style Edge Router 正交总线式边缘路由器
## Organic Edge Router 有机边缘路由器
## Straight Line Router 直线路由器
## Label Placement 标签放置


# tools

“工具”菜单提供了大量有用的工具，可用于
- 获取关于当前编辑文档的信息
- 在视觉上和结构上修改文档
- 从头创建全新的图形文档

Creating Graphs 创建图表

- Grid 网格
- Tree 树
- Planar 平面
- Random 随机

Constraints 约束
此工具可用于定义边缘端点的约束条件。

- Port Constraints 港口限制
允许您将边缘的末端固定在相应节点的特定边上，甚至固定到相对于节点中心的显式坐标。

- Edge Grouping 边缘分组
定义一组边缘端点，它们被捆绑在各自节点的同一坐标上开始。


Select Elements 选择元素
这个工具可以用来选择节点，边缘和弯曲指定变压器。 将显示“查找对话框”中描述的对话框。 最后，所有匹配结果都将被选中。

Analyze Graph 分析图表
该工具对图形结构进行了各种测试和计算。 结果将显示在一个信息窗口中。

Centrality Measures 中心度量
提供了确定图结构中节点相对重要性的各种方法。结果可以用几种方式显示。

Colorize Graph 彩色图形
当复杂的图形结构必须可视化时，这个工具非常有用。它可以自动为节点分配不同的随机颜色。 外向边缘将被分配与它们的源节点相同的颜色。 通过这种方法，可以很容易地找到给定边的源节点。
*注意需要选择一个node作为起点*

Reverse Selected Edges 反向选择边缘
这个工具反转所有选择的边缘，即这些边缘的源节点和目标节点将被交换。

Layout Parallel Edges 平行边布局
此工具将具有相同终端节点的边重新路由。 这些边缘将被布置以便它们的边缘路径并行运行。

Snap To Grid 捕捉到网格
这个工具能够捕捉节点并弯曲到网格。网格可以在首选项对话框中指定。


Fit Node to Label 调整节点到标签
调整所选节点的大小，以便节点标签完全包含在节点的边界中。


Fit Label to Node 将标签适配到 Node
修改每个选定节点的标签，使其适合其节点的边界框。 标签的大小调整可以通过改变字体大小和 / 或在适当的位置引入换行符来实现。

Anonymize 匿名化
通过删除图像、图形和标签文本创建当前图表的匿名副本。