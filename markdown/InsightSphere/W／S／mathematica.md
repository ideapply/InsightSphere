- > Mathematica是美国Wolfram研究公司生产的一种数学分析型的软件，以符号计算见长，也具有高精度的数值计算、强大的图形功能和动画等多媒体集成功能。
- 前期资料收集
    - [Mathematica & Wolfram Language Tutorial: Fast Intro for Math Students](https://www.wolfram.com/language/fast-introduction-for-math-students/zh/?source=footer)
- ### 基本规则
    - 内置函数首字母大写
    - `[]`里面是所需要计算的内容
    - `{}`列表或者范围
    - `shift+enter`执行计算
    - 默认情况下未赋值变量运行后是蓝色字，已赋值变量是黑色提示。
    - 等号是`==`，而`=`是赋值符号
    - 设置工作路径`SetDirectory[NotebookDirectory[]]; SetDirectory["./DataFiles"];`
- ### 基本输入
    1. 默认格式：In[1]:= `8/3` -> Out[1]= 8/3
    2. 近似计算：In[5]:= `N[8/3]` -> Out[5]= 2.66667
    3. 多项式展开：`Expand[(a+1)(a-2)]`
    4. 方程求解：`Solve[x^2+2 x+1==0,x]`
    5. Plot绘图：`Plot[Sin[x], {x, 0, 10}]`
    6. Table输入：In[3]:= `Table[i, {i, 1, 10}]` -> Out[3]= `{1, 2, 3, 4, 5, 6, 7, 8, 9, 10}`
        - In[4]:= `Table[i + j, {i, 1, 5}, {j, 2, 5}]` -> Out[4]= `{{3, 4, 5, 6}, {4, 5, 6, 7}, {5, 6, 7, 8}, {6, 7, 8, 9}, {7, 8, 9, 10}}`
    7. 全局Clear：Clear["Global`*"]
- ### 输入输出
    - 自动补全
    - 普通格式 +-*/
    - 数学2D格式， 善用esc键， 比如输入pi，就esc+pi+esc
    - 百分号+数字：表示引用第几次结果 ，不加数字就是上一个结果
    - 双斜线// ,函数后缀， 里面Simplify[]与//Simplify是等价的
    - mma格式排版：Alt+数字1到7可以得到不同的文档结构
- ### Wolf-Mathematica
    - **定义变量**
        - 定义x=10，计算2的x次方：In[26]:= `x = 10;2^x` -> Out[27]= 1024
        - 判断两个值是否一致：In[28]:= `x == 1023` -> Out[28]= False
        - 加减乘除幂指数括号运算：In[31]:= `(Sqrt[2] + 1)^2 (3 - a)/\[Pi]`
        - 创建列表：In[33]:= `Table[i^2, {i, 1, 10, 2}]` -> Out[33]= {1, 9, 25, 49, 81}
    - **自定义函数**
        - 简单函数，注意下划线与冒号，当然还有更高级用法，两个下划线与三个下划线，以及默认参数等
            - In[35]:= `f[x_, y_] := x^2 y`    
        `f[a, y]`  
        `f[1, 2] `  
Out[36]= a^2 y  
Out[37]= 2
    - **交互式操作**
        - 画一个sin x函数图像,并改变其振幅与周期：
`Manipulate[Plot[A Sin[a x], {x, -5, 5}, PlotRange -> {{-5, 5}, {-5, 5}}], {a, 2, 5, 0.5}, {A, -2, 2, 0.2}]`
        - 改进一下模型，可以自定义函数头{sin,cos,tan}, 以及滑块名称定义，默认值定义。
`Manipulate[Plot[fn[f*x + ps],  {x, 0, 2 \[Pi]}],  {{f, 1, "frequency"}, 1, 5}, 
 {{ps, 1, "phase shift"}, 1, 10},  {{fn, Sin, "function"},   {Sin, Cos, Tan}}]`
    - **使用帮助**
        - 选中需要帮助的函数，按F1快捷键打开帮助文档
        - ？+函数，执行后给出函数帮助信息
    - **2D，3D绘图**
        - 2D图：`Plot[{Sin[x], Cos[x]}, {x, 0, 2 \[Pi]}]`
            - `Plot[{Sin[x], Cos[x]}, {x, 0, 2 \[Pi]}] 
LogPlot[x^x, {x, 1, 10}]
ParametricPlot[{Sin[t], t^2/100}, {t, 0, 10}] 
RegionPlot[x^2 + y^2 <= 6 && y > 0, {x, -3.1, 3.1}, {y, -3.1, 3.1}]`
            - Plot函数属性分叉之多，例如常用的如下:
                - AspectRatio 1/GoldenRatio 高宽比
                - Axes True 是否绘制轴
                - ClippingStyle None 如何绘制曲线被剪切的区域
                - ColorFunction Automatic 确定曲线颜色的方法
                - ColorFunctionScaling True 是否缩放 ColorFunction 的变量
                - PlotLabel None 整个绘图的标签
                - PlotLabels None 曲线的标签
                - EvaluationMonitor None
                - 在每次函数计算时，需要计算的表达式 Exclusions Automatic
                - x 中排除的点 ExclusionsStyle None
                - 排除点的绘制样式 Filling None
                - 每条曲线下填充 FillingStyle Automatic
                - 填充的样式 LabelingSize Automatic maximum size of callouts and labels MaxRecursion Automatic
                - 递归子划分的最大数量 Mesh None
                - 在每条曲线上绘制多少个网格点 MeshFunctions {#1&}
                - 如何决定网格点的放置位置 MeshShading None
                - 如何在网格点间绘制阴影区域 MeshStyle Automatic
                - 网格点的样式 Method Automatic
                - 修饰曲线的方法 PerformanceGoal $PerformanceGoal
                - 试图优化哪些方面的性能 PlotLegends None
                - 曲线的图例 PlotPoints Automatic
                - 样本点的初始数量 PlotRange {Full,Automatic}
                - y 的范围或包含的其它值 PlotRangeClipping True
                - 是否在曲线范围内剪切 PlotStyle Automatic
                - 指定每条曲线样式的图形指令 PlotTheme
                - PlotTheme 绘图的整体外观主题
                - RegionFunction (True&) 如何确定是否包含一个点 ScalingFunctions None
                - 如何缩放单个坐标 TargetUnits Automatic
                - 在绘图中显示的单位 WorkingPrecision
                - MachinePrecision 内部计算使用的精度
        - 3Dplot：`Plot3D[Sin[x + y^2], {x, -3, 3}, {y, -2, 2}]`
            - `VectorPlot3D[{x, y, z}, {x, -1, 1}, {y, -1, 1}, {z, -1, 1}]`
- ### 扩展功能
    - ^^**微分方程**^^
        - __Wolfram 语言可以求解常微分方程、偏微分方程和时滞微分方程 （ODE、PDE 和 DDE）.__
        - [DSolveValue](http://reference.wolfram.com/language/ref/DSolveValue.html) 接受微分方程并返回通解：$$y'+y=x$$
            - in[1]:= `sol=DSolveValue[y'[x]+y[x]==x,y[x],x]`
                - in[2]:= `sol /. C[1] -> 1`
            - in[3]:=`DSolveValue[{y'[x]+y[x]==x,y[0]==-1},y[x],x]`
        - [NDSolveValue](http://reference.wolfram.com/language/ref/NDSolveValue.html) 可求出数值解：$$y'=\cos{x^2}$$
            - in[1]:=`NDSolveValue[{y'[x]==Cos[x^2],y[0]==0},y[x],{x,-5,5}]`
                - in[2]:= `Plot[%,{x,-5,5}]`
    - **绘制数据**
        - 用 [ListPlot](http://reference.wolfram.com/language/ref/ListPlot.html) 绘制数据点：in[1]:= `ListPlot[{1,3,4,7,9,15}]`
        - 用[图表](http://reference.wolfram.com/language/guide/ChartingAndInformationVisualization.html)显示信息： in[2]:= `BarChart[{1,2,3,4,5}]`
        - 多个数据集添加:in[1]:= `ListLinePlot[{{1,2,3,4,5},{1,3,7,10,17}}]`
    - **最佳拟合曲线**
        - 用 [Fit](http://reference.wolfram.com/language/ref/Fit.html) 命令找到最佳拟合曲线： in[1]:= `Fit[{2,3,5,7,11,13},{1,x,x^2},x]`
            - in[2]:=`Show[{Plot[%33, {x, 1, 6}], ListPlot[{2, 3, 5, 7, 11, 13}]}]`
    - **矩阵与线性代数**
        - 表示矩阵
            - Wolfram 语言用列表的列表表示矩阵：in[1]:=`{{1,2},{3,4}}`
            - [MatrixForm](http://reference.wolfram.com/language/ref/MatrixForm.html) 将输出显示为一个矩阵：in[2]:= `MatrixFrom[{{a,b},{c,d}}]`
        - 构建矩阵
            - 可以用迭代函数[构建矩阵](http://reference.wolfram.com/language/guide/ConstructingMatrices.html)：in[1]:= `Table[x,y,{x,1,3},{y,0,2}]`
            - 或[导入](http://reference.wolfram.com/language/guide/ImportingAndExporting.html)表示矩阵的数据：in[2]:=`Import["data.csv"]`
        - 矩阵基本变换
            - 标准的[矩阵运算](http://reference.wolfram.com/language/guide/MatrixOperations.html)对元素进行操作：in[1]:= `{1,2,3}{a,b,c}`
            - 计算两个矩阵的[点积](http://reference.wolfram.com/language/ref/Dot.html)：in[2]:= `{{1,2},{3,4}}.{{a,b},{c,d}}`
            - 求[行列式](http://reference.wolfram.com/language/ref/Det.html)：in[3]:= `Det[{{a,b},{c,d}}]`
            - 获取矩阵的[逆](http://reference.wolfram.com/language/ref/Inverse.html)：in[4]:= `Inverse[{{1,1},{0,1}}]`
        - ^^求解线性系统^^
            - 用 [LinearSolve](http://reference.wolfram.com/language/ref/LinearSolve.html) 求解线性系统：in[1]:= `LinearSolve[{{1,1},{0,1}},{x,y}]`
    - **积分与导数**
        - 积分
            - 用 [Integrate](http://reference.wolfram.com/language/ref/Integrate.html) 计算积分：in[1]:= `Integrate[8x^4,x]`
            - 用 [NIntegrate](http://reference.wolfram.com/language/ref/NIntegrate.html) 来得到数值近似：in[2]:= `NIntegrate[x^3Sin[x]+2Log[3x]^2,{x,0,Pi}]`
        - 导数
            - 用命令 [D](http://reference.wolfram.com/language/ref/D.html) 计算导数： in[1]:= `D[x^6,x]`
            - 或者使用角分符号：in[2]:= `Sin'[x]`
            - 对用户定义的函数求导：in[1]:=`f[x_]:=x^2+2x+1;f'[x]`
            - 多次求导：in[2]:= `D[x^6,{x,3}]`
