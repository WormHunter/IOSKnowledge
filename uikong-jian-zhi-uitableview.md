## tableView 性能优化 - cell的循环利用方式
- 定义一个全局变量
```obj-c
// 定义重用标识
NSString *ID = @"hero";
```
- 注册某个便是对应cell类型
    ```obj-c
    //一般在viewDidLoad 里面写，因为只需要注册一次
    - (void)viewDidLoad{
        [self.tableView registerClass:[UITableViewCell class] forCellReuseIdentifier:ID];
    }
    ```
- 在数据方法中返回cell
    ```obj-c
    - (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath
    {
        // 1.去缓存池中查找cell
        UITableViewCell *cell = [tableView dequeueReusableCellWithIdentifier:ID];
        
        // 2.覆盖数据
        XMGHero *hero = self.heroes[indexPath.row];
        cell.textLabel.text = hero.name;
        cell.imageView.image = [UIImage imageNamed:hero.icon];
        //默认创建，detailTextLabel不显示
        cell.detailTextLabel.text = hero.intro;
        
        return cell;
    }
    ```

## 代理方法
- 取消选中，即上一次选中的被取消

- cell.imageView.superview == cell.contentView,往cell里面加内容都要放到contentView

## 常见属性
    - cell的属性
    ```obj-c
    cell.textLabel.text = @"5345345";
    cell.imageView.image = [UIImage imageNamed:@"173890255948"];
    // 取消选中的样式
    cell.selectionStyle = UITableViewCellSelectionStyleNone;
    
    // 设置选中的背景色
    UIView *selectedBackgroundView = [[UIView alloc] init];
    selectedBackgroundView.backgroundColor = [UIColor redColor];
    cell.selectedBackgroundView = selectedBackgroundView;
    
    // 设置默认的背景色 1
    cell.backgroundColor = [UIColor blueColor];
    
    // 设置默认的背景色 2
    UIView *backgroundView = [[UIView alloc] init];
    backgroundView.backgroundColor = [UIColor greenColor];
    cell.backgroundView = backgroundView;
    
    // 设置指示器
     cell.accessoryType = UITableViewCellAccessoryDisclosureIndicator;
     //可以自定义view，例如设置一个图片view
//    cell.accessoryView =  [[UIImageView alloc] init];
    ```
    
- xib自定义cell
  - 
  
```obj-c
//创建 xxxCell.xib
//在 xxxCell.xib中拖一个Cell控件出来
//给 这个cell 添加 id

//在代理方法里
- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath {
    static NSString *ID = @"xxx";
    xxxCell *cell = [tableView dequeueReusableCellWithIdentifier:ID];
    if(cell == nil){
        [[[NSBundle mainBundle]loadNibNamed:NSStringFromClass([xxxCell class]) owner:nil options:nil] lastObject];
    }
    return cell;
}
```
- xib自定义cell
    - 1.创建一个继承自UITableViewCell的子类，比如XMGDealCell<br>
    - 2.创建一个xib文件（文件名建议跟cell的类名一样）,比如XMGDealCell.xib
        - 拖拽一个UITableViewCell出来
        - 修改cell的class为XMGDealCell
        - 设置cell的重用标识
        - 往cell中添加需要用到的子控件
    - 3.在控制器中
        - 利用registerNib...方法注册xib文件
        - 利用重用标识找到cell(如果没有注册xib文件，就需要手动去加载xib文件)
        -给cell传递模型数据<br>
    - 4.在XMGDealCell中
        - 将xib中的子控件连线到类扩展中
        - 需要提供一个模型属性，重写模型的set方法，在这个方法中设置模型数据到子控件中
        - 也可以将创建获得cell的代码封装起来 (比如自定义一个cellWithTableView:方法)
        
- 代码自定义cell
    - 1.创建一个继承自UITableViewCell的子类，比如XMGDealCell
        - 在initWithStyle:reuseIdentifier:方法中
            - 添加子控件
            - 设置子控件的初始化属性（比如文字颜色、字体等）
        - 在layoutSubviews方法中设置子控件的frame
        - 需要提供一个模型属性，重写模型的set方法，在这个方法中设置模型数据到子控件中
    - 2.在控制器中
        - 利用registerClass...方法注册XMGDealCell类
        - 利用重用标识找到cell（如果没有注册类，就需要手动创建cell）
        - 给cell传递模型数据
        - 也可以将创建获得cell的代码封装起来(比如自定义一个cellWithTableView:方法)




























 

