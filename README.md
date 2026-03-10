# Web Claude Code

通过网页远程调用 Claude Code 的服务。

## 功能特性

- 🌐 网页版 Claude Code 对话界面
- 📤 支持上传图片、视频、文件
- ⚡ 流式输出响应
- 💾 会话历史保存
- 🎨 仿 Claude 官网 UI 设计

## 快速开始

### 本地运行

```bash
# 安装依赖
npm install

# 启动服务
npm start
```

访问 http://localhost:3001

### 服务器部署

```bash
# 1. 安装依赖
npm install

# 2. 配置环境变量（可选）
export ANTHROPIC_AUTH_TOKEN=your_api_key
export ANTHROPIC_BASE_URL=https://api.minimaxi.com/anthropic
export ANTHROPIC_MODEL=MiniMax-M2.5

# 3. 启动服务
npm start
```

### Nginx 配置

```nginx
server {
    listen 80;
    server_name your-domain.com;

    location / {
        proxy_pass http://127.0.0.1:3001;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
    }
}
```

## API

### 对话

```bash
POST /api/chat
Content-Type: multipart/form-data

# 参数
message: string (必填)
sessionId: string (可选)
files: File[] (可选)
```

### 会话管理

```bash
# 创建会话
POST /api/sessions

# 获取会话历史
GET /api/sessions/:sessionId

# 删除会话
DELETE /api/sessions/:sessionId
```

## 技术栈

- Node.js + Express
- SSE (Server-Sent Events) 流式输出
- Claude Code CLI
- MiniMax API

## License

MIT
