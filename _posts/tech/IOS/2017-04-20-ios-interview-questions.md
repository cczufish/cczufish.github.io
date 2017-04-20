---
layout: post
title: iOS面试题
category: iOS
tags: iOS,面试
description:
---

题目来自http://www.cocoachina.com/bbs/read.php?tid-1718238.html，答案是自己作答。

1，下面代码在按钮点击后，在ARC下会发生什么，MRC下呢？为什么？

    @interface ViewController ()
    @property(nonatomic, assign) void(^block)();

    @end

    @implementation ViewController

    - (void)viewDidLoad {
        [super viewDidLoad];

        int value = 10;
        void(^blockC)() = ^{
            NSLog(@"just a block === %d", value);
        };

        NSLog(@"%@", blockC);
        _block = blockC;
    }

    - (IBAction)action:(id)sender {
        NSLog(@"%@", _block);
    }

ARC下：
    2017-04-20 18:51:57.375 Test[30056:1497072] <__NSMallocBlock__: 0x608000051250>
    2017-04-20 18:52:06.999 Test[30056:1497072] <__NSMallocBlock__: 0x608000051250>
MRC下：(按钮点击后崩溃了)
    2017-04-20 18:56:08.819 Test[30148:1503278] <__NSStackBlock__: 0x7fff5ca319f8>
    (lldb) po _block
    0x00007fff5ca31a38

2， 在ARC环境下这段代码为什么不会崩溃？

    @interface ViewController ()
    @property(nonatomic, weak) void(^block)();

    @end

    @implementation ViewController

    - (void)viewDidLoad {
        [super viewDidLoad];

        void(^ __weak blockA)() = ^{
            NSLog(@"just a block");
        };

        _block = blockA;
    }

    - (IBAction)action:(id)sender {
        _block();
    }

3，下面是一个员工表，manager_id表示对应的boss的ID。通过一个SQL找出下表中比boss工资还高的人。。。。
    id    name    salary    manager_id
    1    Noah    70000    NULL
    2    西兰花    80000    1
    3    椰菜花    80000    NULL
    4    没钱花    80000    3

输出格式为：

name
西兰花

4 写一个函数，输入一个数如38，拆分 3 + 8 = 11，1 + 1 = 2，最后2无法拆分就返回（伪代码也行）
    - (int)test:(int)num
    {
        while(num>10)
        {
            num = num/10 + num%10;
        }
        NSLog(@"%d",num);
        return num;
    }

5，通过runtime添加的“关联对象”和类的实例变量有什么区别？使用时要注意什么？

6，用一个生活中的例子来说说同步和异步。

7，线程间通信在OC中有几种方式？分别是？常用那种？

8，使用快速枚举迭代一个可变数组时需要注意什么问题？怎么避免？

9，什么是面向对象的多态性？
多态性，就是一个父类的引用变量，可以指向其任意一个子类对象。
例如，一个animal类，其子类有cat与dog，然后你创建一个父类animal的引用animalAlpha，然后它可以指向cat的对象cat1，或指向dog的对象dog1。

10，UIViewController的presentViewController和UINavigationController的pushViewController方法分别多用于什么交互场景？

11，NSOperation和GCD的区别是什么？前者多用于什么场景？

12，面向接口编程指的是什么？为什么说面向实现编程是一种错误的编程方式？

13，在iOS开发中遇到那些类族(Class Cluster) ？如NSNumber这种。为什么需要这种设计方式？

14，javascript的原型链和OC的继承有什么区别？

15，Hybrid开发的优势在哪里？目前有那些框架可以实现Hybrid开发？
跨平台性，移植成本低,热修复

16，使用了ARC是不是就等于没有内存泄漏了？如果不是的话请举例。
循环引用（Retain Cycle）
Delegate：一定要注意将 delegate 变量声明为weak类型，像这样 
    @property (nonatomic, weak) id delegate;
Block:
    __weak typeof(self)weakself = self;
    self.completionHandler = ^{
        NSLog(@"%@",weakself);
    }
NSTimer:
如果在一个 ViewController 里创建了一个定时器，并且 repeats：值为 YES，一定记得在 pop/dismiss 当前 ViewController 将 timer 设为 invalidate，否则 会造成循环引用，这里要特别需要 注意 的一点是：我们不要在 ViewController 的 dealloc 方法里调用 [timer invalidate]; 因为从来不会调到这里，我们应该在 viewWillDisappear里边调用，像这样：
    - (void)viewWillDisappear:(BOOL)animated{
        [super viewWillDisappear:animated];
        if ([self isMovingFromParentViewController]) {
            [timer invalidate]; //解除对self的引用
        }
    }

17，下面代码中为什么可以直接用self？
[UIView animateWithDuration:1 animations:^{
self.view.backgroundColor = [UIColor yellowColor];
}];

下面这段代码可以用self吗？为什么？
- (void)doSomething {
[BlockClass doSomethingUseBlock:^{
NSLog(@"%@", self);
}];
}

像系统UIView动画的block，我们可以直接在block里写self，而不是weakSelf。而自定义的block如果直接使用了self，或者成员变量的话，都会形成强引用，造成内存泄漏。UIView的动画block不会造成循环引用的原因就是，这是个类方法，当前控制器不可能强引用一个类，所以循环无法形成。

18，进程的内存布局是怎样的？
![](http://oolkmbv7h.bkt.clouddn.com/1164743453630174321.jpg)

19，在GCD中，那几种场景会出现死锁的现象？怎么避免？
第一种情况：代码都是在主线程中，主队列是串行队列，同步添加任务，互相等待造成死锁，用异步解决。
    NSLog(@"=================4");
    dispatch_sync(dispatch_get_main_queue(), ^{ 
        NSLog(@"=================5");
    });
    NSLog(@"=================6");


20，怎么用NSOperation封装一个异步请求？这个Operation需要放到NSOperationQueue里调度的。

21，CoreFoundation和Foundation有什么区别？

22，怎么判断两个链表是双交的？

23，怎么判断一个链表存在环?

24，当一个View的bounds原点不为0的时候会出现什么情况？

1. 它可以修改自己坐标系的原点位置，影响“子view”的显示位置。
2. bounds，它可以通过改变宽高，改变自身的frame，进而影响到再父视图的显示位置和大小。

25，OC的数组是怎么实现的？和C的数组区别在？简单说一下即可。

26，weak和assign有什么区别？
assign 适用于基本数据类型如int,float,struct等值类型，不适用于引用类型。因为值类型会被放入栈中，遵循先进后出原则，由系统负责管理栈内存。而引用类型会被放入堆中，需要我们自己手动管理内存或通过ARC管理。
weak 适用于delegate和block等引用类型，不会导致野指针问题，也不会循环引用，非常安全。

27，setNeedLayout的作用是什么？

28，什么时候用NS_OPTIONS，NS_ENUM?
