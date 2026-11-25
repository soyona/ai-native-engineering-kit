# AI Native 工程规范

在 Codex 中打开项目文件夹，发送：

```text
请读取 https://github.com/soyona/ai-native-engineering-kit 的 README，按照其中的初始化指南，在当前目录初始化我的新项目。
```

## 项目目录结构

以下是**用户项目**的目录。无标记项默认创建；`*` 表示按需启用。技术栈未定时也可以初始化。

```text
项目根目录/
├── README.md                   项目目录指南
├── docs/
│   ├── inputs/                 原始资料：访谈、客户来稿、调研记录
│   ├── requirements/           需求：范围、PRD、验收条件
│   │   └── features/ *         单项功能规格
│   ├── design/
│   │   ├── product/            产品设计：流程、交互、权限
│   │   │   └── prototypes/ *   原型与设计稿
│   │   └── technical/          技术设计：架构、接口、数据模型
│   │       └── decisions/ *    技术取舍及其依据
│   ├── development/            开发计划、任务拆解、变更记录
│   ├── verification/           测试结果、缺陷与验收记录
│   └── delivery/               版本说明、使用手册、交接记录
├── scripts/                    环境准备、校验、构建脚本
├── src/ *                      单应用源码
├── tests/ *                    可执行测试与样本
├── config/ *                   可共享的配置示例，不放密钥
├── apps/<应用名>/ *            多应用同仓，各自组织源码与测试
├── packages/ *                 应用间共享的代码
├── contracts/ *                跨端共用的 API、事件等机器可读契约
├── db/migrations/ *            数据库迁移
├── db/seeds/ *                 开发与测试种子数据
├── deploy/ *                   部署配置
├── infra/ *                    基础设施代码
├── .github/workflows/ *        GitHub Actions 工作流
└── .agents/skills/ *           项目专属 Codex 工作流程
```

**布局优先级：已有路径 → 框架约定 → 通用布局。** 普通单应用用 `src/`、`tests/`、`config/`。Java Maven 用 `src/main/java/`、`src/main/resources/`、`src/test/java/`，不另建根级测试或配置目录。多应用按已确认的模块名和各自技术栈建目录；已有 `frontend/`、`backend/` 就地复用，不再建 `apps/`。`AGENTS.md`、`.gitignore` 等已有文件保留，不自动生成。

## 初始化指南（给 Codex）

1. **选目录。** 只在用户打开的项目中操作。根据用户要求、已有结构和必要的构建清单选择带 `*` 的目录；指南列出某项不代表启用。来源无法确认时停止。
2. **先检查。** 写入前检查目标路径、父目录和根 README。遇到越界、文件占位、符号链接、目录联接或其他重解析点，停止并报告。补写已有 README 前须确认编码、BOM 和换行风格，并核实硬链接数为 1；无法确认或说明冲突时不写入。
3. **建目录，写指南。** 复用已有目录，不搬动原件。根 README 分「已经创建或复用」和「按需启用」，写明实际路径、用途及启用条件。保留原文和格式，只补缺项；已启用的条目不再列为待启用。除根 README 外不生成文件，不提交、不上传。
4. **核对结果。** 逐项核对实际目录与指南，报告新增、复用或受阻的路径。重复执行应无变化；中途失败保留现场，不删除用户文件。
