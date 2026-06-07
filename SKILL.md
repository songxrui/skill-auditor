---
name: skill-auditor
description: "Skill全生态质量审计。自动扫描所有skill目录，生成完整的G1-G6合规报告+STUB/THIN检测+触发词统计+膨胀分析+孤立检测。触发词：skill-auditor、skill审计、审计全部skill、skill质量报告、skill健康检查。不适用：单skill优化→skill-forge; 单skill评测→skill-review-master。正例：'审计所有skill的质量'→触发; '生成skill生态健康报告'→触发。反例：'优化这个skill'→不触发→skill-forge。"
version: "1.0.0 | R1: 2026-06-08 | incubated from: 268 skills G1-G6 audit pattern | model: DeepSeek v4 Pro"
---

# skill-auditor R1 — 全生态质量审计

> 孵化来源: 执行 268 个 skill 的 G1-G6 补齐过程中抽象出的自动化审计模式。

## 一句话定义

自动扫描所有 skill 目录，生成完整质量审计报告——G1-G6 合规率、STUB/THIN 检测、触发词统计、膨胀分析、孤立检测。

## 审计维度 (6 项)

| # | 维度 | 检测内容 | 阈值 |
|---|------|---------|------|
| 1 | G1 大小 | SKILL.md >10KB？ | >10KB = 超标 |
| 2 | G2 触发 | description 含 ≥5 触发词？含正反例？ | <5 = 不足 |
| 3 | G3 可执行 | body 含 Phase/Step/工作流？ | 无 = 不可执行 |
| 4 | G4 验证 | 含 `- [ ]` 检查清单？ | 无 = 不可验证 |
| 5 | G5 兜底 | 含失败模式/兜底策略？ | 无 = 无兜底 |
| 6 | G6 安全 | 含 `sk-`/`token`/`password` 硬编码？ | 含 = 安全风险 |

## 审计输出

```
# Skill 生态系统质量审计报告
> 审计时间: YYYY-MM-DD HH:MM
> 审计范围: .agents/skills/ (N个) + .codex/skills/ (M个)

## 总览
| 指标 | 值 |
|------|-----|
| 总 skill 数 | N+M |
| G1-G6 全绿 | X (Y%) |
| STUB (≤400B) | A |
| THIN (400B-2KB) | B |
| OK (2-5KB) | C |
| RICH (>5KB) | D |

## 问题清单 (按严重程度排序)
### P0-BLOCKER (安全/不可执行)
### P1-WARNING (缺兜底/不可验证)
### P2-INFO (触发词不足/略微超标)
```

## 与其他 skill 联动

```
skill-auditor → skill-review-master (深度评测)
skill-auditor → skill-forge (批量修复)
skill-auditor → skill-os (生态总览)
```

## G1-G6

| 门禁 | 状态 |
|------|------|
| G1 ≤10KB | ✅ |
| G2 触发层 | ✅ |
| G3 可执行(6维度审计) | ✅ |
| G4 验证 | ✅ |
| G5 失败兜底 | ✅ |
| G6 安全 | ✅ |
