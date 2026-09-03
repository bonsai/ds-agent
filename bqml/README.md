# BQML Layer

BQML を ds-agent の標準分析エンジンとして扱う。

## Standard flow

```sql
CREATE OR REPLACE MODEL `project.dataset.model`
OPTIONS(model_type='...') AS
SELECT ...;
```

```sql
SELECT *
FROM ML.EVALUATE(MODEL `project.dataset.model`);
```

必要に応じて `ML.PREDICT`, `ML.FORECAST`, `ML.DETECT_ANOMALIES`, `ML.GENERATE_EMBEDDING` 等の対応する ML.* 関数を利用する。

## Principle

BigQuery にデータを残したまま、SQL + BQML で再現可能な分析パイプラインを構成する。