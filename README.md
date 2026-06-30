# Instagram MERN Web

Instagram 全栈克隆项目，基于 MERN 技术栈和 Socket.IO 实现的社交媒体应用。

## 项目简介

本项目是一个功能完整的 Instagram 克隆应用，实现了 Instagram 的核心功能，包括用户管理、帖子发布、点赞评论、私信聊天、关注系统等。采用前后端分离架构，使用 MongoDB 作为数据库，Express 作为后端服务，React 作为前端框架，通过 Socket.IO 实现实时通信功能。

## 技术架构

### 前端技术栈
- **React 17.0.2** - 核心前端框架
- **Redux + Redux Thunk** - 状态管理
- **React Router 6** - 路由管理
- **Material UI (MUI)** - UI 组件库
- **Tailwind CSS** - CSS 框架
- **Axios** - HTTP 请求库
- **Socket.IO Client** - 实时通信
- **React Toastify** - 消息提示
- **Emoji Mart** - 表情选择器
- **React Infinite Scroll Component** - 无限滚动
- **React Helmet Async** - SEO 管理

### 后端技术栈
- **Node.js** - 运行环境
- **Express.js 4.17** - Web 框架
- **MongoDB + Mongoose 6.1** - 数据库
- **Socket.IO 4.4** - 实时通信服务
- **JWT (jsonwebtoken)** - 身份认证
- **Bcrypt** - 密码加密
- **Multer + AWS S3** - 文件上传和云存储
- **SendGrid** - 邮件服务
- **Cookie Parser** - Cookie 处理

### 数据库设计
- **User Model**: 用户信息，包括姓名、邮箱、用户名、头像、个人简介、网站、帖子列表、收藏列表、粉丝、关注列表等
- **Post Model**: 帖子信息，包括标题、图片、发布者、点赞列表、评论列表、收藏者列表、创建时间等
- **Chat Model**: 聊天会话，包括参与者列表、最新消息等
- **Message Model**: 消息记录，包括发送者、聊天ID、内容、时间等

## 项目结构

```
instagram-mern-web/
├── backend/                 # 后端代码
│   ├── config/             # 配置文件
│   │   ├── config.env      # 环境变量配置
│   │   ├── database.js     # 数据库连接配置
│   ├── controllers/        # 控制器（业务逻辑）
│   │   ├── userController.js    # 用户相关控制器
│   │   ├── postController.js    # 帖子相关控制器
│   │   ├── chatController.js    # 聊天相关控制器
│   │   ├── messageController.js # 消息相关控制器
│   ├── models/             # 数据模型
│   │   ├── userModel.js
│   │   ├── postModel.js
│   │   ├── chatModel.js
│   │   ├── messageModel.js
│   ├── routes/             # 路由定义
│   │   ├── userRoute.js
│   │   ├── postRoute.js
│   │   ├── chatRoute.js
│   │   ├── messageRoute.js
│   ├── middlewares/        # 中间件
│   │   ├── auth.js         # 认证中间件
│   │   ├── catchAsync.js   # 异步错误处理
│   │   ├── error.js        # 错误处理中间件
│   ├── utils/              # 工具函数
│   │   ├── awsFunctions.js     # AWS S3 文件操作
│   │   ├── sendCookie.js       # Cookie 处理
│   │   ├── sendEmail.js        # 邮件发送
│   │   ├── errorHandler.js     # 错误处理
│   ├── app.js              # Express 应用配置
│
├── frontend/               # 前端代码
│   ├── public/             # 静态资源
│   ├── src/                # 源代码
│   │   ├── actions/        # Redux actions
│   │   │   ├── userAction.js
│   │   │   ├── postAction.js
│   │   │   ├── chatAction.js
│   │   │   ├── messageAction.js
│   │   │   ├── reducers/       # Redux reducers
│   │   │   ├── constants/      # 常量定义
│   │   │   ├── components/     # React 组件
│   │   │   │   ├── Home/       # 首页相关组件
│   │   │   │   │   ├── Home.jsx
│   │   │   │   │   ├── PostItem.jsx
│   │   │   │   │   ├── PostsContainer.jsx
│   │   │   │   │   ├── StoriesContainer.jsx
│   │   │   │   │   ├── Sidebar/   # 侧边栏
│   │   │   │   ├── Navbar/     # 导航栏组件
│   │   │   │   │   ├── Header.jsx
│   │   │   │   │   ├── NewPost.jsx
│   │   │   │   │   ├── SearchBar/
│   │   │   │   │   ├── Notifications.jsx
│   │   │   │   ├── User/       # 用户相关组件
│   │   │   │   │   ├── Auth.jsx
│   │   │   │   │   ├── Login.jsx
│   │   │   │   │   ├── SignUp.jsx
│   │   │   │   │   ├── Profile.jsx
│   │   │   │   │   ├── ForgotPassword.jsx
│   │   │   │   │   ├── ResetPassword.jsx
│   │   │   │   │   ├── Update/    # 更新相关
│   │   │   │   │   │   ├── Update.jsx
│   │   │   │   │   │   ├── UpdateProfile.jsx
│   │   │   │   │   │   ├── UpdatePassword.jsx
│   │   │   │   │   ├── Posts/     # 用户帖子
│   │   │   │   ├── Chats/      # 聊天相关组件
│   │   │   │   │   ├── Inbox.jsx
│   │   │   │   │   ├── Message.jsx
│   │   │   │   │   ├── Sidebar.jsx
│   │   │   │   │   ├── ChatListItem.jsx
│   │   │   │   │   ├── SearchModal.jsx
│   │   │   │   ├── Layouts/    # 布局组件
│   │   │   │   │   ├── MetaData.jsx
│   │   │   │   │   ├── SpinLoader.jsx
│   │   │   │   │   ├── BackdropLoader.jsx
│   │   │   │   │   ├── SkeletonPost.jsx
│   │   │   │   │   ├── UsersDialog.jsx
│   │   │   │   ├── Errors/     # 错误页面
│   │   │   │   │   ├── NotFound.jsx
│   │   │   ├── Routes/         # 路由配置
│   │   │   │   ├── PrivateRoute.jsx
│   │   │   ├── App.js          # 应用入口
│   │   │   ├── index.js        # 渲染入口
│   │   │   ├── store.js        # Redux store 配置
│   │   │   ├── utils/          # 工具函数
│   │   │   ├── assests/        # 静态资源（图片等）
│   │   ├── package.json        # 前端依赖配置
│   │   ├── tailwind.config.js  # Tailwind 配置
│   │   ├── postcss.config.js   # PostCSS 配置
│  
├── server.js                # 服务器入口文件（含 Socket.IO）
├── package.json             # 后端依赖配置
├── Procfile                 # Heroku 部署配置
├── vercel.json              # Vercel 部署配置
├── .gitignore               # Git 忽略配置
└── LICENSE.md               # 许可证文件
```

