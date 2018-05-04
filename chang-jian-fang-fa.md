- 延时执行


```c
    // 定时任务
    [self performSelector:@selector(hideHUD) withObject:nil afterDelay:1.5];

```

- `- (void)makeObjectsPerformSelector:(SEL)aSelector;`
向数组中的每个对象发送指定的选择器所标识的消息，从第一个对象开始，并继续通过数组到最后一个对象。


```
    // 让subviews数组中的所有对象都执行removeFromSuperview方法
    [self.scrollView.subviews makeObjectsPerformSelector:@selector(removeFromSuperview)];

```



