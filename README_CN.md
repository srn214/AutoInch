# AutoInch - 优雅的iPhone等比例/全尺寸精准适配工具

![Swift](https://img.shields.io/badge/Swift-4.2-orange.svg)

## 特性

- [x] 数值类型快速转换
- [x] Storyboard 等比例适配支持 
- [x] Xib 等比例适配支持 
- [x] 自定义计算处理
- [x] 各个屏幕尺寸快速匹配


## 安装

AutoInch 仅支持 CocoaPods 方式.

**Podfile**

```ruby
pod 'AutoInch'
```

## 使用

首先导入

```swift
import AutoInch
```

下面是一些简单示例. 支持所有设备和模拟器:

### Auto


AutoLayout (SnapKit): 

```swift
private func setupLayout() {
    cardView.snp.makeConstraints { (make) in
	make.top.equalTo(16.auto())
	make.left.right.equalToSuperview().inset(15.auto())
	make.bottom.equalTo(-26.auto())
    }
	
    lineView.snp.makeConstraints { (make) in
	make.left.right.equalToSuperview().inset(15.auto())
	make.top.equalTo(titleLabel.snp.bottom)
	make.height.equalTo(1)
    }
        
    titleLabel.snp.makeConstraints { (make) in
        make.top.equalToSuperview()
        make.left.equalTo(15.auto())
        make.height.equalTo(48.auto())
    }
        
    stateLabel.snp.makeConstraints { (make) in
        make.top.equalTo(lineView).offset(10.auto())
        make.left.equalTo(15.auto())
        make.height.equalTo(15.auto())
    }
}
```

属性设置 (Then):

```swift
private lazy var cardView = UIView().then {
    $0.cornerRadius = 6.auto()
    $0.backgroundColor = .white
}

private lazy var lineView = UIView().then {
    $0.backgroundColor = .hex("000000", alpha: 0.05)
}

private lazy var titleLabel = UILabel().then {
    $0.textColor = .black
    $0.font = .systemFont(ofSize: 20.auto(), weight: .medium)
}

private lazy var stateLabel = UILabel().then {
    $0.textColor = .gray
    $0.font = .systemFont(ofSize: 12.auto(), weight: .medium)
}
```

Storyboard / Xib:

![约束](Resources/Storyboard%20Constraint.png)
![UILabel 字体大小](Resources/Storyboard%20Label%20Font.png)

### Inch

例子

```swift
// default other screen numberOfLines = 0
// 3.5 inches screen numberOfLines = 1
// 4.0 inches screen numberOfLines = 2
label.numberOfLines = 0.i35(1).i40(2)
```

全部

```swift
print("this is " +
    "default"
    .i35("3.5 inches (iPhone 4, 4s)")
    .i40("3.5 inches (iPhone 5, 5s, SE)")
    .i47("3.5 inches (iPhone 6, 7, 8)")
    .i55("3.5 inches (iPhone 6, 7, 8 Plus)")
    .ifull("full screen (iPhone X, Xs, XsMax)")
    .i58full("5.8 inches (iPhone X, Xs)")
    .i61full("6.1 inches (iPhone XR)")
    .i65full("6.5 inches (iPhone XsMax)")
)
```


## 截屏

![TikTok 1](Resources/Storyboard%20TikTok%20Demo1.jpg)

![TikTok 2](Resources/Storyboard%20TikTok%20Demo2.jpg)

## 贡献

如果您需要实现特定功能或遇到错误，请打开issue。
如果您自己扩展了AutoInch的功能并希望其他人也使用它，请提交拉取请求。

## 协议

AutoInch 使用 GPL 协议. 有关更多信息，请参阅[LICENSE](LICENSE)文件.


>### [相关文章 Inch](https://www.jianshu.com/p/d2c09cb65ef7)
>### [相关文章 Auto](https://www.jianshu.com/p/e0e12206e0c7)
>### [相关文章 Auto](https://www.jianshu.com/p/48c67d0c95b6)
