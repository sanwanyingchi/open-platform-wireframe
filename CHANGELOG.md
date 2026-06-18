# 千问开放平台交互线框图 Changelog

## v5 — 2026-06-18

### 商家入驻控制台（v5）

- 调试工具拆分为两个独立页面：page-skillDebug（Skill 调试）+ page-e2eDebug（端到端调试）
- 调试交互从"解锁门控"改为"推荐引导"：调试不是质检关卡，是商家自助工具
- 提交审核逻辑按调试充分度三档分流（充分 / 仅 Skill 调试 / 未调试）
- 提交审核按钮出现条件改为材料完整性校验（名称+slug+能力描述+触发条件+SKILL.md+to C 数据+KB 绑定），与调试行为无关
- 「从知识库创建 Skill」三处入口统一指向 modal-genSkill 6 字段表单
- 新增 page-qualSubmit 入驻资质提交表单页（5 section + 4 步进度条）

### 三方管控后台（v2）

- Skill 审核 drawer 新增「调试记录摘要」区块（Skill 调试轮次 / E2E 会话次数 / 最近调试时间 + 风险提示）
- 审核 checklist 从"调试通过"改为"调试记录充分（参考摘要）"

---

## v4 — 2026-06-16

### 商家入驻控制台（v4）

- page-kb 改为单 KB 直达（去中间卡片层），文件列表直接呈现
- 召回测试拆为独立 page-recallTest
- Skill-KB 绑定不做默认（仅从 KB 创建时自动绑定）
- drawer-skillConfig KB 卡可绑可解绑
- KB 状态机 8 态定型（uploading/parsing/machine_review/rejected/indexing/staged/online/offline → purged）

---

## v3 — 2026-06-15

### 商家入驻控制台（v3）

- 全流程交互补齐：91 个 button onclick + toast/confirmThen helper
- sendDebugMessage 模拟完整对话流（用户气泡→思考中→工具调用→KB 召回→最终回答）
- 18+ 业务函数（editContact/offlineSkill/unbindKB/bindMoreKB 等）
