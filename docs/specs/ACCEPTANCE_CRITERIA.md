```markdown
# Acceptance Criteria

   ## Scope

   ## Happy Path

   ## Edge Cases

   ## Quality Gates
   - Unit tests:
   - Integration tests:
   - E2E tests:

   ## Release Checklist
   - Monitoring:
   - Rollback:
   - Docs:
```
## V1 - Authoritative Content (Generated)
```markdown
# Acceptance Criteria（MVP）

## 范围
Telegram-only MVP：商家配置、知识库问答、漏斗引导、转人工与通知。

## 售前漏斗 Happy Path
- HP1 用户打招呼 3 秒内收到回复
- HP2 机器人输出 3 条卖点 + CTA
- HP3 提供 App 下载与注册步骤
- HP4 用户确认已注册，机器人给下一步（下单/使用）

## 产品问答
- QA1 命中知识库的问题必须用 KB 回复
- QA2 回复必须包含引用（KB 条目 id/标题）

## 售后
- AS1 常见问题提供排障步骤
- AS2 退款/支付争议直接转人工

## 转人工
- HO1 触发：负向情绪/3 次失败/未知意图/退款争议
- HO2 转人工前收集必要信息（地区、设备、问题摘要、联系方式）
- HO3 Telegram 群收到：原因、摘要、session id、最近 5 条用户消息

## 质量门禁
- 状态机单测覆盖
- DB migrations 可重复
- 不提交任何 token/password
```
