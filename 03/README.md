# 第 3 章 模型测试

|本期版本|上期版本
|:---:|:---:|
`Tue Oct 17 10:47:40 CST 2023` | -


## 3.3 RSpec 的句法


```ruby
expect(user).to be_valid
expect(user.valid?).to eq(true)
```


## 3.4 测试数据验证

```ruby
user.valid?
expect(user.errors[:first_name]).to include("can't be blank")
```

## 3.9 使用 describe、context、before 和 after 去除重复

* 其实，严格来说，describe 和 context 是可以互换的，但我倾向于这么用：describe 用来表示 需要实现的功能，而 context 针对该功能不同的情况
* `@TODO` - 因为 RSpec 会自行清理数据库，所以我很 少使用 after

* `each`、`eaxmple`: 每个测试用例之前运行
* `all`、`context`: 在快中的所有测试用例之前运行
* `suite`: 在整个测试组件之前运行