# PowerBI

标签（空格分隔）： 数据分析 

---

## 数据集
Power BI 用来创建其可视化效果的数据集合。
可以是许多不同源的组合。

## 报表
报表是一起显示在一个或多个页面的可视化效果集合。
报表是彼此相关的项的集合

## 仪表板
仪表板必须位于单个页面，通常称为画布

## 磁贴
磁贴是在报表或仪表板中找到的单个可视化效果。 它是包含每个单个视觉对象的矩形框

## 关系视图
在关系视图中，你可以看到表示各个表的数据块，它们之间的表列和表行就是表示的关系。

添加和删除关系非常简单。 若要删除关系，右键单击它并选择删除。 若要创建关系，拖放想要在表格之间创建链接的字段。![此处输入图片的描述][1]


 

## 计算表
计算表是 DAX 的一个功能，可用于表达一众新增建模功能。 例如，如果你希望进行不同类型的合并联接或以函数公式的结果为基础创建随即变化的新表，使用计算表可以达到此目的。

要创建计算表，请转到 Power BI Desktop 中的数据视图（前台第二个）

## 切片器
如果想在一个表中实时切换显示不同的字段，可以添加切片器到以表中
![此处输入图片的描述][2]

只需要把用来筛选的字段拉到仪表盘内（之前做好的图表不用动，然后点击切片工具就可以筛选了），类似tableau中的标记功能。

## 显示
值属性的上下顺序会影响其对应的列在图表中的前后顺序

## 散点图
如果想要比较两个不同的度量值，例如单位销售额和收入，常见的可视化效果就是使用散点图。
除了要将要比较的两个数据拖进x和y轴，还需要添加‘详细信息’才行，不然就只是个小点。
![此处输入图片的描述][3]
即：如果你仅在散点图中看到一个气泡，是因为 Power BI 正在聚合数据。这是默认行为。 在可视化效果窗格中，向*详细信息*存储桶添加类别以获取更多气泡。

## 瀑布图
瀑布图仅有两个存储桶选项：*类别*和 *Y 轴*。 将基于时间的字段（例如*年份*）拖动到*类别*存储桶，并将你想跟踪的值拖动到 *Y 轴*存储桶。
![此处输入图片的描述][4]
默认情况下，值有所增加的时间段会显示为绿色，而值有所减少的时间段会显示为红色。

漏斗图通常用于显示随特定过程的更改，例如销售管道或网站保留工作。

##可视化效果之间的交互
当同一报表页上具有多个可视化效果时，通过单击或使用切片器选择特定片段将影响该页上的所有视觉对象。 但是，在某些情况下，你可能只想切分特定的视觉对象。若要从交互作用中排除视觉对象，请单击右上角*筛选器*图标旁边的*无*符号。
![此处输入图片的描述][5]
注：在互相交互的视觉对象周围绘制透明形状是一个有用的设计技巧，这样就可以明确告知用户它们具有交互关系。

## 显示不包含数据的类别
默认情况下，列标题仅显示在包含数据的报表中。 例如，如果你按国家/地区显示收入，并且在挪威没有销售额，则挪威不会显示在可视化效果中的任何位置。

若要显示空的类别，请单击可视化效果窗格中你想要更改的字段中的下拉箭头，然后选择显示无数据项。

# DAX
DAX 代表数据分析表达式，是在整个 Power BI 中使用（它也由 Power BI 在后台使用）的公式语言。

数据分析表达式 (DAX) 语言是一种公式语言，允许用户在 PowerPivot 表（“计算列”）和 Excel 数据透视表（“度量值”）中定义自定义计算。 DAX 包含一些在 Excel 公式中使用的函数，此外还包含其他设计用于处理关系数据和执行动态聚合的函数。
## <一>概括
1. 定义：
 - DAX 是一种 *函数语言*，这意味着完整的执行代码包含在一个函数中。
 - 在 DAX 中，函数可以包含其他内容，例如嵌套函数、条件语句和值引用。 DAX 中的执行从最内部函数或参数开始，逐步向外计算。（在 Power BI 中，DAX 公式在单个行中编写，因此函数的正确格式设置对于可读性很重要）
2. 数据类型：
 - DAX 的设计用于处理表格，因此它只有两个主要的数据类型：数字和其他。 数字可以包括整数、小数和货币。 其他可以包括字符串和二进制对象。 
 - 在计算中混合使用各种数据类型，其结果将根据输入中使用的数据类型进行更改。 数据类型转换将自动发生。 
3. 主要作用：
 - 计算列
 - 计算度量值
 - 
