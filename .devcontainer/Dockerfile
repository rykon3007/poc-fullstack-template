# ベースイメージ
FROM node:20

# 作業ディレクトリを /workspaces に設定
WORKDIR /workspaces

# プロジェクトファイルをすべてコンテナにコピー
COPY . /workspaces

# 依存関係をインストール
RUN npm install

# アプリケーションをビルド
RUN npm run build

# ポートを公開
EXPOSE 3000

# データベースディレクトリのパーミッションを設定
RUN mkdir -p /workspaces/sqlite && chmod 777 /workspaces/sqlite

# 環境変数によってサーバー起動を制御し、パーミッションを実行時にも再設定
CMD ["sh", "-c", "chmod 777 /workspaces/sqlite && if [ \"$DEVCONTAINER\" != \"true\" ]; then npm run start; else tail -f /dev/null; fi"]
