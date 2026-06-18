---
name: qwen-platform-wireframe
description: 获取千问开放平台最新交互线框图（商家入驻控制台 + 三方管控后台）。当研发需要查看最新线框图、了解交互变更、获取产品设计稿时使用。触发词：线框图、wireframe、交互稿、产品设计、管控后台交互、商家端交互。
version: 1.0.0
---

# 千问开放平台交互线框图

从 git 仓库拉取最新版本的交互线框图 HTML 文件，并输出本次版本变更说明。

## 执行步骤

### 1. 拉取最新文件

```bash
# 仓库地址（请替换为实际 remote URL）
REPO_URL="https://github.com/sanwanyingchi/open-platform-wireframe.git"
LOCAL_DIR="/tmp/qwen-platform-wireframe"

# 如果本地已有则 pull，否则 clone
if [ -d "$LOCAL_DIR/.git" ]; then
  cd "$LOCAL_DIR" && git pull origin main
else
  git clone "$REPO_URL" "$LOCAL_DIR"
fi
```

执行上述逻辑拉取仓库。如果 clone 失败（比如仓库地址未配置），提示用户检查 git remote 地址。

### 2. 输出变更说明

读取 `$LOCAL_DIR/CHANGELOG.md` 文件，将**最新版本**的变更内容（第一个 `## vX` 区块）输出给用户。格式示例：

```
📋 本次变更（v5 — 2026-06-18）：
- 调试工具拆分为 Skill 调试 + 端到端调试两个独立页面
- 提交审核按钮改为材料完整性驱动
- ...
```

### 3. 呈现线框图文件

将 `$LOCAL_DIR/wireframes/` 下的 HTML 文件复制到当前工作目录，然后用 `present_files` 工具呈现给用户。

文件清单：
- `商家入驻控制台-交互线框图-v5.html` — 商家侧完整交互（8 页面 + drawer + modal）
- `三方管控后台-交互线框图-v2.html` — 内部运营管控（5 页面 + 审核 drawer）

### 4. 使用提示

告知用户：
- HTML 文件可直接在浏览器打开交互体验
- 左侧导航切换页面，按钮均有 onclick 模拟交互
- 如有疑问可参考 CHANGELOG.md 了解各版本演进

## 注意事项

- 如果用户只想看某一端（商家端/管控后台），只呈现对应文件
- 如果拉取失败，检查 git 权限和网络，给出排查建议
- 不要修改仓库内的文件，这是只读消费
