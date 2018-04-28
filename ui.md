## xib/storyboard
1.0 方法 把返回参数void 改成 IBAction 会出现空心圆，用于连线控件
1.0 属性 在类型前加 IBOutlet 会出现空心圆 ,用于连线控件
1.1 一个控件可以与多个方法连线
1.2 一个已经连线的控件，拷贝时，会把对应的连线也一起拷贝
1.3 连线之后，如果代码注释了，那根线却没有注释，所有触发事件时，会报错（奔溃）
1.4 属性声明尽量不要放在.h里，类拓展（可以为某个类增加一些额外的属性和方法）

## UIView
- UIView的常见属性

```objc
@property(nonatomic) CGRect frame;
//控制矩形框在父控件中的位置和尺寸（以父控件的左上角为坐标原点）

@property(nonatomic) CGRect bounds;
//控制矩形框在父控件中的位置和尺寸（以自己左上角为坐标原点，所有bounds的x、y一般为0）

@property(nonatomic) CGPoint center;
//控件中点的位置（以父控件的左上角为坐标原点）
```