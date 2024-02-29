# CSD-Analyzer

## リポジトリに含まれるもの
- `src/segmentation`: U-Netの 事前学習/Fine-tuning/推論 のためのパッケージ
- `src/hough`: U-Netの推論結果から直線パラメータを推定するためのパッケージ
- `inputs`: U-Netの学習や推論、Hough変換への入力画像を格納
- `models`: U-Netの学習済みモデル 
- `docker-compose.yml`: コンテナ上でJupyter Notebookを実行
- `requrements.txt`: 必要ライブラリ
- `setup_environment.sh`: Docker上で学習する場合の環境構築用
- `setup_memo.txt`: Docker上で学習する場合の手順メモ

## src/ 内の Jupyter Notebook について
αファクタ算出まで、手軽に利用できるように実装
### 目的
実機で得たCSDから直線と三角形を検出し、Hough変換により直線の傾きと切片を抽出、αファクタを算出する。

### 処理フロー
1. 対象のCSDを用意
1. U-Netの学習済みモデルを適用
1. 得られた直線画像に三角形のエッジ画像を合わせた画像に対しHough変換を適用、直線パラメータを推定
1. 直線パラメータから三角形の寸法を計算し、αファクタを算出

### 手順
1. 環境構築
    1. docker compose up でコンテナをビルド・起動
    1. VS Codeの場合、拡張機能Dev Containersを追加し、コマンドパレットから"Dev Containers: Attach to Running Container..." を選択。立ち上げたコンテナを選択する。
    1. 拡張機能 Python, Jupyterを有効化
    1. 使用するカーネルは ` /opt/conda/bin/python`
1. 学習済みU-Netを適用
    1. 入出力のパス および 適用モデル を選択
1. 

### 今後について
- 追加のFine-tuning機能の追加
- スライダーなどにより、パラメータ調整をしやすく
    - 参考：https://qiita.com/oyngtmhr/items/15e54d55ef6b760e0bed