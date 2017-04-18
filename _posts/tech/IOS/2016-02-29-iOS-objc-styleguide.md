---
layout: post
title: iOS objc编程规范
category: iOS
tags:
description:
---

今天是4年一次的好日此，在这个日子里，随便写点什么吧。

最近在看objc代码规范相关内容，整理了一些常见的代码规范问题，好记性不如烂笔头，整理一份分享给大家，同时也希望自己时不时的拿出来看一下，或许哪一天我就又忘记了 ：）

最终整理的内容可以看[ios-tips](),这个仓库我会定期整理和更新，涉及的内容更精简。


##  美化代码
-	只使用空格而不要使用tab，且一次缩进两个空格。应该将xcode设置成自动将制表符替换成空格，缩进为2空格
-	方法的大括号和其他的大括号(if/else/switch/while 等) 总是在同一行开始，在新起一行结束
-	尽量让你的代码保持在 80 列之内，通过设置 Xcode > Preferences > Text Editing > Show page guide，来使越界更容易被发现。
-	if语句不要省略{ }
-	方法名与方法类型 (-/+ 符号)之间应该以空格间隔
-	@public 和 @private 访问修饰符应该以一个空格缩进。
-	方法的调用要么所有参数一行，要么每个参数一行且保证冒号都对其，当第一个关键字比其它的短时，保证下一行至少有 4 个空格的缩进

##  最佳实践
-	不要使用尤达表达式

````objc
//尤达是星球大战中的jidi武师，他说话的语法都是很奇怪的倒装句，这里泛指这样的代码
if ([@8 isEqual:a]) // 错误
if ([a isEqual:@8]) // 正确
````
-	不要和YES,NO,Nil这些值做比较

````objc
if (great == YES) //错误
if (great)        //正确
````
-	不过过度使用if嵌套，有时可以用return减少if嵌套

````objc
- (void)someMethod {
  if (![someOther boolValue]) {
      return;
  }
  //Do something important
}
````
-	复杂的表达式应该拆分多个语义更明确的字句
-	三元运算符 ? 应该只用在它能让代码更加清楚的地方
-	注意stong，weak，copy，assign的正确使用
-   尽量避免使用c的基本类型 ，例如：

````objc
  int -> NSInteger
  unsigned -> NSUInteger
  float -> CGFloat
  动画时间 -> NSTimeInterval
  enum -> NS_ENUM
````
-	合理使用参数断言，当特定参数的条件不满足时，使用 ```` NSParameterAssert()```` 来断言条件是否成立或是抛出一个异常
-	工厂方法或类构造器方法，返回类型需要使用instancetype而不要用id类型，方法中需要使用 [[xxx class]alloc] init]方法构造对象而不要用[[XXXClass alloc]init]
-	永远不要在```` init dealloc ````方法中使用 getter，setter，.属性等，你应当直接访问实例变量
-	类的构成方法（init方法）需要遵守Designated Secondary原则。这点在swift中被强制规定init和convenience构造方法。

````
designated 初始化方法一般提供所有的参数，有且只有一个，而secondary 初始化方法是一个或多个，并且提供一个或者更多的默认参数来调用 designated初始化方法
````
-   定义你的 designated initializer，确保调用了直接超类的 designated initializer。
-   重载直接超类的 designated initializer。调用你的新的 designated initializer。
-   为新的 designated initializer 写文档。
-   永远不从 designated initializer 里面调用一个 secondary initializer
-	注意初始化模式的合理使用（类簇，单例）
-	合理使用懒加载Lazy loading

````
当实例化一个对象需要耗费很多资源，或者配置一次就要调用很多配置相关的方法而你又不想弄乱这些方法时，我们需要重写 getter 方法以延迟实例化
````
-	要重写类的相等性时，需要同时实现isEqual和hash方法
-	常量推荐静态常量的声明，如果要暴露给外部，使用extern关键词，例如：

