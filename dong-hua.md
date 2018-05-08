## 基本动画

- 方法一：
    在第一句和最后一句之间写代码
    ```obj-c
    [UIView beginAnimations:nil context: nil];
    [UIView setAnimationDuration:2.0]; //持续时间
    [UIView setAnimationDelegate:self]; // 代理
    [UIView setAnimationDidStopSelector:@selector(stop)];
    [UIView setAnimationWillStartSelector:@selector(start)];
    //改变属性，比如某个控件的frame
    [UIView commitAnimations];
    ```
- 方法二：
    block方式
    ```obj-c
    [UIView animateWith......];
    ```
    
    


