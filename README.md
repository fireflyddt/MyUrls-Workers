# MyUrls-Workers

 [CareyWang/MyUrls](https://github.com/CareyWang/MyUrls) 短链接 Cloudflare Workers & Cloudflare Pages 版本

支持 **订阅转换前端** [CareyWang/sub-web](https://github.com/CareyWang/sub-web) 使用

## 技术栈

### 前端

- **Vue.js 2.6.11** - 渐进式 JavaScript 框架
- **Element UI 2.13.0** - 基于 Vue 的组件库
- **jQuery 3.6.0** - HTTP 客户端
- **Vue-clipboard2 0.3.1** - 剪贴板功能

### 后端

- **Cloudflare Pages** - 静态网站托管服务
- **Cloudflare Workers** - Serverless 计算平台
- **Cloudflare KV** - 键值存储数据库

## 部署方法 (Pages 和 Workers 任选一个)

 ### Cloudflare Pages
  
  1. Fork 本仓库
  2. 在 Cloudflare Pages 中创建新项目
  
  - 连接到您的 GitHub 仓库
  - 构建设置：
    - 构建命令：不需要
    - 输出目录：/
  
  3. 创建 KV 命名空间

  ![e2a62cb147dedf73f76b3d42b3357df](https://github.com/user-attachments/assets/48079ebe-036b-49cc-9d32-c2bf83511c67)
  ![e16e83362b97668fba0d9ec1e100585](https://github.com/user-attachments/assets/2f9ddec3-6ad0-4a11-a1b7-d2c5287ecfb6)

  - 在 Cloudflare 控制台创建 KV 命名空间，命名为 "`LINKS`"
  - 在 Pages 项目设置中绑定 KV：
    - 变量名：`LINKS`
    - KV 命名空间：选择刚创建的命名空间
  ![fe25d11f7ca80cd4ea987d069c81f3f](https://github.com/user-attachments/assets/b15b2b50-b8c5-4ce1-a789-184c022709a6)

  4. 部署后 请重新部署后 即可使用 Pages必须重重试部署 否则无法使用KV空间
 ![49f211b9addcf51a324e8ec6e0f0965](https://github.com/user-attachments/assets/63b64cfa-9d2d-4a64-a2f5-8f1403f6d0d6)

 ### Cloudflare Workers
  
  1. 打开 [_workers.js](https://github.com/kiko923/MyUrls-Workers/blob/main/_workers.js) 文件
  2. 复制全部内容
  3. 创建 Cloudflare Workers 点击 编辑代码 粘贴至代码框内 创建 KV 命名空间
  
  ![e2a62cb147dedf73f76b3d42b3357df](https://github.com/user-attachments/assets/48079ebe-036b-49cc-9d32-c2bf83511c67)
  ![e16e83362b97668fba0d9ec1e100585](https://github.com/user-attachments/assets/2f9ddec3-6ad0-4a11-a1b7-d2c5287ecfb6)
  - 在 Cloudflare 控制台创建 KV 命名空间，命名为 "`LINKS`"
  - 在 Workers 项目设置中绑定 KV：
    - 变量名：`LINKS`
    - KV 命名空间：选择刚创建的命名空间
  ![fe25d11f7ca80cd4ea987d069c81f3f](https://github.com/user-attachments/assets/b15b2b50-b8c5-4ce1-a789-184c022709a6)
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


