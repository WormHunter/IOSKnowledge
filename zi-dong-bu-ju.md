##vfl 已不适用


##原生
NSLayoutConstraint
需要设置(现在就不知道需不需要了)
xxxView.translatesAutoresizingMaskIntoConstraints = NO;

##Masonry
// 右边
make.right.mas_equalTo(self.view).offset(-20);

make.edges.mas_equalTo(self.view).insets(UIEdgeInsetsMake(50, 50, 50, 50));

make.height.mas_equalTo(self.view).multipliedBy(0.5);

// 宽度高度约束
make.size.equalTo([NSValue valueWithCGSize:CGSizeMake(100, 100)]);