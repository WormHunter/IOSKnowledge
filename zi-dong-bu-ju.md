##vfl 已不适用


##原生
NSLayoutConstraint
需要设置(现在就不知道需不需要了)
xxxView.translatesAutoresizingMaskIntoConstraints = NO;

##Masonry

make.edges.mas_equalTo(self.view).insets(UIEdgeInsetsMake(50, 50, 50, 50));

// 宽度高度约束
make.size.equalTo([NSValue valueWithCGSize:CGSizeMake(100, 100)]);