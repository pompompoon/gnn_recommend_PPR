# GNN ファッション レコメンドシステム

HeteroGAT / APPNP (PPR) エンコーダー + BPR Loss による推薦。
購入・閲覧・お気に入りの Multi-Behavior 学習。

## セットアップ & 実行

```bash
pip install -r requirements.txt
createdb fashion_recommend

# GAT で全パイプライン
python main.py --all --db-password パスワード

# APPNP (PPR) で全パイプライン
python main.py --all --encoder appnp --db-password パスワード

# 精度評価
python evaluate.py --db-password パスワード
python evaluate.py --encoder appnp --db-password パスワード

# 可視化
python visualize.py --db-password パスワード --output network.html
python visualize.py --db-password パスワード --output network.png --static
```

## Windows 日本語環境の場合

```powershell
$env:PGCLIENTENCODING="UTF8"
$env:PGPASSFILE="NUL"
python main.py --all --db-password パスワード
```

# 可視化
<img width="1416" height="818" alt="image" src="https://github.com/user-attachments/assets/641cf6bd-3044-4972-92b4-6282ce70010c" />

# 前回 → 今回の比較

| 指標           | 前回 (GAT, 800items) | 今回 (APPNP, 150items) | 改善     |
|----------------|----------------------|------------------------|----------|
| Recall@10      | 0.0138               | **0.0395**             | 2.9倍    |
| NDCG@10        | 0.0097               | **0.0262**             | 2.7倍    |
| HitRate@10     | 0.0376               | **0.1117**             | 3.0倍    |
| MRR            | 0.0151 (66位)        | **0.0406** (25位)      | 2.7倍    |
| Item Coverage  | 10.3%                | **98.7%**              | 大幅改善 |
| ILD (多様性)   | 0.152                | **0.319**              | 2.1倍    |

