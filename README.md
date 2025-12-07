# 型动局-FitnessApp

## 项目简介

型动局-FitnessApp 是一款以健身社交为核心，融合内容分享、互动与管理的多端应用，包括后端服务、微信小程序和 Web 管理后台，采用模块化架构，支持团队高效协同开发与持续交付。

---

## 项目结构说明

```
型动局-FitnessApp/
├── .github/         # Github相关配置，如CI/CD、PR/Issue模板、敏感词过滤
├── docs/            # 项目文档、数据库、API等设计说明
├── backend/         # 统一后端服务（Node.js/Go可选）
├── miniprogram/     # 微信小程序端
└── web-admin/       # Web管理后台（Vue3推荐）
```

**详见 docs/01-Architecture.md 架构图与 docs/03-API-Spec.md 接口规范**

---

## 各模块简介

- **.github/**  
  项目自动化、敏感词、PR/Issue模板等，保障流程和内容安全。

- **docs/**  
  统一技术文档、数据结构、接口定义、API文档，方便规范维护和对接。

- **backend/**  
  - `config/`          后端统一配置项
  - `src/modules/`     三级模块化结构：user(用户/权限)，content(内容/评论/标签)，admin(管理后台)
  - `src/middleware/`  通用中间件，如鉴权、敏感词过滤
  - `src/server.js`    服务启动、主入口

- **miniprogram/**  
  - 参考微信小程序标准工程结构，封装通用组件与工具，页面分 feed/上传/主页/好友等

- **web-admin/**  
  - 管理后台基于 Vue3 + Ant Design/Element & ECharts，前端页面和通用组件集中管理

---

## 开发/协作规范

1. **分支策略（建议）**  
   - `main/master` 生产主分支，仅合并发布代码  
   - `dev`         日常开发集成  
   - `feature/xxx`/`bugfix/xxx` 模块开发/修复专用

2. **代码规范**  
   - 前后端均遵守统一 ESLint/Prettier（或相应 linter）规范  
   - 全部分支 PR 需经评审（Review）后合并

3. **文档协作**  
   - 任何变更须同步更新 docs/ 相关文档  
   - 保持数据库、API文档与代码同步

4. **敏感词与安全**  
   - ✅ `.github/words_filter.txt` 配置违禁词  
   - 前后台均实现敏感内容拦截中间件

5. **提测与集成**  
   - CI/CD在 `.github/workflows/` 配置自动化构建、测试、部署流程  
   - 建议每次功能提交均结合单元测试

---

## 快速启动（举例）

### 1. 初始化依赖

```bash
# 后端
cd backend
npm install

# Web Admin
cd ../web-admin
npm install

# 小程序
# 微信开发者工具导入 miniprogram 文件夹即可
```

### 2. 启动服务（以 Node.js 版后端为例）

```bash
cd backend
npm run dev
```

### 3. 目录/数据库初始化
- 配置数据库连接，可参考 `docs/02-DB-Schema.sql` 初始化表结构
- 配置 `.env`（如有）存放敏感私密信息

---

## 贡献者

所有成员请将基本信息补充进 `docs/README.md` 或单独维护贡献者列表。

---

## 问题反馈

- 拉取最新代码、查阅 docs 文档与 Issue 区
- 有问题请发 Issue 或 PR，描述清楚背景、现象、日志

---

> 本 README 仅为模板，请结合实际补充各子模块的详细协作及开发说明！
