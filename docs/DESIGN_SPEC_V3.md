# Sprout v3 · 案头 · The CEO Desk: Definitive Build Spec

Spine: **boardroom** (highest aggregate score, 127.5).
Grafts: **command** (the front-door capture line, the voice rule for type, role-signed receipts, 汇报 queries, #node 批注, the 全员停工 stop), **org** (the 分派单 routing slip, single-glyph role marks, the glyph wall on 团队, restaffing effect previews, the empty-state forecast, 安静模式), **pipeline** (tiered hold, 10-second undo before agents start, sort by 放行量, the station ruler, the 本周验收 north star).
Every judge must-fix is resolved inline. Section 8 is the review checklist.

Implementation overrides (the prototype follows these where they differ from the text below):
- The page title stays 「Sprout 原型」, so the published link keeps its name.
- Routes live in in-memory state. The artifact viewer only passes plain `#anchor` deep links through, so the `#/biz/:id/...` hashes in §2.1 are not written. The initial deep links `#brief #sign #inbox #biz #ledger #team #ios` are accepted.

Language rule for this document: the prose is in English for the engineer. Every string in 「」 or in a code/copy block is final UI copy in Simplified Chinese and must appear exactly as written.

---

## 1. Concept

### 1.1 Name

**案头 · The CEO Desk**. The app is titled 「Sprout」 in the tab. The company is 「远山一人公司」 and always carries the tag 「示例」.

### 1.2 Thesis

A one-person company has exactly one human, and that human does two things: **说** (say what they want) and **签** (sign where the company needs them). Everything in between is done by the company's AI staff. The 幕僚长 (chief of staff) receives and shapes each idea. 规划 decomposes it into 愿景 → 里程碑 → 功能 → 工单. 工程 (Claude Code 团队, Codex 团队) builds it. 质检 proves it with evidence. 财务 prices it. The interface is one typeset sheet on a cool grey desk, with no cards and no shadows. At the top is a single line where the CEO speaks: 「今天要公司办什么？」. Below it the company answers on the record. Each receipt line is signed by the role that did the work, and each idea visibly moves through six stations: **收件 · 梳理 · 拆解 · 执行 · 验收 · 交付** (the user's own verbs: 被处理 = 梳理, 被分解 = 拆解, 被执行 = 执行). The company can plan, build and test anything. It cannot spend money, ship, cross a red line, or call work done without the CEO. Those moments arrive as short documents in one stack, 待签, each with a recommendation already selected and a button that states its consequence. Money and red lines need a press-and-hold. Everything else is one tap with a 10-second undo. The CEO's own words are set in serif, the largest type on the page. The company speaks in small sans and mono. The only colour in the product is the CEO's pen blue, and it means one thing: *your hand is needed here, or your hand did this.*

**Signature interaction:** 「说一句，签一笔」. The CEO says one sentence. It is received, routed, questioned, decomposed and priced line by line in front of them, and it ends at a signature line. One hold later the work starts. (Specified in §4.3.)

**Bold visual move:** "Two hands on one sheet." Zero cards and zero shadows on content. One white sheet is anchored left on a grey desk. The CEO's words are in Noto Serif SC at up to 40px. The company's words are in 14–15px sans and 12.5px mono. Pen blue is the only chroma. The headline of the day is a single very large, very light sentence. Grandeur (大气) comes from scale, rules and whitespace, never from decoration. A secondary detail is used on exactly one page (团队): giant cropped role glyphs.

### 1.3 Glossary (use these words and no others)

Rule for tone: office words appear only as short labels and tags. Buttons and prose are plain spoken Chinese: 同意 / 通过 / 退回 / 批准 / 确定.

| Product term | UI term (CEO language) | Notes |
|---|---|---|
| Workspace | 公司 | 「远山一人公司」 + tag 「示例」 |
| User | 你 | Never a personal name. Role mark glyph 「你」 in pen |
| Home | 晨报 | A daily brief from the 幕僚长. 「第 24 期」 = the day count since the company started on 9-01 (a real sequence) |
| Capture | 交代 | Hero placeholder 「今天要公司办什么？」. Bottom bar placeholder 「交代一件事，说或写都行…」. Send button 「交给幕僚长」. Mic label 「口述」 |
| Voice transcript raw / cleaned | 原话 / 整理稿 | Raw audio chip 「原始录音 0:23」 |
| Inbox | 收件 | Serial 「收 0924-02」 |
| Triage | 分流 | Three outcomes: 并入 / 立项 / 存档 |
| Triage suggestion | 分派单 | Fields: 建议 / 业务 / 挂在 / 承办 / 预估 / 需要你 / 理由 |
| Idea journey | 流转 | Six stations: 收件 · 梳理 · 拆解 · 执行 · 验收 · 交付 |
| Receipt line | 回执 | One line: time · role mark · text · $ |
| Project | 业务 | List page: 业务一览 |
| New project | 立项 | Nothing is spent before 批准立项 |
| Brief | 一页纸 | Sections: 为谁 / 做什么 / 不做什么 / 假设 / 原则 |
| Goal tree | 拆解 | Levels: 愿景 (L0) / 里程碑 (L1) / 功能 (L2) / 工单 (L3). Views: 结构图 / 大纲 |
| Clarifying question | 拍板 | A 待签 kind |
| Approval gate | 批准 | A 待签 kind. A batch plus 上限 |
| Review | 验收 | A 待签 kind. Actions 通过 / 退回 |
| AI stuck | 上报 | A 待签 kind, from 工程 after 3 failures, a cap, or an external dependency |
| Ball-in-your-court queue | 待签 | Holds only the four kinds above. Count shown in the nav |
| Risky actions | 红线 | Always need your signature, whatever the 授权 |
| Node-level instruction | 批注 | Chips: 拆细 / 换方案 / 省点钱 / 换人做 / 不做了 |
| AI diff | 修订稿 | Actions: 采纳修订 / 不采纳 / 再改一句 |
| Decisions log | 决策记录 | Serial 「D-0924-03」. Kinds: 立项 / 拍板 / 批准 / 验收 / 退回 / 修订 / 派工 / 授权 / 手动修改 |
| Context pack | 档案 | 「每次派工都附上这些」 |
| Evidence | 验收材料 | Types: 测试 / 截图 / 演示 / 文档 |
| Acceptance criteria | 验收标准 | |
| Agent | 执行团队 | 「Claude Code 团队」「Codex 团队」「Cursor 后台 Agent」. Connect = 签约 |
| Model | 人选 | Claude Opus 5.5 / Claude Sonnet 5 / Claude Haiku 4.5 / Codex |
| Model routing | 派工 | Presets 省钱 / 均衡 / 质量优先 / 手动. Auto = 「交给幕僚长」 |
| AI roles | 幕僚长 幕 · 规划 规 · 工程 工 · 质检 检 · 财务 财 | Single-glyph role marks. Never human names or faces |
| Live running work | 值班 | The global strip |
| Spend ledger | 账本 | Every $ is tagged 实计 or 估算 |
| Forecast | 预估 | Always a range plus 「置信度 低/中/高」 |
| Autopilot L0 / L1 / L2 | 授权: 逐项问我 / 按批授权 / 预算内全权 | Default 按批授权. Never label these "L0/L1/L2" in the UI, to avoid clashing with the goal levels |
| Caps | 月度预算 / 单批上限 / 单张工单上限 / 本批上限 | |
| Kill switch | 全员停工 | Hold to confirm |
| Status query | 汇报 | 「汇报一下 PawLog」 typed into the capture line |
| Overnight log | 昨夜 | 22:00–08:30 |
| North star | 本周验收 | Accepted 工单 this week |
| Work released by signing | 放行量 | The default sort of 待签 |

---

## 2. Information architecture

### 2.1 Destinations (hash routes)

| Route | Name | Purpose |
|---|---|---|
| `#/brief` (default) | 晨报 | Front door: capture line, today's count, the 待签 stack, compact overnight / ventures / inbox |
| `#/sign` | 待签 | Register plus reader for every open decision. Supports batch 验收 |
| `#/inbox` | 收件 | Every idea, its 分派单, its 流转 track and receipts |
| `#/charter/:id` | 立项 | New idea: ≤3 questions, then the animated L0–L3 plan, then approve or plan-only |
| `#/biz` | 业务一览 | Portfolio table |
| `#/biz/:id/tree` | 业务 · 拆解 | Header, 结构图 / 大纲, node side sheet, 批注 → 修订稿 |
| `#/biz/:id/money` | 业务 · 账目 | This venture's spend, forecast band, 授权 override |
| `#/biz/:id/file` | 业务 · 档案 | 一页纸, 决策记录, 执行团队, 代码仓库, context pack |
| `#/ledger` | 账本 | Company money, 本周验收, 授权 levels, caps, 红线 |
| `#/team` | 团队 | Org (glyph wall), 派工 strategy, 岗位分工 table, signed teams |
| `#/ios` | 随身 | Prototype-only: 3 interactive phones sharing state |

The node side sheet is state-driven (`ui.sel`) and also writes `?n=2.2.2` into the hash so it survives reload within the session.

### 2.2 Global chrome, desktop (≥761px)

