# Git 提交规范

## 基本结构

一个标准的 Git 提交消息应包含以下三个部分：

```
<类型>[可选的作用域]: <描述>

[可选的正文]

[可选的脚注]
```

## 提交类型

| 类型     | 说明                           | 示例                       |
|---------|-------------------------------|---------------------------|
| feat    | 新增功能                        | feat: 添加用户登录功能       |
| fix     | 修复 bug                       | fix: 修复登录表单验证问题     |
| docs    | 文档更新                        | docs: 更新 API 文档         |
| style   | 代码样式调整（不影响功能）         | style: 统一代码缩进          |
| refactor| 代码重构（不新增功能也不修复 bug）  | refactor: 重构用户服务模块   |
| perf    | 性能优化                        | perf: 优化数据库查询性能     |
| test    | 测试相关                        | test: 添加单元测试           |
| build   | 构建相关                        | build: 更新依赖版本          |
| ci      | CI/CD 配置修改                  | ci: 调整 GitHub Actions 配置 |
| chore   | 其他杂项（如配置文件修改）         | chore: 更新 .gitignore      |

## 格式要求

1. **类型**：使用小写，后跟冒号和空格
2. **作用域**：可选，用括号包围，描述修改的模块
3. **描述**：简短明了（50 字符以内），使用祈使句
4. **正文**：可选，详细描述修改内容（72 字符换行）
5. **脚注**：可选，用于引用 Issue 或 BREAKING CHANGE

## 示例

### 简单提交
```
feat: 添加用户注册功能
```

### 带作用域的提交
```
fix(auth): 修复登录验证逻辑
```

### 带正文的提交
```
refactor(api): 重构 API 响应处理

- 统一错误处理格式
- 优化响应数据结构
- 提高代码可维护性
```

### 带脚注的提交
```
feat: 移除废弃的 API 端点

BREAKING CHANGE: 移除了 /v1/old-api 端点，请使用 /v2/new-api 替代

Closes #123
```

## 工具建议

1. **commitlint**：用于检查提交消息格式
2. **husky**：用于在提交前自动运行检查
3. **commitizen**：提供交互式提交消息生成

## 配置示例

### commitlint 配置（.commitlintrc.js）
```javascript
module.exports = {
  extends: ['@commitlint/config-conventional'],
  rules: {
    'type-enum': [2, 'always', [
      'feat', 'fix', 'docs', 'style', 'refactor', 'perf', 'test', 'build', 'ci', 'chore'
    ]]
  }
};
```

### husky 配置（.husky/commit-msg）
```bash
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

npx commitlint --edit "$1"
```

遵循这些规范可以使提交历史更加清晰，便于团队协作和代码维护。