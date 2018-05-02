## xcode使用

### 技巧

* 注释
  * 文档注释
    ```c
    /**我是label控件*/
    @property (nonatomic,strong)UILabel *label;
    ```

### 出现的问题

* 如果项目启动只显示”device”而 没有模拟器，有可能是因为项目的Deployment Target 版本比当前xcode 的最新版本高。解决方法：把Deployment Target 调低，最好的办法是升级xcode.


* 新建文件时如果没有勾选 Targets,请到TARGETS->Build Phases->Copy Bundle Tesources 添加想要的文件


