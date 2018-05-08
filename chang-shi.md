

- 凡是参数名为File，传递的都是文件的全路径（这说法有点怪）

```obj-c
self.shops = [NSArray arrayWithContentsOfFile:file];

```

- 黄色的文件夹(一般)是虚拟文件夹

- init方法内部会自动调用 initWithFrame,所有自定义View时，建议重写`initWithFrame`

- 一般情况下 方法的参数bundle为nil，就是 mainBundle

    ```obj-c
    UINib *nib = [UINib nibWithNibName:@"Test" bundle:nil];
    ```
    

    