## <二>语法
1. 创建计算列
当你要划分或筛选值，或者要对表中的每一行进行计算时，计算列非常有用。

通过从“建模”选项卡选择“新建列”，你可以在 Power BI Desktop 中创建计算列。 最好采用“数据”视图（而不是“报表”或“关系”视图），因为你可以看到创建的新列以及“编辑栏”填充并准备好用于 DAX 公式。
![此处输入图片的描述][6]
计算列所需的元素如下：
 - 新的列名
 - 至少一个函数或表达式
注:如果在计算列公式中引用一个表或列，则无需在表中指定行 -- Power BI 会为每个计算的当前行计算列。
2. 创建计算度量值
当你计算百分比或比率，或者需要复杂的聚合时，使用计算度量值。
3. 分类：
 - 聚合函数
 - 计数函数
 - 逻辑函数
 - 信息函数
 - 文本函数
 - 日期函数
## <三>函数

## 聚合函数
DAX 提供多种聚合函数，包括以下常用函数：

SUM
AVERAGE
MIN
MAX
SUMX（以及其他 X 函数）

这些函数仅适用于数字列，并通常一次只能聚合一列。

但是以 X 结尾的特殊聚合函数（例如 SUMX） 则可同时处理多列。 这些函数循环访问表，并为每一行计算表达式。
## 计数函数
DAX 中经常使用的计数函数包括：

COUNT
COUNTA
COUNTBLANK
COUNTROWS
DISTINCTCOUNT

这些函数用来计数不同的元素，如非重复值、非空值和表行。

## 逻辑函数
DAX 中的逻辑函数包括：

AND
OR
NOT
IF
IFERROR

这些特殊函数还可以用运算符表达。 例如，在 DAX 公式中 AND 可以输入为（替换为）&&。
## 信息函数
DAX 中的信息函数包括：

ISBLANK
ISNUMBER
ISTEXT
ISNONTEXT
ISERROR

尽管这些函数在具体情况下有用，但提前知道列的数据类型，而不依赖这些函数来提供数据类型仍很有价值。
## 文本函数
DAX 中的文本函数包括：

CONCATENTATE
REPLACE
SEARCH
UPPER
FIXED
## 日期函数
DAX 包含以下日期函数：

DATE
HOUR
NOW
EOMONTH
WEEKDAY


## <四>
### 变量
你可以使用以下语法在 DAX 表达式的任意位置定义一个变量：

`VARNAME = RETURNEDVALUE`
变量可以是任何数据类型，包括整个表。
![此处输入图片的描述][7]
请记住，每次在 DAX 表达式中引用变量时，Power BI 必须根据定义重新计算它的值。 因此，在函数中避免使用重复变量是一个好做法。

### 表的筛选
DAX 和 Excel 公式语言的一个显著区别是 DAX 允许在表达式之间传递整个表，而不仅限于单个值。 DAX 的一项强大功能是允许你在其表达式中筛选表格，然后使用筛选的值集。
![此处输入图片的描述][8]
通过 DAX，你可以创建全新的计算表，然后像处理其他表格一样处理它们 - 包括在这些表和存在于你的数据模型中的其他表之间建立关系。
## 表函数
DAX 提供一套丰富的表函数，包括：

FILTER
ALL
VALUES
DISTINCT
RELATEDTABLE

这些函数返回一个完整的表，而不是一个值。 通常，你会在进一步的分析中将表函数的结果（而不是返回的一个最终值）作为更大的表达式的一部分使用。 值得注意的是，使用表函数时，其结果将继承其列的关系。

可以在表达式中混合使用表函数，前提是每一个表达式只使用一个表并返回一个表。 例如下面的 DAX 表达式：

`FILTER (ALL (Table), Condition)`

该表达式将筛选整个*表*，而忽略当前筛选的任何内容。

DISTINCT 函数返回某一列的各个不同值，这些值在当前上下文中也可见。 因此，以上述 DAX 表达式为例，在表达式中使用 ALL 会忽略筛选，而使用 DISTINCT 替换 ALL 则可查看筛选。

