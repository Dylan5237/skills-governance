# Skills 重叠与重复盘点报告

- 日期：2026-09-21（Asia/Shanghai）
- 机器：ROGStrix37（C:\\Users\\howyo）
- 工具：asm v2.20.1（只报告，不删除、不合并）
- 中央库：Dylan5237/skills-central（约 92 skills）
- 本机扫描：totalSkills=157（含各宿主安装与 plugin）

## 结论

1. 中央库已收编 WorkBuddy 技能约 92 个；本机全域可见约 157 个。
2. 同名重复组：**8**（同一 skill 目录名出现在多个宿主）。
3. 语义重叠对：**18**（异名近义；comparedSkills=97）。
4. 本报告**不执行**合并/删除；合并须人确认闸门。

## 一、同名重复（duplicates）

| # | key | 原因 | 份数 | 位置 |
|---|---|---|---|---|
| 1 | fireworks-tech-graph | same-dirName | 2 | agents C:\Users\howyo\.agents\skills\fireworks-tech-graph<br>claude C:\Users\howyo\.claude\skills\fireworks-tech-graph |
| 2 | gitlab-ops | same-dirName | 2 | agents C:\Users\howyo\.agents\skills\gitlab-ops<br>codex C:\Users\howyo\.codex\skills\gitlab-ops |
| 3 | leader | same-dirName | 2 | agents C:\Users\howyo\.agents\skills\leader<br>codex C:\Users\howyo\.codex\skills\leader |
| 4 | neat-freak | same-dirName | 2 | agents C:\Users\howyo\.agents\skills\neat-freak<br>codex C:\Users\howyo\.codex\skills\neat-freak |
| 5 | officecli | same-dirName | 2 | agents C:\Users\howyo\.agents\skills\officecli<br>claude C:\Users\howyo\.claude\skills\officecli |
| 6 | skill-creator | same-dirName | 2 | agents C:\Users\howyo\.agents\skills\skill-creator<br>claude C:\Users\howyo\.claude\skills\skill-creator |
| 7 | smell | same-dirName | 2 | agents C:\Users\howyo\.agents\skills\smell<br>codex C:\Users\howyo\.codex\skills\smell |
| 8 | tiangong-skill-engineer | same-dirName | 2 | agents C:\Users\howyo\.agents\skills\tiangong-skill-engineer<br>codex C:\Users\howyo\.codex\skills\tiangong-skill-engineer |

### 处理建议（待确认）

- 以 Skills Manager 中央库 + 显式 deploy 为唯一写入面。
- 宿主侧同名副本：优先保留一条权威路径（WorkBuddy / 中央库 deploy），其余标记待清理，**勿 `asm audit -y` 自动删。

## 二、语义重叠（overlap）

按分数从高到低（score 为 asm 相似度，仅供排序）。

| # | score | A | B |
|---|---|---|---|
| 1 | 0.728 | agent-development (plugin) | skill-development (plugin) |
| 2 | 0.696 | command-development (plugin) | skill-development (plugin) |
| 3 | 0.651 | agent-development (plugin) | command-development (plugin) |
| 4 | 0.511 | hook-development (plugin) | skill-development (plugin) |
| 5 | 0.481 | agent-development (plugin) | hook-development (plugin) |
| 6 | 0.468 | skill-creator (agents) | Template Creator (codex-plugin) |
| 7 | 0.468 | skill-creator (claude) | Template Creator (codex-plugin) |
| 8 | 0.440 | github-skill-installer (codex) | GitHub (codex-plugin) |
| 9 | 0.431 | arkcli-pricing (gemini) | arkcli-usage (gemini) |
| 10 | 0.410 | build-mcp-app (plugin) | codex-app-tools (codex-plugin) |
| 11 | 0.400 | arkcli-code-example (gemini) | example-skill (plugin) |
| 12 | 0.400 | Computer Use (codex-plugin) | unified-computer-use (codex-plugin) |
| 13 | 0.400 | example-command (plugin) | example-skill (plugin) |
| 14 | 0.396 | build-mcp-app (plugin) | build-mcp-server (plugin) |
| 15 | 0.368 | arkcli-custommodel (gemini) | arkcli-infer-endpoint (gemini) |
| 16 | 0.366 | build-mcp-server (plugin) | mcp-integration (plugin) |
| 17 | 0.363 | ai-history-daily-report (agents) | hr-weekly-daily-report (claude) |
| 18 | 0.353 | arkcli-billing (gemini) | arkcli-pricing (gemini) |

### 合并闸门（强制）

1. 出报告（本文件）
2. 人选保留方 / 合并产物名
3. 在中央库生成新版本 → SM deploy 到选定宿主
4. 归档或 undeploy 被合并成员
5. **无人确认不落地**

## 三、Residency（低驻留候选摘要）

候选数：48（仅列前 15）

| # | name | provider | 指标 |
|---|---|---|---|
| 1 | neat-freak | ? | 892 |
| 2 | fireworks-tech-graph | ? | 570 |
| 3 | first-principles-product-design | ? | 446 |
| 4 | smell | ? | 388 |
| 5 | arkcli-plans | ? | 374 |
| 6 | kimi-webbridge | ? | 322 |
| 7 | archify | ? | 302 |
| 8 | skill-creator | ? | 268 |
| 9 | officecli | ? | 260 |
| 10 | arkcli-helper | ? | 254 |
| 11 | arkcli-usage | ? | 246 |
| 12 | arkcli-infer-endpoint | ? | 178 |
| 13 | github-skill-installer | ? | 166 |
| 14 | deployment-validator | ? | 154 |
| 15 | fuxi-platform-release | ? | 150 |

## 四、原始数据

- 本机临时：%TEMP%\\asm-dup.json / sm-overlap.json / sm-residency.json
- 治理仓将同步 docs/reports/ 下同名报告与 JSON 摘要