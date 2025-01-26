# MyUrls-Workers
CareyWang/MyUrls 短链接 Cloudflare Pages 版本

## 技术栈

### 前端
- Vue.js 2.6.11 - 渐进式 JavaScript 框架
- Element UI 2.13.0 - 基于 Vue 的组件库
- Axios 0.19.2 - HTTP 客户端
- Vue-clipboard2 0.3.1 - 剪贴板功能

### 后端
- Cloudflare Pages - 静态网站托管服务
- Cloudflare Workers - Serverless 计算平台
- Cloudflare KV - 键值存储数据库

## 部署步骤

1. Fork 本仓库

2. 在 Cloudflare Pages 中创建新项目
   - 连接到您的 GitHub 仓库
   - 构建设置：
     - 构建命令：不需要
     - 输出目录：/

3. 创建 KV 命名空间
   - 在 Cloudflare 控制台创建 KV 命名空间，命名为 "LINKS"
   - 在 Pages 项目设置中绑定 KV：
     - 变量名：LINKS
     - KV 命名空间：选择刚创建的命名空间

4. 完成部署后即可使用

## API 说明

### 创建短链接
- 端点：`POST /short`
- 请求体：
  ```json
  {
    "longUrl": "Base64编码的长链接",
    "shortKey": "可选的自定义后缀"
  }
  ```
- 响应：
  ```json
  {
    "Code": 1,
    "ShortUrl": "生成的短链接"
  }
  ```

### 访问短链接
- 端点：`GET /:shortKey`
- 响应：301重定向到原始链接
