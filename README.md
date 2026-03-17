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
