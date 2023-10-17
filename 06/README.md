# 第 6 章 使用功能测试测试用户界面

|本期版本|上期版本
|:---:|:---:|
`Tue Oct 17 15:07:53 CST 2023` | -

## 6.1 为什么要编写功能测试？

* 功能测试更底层一些，而且能模拟真实用户与应用交互的过程
* 从 Rails 5.1 起，Rails 框架对这种测试提供了内建支持，将其称为系统测试（system testing）

## 6.3 一个简单的功能测试

```bash
bin/rails generate rspec:feature projects
```

```ruby
require 'rails_helper'
RSpec.feature "Projects", type: :feature do
	scenario "user creates a new project" do
	
	end
end
```

## 6.5 调试功能测试

* 默认情况下，Capybara 使用无界面（headless）浏览器运行测试

## 6.6 测试 JavaScript 交互

* 这个驱动是 Rack::Test，它速度快、可信赖，但是不支持 JavaScript。
* 我们将使用 Rails 5.1 自带的 selenium-webdriver gem，这也是 Capybara 默认的 JavaScript 驱动。

```ruby
scenario "user toggles a task", js: true do
end
```

## 6.7 无界面驱动

* `@TODO`

