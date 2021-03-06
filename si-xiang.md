## property用到布尔类型的属性时
- 目的是为了方便阅读，增强可读性
```objc
@property (assign, nonatomic) BOOL *vip;
//建议改成
@property (assign, nonatomic,getter=isVip) BOOL *vip;
```

## 四舍五入

0.3 &gt;&gt; \(int\)\(0.3+0.5\) &gt;&gt; 0  
0.6 &gt;&gt; \(int\)\(0.6+0.5\) &gt;&gt; 1

## 分页

* 循环利用
  * 比如scrollView里有三张图片，分别为UIImageView①②③，每张图片大小等于scrollView的大小，当显示③时，向右滚，我们可以把①拿出来，图片替换一下；

## 分页之无限循环

## 九宫格计算思路

* 利用控件的索引index计算出控件所在的行号和列号
* 利用列号计算控件的坐标x值
* 利用行号计算控件的坐标y值
  ```objc
    for (int i = 0; i<50; i++) {
        int row = i / 3; // 行号
        int col = i % 3; // 列号
        CGFloat x = col * (50 + 30); // 列号决定了X
        CGFloat y = row * (50 + 30); // 行号决定了Y
        //...
    }
  ```

```obj-c
int a = 10;
```

## 懒加载

* 用到时再加载

## 用模型取代字典的好处

* 使用字典的坏处

  * 一般情况下，设置数据和取出数据都使用“字符串类型的key”，编写这些key时，编辑器没有智能提示，需要手敲

    ```obj-c
    dict[@"name"] = @"Jack";
    NSString *name = dict[@"name"];
    ```

    手敲字符串key，key容易写错Key如果写错了，编译器不会有任何警告和报错，造成设错数据或者取错数据

* 使用模型的好处

  * 所谓模型，其实就是数据模型，专门用来存放数据的对象，用它来表示数据会更加专业模型设置数据和取出数据都是通过它的属性，属性名如果写错了，编译器会马上报错，因此，保证了数据的正确性使用模型访问属性时，编译器会提供一系列的提示，提高编码效率

    ```obj-c
    app.name = @"Jack";
    NSString *name = app.name;
    ```

## id类型和instancetype类型

* instancetype在类型表示上，跟id一样，可以表示任何对象类型

* instancetype只能用在返回值类型上，不能像id一样用在参数类型上

* instancetype比id多一个好处：编译器会检测instancetype的真实类型

## 类前缀

使用Objective-C开发iOS程序时，最好在每个类名前面加一个前缀，用来标识这个类的“老家”

* 点击项目 右侧栏的文件属性下 Object Document -&gt;Class Prefix

## view的封装\(自定义View\)

* 如果一个view内部的子控件比较多，一般会考虑自定义一个view，把它内部子控件的创建屏蔽起来，不让外界关心

* 外界可以传入对应的模型数据给view，view拿到模型数据后给内部的子控件设置对应的数据

* 封装控件的基本步骤

  * 在initWithFrame:方法中添加子控件，提供便利构造方法
  * 在layoutSubviews方法中设置子控件的frame（一定要调用super的layoutSubviews）
    增加模型属性，在模型属性set方法中设置数据到子控件上



