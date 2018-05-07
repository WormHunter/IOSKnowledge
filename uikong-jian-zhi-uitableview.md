## tableView 性能优化 - cell的循环利用方式
- 定义一个全局变量
```c
// 定义重用标识
NSString *ID = @"hero";
```
- 注册某个便是对应cell类型
```c
[self.tableView registerClass:[UITableViewCell class] forCellReuseIdentifier:ID];
```
- 在数据方法中返回cell
    ```c
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