## 可能会用到的建模技巧：
1. 日期数据的格式改变：把长格式的日期字符串修改为短的 。
2. 各种度量值的建立：我的度量值主要涉及一些求和、求平均、计数、变化率等。为了更好的管理度量值，我特意新建了一个名为DetialsMeaured的表，公式为：DetailsMesured = ALL(Details[EpisodeID])，然后把建立的各种度量值归到这个表当中 。
3. 百分比值的格式化：求变化率的度量值，可以把显示格式设置为百分比，那么在内置可视化控件中就直接显示为百分比，无需额外设置或者乘100（我使用了一个第三方控件，其无法识别百分比格式，只能在度量值上乘100） 。
4. 建立层级结构：为了支持数据的下钻显示，那么需要建立数据的层次结构，比如财年包含月份。要建立层次结构很简单，直接把一个字段拖动到另外一个字段下面Power BI就会自动创建一个新的层次结构列（包含了你刚刚操作的两个字段），接着可以继续拖入其他列到这个层次结构列下面，还可以拖动来进行排序。
5. 建立日期表：很多分析都是和时间相关的，那么就需要有一张独立的日期表来为维度提供数据（包括年、财年、季度、月、日、天等）。原来的qvf中也存在这一个日期表，也是依靠脚本生成的，对于Power BI而言同样也可以通过脚本来生成一个日期表。生成日期表的脚本如下：

    DateKey =ADDCOLUMNS (CALENDAR (FIRSTDATE (Details [EpisodeAdmissionDate ] ),LASTDATE (Details [EpisodeAdmissionDate ] ) ), " DateAsInt ",FORMAT ( [ Date ], " YYYYMMDD " ), " Year ", YEAR ( [ Date ] ), " Quarter ",VALUE (FORMAT ( [ Date ], " Q " ) ), " YearQuarter ",FORMAT ( [ Date ], " YYYY " ) & " /Q " &FORMAT ( [ Date ], " Q " ), " Month ", MONTH ( [ Date ] ), " MonthName ",FORMAT ( [ Date ], " mmm " ), " Day ", DAY ( [ Date ] ), " WeekNum ",WEEKNUM ( [ Date ] ), " WeekDay ", WEEKDAY ( [ Date ] ), " WeekDayName ",FORMAT ( [ Date ], " ddd " ), " Fiscal Year ", IF ( MONTH ( [ Date ] ) > 3, YEAR ( [ Date ] ) + 1, YEAR ( [ Date ] ) ), " Fiscal Year Name ", IF ( MONTH ( [ Date ] ) > 3, YEAR ( [ Date ] ) & " - " & ( YEAR ( [ Date ] ) + 1 ), ( YEAR ( [ Date ] ) - 1 ) & " - " & YEAR ( [ Date ] ) ))

　　把日期表添加到模型中后，就可以手动把日期表的Date字段和Details表中的EpisodeAdmissionDate字段建立其关系。
　　
## powerBI缺点
Power BI在可视化能力方面确实需要进一步加强，比如我就遇到如下几个问题：
 - 排序只能基于当前使用的维度，不能自定义排序
 - 堆积面积图图例不能下钻
 - 没有竖条仪表图
 - 饼图不能合并为Other
 - 表格不支持下钻
  [1]: https://dpspowerbi.blob.core.windows.net/powerbi-prod-media/powerbi.microsoft.com/zh-cn/documentation/articles/powerbi-learning-2-2-manage-data-relationships/20170303122340/2-2_1.png
  [2]: https://dpspowerbi.blob.core.windows.net/powerbi-prod-media/powerbi.microsoft.com/zh-cn/documentation/articles/powerbi-learning-3-4-create-slicers/20170303122340/3-4_1.png
  [3]: https://dpspowerbi.blob.core.windows.net/powerbi-prod-media/powerbi.microsoft.com/zh-cn/documentation/articles/powerbi-learning-3-7-create-scatter-charts/20170303122340/3-7_2.png
  [4]: https://dpspowerbi.blob.core.windows.net/powerbi-prod-media/powerbi.microsoft.com/zh-cn/documentation/articles/powerbi-learning-3-8-create-waterfall-funnel-charts/20170303122340/3-8_3.png
  [5]: https://dpspowerbi.blob.core.windows.net/powerbi-prod-media/powerbi.microsoft.com/zh-cn/documentation/articles/powerbi-learning-3-11a-create-interaction-between-visualizations/20170303122340/3-11a_2.png
  [6]: https://dpspowerbi.blob.core.windows.net/powerbi-prod-media/powerbi.microsoft.com/zh-cn/documentation/articles/powerbi-learning-7-2-dax-calculation-types/20170303122340/dax-calc-types_2a.png
  [7]: https://dpspowerbi.blob.core.windows.net/powerbi-prod-media/powerbi.microsoft.com/zh-cn/documentation/articles/powerbi-learning-7-4-dax-expressions/20170303122340/dax-variables_1.png
  [8]: https://dpspowerbi.blob.core.windows.net/powerbi-prod-media/powerbi.microsoft.com/zh-cn/documentation/articles/powerbi-learning-7-6-dax-tables-and-filtering/20170303122340/dax-tables-filtering_1.png