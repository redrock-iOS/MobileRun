# iOS MobileRun 项目开发规范
## 项目结构
- 每一个虚拟Group需对应一个实体Folder
- 严格按照[分包结构](http://ryantang.me/blog/2014/08/03/ios-prj-structure/)整理文件：
	- Application：这个group中放的是AppDelegate和一些系统常量及系统配置文件；
	- Base：一些基本父类，包括父ViewController和一些公用顶层自定义父类，其他模块的类一般都继承自这里的一些类；
	- Controller：系统控制层，放置ViewController，均继承于Group Base中的BaseViewController或BaseTableViewController；
	- View：系统中视图层，由于我比较喜欢通过代码实现界面，所以这里放的都是继承于UIView的视图，我将视图从ViewController中分离出来全部放在这里，这样能保持ViewController的精简；
	- Model：系统中的实体，通过类来描述系统中的一些角色和业务，同时包含对应这些角色和业务的处理逻辑；
	- Handler：系统业务逻辑层，负责处理系统复杂业务逻辑，上层调用者是ViewController；
	- Storage：简单数据存储，主要是一些键值对存储及系统外部文件的存取，包括对NSUserDefault和plist存取的封装；
	- Network：网络处理层(RTHttpClient)，封装了基于AFNetworking的网络处理层，通过block实现处理结果的回调，上层调用者是Handler层；
	- Database：数据层，封装基于FMDB的sqlite数据库存取和管理(RTDatabaseHelper)，对外提供基于Model层对象的调用接口，封装对数据的存储过程。
	- Utils：系统工具类(AppUtils)，主要放置一些系统常用工具类；
	- Categories：类别，对现有系统类和自定义类的扩展；
	- Resource：资源库，包括图片，plist文件等；

## 代码规范
- 创建的所有类以MR为前缀
- 宏
	- 能用const static表示的不要用#define
	- 全局宏统一写在pch file中，pch file外尽量少用宏
	- 字符串、颜色统一写在const.h中，const.h外尽量少调用颜色、字符串
	- 宏名称的格式或者为`kAaaaaBbbbbCcccc`，或者为`ABC_DEFG_HIJK`
- 能用`self.`即不应用`_`，用`@property`代替单独的实例变量
- 该缩进的地方必须严格缩进，每个缩进为一个tab
- 未提及的代码规范暂时以[NYTimes代码规范](https://github.com/NYTimes/objective-c-style-guide)为准

## Git/GitHub
- 每一次git commit必须提交备注，并交代详尽所做改动，用英文表达困难的情况下可用中文表达
- 每一次push必须保证工程无错误、冲突已经正确解决
- 不要私自修改他人代码
- 不得在工程中加入超过1M的文件（图片、压缩包）
- 美工没有提供的小icon，统一使用[阿里妈妈](http://www.iconfont.cn/)的iconfont资源，不得使用png、jpg等格式

## 待补充

## TODO
- 郑佩越 

  1. 在Storage里封装UserDefault存取，在Application里创建pchFile
  2. 登陆首页的大致UI、判空和判错处理、错误提示反馈字符串（存在Config.h里）、登陆成功后账号密码存本地
  3. 封装用户头像ImageView为WRProfileIamgeView
  4. 更改签名的vc
  5. 意见反馈的vc
  6. 关于的View
  7. 退出的逻辑
  
- 万致远
  
  1. 地图SDK、分享SDK
  2. 获取跑步路程、步数，防作弊算法
  3. 运动轨迹的绘制
  
 
