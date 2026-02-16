```markdown
# Tech Plan

   ## Architecture

   ## Data Model

   ## API / Interfaces

   ## Implementation Plan
   - Step 1:
   - Step 2:

   ## Testing Strategy

   ## Rollout / Release

   ## Risks & Mitigations
```
## V1 - Authoritative Content (Generated)
```markdown
# Tech Plan: AI 客服/销售漏斗（MVP）

## 架构（MVP）
- Channel：Telegram bot（先跑通）
- Orchestrator：会话状态机 + 规则策略（转人工/漏斗推进）
- KB Store：Postgres（merchant/kb_entries/sessions/messages/handoffs）
- Notifications：Telegram 群（转人工 + 日报）
- Admin：先配置文件/脚本，后续再做 Web UI

## 数据模型（Postgres）
- merchants(id, name, timezone, config_json)
- kb_entries(id, merchant_id, question, answer, tags, enabled, updated_at)
- sessions(id, merchant_id, channel, user_id, state, last_intent, updated_at)
- messages(id, session_id, role, text, ts)
- handoffs(id, session_id, reason, summary, status, created_at)

## 核心流程
1) 漏斗
- 状态：greet -> intro -> register -> verify -> done
- 每次用户消息更新 session.state

2) 知识库问答
- 先：关键词/标签检索
- 后：语义检索 + 引用

3) 转人工
- policy engine 决策
- 创建 handoff 记录
- 发 Telegram 群消息（原因、摘要、session id）

## 实施计划（MVP）
- Step 1 仓库服务骨架（FastAPI 或 Node）
- Step 2 DB migrations + models
- Step 3 Telegram 接入 + session key 规则
- Step 4 漏斗状态机
- Step 5 KB CRUD + 匹配
- Step 6 转人工通知 + 工单
- Step 7 日报汇总

## 测试
- 单测：状态机转移覆盖 >= 80%
- 集成：DB 操作

## 安全
- secrets 只放 env，不写入仓库
- 日志脱敏
- 频控与防刷
```
