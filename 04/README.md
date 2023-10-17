# 第 4 章 创建有意义的测试数据

|本期版本|上期版本
|:---:|:---:|
`Tue Oct 17 11:02:07 CST 2023` | -

## 4.4 使用序列生成唯一的数据

* 序列在需要保证唯一性的属 性中插入一个计数器，每使用预构件创建一个对象，计数器便自增一

```ruby
sequence(:email) { |n| "tester#{n}@example.com" }
```


## 4.5 预构件中的关联

```ruby
factory :user, aliases: [:owner] do
end
```

```ruby
factory :note do
	message "my important note."
	association :project
	user { project.owner }
end
```

## 4.6 避免预构件中出现重复

* 同种类型的数据可以定义多个预构件

```ruby
factory :project do
end

factory :projecrt_due_yesterday, class: Project do
end
```
* 使用预构件继承，只修改有变化的属性

```ruby
factory :project do
	factory :projecrt_due_yesterday do
	end
end
```

* 减少重复的另一个技术是使用性状（trait）构建测试数据，定义有变化的属性

```ruby
trait :due_yesterday do
	due_on 1.day.ago
end

FactoryBot.create(:project, :due_yesterday)
```

## 4.7 回调

```ruby
after(:create) { |project| create_list(:note, 5, project: project) }
```