## 功能模块

### 1. 用户认证与管理模块

**页面组件**:
- Login.jsx - 登录页面
- SignUp.jsx - 注册页面
- ForgotPassword.jsx - 忘记密码页面
- ResetPassword.jsx - 重置密码页面
- UpdateProfile.jsx - 更新个人资料页面
- UpdatePassword.jsx - 更新密码页面

**API 接口**:
- `POST /api/v1/signup` - 用户注册（支持头像上传）
- `POST /api/v1/login` - 用户登录（支持邮箱或用户名登录）
- `GET /api/v1/logout` - 用户注销
- `GET /api/v1/me` - 获取当前用户信息
- `DELETE /api/v1/me` - 删除用户账号
- `GET /api/v1/user/:username` - 获取指定用户详情（含帖子、粉丝、关注）
- `GET /api/v1/userdetails/:id` - 通过 ID 获取用户基本信息
- `GET /api/v1/users/suggested` - 获取推荐用户列表
- `GET /api/v1/users` - 搜索用户（按关键词）
- `GET /api/v1/follow/:id` - 关注/取消关注用户
- `PUT /api/v1/update/profile` - 更新用户资料（支持头像更新）
- `PUT /api/v1/update/password` - 更新密码
- `POST /api/v1/password/forgot` - 发送忘记密码邮件
- `PUT /api/v1/password/reset/:token` - 重置密码

**功能特性**:
- JWT 身份认证，支持 Cookie 存储
- 密码使用 Bcrypt 加密存储
- 支持邮箱和用户名双方式登录
- SendGrid 集成，支持密码重置邮件
- AWS S3 云存储用户头像
- 完整的用户资料管理（姓名、简介、网站、头像）

### 2. 帖子管理模块

**页面组件**:
- Home.jsx - 首页（展示关注用户的帖子）
- PostsContainer.jsx - 帖子容器（无限滚动）
- PostItem.jsx - 单个帖子展示组件
- NewPost.jsx - 发布新帖子
- Profile.jsx - 用户个人主页（展示个人帖子）

**API 接口**:
- `POST /api/v1/post/new` - 发布新帖子（支持图片上传）
- `GET /api/v1/posts?page={page}` - 获取关注用户的帖子（分页）
- `GET /api/v1/posts/all` - 获取所有帖子
- `GET /api/v1/post/detail/:id` - 获取帖子详情
- `GET /api/v1/post/:id` - 点赞/取消点赞帖子
- `POST /api/v1/post/:id` - 收藏/取消收藏帖子
- `PUT /api/v1/post/:id` - 更新帖子标题
- `DELETE /api/v1/post/:id` - 删除帖子
- `POST /api/v1/post/comment/:id` - 发表评论

**功能特性**:
- 无限滚动加载帖子
- 双击快速点赞功能
- 帖子评论和互动
- 收藏/取消收藏帖子
- 编辑和删除帖子
- AWS S3 云存储帖子图片
- 自动关联发布者信息

### 3. 聊天与消息模块

