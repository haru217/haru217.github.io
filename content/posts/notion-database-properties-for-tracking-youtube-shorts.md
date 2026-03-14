---
title: "Notion database properties for tracking YouTube Shorts (simple, useful setup)"
date: 2026-03-14T23:46:00+09:00
draft: false
description: "A practical list of Notion database properties to track YouTube Shorts performance (views, retention, hooks, CTA) without overcomplicating your system."
tags: ["notion", "youtube-shorts", "analytics", "workflow"]
---

## TL;DR
- 最小構成は **Title / URL / Publish date / Topic / Hook / Views / Likes / Comments / Watch time / Next idea**
- 数値は「全部」集めない。**改善アクションに直結する列だけ**残す
- まずは **1つのDB** に集約 → 必要になってから Viewsログ用の別DBを足す

## The problem
YouTube Shorts を伸ばしたいのに、
- 何が効いたのか（フック？尺？CTA？）が記録されていない
- 記録がバラバラ（Googleスプレッドシート、メモ、頭の中）
- 逆に列を作りすぎて運用が崩壊

…という状態になりがちです。

Notion で「改善のための最低限の証拠」を残すには、**DBの列（properties）設計**がすべてです。

## The quick answer
最初は「作る→投稿→ふり返り」が回ることだけを優先して、DBは次の3ブロックに分けて設計します。

1) **制作（Input）**: ネタ、フック、台本の型
2) **公開（Publish）**: URL、投稿日、サムネ/音源
3) **結果（Outcome）**: Views など最低限の数字 + 次に変えること

## Step-by-step

### Step 1: 必須のプロパティ（最小で回す）
最初に作るのはこのセットだけでOKです。

- **Title** (Title)
- **Shorts URL** (URL)
- **Status** (Select)
  - Ideas / Script / Recorded / Posted / Reviewed
- **Publish date** (Date)
- **Topic / Niche** (Multi-select)
- **Hook (first line)** (Text)
- **Script type** (Select)
  - Explainer / Ranking / Story / Tutorial / Reaction
- **CTA type** (Select)
  - Comment / Follow / Watch next / None
- **Views (24h)** (Number)
- **Views (7d)** (Number)
- **Likes** (Number)
- **Comments** (Number)
- **Notes (what I’d change next time)** (Text)

ポイント: **Viewsを2つ（24h/7d）だけ**に絞ると運用が続きます。
「投稿直後の勢い」と「少し寝かせた結果」が分かれれば、改善に十分です。

### Step 2: あると強いプロパティ（運用が乗ってから追加）
運用が続いて「ここまで見たい」が出たら、次を追加します。

- **Video length (sec)** (Number)
- **Format** (Select)
  - Talking head / Screen / Text-only / B-roll
- **Retention clue** (Select)
  - Drop at 0–2s / Drop mid / Stable
- **Hook pattern** (Select)
  - Problem→Promise / Counterintuitive / Mistake / Checklist / Story
- **Series** (Relation または Select)
  - 「同じテーマで連投」を追いやすくなる

### Step 3: 関係（Relation）を入れるならこの2つだけ
Notion はリレーションを入れるほど強いですが、最初は増やしすぎ注意。

おすすめは次の2つだけです。

1) **Ideas DB**（ネタ帳） → Shorts DB に relation
2) **Scripts DB**（台本） → Shorts DB に relation

「Shorts 1本＝台本1つ」なら relation は不要で、Shorts DB 内に script を直接書くほうが速いです。

## Common mistakes
- **列を増やすことが目的になって、記録しなくなる**
  - 1週間記録できなかった列は削除候補
- **数値の粒度を上げすぎる（毎日Viewsを取る）**
  - 24h と 7d だけで十分
- **Statusが曖昧**
  - 「どこで詰まっているか」が見えないと改善できない

## Template / checklist
このチェックリストで「改善に効くDB」になっているか確認できます。

- [ ] Status が制作フローに一致している（Ideas→Script→Posted→Reviewed）
- [ ] Hook（1行）が必ず入る
- [ ] Views は 24h と 7d の2つだけ（まずは）
- [ ] Notes に「次に変える1点」が毎回入る
- [ ] 1週間運用して、使ってない列を消した

## Related
- [YouTube Shorts analytics tracking template](/posts/youtube-shorts-analytics-tracking-template/)
- [Notion workflow for video ideas to scripts to publish log](/posts/notion-batch-youtube-shorts-scripts-workflow/)
