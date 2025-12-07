/backend
├── config/             # 统一配置 (DB credentials, Ports, OSS keys)
├── node_modules/
├── src/
│   ├── common/         # 公共工具和常量 (如 API 响应格式、错误代码)
│   ├── middleware/     # 中间件
│   │   ├── auth.js     # JWT 鉴权中间件 (Backend A 核心)
│   │   └── sensitiveFilter.js # 敏感词过滤 (Backend B 核心)
│   ├── models/         # 数据库模型定义 (Backend A/B 共享)
│   │   ├── User.js     # 用户模型
│   │   ├── Content.js  # 内容模型
│   │   └── ...
│   ├── modules/        # 业务逻辑模块 (按业务分工)
│   │   ├── user/       # 用户、认证、好友 (Backend A)
│   │   │   ├── user.controller.js
│   │   │   ├── user.service.js
│   │   │   └── user.router.js
│   │   ├── content/    # 内容、评论、标签 (Backend B)
│   │   │   ├── content.controller.js
│   │   │   ├── content.service.js
│   │   │   └── content.router.js
│   │   └── admin/      # 管理接口、统计分析 (Backend C)
│   │       ├── admin.controller.js # 用户/内容管理
│   │       └── stats.service.js  # 统计聚合查询
│   └── app.js          # 应用入口文件 (路由加载)
├── tests/              # 单元测试和集成测试
├── .env                # 环境变量
└── package.json