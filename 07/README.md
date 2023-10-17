# 第 7 章 使用请求测试测试 API

|本期版本|上期版本
|:---:|:---:|
`Tue Oct 17 15:14:57 CST 2023` | -

## 7.1 请求测试 vs. 功能测试

* 对 RSpec 来说，这种专门针 对 API 的测试最好放在 `spec/requests` 目录中，与前面编写的功能测试分开

## 7.2 测试 GET 请求

```bash
bin/rails g rspec:request projects_api
```

```ruby
RSpec.describe "ProjectsApis", type: :request do
	get projects_apis_path
	expect(response).to have_http_status(200)
end
```