### 一、RecyclerView的使用和适配器模式

#### 1. 适配器模式

- 定义；适配器模式将一个类的接口，转换成客户期望的另一个接口。适配器让原本接口不兼容的类可以合作无间。
- 生活中的例子：mac电脑的转接器

#### 2. RecyclerView.Adapter

- 作用：为RecyclerView提供数据源，创建布局item，将数据和布局item进行绑定

- 三个抽象的关键方法（必须实现）：

  - getItemCount：获取item的总数   最先被调用
  - onCreateViewHolder: 创建ViewHolder
  - onBindViewHolder：将数据和ViewHolder进行绑定

- demo:

  ```java
  
  ```

  

#### 3. RecyclerView.LayoutManager

- 作用：设置每一个item在RecyclerView中的位置布局。
- 系统提供了三个实现类：
  - LinearLayoutManager: 线性布局，可以垂直可以水平，默认是垂直布局
  - GridLayoutManager：网格布局
  - StaggeredGridLayoutManager：流式布局,例如瀑布流效果

