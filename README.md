# Chris Blog - 个人博客系统

一个现代化的个人博客系统，采用前后端分离架构，提供文章发布、音乐播放、管理后台等功能。

## 项目概述

本项目是一个完整的个人博客系统，包含前端展示和后端API服务。前端基于Vue 3开发，后端使用Flask框架构建RESTful API。

## 技术栈

### 前端

- **框架**: Vue 3 (使用Composition API)
- **构建工具**: Vite
- **依赖管理**: npm
- **其他库**: crypto-js

### 后端

- **框架**: Flask
- **数据库**: MySQL (通过SQLAlchemy ORM)
- **认证**: JWT (Flask-JWT-Extended)
- **API文档**: RESTful API
- **环境变量**: python-dotenv

## 功能特点

- 文章管理：发布、编辑、删除文章
- 文章状态：已发布、待审核、已拒绝
- 音乐播放器：支持播放本地音乐文件
- 管理后台：文章管理、用户认证
- 投稿功能：允许用户提交文章
- 响应式设计：适配不同设备屏幕

## 目录结构

```
├── src/                  # 前端源代码
│   ├── components/       # Vue组件
│   ├── services/         # API服务
│   ├── utils/            # 工具函数
│   ├── App.vue           # 主应用组件
│   └── main.js           # 应用入口
├── public/               # 静态资源
│   ├── music/            # 音乐文件
│   └── articles.json     # 文章数据
├── chris-blog-backend/   # 后端源代码
│   ├── app/              # Flask应用
│   │   ├── api/          # API路由
│   │   └── models.py     # 数据模型
│   ├── config.py         # 配置文件
│   └── app.py            # 应用入口
└── articles/             # 文章内容
    ├── published/        # 已发布文章
    ├── pending/          # 待审核文章
    └── rejected/         # 已拒绝文章
```

## 安装与使用

### 前端

1. 安装依赖

```bash
npm install
```

2. 开发模式运行

```bash
npm run dev
```

3. 构建生产版本

```bash
npm run build
```

4. 预览生产版本

```bash
npm run preview
```

### 后端

1. 创建虚拟环境（推荐）

```bash
python -m venv .venv
```

2. 激活虚拟环境

- Windows:
```bash
.venv\Scripts\activate
```

- Linux/Mac:
```bash
source .venv/bin/activate
```

3. 安装依赖

```bash
pip install -r requirements.txt
```

4. 配置环境变量

创建 `.env` 文件在 `chris-blog-backend` 目录下，添加以下内容：

```
SECRET_KEY=your-secret-key
JWT_SECRET_KEY=your-jwt-secret-key
DEV_DATABASE_URL=mysql+pymysql://username:password@localhost/chris_blog
```

5. 初始化数据库

```bash
flask db init
flask db migrate
flask db upgrade
```

6. 运行开发服务器

```bash
python run.py
```

## 部署

### 前端部署

1. 构建生产版本

```bash
npm run build
```

2. 将 `dist` 目录部署到您的Web服务器

### 后端部署

1. 使用 Gunicorn 运行（生产环境）

```bash
gunicorn -w 4 -b 0.0.0.0:5000 run:app
```

2. 配置反向代理（Nginx示例）

```nginx
server {
    listen 80;
    server_name yourdomain.com;

    location / {
        proxy_pass http://127.0.0.1:5000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

## API文档

### 文章API

- `GET /api/articles` - 获取所有已发布文章
- `GET /api/articles/all` - 获取所有状态的文章（需要认证）
- `GET /api/articles/<id>` - 获取单篇文章
- `POST /api/articles` - 创建新文章（需要认证）
- `PUT /api/articles/<id>` - 更新文章（需要认证）

### 认证API

- `POST /api/auth/login` - 用户登录
- `POST /api/auth/refresh` - 刷新访问令牌

### 音乐API

- `GET /api/music` - 获取音乐列表

## 贡献指南

1. Fork 本仓库
2. 创建您的特性分支 (`git checkout -b feature/amazing-feature`)
3. 提交您的更改 (`git commit -m 'Add some amazing feature'`)
4. 推送到分支 (`git push origin feature/amazing-feature`)
5. 打开一个 Pull Request

## 许可证

[MIT](LICENSE)

## 联系方式

如有任何问题或建议，请通过以下方式联系：

- 项目维护者：Chris
- 电子邮件：Chris@gbkgov.cn
- 博客：[https://gbkgov.cn](https://gbkgov.cn)
