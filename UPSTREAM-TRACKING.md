# 上游跟踪基线（Upstream Tracking Baseline）

本仓库（fcmyoo/love-strategist）是「恋爱小助手」合并技能的 fork，直接跟踪两个原始源仓库，
绕过中间合并容器 Xuefeng122/love-strategist（后者 2026-10-11 后无更新，仅一次性合并快照）。

## 血缘关系

| 角色 | 仓库 | 远程名 |
|---|---|---|
| 本仓库（用户 fork） | fcmyoo/love-strategist | origin |
| 源仓库 1：狗头军师（系统化分析框架/知识库） | shengjidaguai-china/goutoujunshi | goutoujunshi |
| 源仓库 2：童锦程（直白风格/心智模型） | hotcoffeeshake/tong-jincheng-skill | tongjincheng |
| 中间容器（不再跟踪） | Xuefeng122/love-strategist | — |

## 已吸收基线（last absorbed commit）

更新上游后必须把此处推进到新 HEAD，并提交推送。

- goutoujunshi: `6db7354a40`（2026-09-15，合并日前，内容已全量吸收）
- tongjincheng: `4ae93806a3`（2026-10-27，合并日后 3 个提交已审计：**无可合并实质内容**）
  - #21 README 推广/二维码 → 不合并
  - #22 FIDELITY.md 保真度评分卡（nuwa 平台元数据）→ 不合并
  - #23 删"北方口音"备注 → 合并版本来就不含该描述，无需合并

## 合并规则

1. **合并什么**：SKILL 内容、references/ 下的知识与话术文档的实质改动。
2. **不合并**：README 推广物料、二维码图片、FIDELITY.md 等平台体检元数据、
   依赖特定平台的安装说明。
3. **合并方式**：源仓库内容在合并容器中被改写过（如童锦程 SKILL.md →
   `references/practical/童锦程风格与心智模型.md`），不做 git merge，
   而是内容级比对后手工移植。
4. 合并后同步三处：本仓库 main（push 到 origin）→ 本机技能目录
   `C:/Users/leewi/.workbuddy/skills/love-strategist/` → 更新本文件基线。
5. 判断不确定或有冲突时：**不要 push**，向用户汇报等待指示。

## 本地定制区（上游更新不得覆盖）

以下内容是用户本机定制，不来自任何源仓库，合并时必须保留：

- `references/practical/weflow-cli微信聊天记录分析适配.md`
  —— 2026-10-30 将原 ChatLab 适配替换为用户自有的本机工具 weflow-cli
  （<https://github.com/fcmyoo/weflow-cli>）命令面：contacts / messages / export /
  evidence / report / chat-stats / awaiting / draft / sync 等。
  两个源仓库若将来出现同名或等价的"聊天记录分析适配"文件，
  **不要用它覆盖本文件**；如需整合，只做增量补充并保留 weflow-cli 命令面。
- `scripts/memory_store.py` 的 `weflow` source_type（`chatlab` 仅作旧记录兼容）。
- **已移除文件**：`references/knowledge/11-婚姻家庭与生命周期.md`
  —— 2026-10-30 删除。理由：与 02 总论、12 金钱家务育儿、13/14 家庭结构内容重复；
  无 SKILL.md 按需加载入口（永不触发）；婚内长期生命周期与本 skill 的
  恋爱／暧昧／关系决策主场景不匹配。
  **上游 goutoujunshi 仍保留同名文件，同步时不要把它重新引入**；
  若上游对该主题有实质修订，只把改动要点并入 12 或 14，不恢复整篇。
  编号 11 保留为空洞位，不重排后续文件编号（避免破坏与上游的文件名对应关系）。