````objc
extern NSString *const ZOCCacheControllerDidClearCacheNotification;
static NSString * const ZOCCacheControllerDidClearCacheNotification = @"ZOCCacheControllerDidClearCacheNotification";
````
-	定义你自己的 NSNotification 的时候你应该把你的通知的名字定义为一个字符串常量

````objc
// Foo.h
extern NSString * const ZOCFooDidBecomeBarNotification
// Foo.m
NSString * const ZOCFooDidBecomeBarNotification = @"ZOCFooDidBecomeBarNotification";
````
-	objc中可以合理使用代码块的特性，使局部变量更清晰

````objc
//代码块如果在闭合的圆括号内的话，会返回最后语句的值
NSURL *url = ({
    NSString *urlString = [NSString stringWithFormat:@"%@/%@", baseURLString, endpoint];
    [NSURL URLWithString:urlString];
});
````
-	合理使用Pragma Mark区分：不同功能组的方法，protocols 的实现，对父类方法的重写,View 的生命周期,自定义访问器,
-	方法注释最好用/** 开头，换行后第一句写方法的一句话描述，空一行后在写余下的描述，
还可以使用 | 来引用注释中的变量名及符号名而不是使用引号，例如
```` // Sometimes we need |count| to be less than zero. ````

-	函数定义中的block参数应该尽量放到最后一个参数，把需要提供的数据和错误信息整合到一个单独 block 中，比分别提供成功和失败的 block 要好

````objc
- (void)downloadObjectsAtPath:(NSString *)path
                   completion:(void(^)(NSArray *objects, NSError *error))completion;
````
-	函数定义中的error参数，尽可能方法函数的最后一个函数，并且遵循，数据为空，那么error不为nil，和error不为空，数据必须为空
-	block合理的使用self，weakself，strongSelf

````
一般来说：如果block不是属性则使用self，是属性但block中调用单个self的方法时用weakSelf，多个方法用strongSelf
````
-	block如果一行可以写完块，则没必要换行,块内的代码须按 4 空格缩进,果块太长，比如超过 20 行，建议把它定义成一个局部变量，然后再使用该变量,
-	不要使用new方法创建对象


##  命名规范
###  方法的命名：
-	不要使用and连接参数，第一个参数可以用with，若有动词可以使用for,委托用did，will表示状态
-	如果方法表示让对象执行一个动作，使用动词打头来命名
-	category方法前加上自己的小写前缀以及下划线，比如- (id)zoc_myCategoryMethod
-	方法的定义，当一行有非常多的参数，更好的方式是将每个参数单独拆成一行。如果使用多行，将每个参数前的冒号对齐，当第一个关键字比其它的短时，保证下一行至少有 4 个空格的缩进

###  类，协议命名
-	类名应该以三个大写字母作为前缀（双字母前缀为 Apple 的类预留），首字母大写
-	方法名首字母小写
-	变量名首字母小写，私有变量名称可以用"_"作为后缀，例如```` myInstanceVariable_ ````
-	常量命名可以使用字母'k'作为前缀
-	子类命名应该把说明性的部分放在前缀和父类名的在中间，例如````  ZOCNetworkClient => ZOCTwitterNetworkClient ````

###  属性
-	属性应该尽可能的描述性地命名，避免缩写，并且小写字母开头的驼峰命名。 *符号要靠近名称，如```` NSString *text ````
-	属性尽可能使用.符号调用
-	属性定义排列顺序：原子性，读写性，内存管理，例如 ```` @property (nonatomic, readwrite, copy) NSString *name; ````
-	私有属性定义在实现文件中。


本文根据 [objc禅翻译](https://github.com/oa414/objc-zen-book-cn/)，[Google 开源项目风格指南 - objc](http://zh-google-styleguide.readthedocs.org/en/latest/google-objc-styleguide/contents/)
整理而成，大家可以去读一下这两篇文章，推荐。


##  最后

感谢收看，如果对大家有帮助，请[github上follow和star](https://github.com/coolnameismy)，本文发布在[刘彦玮的技术博客](http://liuyanwei.jumppo.com/)，转载请注明出处