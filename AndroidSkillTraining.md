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

### 二、git

- 四个区：
  - 工作区：workSpace 工作区的文件需要执行add命令，加入到缓存区，才可以纳入到版本控制
  - 暂存区：Index/Stage，提交代码，解决冲突的中转站
  - 本地仓库：Repository，暂存区的文件通过commit命令，变化纳入到本地仓库，每次commit都会生成一个hash值，作为commit id, commit id标识本次提交
  - 远程仓库：Remote。本地仓库的文件通过push命令，将commit更新到远程仓库
- branch:
  - 使用分支意味着你可以把你的工作从开发主线上分离开来，以免影响开发主线
  - 分支间可进行切换、merge
- 常用操作：
  - add
  - commit
  - pull: pull等于fetch+merge，从远程仓库对应分支拉取变动后和本地仓库进行合并。
  - push：把本地仓库的commit推送到远程仓库，需要特别注意的是：**先拉后推，否则远程仓库会拒绝你的push请求**