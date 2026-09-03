# ds-agent

BigQuery ML (BQML) を分析エンジンとして使う、データアナリスト・エージェント。

## Purpose

データを「集計する」だけでなく、BQML を中心に **探索 → 特徴量化 → モデル化 → 評価 → 洞察 → 意思決定** までを一貫して支援する。

## Architecture

```text
Data Sources
    ↓
BigQuery
    ↓
Data Profiling / SQL
    ↓
BQML
 ┌──┼──────────────┐
 │  │              │
EDA Forecasting  Classification / Regression
 │  │              │
 └──┼──────────────┘
    ↓
Evaluation
    ↓
Insight Agent
    ↓
Decision / Report
```

## Agent Roles

- **Profiler** — スキーマ、欠損、分布、外れ値、品質を把握
- **Explorer** — SQL/EDA で仮説を探索
- **Feature Engineer** — BQML で扱える特徴量を設計
- **Modeler** — 回帰、分類、クラスタリング、時系列などを選択
- **Evaluator** — 指標・検証結果・リークを確認
- **Insight** — 数値を意味に変換し、仮説と示唆を生成
- **Decision** — 分析結果をアクション候補へ変換

## Design Principles

1. **BQML-first**: モデル実行は原則 BigQuery 上で完結
2. **SQL-first**: データ変換・再現可能性を SQL として残す
3. **Evidence-first**: 洞察には元データ・SQL・モデル指標を紐付ける
4. **Agent ≠ Calculator**: エージェントは分析手順を選択・検証する
5. **Human-in-the-loop**: 重要な意思決定は人間が承認
6. **Artifact-driven**: 分析結果を JSON / Markdown / SQL として保存

## Suggested Tree

```text
ds-agent/
├── README.md
├── AGENTS.md
├── ontology.json
├── agents/
│   ├── profiler.md
│   ├── explorer.md
│   ├── feature-engineer.md
│   ├── modeler.md
│   ├── evaluator.md
│   ├── insight.md
│   └── decision.md
├── bqml/
│   ├── README.md
│   ├── templates/
│   └── models/
├── schemas/
│   ├── analysis.schema.json
│   └── insight.schema.json
├── sql/
├── analyses/
├── reports/
└── .github/
    └── workflows/
```

## MVP

- BigQuery dataset を入力として受け取る
- スキーマとデータ品質を自動プロファイリング
- 分析目的から BQML モデル種別を選択
- BQML の評価指標を取得
- 根拠付き Markdown / JSON レポートを生成

## Status

Skeleton / Architecture phase.
