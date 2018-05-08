## 什么是Plist文件

* 直接将数据直接写在代码里面，不是一种合理的做法。如果数据经常改，就要经常翻开对应的代码进行修改，造成代码扩展性低

* 因此，可以考虑将经常变的数据放在文件中进行存储，程序启动后从文件中读取最新的数据。如果要变动数据，直接修改数据文件即可，不用修改代码

* 一般可以使用属性列表文件存储NSArray或者NSDictionary之类的数据，这种“属性列表文件”的扩展名是**plist**，因此也称为“plist文件”

  ### 加载plist

```objc
///加载plist
self.shops = [NSArray arryWithContentsOfFile:file];
```

### Xib加载

* 方法1

  ```obj-c
    NSArray *views = [[NSBundle mainBundle] loadNibNamed:@"xib文件名" owner:nil options:nil]
  ```

* 方法2

  ```
    UINib *nib = [UINib nibWithNibName:@"xib文件名" bundle:nil];
    NSArray *views = [nib instantiateWithOwner:nil options:nil];
  ```

  ### xib

```obj-c
/**
 * 当控件通过代码创建时，就会调用这个方法
 * 当控件通过代码创建时，想做一些初始化操作。应该在这个方法中执行
 */
- (instancetype)initWithFrame:(CGRect)frame
{
    if (self = [super initWithFrame:frame]) {
        [self setup];

        // 添加子控件代码
    }
    return self;
}

/**
 * 当控件是通过xib\storyboard创建时，会调用这个方法来初始化控件
 */
- (id)initWithCoder:(NSCoder *)aDecoder
{
    if (self = [super initWithCoder:aDecoder]) {
    }
    return self;
}

/**
 * 当控件从xib\storyboard中创建完毕时，就会调用这个方法
 * 当控件从xib\storyboard中创建完毕后的初始化操作。应该在这个方法中执行
 */
- (void)awakeFromNib
{
    [self setup];
}

/**
 * 自定义的方法（不是系统方法）
 * 初始化代码
 */
- (void)setup
{
    self.scrollView.backgroundColor = [UIColor redColor];
}
```

* 基于Autolayout的动画
  ```obj-c
  //在修改了约束之后，只要执行下面代码，就能做动画效果
  [UIView animateWithDuration:1.0 animations:^{
    [添加了约束的view layoutIfNeeded];
  }];
  ```