**页面组件**:
- Inbox.jsx - 聊天列表页面
- Sidebar.jsx - 聊天侧边栏
- Message.jsx - 消息组件
- ChatListItem.jsx - 聊天列表项
- SearchModal.jsx - 搜索用户发起聊天

**API 接口**:
- `POST /api/v1/newChat` - 创建新聊天会话
- `GET /api/v1/chats` - 获取所有聊天列表
- `POST /api/v1/newMessage` - 发送新消息
- `GET /api/v1/messages/:chatId` - 获取聊天消息记录

**功能特性**:
- 实时消息传递（Socket.IO）
- 自动检测已存在的聊天会话
- 搜索用户快速发起聊天
- 最新消息预览
- 聊天列表按最新消息排序

### 4. 搜索与发现模块

**页面组件**:
- SearchBox.jsx - 搜索用户组件
- UserListItem.jsx - 用户列表项
- Sidebar.jsx - 推荐用户侧边栏

**功能特性**:
- 搜索用户（按姓名或用户名）
- 推荐用户列表（非当前粉丝）
- 快速关注功能

### 5. 通知与互动模块

**功能特性**:
- 点赞通知
- 评论通知
- 关注通知
- Socket.IO 实时推送

### 6. 布局与通用组件

**组件列表**:
- Header.jsx - 导航栏（含搜索、通知、新建帖子）
- PrivateRoute.jsx - 私有路由保护
- MetaData.jsx - SEO 元数据管理
- SpinLoader.jsx - 加载动画
- BackdropLoader.jsx - 背景加载动画
- SkeletonPost.jsx - 帖子骨架屏
- UsersDialog.jsx - 用户列表对话框
- NotFound.jsx - 404 错误页面

## 启动方式

### 环境要求
- Node.js >= 14.x
- MongoDB >= 4.x
- npm 或 yarn

### 安装步骤

1. **克隆项目**
```bash
git clone https://github.com/jigar-sable/instagram-mern.git
cd instagram-mern-web
```

2. **安装后端依赖**
```bash
npm install
```

3. **配置环境变量**
复制 `backend/config/config.env.example` 为 `backend/config/config.env`，并填写以下配置：

```env
PORT=4000
MONGO_URI=mongodb://localhost:27017/Instagram

JWT_SECRET=your_jwt_secret_key
JWT_EXPIRE=7d
COOKIE_EXPIRE=5

SENDGRID_API_KEY=your_sendgrid_api_key
SENDGRID_MAIL=your_email@example.com
SENDGRID_RESET_TEMPLATEID=your_template_id

AWS_BUCKET_NAME=your_s3_bucket_name
AWS_BUCKET_REGION=your_region
AWS_IAM_USER_KEY=your_access_key
AWS_IAM_USER_SECRET=your_secret_key

NODE_ENV=development
```

4. **安装前端依赖**
```bash
cd frontend
npm install
cd ..
```

5. **启动 MongoDB**
确保 MongoDB 服务已启动。

### 开发模式运行

**后端服务（开发模式）**:
```bash
npm run dev
```
后端服务运行在 http://localhost:4000

**前端服务（开发模式）**:
```bash
cd frontend
npm start
```
前端服务运行在 http://localhost:3000

### 生产模式运行

**构建前端**:
```bash
cd frontend
npm run build
cd ..
```

**启动后端服务（生产模式）**:
```bash
npm start
```

### 部署配置

**Heroku 部署**:
项目已配置 Procfile 和 heroku-postbuild 脚本，部署时会自动构建前端：
```
web: node server.js
```

**Vercel 部署**:
项目已配置 vercel.json 文件，支持 Vercel 平台部署。

## 数据库配置

### MongoDB 连接
在 `backend/config/database.js` 中配置 MongoDB 连接：

```javascript
mongoose.connect(process.env.MONGO_URI, {
    useNewUrlParser: true,
    useUnifiedTopology: true,
});
```

### 数据模型
- User: 用户信息模型
- Post: 帖子模型
- Chat: 聊天会话模型
- Message: 消息模型

## API 文档

所有 API 接口遵循 RESTful 规范，返回 JSON 格式数据。

### 认证方式
使用 JWT 进行身份认证，Token 存储在 Cookie 中。

### 错误处理
统一错误处理中间件，返回标准错误格式：
```json
{
  "success": false,
  "message": "错误信息"
}
```

### 成功响应
标准成功响应格式：
```json
{
  "success": true,
  "data": {}
}
```

## 开发注意事项

1. **环境变量**: 请确保在生产环境中使用正确的环境变量配置
2. **AWS S3**: 需要配置 AWS S3 bucket 和 IAM 用户权限
3. **SendGrid**: 需要配置 SendGrid API key 和邮件模板
4. **MongoDB**: 建议使用 MongoDB Atlas 云服务或本地 MongoDB 服务
5. **CORS**: Socket.IO 配置了 CORS，支持跨域通信

## 许可证

本项目采用 ISC 许可证，详见 LICENSE.md 文件。