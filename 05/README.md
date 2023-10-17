# 第 5 章 控制器测试

|本期版本|上期版本
|:---:|:---:|
`Tue Oct 17 11:17:52 CST 2023` | -

* Rails 和 RSpec 团队都建议换掉或删除应用的控制器测试（这是我们熟知的功能测试），转而直接测试 模型（单元测试），或者使用更高层级的集成测试

## 5.1 控制器测试基础

```bash
bin/rails g rspec:controller home
```

```ruby
require 'rails_helper'

RSpec.describe HomeController, type: :controller do
	it "responds successfully" do
		get :index
		expect(response).to be_success
	end
end
```

* `response` 对象包含应用返回给浏览器的所有数据
* `be_success` 检查响应的状态是成 功（200 响应）还是失败（例如 500 异常）
* `have_http_status "200"` 还可以检查响应的具体状态码



## 5.2 要验证身份的控制器测试

**Devise**

> `spec/rails_helper.rb`

```ruby
config.include Devise::Test::ControllerHelpers, type: :controller
```

```ruby
def sign_in(user)
	cookies[:auth_token] = user.auth_token
end
```
* `redirect_to`


## 5.3 测试用户输入

```ruby
FactoryBot.attributes_for(:project)
```

```ruby
expect{
	delete :destroy, params: { id: @project.id }
}.to change(@user.projects, :count).by(-1)
```

## 5.5 处理非 HTML 输出

```ruby
get :show, format: :json
expect(response.content_type).to eq "application/json"
```