1. **Masthead**: 56px, sticky, sheet colour, 1px rule under it, then a 3px ink rule 2px below that (a double rule).
   - Left: 「远山一人公司」 (sans 500 16px) + tag 「示例」 (1px ink-3 border, 11px).
   - Text nav: 晨报 · 待签 `6` · 收件 `3` · 业务 · 账本 · 团队. The active item gets a 2px ink underline. The 待签 count is a pen-outlined numeral box. The 收件 count is plain ink-3.
   - Right: 「随身」 (link to #/ios, suffixed 「预览」 in ink-3) · 「日 / 夜」 text toggle · 「全员停工」 (ink-3 text, turns risk colour on hover; hold 1200ms).
2. **值班条**: 36px, sticky under the masthead, sheet-2 background, 1px rule under it. It scrolls horizontally inside its own container.
   - Chips: `[工] Codex 团队 · PawLog 2.2.1 订阅喂食记录的变更 · 62% · 21 分钟 · $2.40`. Each chip is 28px tall, has a 1px rule border and 2px radius, and carries a 1px ink progress hairline along its bottom edge.
   - Right-aligned (sticky inside the strip): 「今日 $13.20 · 本月 $34.15 / $80 · 授权 按批」 in mono 12.5, plus a 「安静」 toggle.
   - When more than 3 runs are active, the chips collapse to 「5 项在跑 · 今日 $x」 with an expand caret.
3. **The sheet**: white, 1px rule border, radius 0. `margin-left: clamp(0px, 3vw, 40px)`, max-width 1240px, right side free, so the grey desk shows on the right on wide screens. **Left-anchored, never centered.** Inner padding is 40px 48px.
   - Inner grid at ≥1180px: `grid-template-columns: minmax(0,720px) 320px; column-gap: 56px`. The margin column is divided by a 1px rule on its left and is sticky (`top: 108px`).
   - 761–1179px: one column. Margin content becomes a 2-column figure strip under the headline.
4. **Bottom 交代 bar**: fixed, 56px, sheet colour, 1px rule on top. Left edge is aligned to the sheet's main column, max-width 720px.
   - Contents: input 「交代一件事，说或写都行…」, mic 「口述」, button 「交给幕僚长」.
   - Hidden on 晨报 while the hero capture line is in view (IntersectionObserver). Also hidden when any side sheet is open.
5. **Toast area**: bottom-left, above the bar, max-width 440px.

### 2.3 Global chrome, phone (≤760px, designed at 400px)

- **Masthead**: 48px. Wordmark 「远山一人公司」 + 「示例」, then the theme toggle on the right. No text nav.
- **值班条**: stays at 32px and scrolls horizontally inside itself. The right-hand figures shorten to 「今日 $13.20」.
- **Bottom tab bar**: 64px + `env(safe-area-inset-bottom)`, 5 slots: 「晨报」 · 「待签」(count) · centre 52px ink circle mic 「口述」 · 「业务」 · 「更多」.
  - 更多 opens a bottom sheet listing: 收件 (count) · 账本 · 团队 · 随身预览 · 日 / 夜 · 安静模式 · 全员停工 · 重置示例.
- The fixed 交代 bar does not exist on phone. The centre mic opens the **交代 sheet** (bottom sheet, 90vh) with the text field, mic, waveform and the live receipt.
- The sheet is full width with no border. Side gutters are 16px. **No page-level horizontal scroll.** Only the 值班条, the 结构图, the ledger chart, wide tables and the 流转 track (when it is horizontal) scroll inside their own containers.
- Side sheets become bottom sheets at 88vh with a 4×36px grab handle.
- A document's sticky sign block sits at `bottom: calc(64px + safe-area)`, above the tab bar, so they never overlap.

---

## 3. The idea lifecycle as the CEO sees it

Six stations are used identically everywhere: the 流转 track on every idea, the station ruler on 晨报 and on each 业务, and the node side sheet.

| Station | What happens | Who (role mark) | What the CEO sees |
|---|---|---|---|
| 收件 | The idea is captured (web text, web simulated voice, iPhone voice, share) | 幕 | The sentence lands in serif with its source, time and 「原始录音 0:23」 chip. The track fills segment 1 |
| 梳理 (被处理) | Clean-up (fillers struck through), key points, 分派单 (并入 / 立项 / 存档), up to 3 拍板 questions | 幕 | The 分派单 rows fill in one by one. **The CEO confirms with one tap** (「同意」 or 「改为 ▾」). Nothing is filed automatically and nothing is spent. Bulk: 「都照建议（3）」 |
| 拆解 (被分解) | The plan (new venture) or a 修订稿 on an existing node; each 工单 gets 验收标准, evidence type, 人选 and a price range | 规, 财 | A mini outline unfolds in the receipt. On the 业务 page the nodes animate into the 结构图. Then the price: 「预估 $3.1–5.0 · 约 1 小时 · 置信度 中（同类 11 张）」 |
| (gate) | Authority check | 幕 | 「在你的授权内，10 秒后开工」 or a 批准 document with a sign line (hold) |
| 执行 (被执行) | 工程 runs; live %, time and $ | 工 | A chip in the 值班条. Outline rows pulse. A mono log tail in the side sheet. After 3 failures: 上报 with priced options |
| 验收 | 质检 attaches screenshots, tests and a criteria↔evidence map | 检 | A 验收 document in 待签 (+ iPhone push). 通过 or 退回 with a reason |
| 交付 | Accepted; counts toward 本周验收 | 你 | The track completes. The 收件 entry reads 「已交付 · 共 $1.24 · 38 分钟 · 看验收材料」. Next morning's 晨报 lists it |

Track rendering: 6 segments of 28×3px (desktop row), 64×3 with 12px labels (expanded). Colours:
- Done = ink.
- Current and company working = ink-2 with a 24px highlight gliding along it (2.4s loop).
- Current and waiting on the CEO = pen, plus a 6px pen dot above it.
- Current and stuck = risk.
- Future = rule.

Hovering a segment shows 「拆解 · 09:14 · 规划 · Claude Opus 5.5」.

Reverse move: 退回 draws the track's 执行 segment again with the label 「返工」 and adds a receipt line 「决策记录 已记下退回原因，工程按这个返工」.

---

## 4. Screens

Shared components (build once, reuse everywhere): `RoleMark`, `KindTag`, `Track`, `Receipt`, `DispatchSlip`, `Doc` (the decision document), `SignControl`, `NodeRow`, `NodeSheet`, `Figure`, `Toast`, `Sheet`. One state store (§7.4). Every surface re-renders from it, so signing on the memo, in 待签, in a node sheet or on a phone updates every count and mark at once.

### 4.1 晨报 (home) · `#/brief`

**Purpose:** in 10 seconds, know what needs you and how long it takes. Say a new thing in 3 seconds. Clear decisions without leaving the page.

**Layout, desktop (≥1180):** main column (720) + margin (320).

Main column, top to bottom:

1. **Meta line** (mono 12.5, ink-3): `[幕] 晨报 · 第 24 期 · 9 月 24 日 周四 · 幕僚长 08:30 发出`.
2. **Hero capture line (front door)**, 24px below the meta line. Hidden on phone, where the centre mic replaces it.
   - Label 「交代一件事」 (12px label style).
   - An auto-growing textarea, 1–4 lines. Noto Serif SC 600, `clamp(26px, 2.8vw, 40px)`, line-height 1.3. Caret colour pen. Placeholder 「今天要公司办什么？」 in ink-3.
   - No box, only a 2px ink rule under it.
   - Control row (44px):
     - Mic 40px circle, 1px ink border, label 「口述」 via aria. Recording = pen fill + a 5-bar waveform + a mono timer.
     - Hint (ink-3 12.5px): 「Enter 交给幕僚长 · M 口述 · 可写 @业务 或 #节点」.
     - Live 分流 chip (see §4.3).
     - Button 「交给幕僚长」 (ink fill, sheet text, 2px radius, 40px tall).
   - When empty, 3 ghost suggestion chips: 「汇报一下 PawLog」 「#2.2.2 先不做离线写入」 「这个月还能花多少」.
   - After sending, the live receipt for the new idea renders **inline directly under the hero** (§4.3). Only one live receipt shows here at a time. Older ones move to 收件.
3. **Headline** (Noto Sans SC 300, `clamp(30px,4.6vw,56px)`, line-height 1.15, letter-spacing -0.01em): 「今天有 6 件事等你签，约 4 分钟。」
   - 「6 件」 is wrapped in a span with a 2px pen underline.
   - It recounts live. At 1 item: 「还有 1 件等你签，约 1 分钟。」 At 0: 「都签完了。」
   - Time estimate: 拍板 20s, 验收 45s, 上报 40s, 批准 30s, 红线 60s, rounded up to minutes.
4. **Standfirst** (sans 17px/1.8, ink-2, 2 lines max, all figures derived): 「昨晚交付 2 张工单，花了 $9.60。PawLog 的离线同步卡住了，需要你定方向。本月预算用了 43%，按现在速度够用。」
5. **Station ruler** (desktop 44px, full main width, 6 equal cells split by hairlines).
   - Each cell: station name (13px 500) and a count in Source Serif 4 22px.
   - If 待签 items sit at that station: a pen dot plus a count, e.g. 「● 2 等你」.
   - Initial values: 收件 3（● 3 等你分流）· 梳理 1（● 1）· 拆解 2 · 执行 3（● 1 批准 · 1 上报 in risk）· 验收 1（● 1）· 交付 本周 2.
   - Mapping of 待签 to stations: 拍板 → 梳理 (for 立项 questions and node questions); 批准 → 执行; 上报 → 执行 (risk dot); 验收 → 验收; 红线批准 → 交付.
   - Clicking a cell filters the 待签 stack below to that station. Clicking 收件 scrolls to the 收件 block.
6. **待签 stack**:
   - Header row: 「待签」 (h2 20px/500) + 「6 件 · 约 4 分钟」 + sort segmented 「按放行量 | 按等待时间」 + kind chips 「全部 6 · 拍板 2 · 批准 2 · 验收 1 · 上报 1」 + ‹ › buttons + link 「全部 →」 (to #/sign).
   - **Top document** is fully expanded (the Doc component, §4.2). Under it, two hairline "paper edges" offset 4px and 8px (1px rule lines, no shadow) indicate more sheets.
   - Remaining items are **compact register rows** (48px): KindTag · 「PawLog · 2.1.1 邀请链接与加入流程」 · one-line 签了之后 text · 「等了 6 小时」 (mono) · impact figure (Source Serif 4 tabular), e.g. 「上限 $6.50」 「+$1.20」 「测试 11/11」 「红线」. Clicking a row makes it the top document (240ms slide).
   - At most 5 rows show, then 「还有 N 件 →」.
   - With more than 6 items, rows group by 业务 with a group header.
   - Items that arrived after 08:30 carry a small mono tag 「新到 09:14」 and sit under a label 「08:30 之后新到 1 件」.
   - **已签 tray** under the stack: 「今天已签 2 件 ›」 expands to signed lines, each with a mini mark 「已通过 · 09:12 · D-0924-02」.
7. **Empty / complete state** (when 待签 = 0):
   - Headline: 「都签完了。」
   - Sub (sans 17): 「团队会按你的批示继续。下一件预计 11:30 左右到：PawLog 2.2.1 验收。」 (derived from the earliest running node's ETA).
   - Closing mark at the foot of the stack: pen-bordered rectangle 「本期已全部签完 · 09:16」 (unrotated).
8. **昨夜** (one line, expandable): 「昨夜 · 6 条记录 · 交付 2 张 · 花了 $9.60 ›」. Expanded:
   - Ledger rows: time (mono) · RoleMark · text · $ (right).
   - The subtotal row has the accounting double underline (1px + 3px gap + 1px).
9. **业务近况** (compact): one 52px row per active 业务:
   - Name (sans 500 16px).
   - Segmented progress bar, 160×4. Segments: accepted = ink, waiting on you = pen, running = ink-2, not started = rule.
   - 「5 / 11 已验收」, KindTags for blockers, 「还需 $22–31」.
   - Then a folded row 「其他 2 条 · 1 条已暂停 · 1 条已交付 ›」.
   - Row click → the 业务.
10. **收件** block: header 「收件 · 3 件等你分流」 + a button 「都照建议（3）」 (tap, 10s undo).
    - Rows: the idea in serif 20px (2-line clamp), a source line, a compact 分派单 line `[幕] 建议 并入 播客周报 · 2.2 邮件模板 · 预估 +$0.2–0.4`, and buttons 「同意」 (ink) + 「改为 ▾」 (ghost).
11. **想法去向** (one line, ink-2): 「本月交代 16 件：立项 5 · 并入 5 · 存档 3 · 等你分流 3。」 Each count links to 收件 filtered.
12. **Footer** (ink-3 12px): 「本页所有公司、业务和数字都是示例。」 · 「重置示例」.

**Margin column (sticky):**
- Figure 「本月已用」: `$34.15` (Source Serif 4 300, 44px) + 「/ 预算 $80」, plus a hairline budget bar (ink spent, hatched forecast range, a tick at $80).
- 「今日 $13.20」 · 「月底预估 $47–58（置信度 中）」 · 「按现在速度，本月预算够用」. Runway is shown only when it is shorter than the days left: 「按现在速度，预算还能用 N 天」 in risk colour.
- 「本周验收 2 张 · 上周 4」 + 4 thin bars [3,4,4,2] (last bar ink, others ink-3) + caption 「这是公司唯一的进度：你通过的工单」.
- 「授权 · 按批授权 · 单批上限 $15 ›」 (to #/ledger).
- 「最近决策」: the last 3 D-lines, mono serial + one line each.

**400px layout:** meta line → headline (30px) → standfirst → the top 待签 document with its sign block → compact rows → station ruler (3×2 grid) → 昨夜 → 业务近况 → 收件 → figures (2×2 grid) → footer.
**First screen must show the headline, the top document and its action button.**

**Live behaviour:** every 3s (unless 安静 or 停工), running nodes tick (§7.3), and the figures, standfirst and 值班 roll their digits (200ms vertical roll).

### 4.2 待签 (sign-off) · `#/sign`

**Purpose:** clear everything that needs you, fast, one document at a time or in bulk.

**Desktop layout:** inside the sheet, a 2-pane grid `340px | minmax(0,1fr)` split by a 1px rule.
- Left: a filter row (kind chips + sort) and the register list.
- Right: the reader, which shows one Doc (max 720px) and a top progress line 「第 2 件 / 共 6 件 · 约 3 分钟」 with a 2px pen progress rule.

**400px:** list only. Tapping a row pushes the reader full screen with a back header 「‹ 待签 2 / 6」 and the sign block sticky above the tab bar.

**Register row:** a 2px pen rule on the left when unsigned. KindTag, 「业务 · id 标题」, 「等了 6 小时」, impact. Signed rows drop to ink-3 with a mini mark. Verified 验收 rows (all criteria have passing evidence) show a checkbox. When ≥2 are checked, a bar appears: 「批量通过（2）」 (tap, 10s undo).

**Doc anatomy** (the same component on 晨报, 待签, the node sheet and iOS):

1. Header row:
   - KindTag: a 2-char tag in a 1px box. Pen for 拍板 / 批准 / 验收, risk for 上报.
   - Serial `S-0924-04`, 「PawLog · 3.1」, 「等了 3 小时」.
   - Red-line variant: a full-width risk-wash band above the header: 「红线 · 不管授权到哪一级，都要你亲自签」.
2. Title: sans 500, `clamp(20px,2.4vw,26px)`.
3. 来自 line: RoleMarks + text, e.g. `[检] 质检 · [工] Claude Code 团队 · Claude Sonnet 5 · 27 分钟 · 331k tokens · $2.95 实计`.
4. 情况: max 2 lines, sans 15.
5. 材料: evidence / batch table / attempts (per kind below).
6. 建议 line: `[幕] 幕僚长建议：…`.
7. 选项: radio rows, 48px, with key caps 1–3. The recommended row is preselected and tagged 「幕僚长建议」. Per-option impact is right-aligned in mono.
8. 签了之后 line (ink-2): e.g. 「签了之后：3.1.1、3.1.2 在 10 秒后开工，预计 35–50 分钟后到验收。」
9. Authority verdict (12.5 mono): 「在你的授权内（按批授权 · 单张工单上限 $6）」 or 「超过单张工单上限 $6，需要按住批准」.
10. **签字栏**:
    - Left: the 「你」 pen RoleMark.
    - Centre: a 1px ink signature rule, 240px, with 「你 · CEO」 in 12px ink-3 under it.
    - Right: a mono date that fills itself.
    - Below: the **SignControl** (44px, 2px radius, 1.5px pen outline, pen text; full width on phone, 320px on desktop). Its label always states the consequence (table below).

**SignControl behaviour:**

| Kind | Gesture | Label example |
|---|---|---|
| 拍板 | tap | 「确定：只有记录者本人和管理员能删」 |
| 验收 | tap (primary) · 「退回…」 secondary ghost | 「通过验收」 |
| 上报, option within caps | tap | 「按这个方向继续 · +$1.20」 |
| 上报, option over a cap | hold 600ms | 「按住批准 · 换 Claude Opus 5.5 再试 · +$2.80」 |
| 批准 (batch) | hold 600ms | 「按住批准 · 第 3 批，上限 $6.50」 |
| 红线, cap raise, 授权 raise | hold 1200ms; disabled until the 材料 block has been scrolled ≥80% into view, showing 「先看完材料」 | 「按住批准 · 播客周报上线」 |

- **Hold:** pointerdown, or keydown Enter/Space while focused, starts a pen-wash fill sweeping left to right (rAF, linear). At the same time a 1.5px pen line draws along the signature rule (stroke-dashoffset). Releasing early drains it back in 150ms and nothing is recorded.
- **Complete:**
  - A mark presses onto the right end of the signature rule: a pen-bordered rectangle, **not rotated**, 「已批准」 (sans 700 13px) over mono 「09:12 · D-0924-03」. Scale 1.06→1, opacity 0→1, 160ms.
  - The control is replaced by 「撤回（10）」 with a live countdown.
  - Money kinds add: 「10 秒后开工，可撤回」. Agents start only when the countdown ends.
  - After 600ms the Doc folds (height collapse, 280ms) into its signed line in the 已签 tray, and the next document rises (translateY 8→0, 320ms).
- **Tap kinds** mark immediately with the same mark, e.g. 「已确定 · 09:13 · D-0924-04」 or 「已通过 · 09:12 · D-0924-02」, plus a 10s 「撤回」.
- **撤回** restores the doc, the state, the counts and the decision log (it deletes the D-entry and restores the serial counter).
- **退回:**
  - An inline textarea (placeholder 「哪里不对？例如：链接改成 24 小时过期」).
  - A 「口述」 button simulates voice and fills 「邀请链接改成 24 小时过期，过期后提示对方重新邀请。」.
  - Button 「退回给工程」 (tap, disabled while empty).
  - The reason goes to 决策记录 as 退回. The node returns to 执行 with 「返工」. Receipt: 「[工] 收到退回原因，按这个返工」.
- **Accessibility:** `aria-label` states the full consequence and hold time, e.g. 「按住约 0.6 秒批准：第 3 批，上限 $6.50」. An `aria-live=polite` region announces 「已批准，决策 D-0924-03」.
- **Reduced motion:** a hold becomes tap-to-arm (label 「再点一次确认批准」, 4s timeout) and then tap to confirm. There is no fill animation.

**The six initial documents**, in default 按放行量 order (`releaseScore` given):

1. **批准 · PawLog 第 3 批 · 推送提醒** (S-0924-01, score 2, 等了 3 小时)
   - 来自 `[规] 规划 · [财] 财务`.
   - 情况: 「里程碑 3 的第一批，2 张工单。」
   - Batch table (工单 / 人选 / 预估 / 时长 / 验收材料):
     - 3.1.1 接入 APNs 推送 · Claude Sonnet 5 · $2.4–3.6 · 约 25 分钟 · 真机录屏、测试
     - 3.1.2 提醒时间设置页 · Claude Haiku 4.5 · $1.7–2.7 · 约 15 分钟 · 页面截图
   - 合计 「$4.10–6.30 · 35–50 分钟 · 置信度 中（同类 9 张）」.
   - 本批上限 stepper: default $6.50, step $0.50, range $4.50–15.00. Changing it rewrites the button label.
   - Secondary text button 「只批 3.1.1」 (re-labels to 「按住批准 · 只批 3.1.1，上限 $3.60」).
   - 签了之后 「3.1.1、3.1.2 在 10 秒后开工，预计 35–50 分钟后到验收。」
2. **上报 · PawLog 2.2.2 离线同时写入的冲突处理** (S-0924-02, score 1.5, 等了 4 小时)
   - 来自 `[工] Claude Code 团队 · Claude Sonnet 5`.
   - 情况: 「测试连续失败 3 次。两台设备同时离线记同一餐，联网后出现重复记录。根因是设备时钟不一致，去重失效。」
   - Attempts (mono):
     - 03:10–03:22 尝试 1 · 重复记录 2 条 · $1.30
     - 03:52–04:05 尝试 2 · 改成客户端去重，时钟不一致仍然重复 · $1.45
     - 04:46–05:02 尝试 3 · 加版本号后离线合并丢了 1 条 · $1.60
     - Total 「已花 $4.35 · 41 分钟 · 已暂停」.
   - Options:
     1. 改用服务端时间戳和去重键 · +$1.20 · 幕僚长建议
     2. 换 Claude Opus 5.5 再试一次 · +$2.80
     3. 第一版先不支持离线写入 · 省 $2
   - 签了之后 「2.2.2 继续，里程碑 2 不再卡在这里。」
3. **验收 · PawLog 2.1.1 邀请链接与加入流程** (S-0924-03, score 1.2, 等了 6 小时)
   - 来自 `[检] 质检 · [工] Claude Code 团队 · Claude Sonnet 5 · 27 分钟 · 331k tokens · $2.95 实计`.
   - 材料, 2 columns (stacked on phone):
     - Left, a mock phone screen (CSS): title 「邀请家人」, a QR (a CSS grid of 21×21 cells from a seeded pattern), 「pawlog.app/j/8KQ2」, 「7 天内有效 · 随时可撤销」.
     - Right: 「✓ 11 / 11 测试通过」 (pass colour) + 3 test names in mono: `creates invite with 7d expiry` · `joins household via token` · `revoked token is rejected`.
     - Then the 标准 ↔ 材料 table: 生成 7 天有效的邀请链接 → 测试 1、截图 / 对方打开链接后加入同一个家庭 → 测试 2 / 链接可以随时撤销 → 测试 3.
   - 签了之后 「计入进度：PawLog 6 / 11 已验收，本周验收 3 张。」
4. **拍板 · PawLog 2.3.1 谁可以删除喂食记录** (S-0923-05, score 1, 等了 15 小时)
   - 来自 `[规] 规划`.
   - Title 「家里有人想删掉一条喂食记录，应该怎么处理？」
   - Why line 「为什么问你：这决定数据表的权限规则，以后改代价大。」
   - Options: 任何成员都能删 / 只有记录者本人和管理员能删（幕僚长建议）/ 删除需要管理员确认. Plus a link 「其他想法：说或写」 (opens the capture line prefilled 「#2.3.1 」).
   - 签了之后 「2.3.1 进入第 3 批待批，预估 $0.8–1.2。」
5. **批准 · 红线 · 播客周报上线** (S-0923-04, score 1, 等了 12 小时)
   - Risk band.
   - 情况: 「2.1.1、2.2.1 验收后，9 月 28 日周一 07:00 首次发给 12 位订阅者。」
   - 红线 items, each with a lock glyph: 「对真实用户发送消息」 「部署到正式环境」.
   - 材料: a mock email preview (subject 「本周播客摘要 · 9 月第 4 周」, 3 bullet lines), and the recipient count 「12 位订阅者（示例）」.
   - Hold 1200ms, gated by scroll. Label 「按住批准 · 播客周报上线」.
6. **拍板 · 市集地图 立项：3 个问题** (S-0922-03, score 0.5, 等了 2 天)
   - 情况: 「回答之前不会花钱。」
   - Primary tap button 「开始回答（约 1 分钟）」 → `#/charter/market`.

Sort 「按等待时间」 orders by wait, longest first.

Empty state: 「待签清空了。下一件预计 11:30 左右到：PawLog 2.2.1 验收。」 + link 「回到晨报」.

### 4.3 交代 + 分流 + the signature interaction 「说一句，签一笔」

**Entry points:**
- The hero line on 晨报.
- The fixed bottom bar on other pages (desktop).
- The centre mic tab (phone).
- Keys: `/` focuses the nearest capture input. `M` toggles simulated recording (only when focus is not in a text field). `⌘K` / `Ctrl+K` also focuses capture.

**Context scoping:**
- On a 业务 page the bar pre-inserts a token chip 「@PawLog」.
- With a node selected it inserts 「#2.2.2」.
- Tokens render as 1px-bordered inline chips (removable with Backspace).

**Live 分流 chip:** appears once 4+ characters are typed and re-evaluates on input. The rules, in order:

| Match | Result | Chip text |
|---|---|---|
| Starts with `#<id>` | 批注 on that node → 修订稿 | 「批注 PawLog · 2.2.2」 |
| Contains 汇报 / 进度 / 卡在 / 还能花 | status query | 「汇报」 |
| @业务 token | 并入 that venture | 「并入 PawLog」 |
| 猫 / 喂 / 猫粮 / PawLog | 并入 PawLog (3.2 when it contains 粮 / 快吃完 / 提醒买) | 「像是 PawLog 的事 · 靠近 3.2 预测下一次喂食时间」 |
| 播客 / 周报 / 摘要 | 并入 播客周报 | 「像是 播客周报 的事」 |
| 市集 / 摊位 | 并入 市集地图 | 「像是 市集地图 的事」 |
| Starts with 感觉 / 好像 / 最近, and length < 16 | 存档 | 「像一句感想 · 建议存档」 |
| Otherwise | 立项 | 「像一件新事 · 建议立项」 |

Clicking the chip opens a menu: 并入… (业务 list) / 立项 / 存档. The choice overrides the rule, and the chip shows 「你改的」.

**Simulated voice (no microphone access):**
- The mic turns pen-filled. A 5-bar waveform animates (CSS keyframes with staggered delays) and a timer counts `0:00` upward.
- The raw transcript types in at 35ms per character (ink-3 characters settling to ink over 300ms): 「嗯，那个，猫粮快吃完的时候能不能提醒我买一下，就是根据每天喂多少算一下还能吃几天」
- Stop (click the mic again, press `M`, or the script auto-stops at the end):
  - The fillers 「嗯，」 「那个，」 「就是」 get a 1px ink-3 strike drawn left to right (200ms), hold 400ms, then collapse their width (250ms).
  - The field ends with the 整理稿 「猫粮快吃完时提醒我买。按每天的喂食量估算还能吃几天。」
  - A chip 「原始录音 0:23 · 保存 30 天」 attaches under the field.
- Typed input skips this step.
- If the mic is started while text already exists, the script appends.
- A second scripted utterance is used on the iPhone preview (§4.10).

**Send** (Enter or 「交给幕僚长」), the orchestrated moment. Default durations are given below. Under reduced motion every step's end state appears at once.

1. **Lift (320ms FLIP):** the sentence leaves the input and settles as the header of a new **Receipt** block. On 晨报 it goes directly under the hero. Elsewhere, the 交代 sheet (desktop: a bottom sheet anchored to the main column, max-width 760, 72vh, top shadow; phone: 90vh) stays open and shows it. Font size animates from 40 to 22px, serif. The input clears immediately. The 收件 nav count rolls +1 and the station ruler 收件 cell +1.
2. **Receipt lines print** down a 1px vertical spine, 350–600ms apart. Each is `time (mono 64px) | RoleMark | text`, fading in and rising 4px over 180ms, with a 1ch pen caret blinking at the end of the line being written. History receipts elsewhere render static.
   - `09:14:02 [幕] 收到。原始录音 0:23 已保存，去掉口头语 3 处。`
   - `09:14:03 [幕] 要点：余量估算 · 快吃完时提醒`
3. **分派单 fills in** as a hairline-bordered block (no fill, 12px label column). Rows appear 180ms apart:

   ```
   分派单 · 幕僚长 · 09:14
   建议    并入现有业务
   业务    PawLog 喂猫记录
   挂在    3.2 预测下一次喂食时间（还没拆）
   承办    [规] 规划 · Claude Opus 5.5
   预估    $3.1–5.0（连同 3.2 一起拆）· 约 1 小时
   需要你  1 个拍板                      ← pen
   理由    和喂食预测用同一份数据
   ```

   - Buttons: 「同意」 (ink primary) · 「改为 ▾」 · 「存档」.
   - The Track in the block header now shows 收件 ✓ and 梳理 current (pen dot).
   - **Nothing happens until the CEO taps.** If the CEO leaves, the idea waits in 收件 as 「等你分流」.
4. **同意** (tap):
   - `09:14:10 [你] 同意：并入 PawLog · 3.2` (pen text).
   - The 分派单 folds to one line. A 1.5px ink line draws from the 幕 mark to the 规 mark down the spine (stroke-dashoffset, 600ms).
   - A 值班 chip `[规] 规划 · PawLog 3.2 · 拆解中` appears.
   - `09:14:11 [规] 读了 PawLog 档案和 3.2 的现状。`
5. **拍板 inline** (a compact Doc, tap kind): 「猫粮余量从哪来？」. Why: 「为什么问你：决定要不要多一个录入步骤。」 Options:
   1. 买粮时记一下重量，按每天喂食量扣减（幕僚长建议）
   2. 只按喂食次数粗估
   3. 接入购物平台的订单 · with the tag 「红线 · 接入外部服务」

   It also appears in 待签 as 拍板 (count +1) until answered. After the tap: `09:14:20 [你] 拍板：买粮时记重量，按喂食量扣减 · D-0924-0x`.
6. **拆解:** `09:14:21 [规] 把 3.2 拆成 4 张工单`. A mini outline unfolds under it, rows 60ms apart, with a connector hairline drawing in:

   ```
   + 3.2.1 读取最近 14 天喂食记录        [工] Claude Haiku 4.5   $0.5–0.8   测试
   + 3.2.2 计算平均间隔，预测下一次喂食   [工] Claude Sonnet 5    $1.0–1.6   测试
   + 3.2.3 首页显示下一次喂食时间         [工] Claude Haiku 4.5   $0.6–1.0   截图
   + 3.2.4 猫粮余量估算，剩 3 天时提醒    [工] Claude Sonnet 5    $1.0–1.6   测试 · 截图   新 · 收 0924-02
   ```

   - Simultaneously, the PawLog tree in state gets these nodes (status 就绪), so they exist if the CEO opens the 业务 now.
   - `09:14:22 [财] 预估 $3.1–5.0 · 约 1 小时 · 置信度 中（同类 11 张）`
   - The Track: 拆解 ✓.
7. **Authority gate:** `09:14:23 [幕] 按批授权：这一批要你批准。` An inline **批准 Doc** prints: 「PawLog 第 4 批 · 3.2.1–3.2.4」, 本批上限 stepper $5.00, verdict 「在单批上限 $15 内」, SignControl 「按住批准 · 第 4 批，上限 $5.00」. It is also added to 待签 (tag 「新到 09:14」), and the headline recounts to 「今天有 7 件事等你签…」.
8. **Sign (hold 600ms):**
   - The mark 「已批准 · 09:14 · D-0924-0x」 appears.
   - A receipt line with a countdown: 「10 秒后开工，可撤回」.
   - At 0: `[工] Claude Code 团队 · Claude Haiku 4.5 接手 3.2.1` and `[工] Claude Code 团队 · Claude Sonnet 5 接手 3.2.4`, and 「3.2.2、3.2.3 排队（依赖 3.2.1）」.
   - Two new 值班 chips appear.
   - The Track 执行 segment gets the gliding highlight.
9. **Demo fast-forward:** a prototype-only text button 「快进（演示）」, with an ink-3 dashed underline and the tag 「演示」.
   - `[工] 3.2.4 交付 · 18 分钟 · $1.12` then `[检] 3.2.4 验收材料：截图 1 张 · 测试 7/7 · $0.12`.
   - An inline **验收 Doc** renders: a mock phone home screen with 「下一次喂食 18:30」 and 「猫粮还够 5 天」, 「✓ 7 / 7 测试通过」, and the criteria 「根据近 14 天喂食量估算剩余天数」 「剩 3 天时推送提醒」 「买粮时两步内记下重量」.
   - It is added to 待签 as well.
10. **通过** (tap):
    - The mark 「已通过」.
    - The Track completes: 交付 ✓.
    - The last receipt: `[幕] 已交付。这件事共花 $1.24，用时 38 分钟（演示时间）。`
    - 本周验收 rolls 2→3 (or 3→4 if 2.1.1 was already accepted).
    - The 收件 entry state becomes 「已交付」.

**Other send outcomes:**

- **汇报** (e.g. 「汇报一下 PawLog」): the Track is only 收件 → 汇报. A single 幕 receipt paragraph, derived from state: 「PawLog：11 张工单已验收 5 张。卡在 4 处：2.2.2 上报（测试连续失败 3 次）、2.3.1 等你拍板、3.1 等你批准、2.1.1 等你验收。本月花了 $18.40，还需 $22–31（置信度 中），预计 9 月 30 日 ±2 天完成第一版。」
  - 「这个月还能花多少」 → 「本月预算 $80，已用 $34.15，还剩 $45.85。按近 7 天日均 $2.68，月底预估 $47–58，够用。」
- **批注** (`#2.2.2 先不做离线写入`): the receipt shows `[规] 按你的批注起草了修订稿` plus the 修订稿 block (§4.6). 采纳 resolves the related 上报 doc with the mark 「已由修订稿处理」.
- **立项:** the 分派单 says 建议 立项 with 需要你 「最多 3 个问题」. 「同意」 opens `#/charter/:id`.
- **存档:** 同意 files it. The receipt reads 「[幕] 存档了。每周一汇总存档时会再提给你。」

### 4.4 收件 · `#/inbox`

**Purpose:** every idea ever said, what the 幕僚长 proposes, and what each became.

**Layout:**
- h1 「收件」 (sans 400, `clamp(26px,3.2vw,36px)`).
- The 幕僚长 note (sans 15, ink-2), followed by the 幕 RoleMark and 「幕僚长」 (no dash signature): 「本周交代了 4 件：1 件已立项，3 件等你分流。这周 3 次提到和猫有关的事，都在 PawLog 里。」
- Segmented filter 「等你分流 3 · 已并入 · 已立项 · 已交付 · 存档」.
- A button 「都照建议（3）」.

**Row (desktop grid `minmax(0,7fr) minmax(0,5fr)`, gap 32, hairline separators):**
- Left:
  - Mono meta 「收 0923-03 · 昨天 23:40 · 网页」 or 「iPhone 语音 · 0:09」.
  - The idea in serif 20px.
  - Voice entries: a 「原始录音 0:09 ▸」 chip (a fake 3s progress bar when played) and a 「看原话」 toggle that shows the raw transcript with fillers struck.
- Right: the full **DispatchSlip** (label/value rows, as §4.3) plus actions 「同意」 / 「改为 ▾」 / 「存档」.
  - 改为 → another 业务 rewrites 业务 / 挂在 / 承办 / 预估, with fields refilling at a 120ms stagger.
- Processed rows: a full-width **Track** under the row with labels and per-station time + RoleMark. Current station: pen (waiting on you) or ink-2 glide (working).
  - 「展开回执」 shows the static Receipt.
  - 「已成为 PawLog 3.2.4」 links to the node.
- **400px:** the slip goes under the text; the Track becomes vertical (a 6-row list with time and mark).

**Initial ideas:** see §5.6.

**Weekly archive note** at the bottom, shown because the demo date is a Thursday and it reads as a summary: 「存档 3 件 · 周一 20:00 汇总一次」, with themes 「咖啡 ×1 · 效率工具 ×1 · 阅读 ×1」.

### 4.5 立项 (clarify + animated decomposition) · `#/charter/market` and `#/charter/star`

**Purpose:** turn a new idea into a priced L0–L3 plan with ≤3 single-choice questions, spending nothing until you approve.

**Layout:** left-anchored document column max 760px. Margin (≥1180): 「立项前不花钱」 in the label style, and an estimate figure that narrows after each answer: 「$6–30」 → 「$9–22」 → 「$11–20」 (Source Serif 4, 36px, digit roll). At <1180 the estimate is a line under the title.

**Elements:**
1. Label `[幕] 立项 · 市集地图（示例）· 来自 收 0922-02 · 还没花钱`.
2. **原话**, the CEO's words: serif 26px, pen-coloured quote marks 「」, 2px ink rule on the left: 「周末想逛市集，但每次都不知道这周哪里有。想要一张地图，把附近的市集都标出来，还能看有哪些摊位。」 + 「原始录音 0:31 ▸」.
3. 「幕僚长的理解」: 3 short sans lines: 「给周末想逛市集的人用。核心是这周哪里有市集。摊位信息是加分项。」
4. **Question block:**
   - Pips `● ○ ○` + mono 「1 / 3」 (a real sequence).
   - The question in sans 500 28px, the why line, and 3 option rows (56px, key caps 1–3), with the default tagged 「幕僚长建议」.
   - Questions (default marked *):
     1. 主要给谁用？ 只给我自己 / 同城的朋友们* / 公开给所有人. Why 「决定要不要做登录和分享」.
     2. 市集信息从哪里来？ 我自己手动录入* / 摊主自己提交 / 从公众号、小红书自动整理. Why 「决定数据怎么进来，最后一项会碰红线：抓取外部内容」.
     3. 第一版做成什么？ 网页* / iOS App / 微信小程序. Why 「决定用哪支执行团队和多久能看到东西」.
   - Answering (tap or key) crossfades to the next with an 8px rise (220ms). Each answer writes 「拍板」 to 决策记录 immediately.
   - Links: 「全部用默认」 (answers the rest with defaults and marks them 「假设」) and 「上一题」.
5. **Generating** (after Q3, about 1.4s):
   - A 规 row 「规划 · Claude Opus 5.5 · 正在拆解」.
   - 3 lines with CSS spinners that turn to ✓ in sequence: 「读你的原话和 3 个回答」 「拆出里程碑和功能」 「给每张工单写验收标准和预估」.
6. **The plan appears, animated level by level:**
   - Desktop ≥1024: **结构图**. Connectors draw with stroke-dashoffset, L0 at 0ms, L1 at 260ms, L2 at 520ms, L3 at 780ms, 40ms stagger per sibling. Nodes fade in as their stroke arrives. Estimates fade in last (+300ms).
   - Otherwise **大纲**: rows rise 6px with a 40ms stagger.
   - Tree: §5.4. The platform word follows answer 3: 网页 → 「网页地图页」, iOS App → 「iOS 地图页」, 微信小程序 → 「小程序地图页」. Assumed answers get a dotted underline + superscript 「假设」.
7. **Summary figures:** 「预估 $11–20 · 置信度 低（新业务没有历史）· 约 10 月 8 日 ±3 天 · 工单 8 张」.
   - 「派工（交给幕僚长）」 row: `[规] Claude Opus 5.5 · [工] Claude Code 团队 · Claude Sonnet 5 / Claude Haiku 4.5 · [检] Claude Haiku 4.5` + link 「在团队页调整」.
8. **签字栏**: 「按住批准 · 立项市集地图，首批上限 $7」 (hold 600ms; first batch = milestone 1: 1.1.1, 1.1.2, 1.2.1, 1.2.2, $4.1–6.8). Plus a text button 「先只要计划，不花钱」.
   - Approve: 10s undo → the venture becomes 建设中 and 1.1.1 starts (值班 chip). Navigate to `#/biz/market/tree`. Toast 「市集地图已立项。首批 4 张工单 10 秒后开工。」
   - Plan only: the venture becomes 「筹备中 · $0」. The decision is logged 「立项：只要计划」.

`#/charter/star` (the GitHub star board idea) uses the same screen with its own questions and tree (§5.5).

### 4.6 业务 · 拆解 · `#/biz/:id/tree`

**Purpose:** see the whole plan L0–L3 with who holds each 工单, where it is stuck and what it costs. Edit directly, or 批注 and review a 修订稿.

**Header** (shared by the 3 tabs):
- Crumb 「业务 / PawLog」.
- h1 「PawLog 喂猫记录（示例）」.
- 源头 (CEO's words, serif 20px): 「想做个 App，家里人一起记猫吃了没，到点提醒一下，别重复喂也别忘了喂。」 + mono 「收 0911-01 · 0:19」.
- L0 (company text, sans 17 ink-2): 「愿景：让养猫的家庭一起记录喂食，到点提醒」 + the 假设 note 「假设：先做 iOS，后端用 Supabase」.
- **Figures row** (Source Serif 4 300 28px, labels 12px): 「已验收 5 / 11」 · 「已花 $18.40 / 上限 $60」 · 「还需 $22–31 · 置信度 中」 · 「预计 9 月 30 日 ±2 天」 · 「授权 按批」. It wraps to 2 columns at 400px.
- **卡在** line: 「卡在 4 处：」 followed by clickable KindTag chips: 「上报 2.2.2」 「拍板 2.3.1」 「批准 3.1」 「验收 2.1.1」. Each opens the node sheet.
- Station ruler (this venture only).
- Meta: 「github.com/you/pawlog · 执行团队 Claude Code、Codex」.
- Tabs 「拆解 · 账目 · 档案」 (text, 2px underline).

**Toolbar:** 「展开到 里程碑 | 功能 | 工单」 · filter 「全部 | 等你 | 执行中 | 已验收」 · 「按角色」 select (全部 / 工程 / 质检 / 规划) · view 「结构图 | 大纲」 (default 结构图 at ≥1024, 大纲 below) · a legend toggle.

**结构图:**
- A scroll container (`overflow-x:auto`), sheet-2 background inset with a 1px rule. **The only horizontal scroll on the page.**
- Columns: 愿景 240 · 里程碑 200 · 功能 212 · 工单 280. Gap 48, row pitch 56, mono column heads.
- Nodes are absolutely positioned HTML (1px rule border, 2px radius, sheet fill, 44px tall). Connectors are one SVG layer with cubic curves in rule colour (1.5px). Paths to waiting nodes are pen at 60%.
- L0: an ink-filled block, sheet-colour text.
- L1: title + fraction 「1 / 5」 + a 3-part segment bar (ink done / pen waiting / ink-2 running).
- L3 node: status mark, mono id, title (ellipsis), and on the right the RoleMark 「工」 with a 2-letter model hint (`So`, `Ha`, `Op`, `Cx`) in mono.
- 待拆解 nodes: dashed border, 「待拆解 · $3–6」.
- A pending 修订稿 shows dashed pen ghost nodes for additions and struck titles for removals.

**大纲:**
- Indented 16px per level, with collapsible L1/L2 rows (caret).
- L3 row: status mark · mono id · title · leader dots · right columns 「人选」 「$ 实计 or 预估」 「验收材料」. At 400px only status + title + $.

**Status marks (shape + text, never colour alone):**

| State | Mark | Text |
|---|---|---|
| 已验收 | ✓ in ink | 已验收 |
| 执行中 | ● ink with a 1.6s pulse + % | 执行中 62% |
| 就绪 / 排队 | ○ ink-3 | 就绪 / 排队 |
| 待拆解 | dashed outline | 待拆解 |
| 等你 | ● pen + KindTag (拍板 / 批准 / 验收) | 等你拍板 / 等你批准 / 等你验收 |
| 上报 | a risk-filled 12px square with 「!」 | 上报 |
| 已搁置 | title struck through, ink-3 | 已搁置 |
| 假设 | dotted underline + superscript | 假设 |

Waiting nodes also get a pen-wash background.

**Interactions:**
- Click a node → **NodeSheet**. Arrow keys move the selection. Esc closes.
- Double-click a title → inline edit. Enter saves and logs 「手动修改：你改了 2.2 的标题」.
- Hovering an L3 shows a tooltip 「2.2.1 订阅喂食记录的变更 · 执行中 62% · Codex · $2.40」.
- 「按角色」 dims non-matching nodes to 25%.

**NodeSheet** (desktop 460px right slide-over with a shadow and a 28% scrim that does not block the tree scroll; phone 88vh bottom sheet):

1. Header:
   - Level label 「L3 工单 · 2.1.1」.
   - Editable title (sans 500 22px).
   - State line with KindTag.
   - Source: 「来自你 9 月 11 日：」 + a serif excerpt if the node was spawned by an idea (3.2.4 shows 「来自 收 0924-02」).
2. **流转**: the 6-station Track with lines under the passed stations, e.g.
   - 「拆解 09-12 · [规] Claude Opus 5.5」
   - 「执行 09-24 01:47–02:14 · [工] Claude Code 团队 · Claude Sonnet 5 · 331k · $2.95」
   - 「验收 09-24 02:31 · [检] Claude Haiku 4.5 · 11/11」
3. **Action block** by status:
   - 验收 / 拍板 / 批准 / 上报 = the same Doc body and SignControl as 待签.
   - 执行中 = a progress bar, elapsed, ticking $, and a mono log tail in a sheet-2 well: 「09:41 读取项目档案」 「09:43 新增 useFeedingsRealtime」 「09:52 写了 6 个测试，4 个通过」 「09:58 正在修复重连后重复订阅…」.
   - 已验收 = the evidence, read-only, + 「D-0918-02 你通过」.
   - 待拆解 = 「还没拆。批注“拆细”让规划起草。」
4. **验收标准**: a checklist. Each item has an evidence chip (测试 / 截图 / 演示 / 文档) and is editable inline. 「+ 加一条」. Edits log 手动修改. Header note 「开工前定好，质检按这个准备材料」.
5. **派工**:
   - 执行团队 select (Claude Code 团队 / Codex 团队).
   - 人选 select (4 models + 「交给幕僚长」).
   - Reason line 「为什么是它：增删改查类工单，Claude Sonnet 5 首次通过率 94%（同类 16 张）」.
   - Changing a select shows an effect preview row: 「换成 Claude Opus 5.5：这张 $0.8–1.2 → $1.5–2.3；首次通过率约 81% → 90%（同类 9 张）」 with buttons 「确认调整」 / 「算了」. Confirm logs 「派工：2.3.1 人选改为 Claude Opus 5.5」.
6. **花费**: 「已花 $2.95 实计 · 331k tokens · 27 分钟」 or 「预估 $2.4–3.6 · 约 25 分钟」.
7. **依赖**: e.g. 「3.2.2 依赖 3.2.1」.
8. **批注 composer** (sticky at the sheet bottom):
   - Chips 「拆细」 「换方案」 「省点钱」 「换人做」 「不做了」.
   - An input 「对这里批注…」 + mic (simulated: fills 「这里先做简单版」) + 「发出」.
   - On send: a row `[规] 规划正在改…` shows for 600ms, then the **修订稿** block:
     - Banner 「规划的修订稿 · 基于你对 2.2.2 的批注「不做了」」.
     - Diff lines in a sheet-2 well, mono: `+` rows underlined in pass colour, `−` rows struck in ink-3, `~` rows showing old struck + new underlined. Each row carries its RoleMark + model + $.
     - Deltas: 「预估 −$0.8 ~ −$2.1 · 工期 −1 天 · 首次通过率约 71% → 88%（同类 7 张）」.
     - 「将写入 D-0924-0x」.
     - Buttons 「采纳修订」 (ink) · 「不采纳」 · 「再改一句」 (reopens the composer with the previous 批注 quoted).
     - While pending, the tree shows ghost nodes.
     - 采纳: the ghosts go solid (300ms), removed nodes collapse (250ms), the log is written, toast 「拆解已更新，记进了决策记录」, and a static receipt is added to 收件 as a 批注 entry.
     - 不采纳: the ghosts clear and 「不采纳」 is logged.
   - Canned 修订稿 templates are in §5.7.

### 4.7 业务 · 账目 · `#/biz/:id/money`

- Budget bar: 已花 $18.40 (ink) | 已批未花 up to $3.84 (pen hatch; the batch 2 cap $14 minus $10.16 used) | 预估 $40–49 (dotted band) | a marker 「上限 $60」. Mono 「3.13M tokens · 实计」.
- **Cumulative chart** (SVG, 640×240 viewBox, width 100%, inside its own scroll container at <480px, min-width 480):
  - Ink line for actual spend (§5.9 PawLog series).
  - An ink 10% forecast band from today to 10-01 (low 40, high 49).
  - A risk dashed line for the cap 「上限 $60」 and a today marker.
  - Hover shows a crosshair and tooltip 「09-18 · 累计 $6.70 · 当天 $0.40」.
- 「按人选」 bars: Claude Sonnet 5 $11.24 (1.29M) · Claude Opus 5.5 $2.52 (0.38M) · Codex $2.40 (0.32M) · Claude Haiku 4.5 $2.24 (1.14M).
- 「按阶段」 line: 「梳理与拆解 $2.52 · 执行 $15.00 · 验收 $0.88」.
- **授权 for this 业务**: segmented 「逐项问我 | 按批授权 | 预算内全权」 with 「沿用公司默认」 or 「覆盖了公司默认」 note, plus a 上限 stepper. Raising either one needs an inline 签字栏 (hold 1200ms). Lowering applies at once and is logged.

### 4.8 业务 · 档案 · `#/biz/:id/file`

Two columns (5/7), stacked at ≤760.

- Left:
  - **一页纸** (editable inline; click a paragraph to edit, blur saves and logs 「手动修改：一页纸 · 不做什么」):
    - 为谁 「家里有 1–3 只猫、2–4 个家庭成员」
    - 做什么 「一起记录喂食，到点提醒，别重复喂也别忘了喂」
    - 不做什么 「Android、多语言、智能喂食器」
    - 假设 「先做 iOS，后端用 Supabase」
    - 原则 「记录一次不超过两步」
  - Then 「上次修改：你 · 09-18」.
  - **执行团队 for this 业务**: toggle rows. Claude Code 团队 ✓ · Codex 团队 ✓ · Cursor 后台 Agent 「未签约」 + 「去团队页签约」. Turning one off shows 「2.2.1 会改派给 Claude Code 团队 · 预估 +$0.3」 with 「确认」.
  - **代码仓库**: 「github.com/you/pawlog · main · 最近提交 09-24 02:14 feat: household invite」 + 「CLAUDE.md ✓ · AGENTS.md ✓」.
  - **上下文包**: mono list 「BRIEF.md 1.2k tokens · DECISIONS.md 0.8k · TREE.json 2.1k · 仓库」 + note 「每次派工都附上这些。换人选、换执行团队，读的都是同一份。」
- Right: **决策记录**. A filter by kind. Each row: mono D-serial · date · RoleMark (你 / 幕) · KindTag-style plain tag · text · a node link. New entries slide in at the top (6px rise). Data in §5.8.

### 4.9 业务一览 · `#/biz`

- Header figures (Source Serif 4 300, `clamp(36px,5vw,56px)`): 「5 条业务」 · 「2 条在推进」 · 「本周验收 2 张」.
- A full-width table with 72px rows and hairlines, inside its own container at ≤760 where it becomes stacked rows. Columns:
  - 业务: name sans 500 17 + L0 in ink-3 13.
  - 阶段: 立项中 / 建设中 / 已暂停 / 已交付.
  - 进度: 「5 / 11」 + segment bar.
  - 卡点: KindTags, or 「无」.
  - 已花 / 上限.
  - 还需.
  - 预计.
  - 授权.
- Rows:
  - PawLog 喂猫记录: 建设中 · 5/11 · 上报 拍板 批准 验收 · $18.40 / $60 · $22–31 · 9 月 30 日 ±2 天 · 按批
  - 播客周报: 建设中 · 2/4 · 批准(红线) · $6.30 / $30 · $3–5 · 9 月 27 日 ±1 天 · 预算内全权
  - 市集地图: 立项中 · 拍板 0/3 · 「还没花钱」 · 预估 $11–20 · 待定 · 按批
  - Folded 「其他 2 条 ›」: 读书卡片 已暂停 09-08 · 3/7 · $3.20 / $20 · 「暂停中不花钱」 and 记账快捷指令 已交付 09-10 · 3/3 · $4.10 / $10.
- Sort by 卡点 (default) / 花费 / 进度 / 预计. A KindTag click opens that Doc in 待签. A row click opens the 业务.

### 4.10 账本 (money + autopilot) · `#/ledger`

**Top band**, four figures (Source Serif 4 300, `clamp(40px,6vw,80px)`):
- 「本月已用 $34.15」 with a double underline, 「预算 $80」.
- 「今日 $13.20」.
- 「近 7 天日均 $2.68」.
- 「月底预估 $47–58」 + 「置信度 中」.

Then the sentence 「按现在速度，本月预算够用。」 and 「5.96M tokens · 全部实计」.

**Chart:** cumulative company spend 9-01 → 9-30. Ink line to today, forecast band to 9-30 ($47–58), budget line $80 (risk dashed), today marker, hover tooltip 「09-15 · 累计 $12.95 · 当天 $2.10」. Its own container. A range switch 「本月 | 全部」 (identical data; 全部 just relabels).

**Breakdowns:**
- **按业务** table: PawLog $18.40 · 播客周报 $6.30 · 记账快捷指令 $4.10 · 读书卡片 $3.20 · 幕僚长日常（收件、晨报、分流）$2.15 · 市集地图 $0.00. The total row has a double underline: $34.15.
- **按人选** bars (ink, with tabular values and tokens): Claude Sonnet 5 $16.94 · 1.93M / Claude Opus 5.5 $7.07 · 1.07M / Codex $5.60 · 0.68M / Claude Haiku 4.5 $4.54 · 2.28M.
- **按执行团队**: Claude Code 团队 $21.48 · API key · 实计 / Codex 团队 $5.60 · API key · 实计 / 幕僚长与规划（Sprout 内置）$7.07 · 实计. Note 「订阅制团队拿不到逐次成本，只记运行时长，标为估算。」
- **本周验收**: 4 weekly bars 「9/1 3 · 9/7 4 · 9/14 4 · 9/21 2」 + 「这是北极星：你点了通过的工单数」.

**授权 section** (full width):
- Three option rows (radio style, 64px):
  - 「逐项问我 · 每张工单开工前都问你」
  - 「按批授权 · 你批一批和上限，批内自动做（默认）」
  - 「预算内全权 · 月度预算内自己推进，超了或碰到红线再问你」
- A current-behaviour sentence: 「现在：公司默认按批授权。播客周报覆盖为预算内全权。」
- Caps with steppers: 「月度预算 $80」 · 「单批上限 $15」 · 「单张工单上限 $6」. A hit cap pauses the work and files an 上报: note 「碰到上限会自动暂停，并发来一份上报」.
- Any **raise** (a higher 授权 level or a higher cap) inserts an inline 签字栏, 「按住批准 · 授权改为 预算内全权」 (1200ms). **Lowering** is immediate. Both log 授权 and toast 「授权改为 按批授权」.
- Per-业务 matrix: one row per venture (segmented control + 上限 + 本月已用).
- **红线** list, headed by a 2px risk rule: 「删除或迁移数据」 「部署到正式环境、上架 App Store」 「接入付费服务或外部服务」 「使用或改动密钥」 「对真实用户发送消息」 「提高预算、上限或授权」. Each has a lock glyph (an inline SVG padlock). Caption: 「不管授权到哪一级，这些都要你亲自签。」 Not editable.

### 4.11 团队 (org + routing) · `#/team`

**Org (the page's one moment of grandeur):**
- Desktop: a left-anchored row. The CEO tile, then a 1px ink bus line, then 5 role tiles (200×248 each, 1px rule border, radius 0, gap 24). It scrolls inside its own container if it is narrower than the content.
- Each tile has a **giant cropped glyph**: Noto Sans SC 900, 190px, line-height .8, positioned bottom-right at -18px/-24px so the card edge crops it, colour ink at 7% (dark mode 9%).
- Tile text, top-left: role name sans 500 17, 人选 13 ink-2, duties 13 ink-3, and at the bottom 「本月 $4.92」 + status 「在岗 · 1 项」 / 「待命」.
- Tiles:
  - 「你」 CEO, pen border: 「只做两件事：说和签」 「待签 6」.
  - 幕 幕僚长 · Claude Opus 5.5 · 收件、晨报、分流、提问 · 本月 $2.15.
  - 规 规划 · Claude Opus 5.5 · 拆解、验收标准、预估 · 本月 $4.92.
  - 工 工程 · Claude Code 团队（Claude Sonnet 5、Claude Haiku 4.5）· Codex 团队（Codex）· 本月 $25.20 · 首次通过率 78%（同类 18 张）.
  - 检 质检 · Claude Haiku 4.5 + 自动截图 · 测试、截图、演示录屏 · 本月 $1.88.
  - 财 财务 · 规则计算 · 记账、预估、授权检查 · 「不单独计费」.
- The sum check is shown under the row: 「合计 $34.15」.
- ≤760: tiles in a 2-column grid (width calc(50% - 6px), height 200), glyph 140px; the CEO tile spans 2 columns.

**派工策略:**
- Segmented 「省钱 | 均衡 | 质量优先 | 手动」 (default 均衡; the first three are auto modes labelled 「交给幕僚长」).
- Effect line: 「按均衡，PawLog 剩下的预估 $22–31；省钱 $14–19；质量优先 $41–58。」
- Switching re-renders the rows. The PawLog header 还需 rolls to the new range. The change is logged 派工 with toast 「派工策略改为 质量优先」.

**岗位分工 table** (岗位 → 人选 select → 为什么 → 首次通过率). Selects are disabled unless 手动:

| 岗位 | 人选 | 为什么 | 首次通过率 |
|---|---|---|---|
| 规划与拆解 | Claude Opus 5.5 | 拆错一次返工最贵 | — |
| 常规编码（增删改查） | Claude Sonnet 5 | 这类工单通过率最高 | 94%（同类 16 张） |
| 难题（并发、同步） | Claude Opus 5.5 | 2.2.2 这类问题 Sonnet 连续失败 | 80%（同类 5 张） |
| 小改动与页面 | Claude Haiku 4.5 | 便宜，页面有截图兜底 | 86%（同类 7 张） |
| 实时与后端集成 | Codex | PawLog 手动指定 | 67%（同类 3 张） |
| 质检与截图 | Claude Haiku 4.5 | 按标准跑，便宜 | — |
| 卡住后接手 | Claude Opus 5.5 | 失败 3 次后升级 | — |

**已签约团队:** Claude Code 团队 「云端沙盒 · 已签约」 · Codex 团队 「API key · 已签约」 · Cursor 后台 Agent 「未签约」 + a button 「签约」.
- 签约 opens an inline mini form: 「API key」 input (masked, no real auth).
- Then a 签字栏 「按住签约 · Cursor 后台 Agent 可以读写你的仓库」 (1200ms, because it grants repo access, a red line).
- Then the row shows 「已签约」 and the team appears in 业务 · 档案 toggles.

**隐私** line: 「原始录音保存 30 天」 select (7 天 / 30 天 / 90 天 / 不保存) · 「代码不用于训练」.

### 4.12 随身 (iOS preview) · `#/ios`

- Intro, left-aligned: 「手机只做三件事：交代、签、验收。改拆解、派工、看账本在网页上做。」
- Three phone frames: 300×620, 40px radius, 1px rule outline, a 10px sheet-2 bezel, a Dynamic Island pill (96×28 ink). Left-aligned in a row on desktop, stacked at ≤760 (max-width 100%). Each has a 13px caption: 「交代」 「待签」 「验收」.
- Interiors reuse the same tokens and components.
- Above phone 1: a Live Activity mock bar 「[工] 2 项在跑 · 今日 $13.20」. Above phone 2: a notification mock 「幕僚长 · PawLog 2.1.1 已交付 · 测试 11/11 · $2.95 · 看材料」.

1. **Phone 1 · 交代**
   - A 120px hold-to-talk circle (ink; pen while recording) with the caption 「按住说，松开交给幕僚长 · 锁屏小组件、操作按钮、分享也能用」.
   - Press starts the simulated transcript (serif 18px) of 「嗯，给播客周报加个功能，每周挑一集最值得听的放在最上面」 → cleaned 「给播客周报加个功能：每周挑一集最值得听的放在最上面。」
   - Release: the compact 分派单 「建议 并入 播客周报 · 2.1 要点」 with 「同意」 「改为」.
   - Below: the last 3 交代 items, each with its Track (6 dots) and 「在谁手里」: 「在 [规] 规划手里 · 拆解中」 / 「等你拍板」 / 「已交付」.
   - This creates a real idea in the web state + toast 「手机交代了一件事，在收件里」.
2. **Phone 2 · 待签**
   - Header 「6 件 · 约 4 分钟」. The top Doc in compact form, two hairline edges under it.
   - Tap kinds: a 「通过」 / 「确定」 button, or swipe right (pointer drag > 80px).
   - Swipe left = 「稍后」 (moves it to the end).
   - 批准: hold on the sign rule (600ms) with a text hint 「按住签 · 会有轻震动」. Red-line docs show 「需要面容 ID」 as a second step button (simulated, tap).
3. **Phone 3 · 验收**
   - Full-bleed mock screenshot of 2.1.1 (the invite screen), a dot pager of 2 screenshots.
   - 「✓ 11 / 11 测试通过」, the 3 criteria ticked, 「$2.95 · 27 分钟 · Claude Sonnet 5」.
   - Thumb-zone buttons 「通过」 / 「退回」. 退回 opens a hold-mic that fills a reason by script.
   - This calls the same action as the web; the 晨报 count, the 本周验收 figure and the node state update.

---

## 5. Sample data

All names, amounts and repos are fictional and shown as examples. **All totals shown in the UI are derived from these records**; the expected initial values are listed so the build can be checked.

### 5.1 Company & clock

- Company: 「远山一人公司」 (示例). Founded 9-01.
- Demo clock: starts at **2026-09-24 周四 09:12:00** on load and advances in real time.
- Budget: 月度预算 $80 · 单批上限 $15 · 单张工单上限 $6 · default 授权 按批授权.
- Decision serial: today's counter starts at 02 (D-0924-01 already exists: the phone acceptance at 07:55).

### 5.2 Ventures

| id | Name | Stage | 源头 (CEO words) | L0 | Repo / teams | 授权 · 上限 | Spent (Sept) |
|---|---|---|---|---|---|---|---|
| pawlog | PawLog 喂猫记录 | 建设中 since 09-12 | 「想做个 App，家里人一起记猫吃了没，到点提醒一下，别重复喂也别忘了喂。」 (收 0911-01, 0:19) | 让养猫的家庭一起记录喂食，到点提醒 | github.com/you/pawlog · Claude Code、Codex | 按批 · $60 | $18.40 |
| pod | 播客周报 | 建设中 since 09-16 | 「每周一早上给我一封邮件，把我订阅的播客这周讲了什么说清楚。」 (收 0915-02) | 每周一早上收到订阅播客的摘要 | github.com/you/pod-digest · Claude Code | 预算内全权 · $30 | $6.30 |
| market | 市集地图 | 立项中 | 「周末想逛市集，但每次都不知道这周哪里有。想要一张地图，把附近的市集都标出来，还能看有哪些摊位。」 (收 0922-02, 0:31) | (generated) | none yet | 按批 | $0.00 |
| books | 读书卡片 | 已暂停 09-08 | 「读完一本书，自动做一张能分享的摘抄卡片。」 | 读完一本书就有一张能分享的卡片 | github.com/you/book-cards | 按批 · $20 | $3.20 (3/7 已验收) |
| ledger | 记账快捷指令 | 已交付 09-10 | 「用快捷指令一句话记一笔账。」 | 一句话记一笔账 | github.com/you/quick-ledger | 按批 · $10 | $4.10 (3/3) |
| (ops) | 幕僚长日常 | n/a | n/a | n/a | Sprout 内置 | n/a | $2.15 |

Company total: 18.40 + 6.30 + 0 + 3.20 + 4.10 + 2.15 = **$34.15**.

### 5.3 PawLog tree (main venture; 23 nodes, 11 executable L3 + 2 待拆解 branches)

Columns: id · title · status · 人选 / team · cost · tokens · time · ETA or estimate · 验收标准 · evidence.

| id | L | Title | Status | 人选 · 团队 | $ | tok | 时长 | Est / ETA | 验收标准 (evidence) |
|---|---|---|---|---|---|---|---|---|---|
| 0 | L0 | 让养猫的家庭一起记录喂食，到点提醒 | n/a | n/a | n/a | n/a | n/a | n/a | 假设：先做 iOS，后端用 Supabase |
| 1 | L1 | 一个人能记录喂食 | 已交付 09-18 (4/4) | | | | | | |
| 1.1 | L2 | 喂食记录的增删改查 | rollup | | | | | | |
| 1.1.1 | L3 | 数据模型与 API | 已验收 09-13 | Claude Sonnet 5 · Claude Code 团队 | 1.84 | 212k | 18 分钟 | n/a | POST /feedings 可以创建记录 (测试) · 按天分页查询 (测试) · 份量必须大于 0 (测试) · tests 24/24: `creates feeding record` `paginates by day` `rejects zero amount` |
| 1.1.2 | L3 | 记录喂食页面 | 已验收 09-16 (退回 1 次) | Claude Sonnet 5 · Claude Code 团队 | 2.10 | 248k | 22 分钟 | n/a | 两步之内完成一次记录 (截图) · 可以选择是哪只猫 (截图) · 默认填入当前时间 (测试) |
| 1.2 | L2 | 喂食历史 | rollup | | | | | | |
| 1.2.1 | L3 | 按天分组的时间线 | 已验收 09-17 | Claude Haiku 4.5 · Claude Code 团队 | 0.52 | 260k | 15 分钟 | n/a | 按天分组，最新的在上面 (截图) · 显示记录人和份量 (截图) |
| 1.2.2 | L3 | 按猫筛选记录 | 已验收 09-18 | Claude Haiku 4.5 · Claude Code 团队 | 0.38 | 190k | 9 分钟 | n/a | 可以只看一只猫 (截图) · 筛选后数量正确 (测试 6/6) |
| 2 | L1 | 家庭成员共享记录 | 1/5 | | | | | | |
| 2.1 | L2 | 邀请家人 | rollup | | | | | | |
| 2.1.1 | L3 | 邀请链接与加入流程 | **等你验收** | Claude Sonnet 5 · Claude Code 团队 | 2.95 | 331k | 27 分钟 | n/a | 生成 7 天有效的邀请链接 · 对方打开链接后加入同一个家庭 · 链接可以随时撤销 · tests 11/11 + 2 screenshots |
| 2.1.2 | L3 | 成员列表与移除 | 已验收 09-22 | Claude Haiku 4.5 · Claude Code 团队 | 0.46 | 230k | 11 分钟 | n/a | 显示所有成员 (截图) · 管理员可以移除成员 (测试 5/5) |
| 2.2 | L2 | 多台设备实时同步 | rollup | | | | | | |
| 2.2.1 | L3 | 订阅喂食记录的变更 | **执行中 62%** (started 08:51) | Codex · Codex 团队 | 2.40 (ticks) | 318k | 21 分钟 | 预计 09:40 前交付 · 还需 $0.8–1.2 | A 手机记录后 2 秒内出现在 B 手机上 (演示) · 断网重连后自动补齐 (测试) |
| 2.2.2 | L3 | 离线同时写入的冲突处理 | **上报** (paused 05:02) | Claude Sonnet 5 · Claude Code 团队 | 4.35 | 497k | 3 次 · 41 分钟 | fix $1.2–2.8 | 两台设备离线各记一次，联网后不重复 (测试) · 冲突时保留两条并提示 (截图) |
| 2.3 | L2 | 成员权限 | rollup | | | | | | |
| 2.3.1 | L3 | 谁可以删除喂食记录 | **等你拍板** | Claude Haiku 4.5 (planned) | 0 | n/a | n/a | $0.8–1.2 | 按选定规则限制删除 (测试) · 没有权限时说明原因 (截图) |
| 3 | L1 | 到点提醒喂食 | 0/2 | | | | | | |
| 3.1 | L2 | iOS 推送提醒 | rollup | | | | | | |
| 3.1.1 | L3 | 接入 APNs 推送 | **等你批准** (第 3 批) | Claude Sonnet 5 · Claude Code 团队 | 0 | n/a | n/a | $2.4–3.6 · 约 25 分钟 | 到设定时间收到推送 (演示：真机录屏) · 点推送直接打开记录页 (测试) |
| 3.1.2 | L3 | 提醒时间设置页 | **等你批准** (第 3 批) | Claude Haiku 4.5 · Claude Code 团队 | 0 | n/a | n/a | $1.7–2.7 · 约 15 分钟 | 每只猫可以设多个提醒 (截图) · 有人喂过就不再提醒 (测试) |
| 3.2 | L2 | 预测下一次喂食时间 | **待拆解** | n/a | n/a | n/a | n/a | $3–6（未拆，置信度 低） | 假设：用最近 14 天的记录 |
| 4 | L1 | 上架 App Store | **待拆解** | n/a | n/a | n/a | n/a | $9–10 | tag 「红线 · 上架」 |

Plus PawLog non-node lines: 规划 (Claude Opus 5.5) $2.52 · 380k; 质检 (Claude Haiku 4.5) $0.88 · 460k (of which the 2.1.1 materials at 02:31 cost $0.12).

Check: node spend 1.84+2.10+0.52+0.38+0.46+2.95+2.40+4.35 = 15.00; + 2.52 + 0.88 = **$18.40** ✓. 已验收 5 / 11 ✓. Milestone 1 4/4 ✓.

Batches: 第 1 批 (1.1.1–1.2.2) 上限 $6, used $4.84. 第 2 批 (2.1.1, 2.1.2, 2.2.1, 2.2.2) 上限 $14, used $10.16 (+2.2.1 ticks). 第 3 批 = the pending 批准 doc.

还需 check: 2.2.1 0.8–1.2 + 2.2.2 1.2–2.8 + 2.3.1 0.8–1.2 + 3.1 4.1–6.3 + 3.2 3–6 + 4 9–10 + 规划/质检 3–4 ≈ **$22–31** ✓.

Nodes added by the signature flow (§4.3): 3.2.1–3.2.4 with their estimates (sum $3.1–5.0); 3.2.4 delivered at $1.12 + 质检 $0.12 = $1.24.

**播客周报 tree:**
- 0 每周一早上收到订阅播客的摘要.
- 1 抓取与转写:
  - 1.1 订阅源 → 1.1.1 拉取 RSS: 已验收 09-18, Claude Haiku 4.5, $0.40, 150k.
  - 1.2 转写 → 1.2.1 音频转文字: 已验收 09-24 07:55 on the phone, Claude Sonnet 5, $2.10, 236k, 测试 9/9.
- 2 摘要邮件:
  - 2.1 要点 → 2.1.1 每集 5 条要点: 执行中 40% (started 08:40), Claude Sonnet 5, $1.20 (ticks), 135k.
  - 2.2 邮件 → 2.2.1 邮件模板: 排队, Claude Haiku 4.5, est $0.3–0.6.
- Non-node: 规划 Opus $1.60 · 240k; 质检 Haiku $1.00 · 520k.
- Check: 0.40 + 2.10 + 1.20 + 1.60 + 1.00 = **$6.30** ✓. Progress 2/4.

### 5.4 市集地图 generated tree (default answers)

```
0  让同城朋友周末能快速找到附近的市集和摊位                     假设：只在一个城市
1  能在地图上看到这周的市集
   1.1 市集录入
       1.1.1 录入市集（名称、地点、时间）   Claude Haiku 4.5   $0.8–1.4   截图
       1.1.2 批量导入往期市集               Claude Haiku 4.5   $0.6–1.0   测试
   1.2 地图展示
       1.2.1 网页地图页，标出本周市集       Claude Sonnet 5    $2.0–3.2   截图 · 演示
       1.2.2 按日期筛选                     Claude Haiku 4.5   $0.7–1.2   测试
2  能看到摊位
   2.1 市集详情
       2.1.1 市集详情页与摊位列表           Claude Sonnet 5    $1.6–2.6   截图
   2.2 收藏
       2.2.1 收藏市集，周五提醒             Claude Sonnet 5    $1.5–2.5   测试
3  分享给朋友
   3.1 分享
       3.1.1 生成分享链接和预览图           Claude Sonnet 5    $1.2–2.0   截图
   3.2 上线
       3.2.1 部署到正式环境                 Claude Haiku 4.5   $0.5–1.0   红线
```

Sum $8.9–14.9, plus 规划 and 质检 overhead, gives **$11–20**. First batch (milestone 1) $4.1–6.8, 首批上限 $7.
- If answer 1 = 只给我自己: drop 3.1.1 and change L0 to 「让我周末能快速找到附近的市集和摊位」.
- If answer 2 = 从公众号、小红书自动整理: 1.1.1 becomes 「自动整理公众号、小红书的市集信息」 with the tag 「红线 · 抓取外部内容」.

### 5.5 星标看板 (charter from inbox idea 收 0923-03)

- Questions:
  - 看哪些仓库？ 我自己的公开仓库* / 加上我 star 过的 / 手动挑选
  - 放在哪？ 网页* / 菜单栏小工具 / 每周邮件
  - 多久更新？ 每天* / 每周 / 打开时
- Tree:
  - 0 「一眼看到我所有 side project 的 star 变化」
  - 1 看板能用:
    - 1.1 数据 → 1.1.1 拉取仓库和 star 数 (Haiku $0.6–1.0)
    - 1.2 页面 → 1.2.1 看板页和排序 (Sonnet $1.8–2.8) · 1.2.2 近 30 天趋势线 (Sonnet $1.4–2.4)
  - 2 自动更新:
    - 2.1 定时 → 2.1.1 每天定时刷新 (Haiku $0.5–0.9)
- Total **$8–14**, 置信度 低, 首批上限 $5.

### 5.6 收件 ideas (initial)

| Serial | Time · source | Idea (serif) | State | 分派单 |
|---|---|---|---|---|
| 收 0924-01 | 今天 07:40 · iPhone 语音 0:14 | 播客周报的邮件标题能不能带上本周最火的那一集 | 等你分流 | 并入 · 播客周报 · 挂在 2.2 邮件 · 承办 [规] · 预估 +$0.2–0.4 · 需要你 0 · 理由 「只是模板里多一个字段」 |
| 收 0923-03 | 昨天 23:40 · 网页 | 做一个把我所有 side project 的 GitHub star 汇总起来的小看板 | 等你分流 | 立项 · 新业务「星标看板」· 预估 $8–14 · 需要你 最多 3 个问题 · 理由 「和现有业务都没关系」 |
| 收 0923-02 | 昨天 19:05 · iPhone 语音 0:09 | 感觉最近咖啡喝太多了 | 等你分流 | 存档 · 理由 「更像一句感想，周一汇总时再看」 |
| 收 0922-02 | 09-22 · iPhone 语音 0:31 | (市集地图 源头) | 已立项 · 等你拍板 | track: 收件 ✓ 梳理 ● (pen) |
| 收 0920-01 | 09-20 · 分享 | 播客周报里加一个“本周值得听”的排行 | 已并入 播客周报 2.1 · 执行中 | track: 收件 ✓ 梳理 ✓ 拆解 ✓ 执行 ● |
| 收 0911-01 | 09-11 · iPhone 语音 0:19 | (PawLog 源头) | 已立项 · 执行中 5/11 | track to 执行 ● |
| 收 0908-02 | 09-08 · 网页 | 用快捷指令一句话记一笔账。 | 已交付 · 共 $4.10 | full track ✓ |
| 收 0916-03 | 09-16 · 网页 | 想学一下手冲 | 存档 | n/a |
| 收 0914-01 | 09-14 · iPhone 语音 0:06 | 读书卡片先停一下 | 并入 读书卡片 · 已暂停 | n/a |

The demo flow adds 收 0924-02 (the 猫粮 idea). Month summary: 交代 16 件 = 立项 5 · 并入 5 · 存档 3 · 等你分流 3 (the rows not listed above are hidden under 「更早 7 件」, count only).

### 5.7 Canned 修订稿

- **2.2.2 「不做了」 (also the `#2.2.2 先不做离线写入` query):**
  - `− 2.2.2 离线同时写入的冲突处理`
  - `+ 2.2.3 离线时禁用记录按钮，联网后再记 · Claude Haiku 4.5 · $0.4–0.7`
  - `~ 一页纸 · 不做什么：+ 第一版不支持离线记录`
  - Deltas: 「预估 −$0.8 ~ −$2.1 · 工期 −1 天」.
- **2.2.2 「换人做」:** `~ 承办 Claude Sonnet 5 → Claude Opus 5.5`. Deltas: 「预估 +$1.6 · 首次通过率约 71% → 88%（同类 7 张）」. This exceeds the per-ticket cap, so 采纳 becomes a 600ms hold.
- **2.2.2 「换方案」:** `~ 2.2.2 改用服务端时间戳和去重键`, `+ 2.2.4 旧数据补去重键 · Claude Haiku 4.5 · $0.3–0.5`. Deltas: 「预估 +$1.2–1.8」.
- **3.1.1 「省点钱」:** `~ 人选 Claude Sonnet 5 → Claude Haiku 4.5`. Deltas: 「预估 $2.4–3.6 → $1.1–1.8 · 首次通过率约 90% → 76%（同类 7 张）」.
- **3.2 「拆细」:** produces 3.2.1–3.2.3 (as §4.3, without 3.2.4). Deltas: 「预估 $3–6 → $2.1–3.4 · 置信度 低 → 中」.
- **Generic fallback for any other node:**
  - 拆细: `+ {id}.a 先做最小版本`, `+ {id}.b 补全边界情况`, cost split 40/70% of the original.
  - 省点钱: the model steps down one tier.
  - 换人做: the model steps up.
  - 不做了: `−` the node, cost freed.
  - 换方案: `~ {title}（换个做法）`, ±15%.

### 5.8 决策记录 (PawLog + company)

| Serial | By | Kind | Text |
|---|---|---|---|
| D-0912-01 | 你 | 立项 | 立项 PawLog，首批上限 $6 |
| D-0912-02 | 你 | 拍板 | 后端选 Supabase，因为自带实时订阅和登录 |
| D-0912-03 | 你 | 拍板 | 第一版只做 iOS |
| D-0915-01 | 你 | 退回 | 退回 1.1.2：记录要两步完成，原稿要四步 |
| D-0918-01 | 你 | 派工 | 规划用 Claude Opus 5.5，执行默认用 Claude Sonnet 5 |
| D-0918-02 | 你 | 验收 | 里程碑 1 全部通过 |
| D-0922-01 | 你 | 批准 | 第 2 批（2.1.1、2.1.2、2.2.1、2.2.2），上限 $14 |
| D-0922-02 | 你 | 派工 | 2.2.1 交给 Codex 团队（实时订阅，手动指定） |
| D-0923-01 | 幕 | 授权 | 播客周报沿用你 09-16 的设置：预算内全权 |
| D-0924-01 | 你 | 验收 | 在手机上通过 播客周报 1.2.1 |

### 5.9 Overnight log (昨夜, 22:00–08:30) and today

| Time | Mark | Text | $ |
|---|---|---|---|
| 01:47 | 工 | PawLog 2.1.1 开工 · Claude Code 团队 · Claude Sonnet 5 | n/a |
| 02:14 | 工 | PawLog 2.1.1 邀请链接与加入流程 交付，等你验收 | 2.95 |
| 02:31 | 检 | 2.1.1 验收材料备好：测试 11/11、截图 2 张 | 0.12 |
| 03:40 | 工 | 播客周报 1.2.1 音频转文字 交付，测试 9/9 | 2.10 |
| 05:02 | 工 | PawLog 2.2.2 试了 3 次都失败，已暂停并上报 | 4.35 |
| 07:55 | 你 | 在手机上通过 播客周报 1.2.1 | n/a |
| 08:30 | 幕 | 晨报发出 | 0.08 |

Subtotal **$9.60** (double underline). Today after 08:30: 08:40 播客 2.1.1 开工 ($1.20 so far), 08:51 PawLog 2.2.1 开工 ($2.40 so far). **今日 = $13.20.**

### 5.10 Spend series (company, daily $ for September; cumulative is derived)

```
09-01 0.90  09-02 0.60  09-03 0.70  09-04 0.50  09-05 0.30  09-06 0.00  09-07 0.20   (读书卡片 = 3.20)
09-08 1.20  09-09 1.70  09-10 1.20                                                    (记账快捷指令 = 4.10)
09-11 0.10  09-12 1.60  09-13 1.50  09-14 0.40  09-15 2.10  09-16 1.30  09-17 1.10
09-18 1.30  09-19 1.60  09-20 0.60  09-21 0.90  09-22 0.80  09-23 0.35
09-24 13.20 (live: derived from today's runs)
```

Cumulative through 09-23 = 20.95. Today = 13.20. **Month = 34.15.** 近 7 天 (09-18..09-24) = 18.75, so 日均 $2.68. Month-end forecast = 34.15 + 6.6 × 2.68 ≈ 51.8, shown as **$47–58（置信度 中）**.

PawLog cumulative: 09-12 1.60 · 13 3.10 · 14 3.50 · 15 5.60 · 16 5.90 · 17 6.30 · 18 6.70 · 19 7.40 · 20 7.70 · 21 8.10 · 22 8.40 · 23 8.58 · 24 18.40. Forecast band to 10-01: $40–49. Cap $60.

By model (month): Sonnet 16.94 / 1.93M · Opus 7.07 / 1.07M · Codex 5.60 / 0.68M · Haiku 4.54 / 2.28M (sum $34.15, 5.96M tokens).
By team: Claude Code 21.48 · Codex 5.60 · 幕僚长与规划 7.07.
By role: 幕 2.15 · 规 4.92 · 工 25.20 · 检 1.88.

Weekly accepted: [3, 4, 4, 2]. Station ruler initial values: 收件 3 · 梳理 1 · 拆解 2 · 执行 3 · 验收 1 · 交付 本周 2.

---

## 6. Visual system

### 6.1 Tokens

```css
:root{
  --desk:#EBEDF0; --sheet:#FFFFFF; --sheet-2:#F4F5F7;
  --ink:#111418; --ink-2:#474D55; --ink-3:#6B717B;
  --rule:#D9DCE1;
  --pen:#2436C4; --pen-wash:#EAEDFC; --pen-on:#FFFFFF;
  --risk:#9A5B00; --risk-wash:#F8EFDD;
  --pass:#2F6B4F;
  --scrim:rgba(17,20,24,.28);
  --shadow-sheet:0 24px 64px -24px rgba(17,20,24,.30);
  --glyph-a:.07;
}
@media (prefers-color-scheme:dark){ :root:not([data-theme="light"]){
  color-scheme:dark;
  --desk:#0C0F13; --sheet:#13171D; --sheet-2:#1A1F26;
  --ink:#E8EBEE; --ink-2:#AEB5BE; --ink-3:#858D98;
  --rule:#313843;
  --pen:#8E9CFF; --pen-wash:#1B2140; --pen-on:#0C0F13;
  --risk:#E0A548; --risk-wash:#2A2114;
  --pass:#6FC39A;
  --scrim:rgba(0,0,0,.55);
  --shadow-sheet:0 24px 64px -16px rgba(0,0,0,.70);
  --glyph-a:.09;
}}
:root[data-theme="dark"]{ /* identical dark values */ }
body{ background:var(--desk); color:var(--ink); }
```

Contrast: ink-3 is ≥4.5:1 on sheet in both themes. Pen and risk are used as text only at ≥4.5:1. The dark rule #313843 on #13171D stays visible.

### 6.2 Fonts

`https://fonts.googleapis.com/css2?family=Noto+Serif+SC:wght@600&family=Noto+Sans+SC:wght@300;400;500;700;900&family=Source+Serif+4:opsz,wght@8..60,300;8..60,400;8..60,600&family=Source+Code+Pro:wght@400;500&display=swap`

- `--f-voice: "Noto Serif SC","Songti SC",serif;` for the **CEO's own words only, at ≥20px**: the capture line, 原话, 源头, and idea text in 收件.
- `--f-ui: "Noto Sans SC","PingFang SC","Microsoft YaHei",system-ui,sans-serif;` for all company text, UI and headlines. Weight 900 only for the 团队 glyphs.
- `--f-fig: "Source Serif 4","Noto Serif SC",serif;` for large figures only (≥22px), `font-variant-numeric: tabular-nums lining-nums`.
- `--f-mono: "Source Code Pro","Noto Sans SC",ui-monospace,monospace;` for time, ids, serials, $, tokens, logs, receipts, key caps. Tabular nums.

Type scale:

| Role | Spec |
|---|---|
| headline | Sans 300 `clamp(30px,4.6vw,56px)`/1.15 |
| capture line | Serif 600 `clamp(24px,2.8vw,40px)`/1.3 |
| h1 | Sans 400 `clamp(26px,3.2vw,36px)`/1.2 |
| doc title | Sans 500 `clamp(20px,2.4vw,26px)`/1.3 |
| h2 | Sans 500 20/1.3 |
| standfirst | Sans 400 17/1.8 |
| body | Sans 400 15/1.7 |
| small | 13 |
| label | Sans 500 12, letter-spacing .12em, ink-3 |
| mono | 12.5/1.7 |
| hero figures | Source Serif 4 300 `clamp(40px,6vw,80px)` |
| figure row | 28 |
| glyph tile | Noto Sans SC 900 190px (140 on phone) |
| RoleMark | 20×20 box, 12px/700 glyph |

No italics. Max line length 38 CJK characters in prose.

### 6.3 Spacing, radii, shadows, rules

- Spacing on a 4px base: 4 / 8 / 12 / 16 / 24 / 32 / 48 / 72 / 96. Section gap 48 on desktop, 32 on phone.
- Radii: surfaces 0, controls and tags 2px, the mic and status dots round, phone frames 40px.
- Shadows **only** on overlays (side sheet, bottom sheet, 交代 sheet, toast): `--shadow-sheet`. Content never has a shadow.
- Rules:
  - Hairline 1px `--rule` between rows.
  - 2px ink rule opens a section (12px above the section label).
  - Masthead double rule (1px + 2px gap + 3px).
  - Accounting double underline on totals (1px, 2px gap, 1px).

### 6.4 Colour meaning (strict)

- **Pen = the CEO's hand**, and only this: 待签 counts, KindTags 拍板 / 批准 / 验收, SignControl, signed marks, the capture caret, the 你 RoleMark, CEO receipt lines, waiting nodes, pen dots on the ruler, the recording mic.
  - Links are ink with a 1px underline, **never pen**.
  - Focus rings are 2px ink with a 2px offset.
- **Risk (ochre)** = 上报, 红线, over-cap, and budget lines on charts only. It never means "your turn". It always comes with a text label.
- **Pass (green)** = passed tests and `+` diff lines, as small text only.
- Everything else is grey scale. No department colours. No gradients.

Status encoding summary: every state has a shape and a word (§4.6 table). A KindTag is always a 2-character word in a 1px box.

### 6.5 Motion

- Easing `cubic-bezier(.2,.7,.1,1)`. Hover and press 120ms. Receipt line 180ms. Collapse and slide 240–320ms. Sheets open 360ms ease-out.
- **The one orchestrated moment:** 「说一句，签一笔」 (§4.3). Its steps: FLIP lift 320ms → receipt lines 350–600ms apart → 分派单 rows 180ms stagger → a handoff line drawn 600ms → mini outline rows 60ms stagger → hold fill 600ms → mark 160ms → 10s countdown → 值班 chip enters (8px slide).
- Other motion:
  - Digit rolls 200ms.
  - Plan generation (§4.5) < 1.8s total.
  - 修订稿 underlines grow and strikes draw at 240ms with a 60ms stagger.
  - Running hairline glide 2.4s linear.
  - Running dot pulse 1.6s.
  - Nothing moves at rest except running work.
- 安静模式 freezes tickers and pulses.
- `prefers-reduced-motion`: every animation is instant, holds become tap-to-arm then confirm, and no caret blink or glide. Counts and marks still update.

### 6.6 Banned looks (review will reject)

- Cream or beige grounds, terracotta, a lone acid-green or vermilion pop, purple-blue gradients, glassmorphism.
- Inter, Space Grotesk, or Geist as the voice.
- Centered hero layouts or a centered floating sheet. Everything left-anchored.
- Rounded-lg + shadow cards on content blocks. Chat bubbles. Avatars, faces, human names for AI roles.
- Numbered section markers (一 二 三, 01 02 03) that are not a real sequence. Only real sequences are numbered: 1.1.1, D-serials, 收 serials, 1 / 3 pips.
- Emoji anywhere. Em-dash asides in copy.
- Rotated rubber stamps and fake handwritten signatures.
- Blue links. Colour-only status.
- Department colour stripes. Ticking wages presented as precise for subscription work.

---

## 7. Interaction details

### 7.1 Keyboard

| Key | Action |
|---|---|
| `/`, `⌘K` / `Ctrl+K` | Focus capture (hero on 晨报, else the bottom bar, else open the 交代 sheet) |
| `M` (not in a field) | Start / stop simulated recording |
| `Enter` in capture | 交给幕僚长 · `Shift+Enter` newline · `Esc` blur (keeps the draft) |
| `G` then `S` / `B` / `I` / `L` / `T` | Go to 待签 / 业务 / 收件 / 账本 / 团队 |
| `J` / `K` or `←` / `→` | Next / previous document (晨报 stack, 待签) |
| `1`–`3` | Choose an option in the focused Doc |
| `Enter` on a tap-kind Doc | Confirm the preselected option (拍板 / 验收 通过 / 上报 within caps) |
| Hold `Enter` / `Space` on a focused SignControl | Hold-to-sign |
| `R` | Open 退回 on a 验收 Doc |
| `L` | 稍后 (move to the end, note 「明早晨报再提」) |
| `U` | 撤回 the last signature within 10s |
| `↑` / `↓` in 结构图 / 大纲 | Move the selection · `Enter` open sheet · `N` focus 批注 · `Esc` close sheet (focus returns to the node) |
| `?` | Shortcut sheet (a bottom sheet listing this table) |

Keys never fire while focus is in an input/textarea, except Enter/Esc for that field.

### 7.2 Toast copy (bottom-left; ink fill with sheet text, 2px radius, 3.4s, with an optional action)

- 「已交给幕僚长」 + 「看回执」
- 「已并入 PawLog · 3.2」 + 「撤回」
- 「都照建议分流了 3 件」 + 「撤回」
- 「已批准第 3 批，上限 $6.50。10 秒后开工。」 + 「撤回」
- 「已通过 2.1.1，本周验收 3 张」 + 「撤回」
- 「已退回 2.1.1，理由记进了决策记录」
- 「拆解已更新，记进了决策记录」
- 「派工策略改为 质量优先」
- 「授权改为 按批授权」
- 「全员停工了。进行中的工作保存了现场。」 + 「恢复」
- 「已恢复，2 项继续」
- 「手机交代了一件事，在收件里」
- 「市集地图已立项。首批 4 张工单 10 秒后开工。」
- 「示例已重置」

### 7.3 Live simulation

- Every 3s (if not 安静 and not 停工): each running node gets progress +1 (cap 97%) and cost + its rate (2.2.1 +$0.03, 播客 2.1.1 +$0.02, new 3.2.x +$0.02). Totals, the 今日 figure, the month figure, the standfirst % and 值班 chips all re-derive with a digit roll.
- 全员停工: hold 1200ms (masthead or 更多). Running nodes get status 暂停. The 值班条 is replaced by a risk-wash band 「已全员停工 · 09:20 · 2 项工作保存了现场」 + 「恢复」 (tap).

### 7.4 State & persistence

- One `state` object: `{clock, theme, quiet, halted, ventures, nodes (by venture), desk[] (derived from nodes plus venture-level items), ideas[], receipts{ideaId:[]}, decisions[], daily[], caps, authority{company, perVenture}, routing{strategy, rows}, ui{route, sel, sheet, sort, filter, stackIndex, pendingProposal, undo}}`.
- Every view is a pure `render(state)` into `#app`. Event delegation on `document`, using `data-act` attributes.
- **待签 is derived:** nodes with status question / approval / review / stuck, plus venture-level red-line docs and charters. This guarantees the same count everywhere.
- Undo: `ui.undo = {label, revert(), expiresAt}`. Only one at a time. A new signature commits the previous one.
- Persistence: `localStorage` holds only `theme` and `quiet`, wrapped in try/catch. All demo state is in memory. 「重置示例」 re-initialises from the seed.
- No `alert` / `confirm` / `prompt`. No `getUserMedia`. No iframes. External resources: Google Fonts only; no scripts are required (vanilla JS).
- File shape: starts with `<title>Sprout · 远山一人公司（示例）</title>` then `<link>`s for fonts, then `<style>`, markup, `<script>`. No doctype/html/head/body tags. Target 1,300–1,800 lines.

---

## 8. Acceptance checklist

**Artifact contract & robustness**
1. The file starts with `<title>` and has no `<!doctype>`, `<html>`, `<head>` or `<body>` tags. It has one `<style>`, inline script, fonts only from fonts.googleapis.com, and no other external scripts. No iframes.
2. No `alert` / `confirm` / `prompt` calls and no microphone or camera API calls (grep).
3. Zero console errors on load and after running every flow in items 10–33, in both themes.
4. `localStorage` access is wrapped in try/catch, and the page renders fully when storage throws.

**CEO framing**
5. The 晨报 hero shows the serif capture line 「今天要公司办什么？」 above the headline on desktop. On phone the centre mic tab is always visible.
6. The headline reads 「今天有 6 件事等你签，约 4 分钟。」 on load and recounts after each signature, reaching 「都签完了。」 plus the empty-state forecast sentence.
7. No AI role has a human name or face. Every receipt line, log line and L3 row carries a RoleMark (幕 / 规 / 工 / 检 / 财 / 你).
8. The CEO's own words (capture, 原话, 源头, idea text) are the only serif text, and none is below 20px.
9. Pen blue appears only on CEO-hand elements (§6.4). No link is pen-coloured.

**R1 / R2 capture & voice**
10. `/` focuses capture from every page. Enter sends. The bottom bar exists on every desktop page except while the 晨报 hero is visible.
11. Mic / `M` runs the simulated recording: waveform, timer, character streaming, the three fillers struck then collapsed, the 整理稿, and a 「原始录音 0:23 · 保存 30 天」 chip. 收件 has a 「看原话」 toggle showing the struck raw text.

**Processed → decomposed → executed (signature)**
12. Sending the 猫粮 sentence produces, in order: 幕 receipt lines, a 分派单 filling row by row, and **no filing until 「同意」 is tapped**.
13. 同意 → an inline 拍板 → answering prints the 4-node mini outline (3.2.1–3.2.4) with 人选 and $, then the 财 estimate, then an inline 批准 Doc also counted in 待签 (count 6→7).
14. Holding 600ms signs it, shows an unrotated mark with a D-serial, runs a 10s 撤回 countdown, then adds 值班 chips for 3.2.1 and 3.2.4. Releasing early records nothing.
15. 「快进（演示）」 produces a 验收 Doc with a mock screenshot and 「测试 7/7」. 通过 completes all 6 Track segments and 本周验收 increments.
16. The idea's 6-station Track is visible on 收件 and updates live. Hover shows station, time and role.

**R3 / R4 / R5 plan**
17. 市集地图 立项 asks exactly 3 single-choice questions one at a time with pips 1/3 → 3/3, keys 1–3 work, 「全部用默认」 marks 假设, and the estimate narrows $6–30 → $9–22 → $11–20.
18. After the questions, the L0–L3 plan animates in level by level (结构图 on desktop, 大纲 on phone) in under 2s, and the platform wording follows answer 3.
19. PawLog 拆解 shows the fixed columns 愿景 / 里程碑 / 功能 / 工单. L1/L2 roll up from L3. 展开到 works. 结构图 is default at ≥1024 and 大纲 below.

**R6 edit & 批注**
20. A double-click edits a node title inline. Enter saves and adds a 手动修改 entry to 决策记录.
21. 批注 「不做了」 on 2.2.2 shows a 修订稿 with + / − / ~ lines and deltas, and ghost nodes on the map. 采纳修订 applies it, logs it, and resolves the 2.2.2 上报 doc. 不采纳 reverts.
22. Typing `#2.2.2 先不做离线写入` in capture yields the same 修订稿.

**R7 / R8 / R9 context, agents, models**
23. 档案 shows the editable 一页纸, the 决策记录 (filterable, D-serials, author marks), repo, 执行团队 toggles and the context-pack list with its note.
24. 团队 shows signed teams plus Cursor 「未签约」. 签约 requires a 1200ms hold and then the team appears in 档案 toggles.
25. 派工 presets change the PawLog remaining forecast ($14–19 / $22–31 / $41–58). 手动 enables per-row selects. A node's 人选 change shows an effect preview and needs 「确认调整」.

**R10 / R11 / R12 progress & money**
26. The 值班条 is present and sticky on every page at 400px and desktop, ticks every 3s, and is frozen by 安静.
27. 业务 header 「卡在 4 处」 lists the four reasons as clickable tags, and the station ruler shows counts plus pen / risk dots.
28. 账本 totals reconcile: by 业务 = by 人选 = by 执行团队 = by role = $34.15 at load. The 昨夜 subtotal is $9.60 and 今日 is $13.20. Every $ has 实计 / 估算. Every forecast is a range with 置信度.
29. Both charts render a forecast band plus a budget line and a hover tooltip, and scroll inside their own container at 400px.

**R13 authority**
30. 批准 needs a 600ms hold. 红线 needs 1200ms and stays disabled (「先看完材料」) until the materials are scrolled into view. 拍板 / 验收 / 上报 within caps are single taps. All have a 10s 撤回 that fully reverts.
31. The 2.2.2 option 「换 Claude Opus 5.5 再试一次 +$2.80」 switches the control to a hold with the verdict 「超过单张工单上限 $6」.
32. Raising 授权 or a cap on 账本 inserts an inline hold-to-sign. Lowering applies immediately. Both are logged. The 红线 list is shown and not editable.
33. 全员停工 requires a hold, pauses all running nodes, shows the risk band, and 恢复 resumes.

**R14 evidence**
34. Every L3 shows 验收标准 with an evidence type before it starts. The 2.1.1 验收 Doc shows a mock screenshot, 「✓ 11 / 11 测试通过」 with test names, and a criteria↔evidence table.
35. 退回 requires a reason (typed, or simulated 口述). The reason appears in 决策记录 and the node returns to 执行 with 「返工」. Only 通过 increments 已验收 and 本周验收.

**Triage & four kinds consistency**
36. 收件 shows the 3 initial ideas with full 分派单s. 同意 / 改为 / 存档 and 「都照建议（3）」 work with 撤回. 改为 refills the slip fields.
37. The kind words 拍板 / 批准 / 验收 / 上报 and their colours are identical on 晨报, 待签, the 结构图 / 大纲, 业务一览 卡点 and the iOS phones.

**iOS**
38. 随身 shows 3 phone frames (交代 / 待签 / 验收). Signing or 通过 on a phone updates the web counts and node states. Phone 1 capture creates a 收件 entry.

**Responsiveness & theming**
39. At 400px: no horizontal page scroll (`document.documentElement.scrollWidth <= innerWidth`), 16px gutters, bottom tab bar with safe-area, side sheets as 88vh bottom sheets, and the sign block never overlaps the tab bar. The first screen of 晨报 shows the headline, the top Doc and its action.
40. Desktop ≥1180: the sheet is left-anchored with the main + margin grid, and nothing content-level is centered.
41. Light / dark follow the system. The 日 / 夜 toggle sets `data-theme` on `:root`. `body` has an explicit background. Dark hairlines are visible and pen / risk text pass 4.5:1.
42. `prefers-reduced-motion`: no animations, holds become arm-then-confirm, and states / counts / marks still update.

**Copy & visual quality**
43. All UI copy is Simplified Chinese, plain and direct. No emoji, no em-dash asides, no marketing words. Every example surface carries 「示例」 and the footer note is present.
44. Only the four model names Claude Opus 5.5 / Claude Sonnet 5 / Claude Haiku 4.5 / Codex appear.
45. None of the §6.6 banned looks are present: no content shadows, no cards with rounded-lg, no unreal numbered markers, no rotated stamps, no department colours.
