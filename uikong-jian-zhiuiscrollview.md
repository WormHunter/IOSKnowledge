## UIScrollView
- UIScrollView缩放实现步骤
    1. UIScrollView的id<UISCrollViewDelegate> delegate代理对象
    2. 设置minimumZoomScale ：缩小的最小比例
    3. 设置maximumZoomScale ：放大的最大比例
    4. 让代理对象实现下面的方法，返回需要缩放的视图控件

```obj-c
   - (UIView *)viewForZoomingInScrollView:(UIScrollView *)scrollView;
//跟缩放相关的其他代理方法    
//缩放完毕的时候调用 
- (void)scrollViewWillBeginZooming:(UIScrollView *)scrollView withView:(UIView *)view
//正在缩放的时候调用
- (void)scrollViewDidZoom:(UIScrollView *)scrollView
```


