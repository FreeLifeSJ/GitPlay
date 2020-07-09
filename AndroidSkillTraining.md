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

  ![git](/Users/free/Desktop/GitPlay/image/git.png)

- branch:
  - 使用分支意味着你可以把你的工作从开发主线上分离开来，以免影响开发主线
  - 分支间可进行切换、merge
  
- 常用操作：
  - add
  - commit
  - pull: pull等于fetch+merge，从远程仓库对应分支拉取变动后和本地仓库进行合并。
  - push：把本地仓库的commit推送到远程仓库，需要特别注意的是：**先拉后推，否则远程仓库会拒绝你的push请求**

### 三、Butterknife使用和原理

- 使用

  - 绑定和解绑要对应 (在ViewHolder中使用不需要解除绑定)

    ```java
    private Unbinder mUnbinder;
    //Activity中 onCreate中调用 绑定
    mUnbinder = ButterKnife.bind(this);
    //销毁的时候解除绑定
    @Override
    protected void onDestroy() {
        mUnbinder.unbind();
        super.onDestroy();
     }
    ```

    

  - 安装插件，生成注解。插件是Android ButterKnife Zelezny

  - 可以绑定view，也可以绑定事件

    ```java
        @OnClick({R.id.tv_first,R.id.tv_second})
        public void clickll(){
            Toast.makeText(this,"ButterKnife绑定的点击事件",Toast.LENGTH_SHORT).show();
        }
    ```

- 原理涉及到注解和编译时生成代码等相关知识，暂时略过。

### 四、Json

- 序列化和反序列化

  - 序列化：将数据结构或对象转换成二进制串的过程

  - 反序列化：将在序列化过程生成的二进制串转换成数据结构或者对象。

  - 系统底层，数据的传输形式是简单的字节序列形式，即系统不认识对象，只认识字节序列，为了达到进程通讯的需求，需要先将数据序列化。无论是进程间通信，还是本地存储、网络传输，都需要先将数据序列化。进程之间是不共享数据的，线程是可以共享的。从广义上讲，数据序列化就是将数据结构或对象转换成我们可以存储或者传输的数据格式的一个过程。
  - 常见序列化协议：xml，json, Protobuf

- json基础概念
  - 定义：轻量级数据交换格式
  - 作用、数据标记、传输、存储
  - 独立于平台、语言
  - 解析方式：jackson fastjson Gson

- json：键值对，键必须是字符串，值可以是以下类型

  - String
  - Number，包括整数，浮点数
  - 布尔值：true, false
  - 对象：{}
  - 数组：[]
  - null值

- 解析时出现异常，基本是因为JavaBean中属性的类型和json中对应值类型不兼容引起的，如

  ```java
  int topicId;
  
  {"topicId".""} //这里当字符串为空或者字符串不能解析为数值时就会报异常，即NumberFormatException
  ```

  

- demo

  ```json
  {
      "code": 200,
      "message": "[ACCOUNT]检查用户Token:OK",
      "result": {
          "gender": "MALE",
          "purchaseBookIds": "",
          "dcStudyType": "",
          "rdmExperienceTopicInfoList": [
              {
                  "topicId": 79,
                  "experienceTotalNum": 3112,
                  "topicName": "日签听我的",
                  "topicImg": "http://res.towords.com/img/find/topic/79.png",
                  "topicBackgroundUrl": "http://res.towords.com/img/find/topic/banner_79.png",
                  "topicDescription": "日签听我的",
                  "topicDes": "你的思想应该被看见",
                  "topicUrl": "https://www.towords.com/events/20200403"
              },
              {
                  "topicId": 68,
                  "experienceTotalNum": 22037,
                  "topicName": "想说就说呗",
                  "topicImg": "http://res.towords.com/img/find/topic/68_v2.png",
                  "topicBackgroundUrl": "http://res.towords.com/img/find/topic/banner_68.png",
                  "topicDescription": "想说就说呗",
                  "topicDes": "拓词树洞"
              },
              {
                  "topicId": 62,
                  "experienceTotalNum": 1174,
                  "topicName": "词组终结者",
                  "topicImg": "http://res.towords.com/img/find/topic/62_v2.png",
                  "topicBackgroundUrl": "http://res.towords.com/img/find/topic/banner_62.png",
                  "topicDescription": "词组终结者",
                  "topicDes": "提笔文采斐然，张口妙语连珠，就靠它!",
                  "topicUrl": "https://wx.towords.com/towordscamp/phrase_book"
              },
              {
                  "topicId": 8,
                  "experienceTotalNum": 1753,
                  "topicName": "英语下午茶",
                  "topicImg": "http://res.towords.com/img/find/topic/8_v2.png",
                  "topicBackgroundUrl": "http://res.towords.com/img/find/topic/banner_8.png",
                  "topicDescription": "英语下午茶",
                  "topicDes": "每天一杯下午茶，英语进步看得见",
                  "topicUrl": "http://api.towords.com/lesson/purchase_list?product_id=7"
              }
          ],
          "androidAppVersion": 9.52,
          "devilCampStatus": false,
          "initUserWordData": false,
          "wordLinkStatus": false,
          "favMaxNum": 800,
          "androidLastUpdateDetail": "全新起航，不负每一份坚持！\n1. 新增学英语板块，查词，随声听，词库，课程，都在这里。\n2. 拓友圈和发现页合并，话题回归，用心得记录你的成长～\n3. 修复日历Bug一个。\n\n如果有任何建议或是问题，都可以在「心得-帮拓词做大做强」反馈，我们会尽快回复和解答的。",
          "identity": "JUNIOR_SCHOOL_STUDENT",
          "senseIdBlacklistVersion": 2,
          "bookInfoMd5": "401e897be11822f173aaf46e537f3532",
          "hasCreatedLearnPlan": true,
          "partnerStatus": false,
          "dcExperienceStatus": false,
          "appStorePublishStatus": false,
          "iosLastUpdateDetail": "全新起航，不负每一份坚持！\n1. 新增学英语板块，查词，随声听，词库，课程，都在这里。\n2. 拓友圈和发现页合并，话题回归，用心得记录你的成长～\n3. 修复了一些bug\n\n如果有任何建议或是问题，都可以在「心得-帮拓词做大做强」反馈，我们会尽快回复和解答的。",
          "joinTime": "2019-12-20",
          "partnerDeedStatus": false,
          "dcAccuracy": 0.95,
          "iosAppVersion": 9.51,
          "latestNoticePublishTime": 1594112669000,
          "target": "",
          "wordAudioReviseVersion": 5,
          "vipExpireTip": "你的PLUS会员已过期 1 天",
          "onceBeenDevilCamp": false,
          "currentGroupId": 12864,
          "phvbStatus": false,
          "targetDeadLine": "",
          "userVipInfo": {
              "vipStatus": false,
              "neverBeenVipStatus": false,
              "autoRenewableStatus": false,
              "experimentVipStatus": false,
              "startDate": "",
              "expireDate": ""
          },
          "learnEnglishPageNoticeTag": false,
          "status": "VALID"
      }
  }
  ```

  