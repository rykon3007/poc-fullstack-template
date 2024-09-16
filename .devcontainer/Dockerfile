# ベースイメージ
FROM node:20

# 作業ディレクトリを /workspace に設定
WORKDIR /workspace

# package.json と package-lock.json をコピー（キャッシュ効率化のため）
COPY package*.json ./

# 依存関係をインストール
RUN npm install

# アプリケーションのソースコードをコピー
COPY . .

# 必要に応じてアプリケーションをビルド
RUN npm run build

# ポートを公開
EXPOSE 3000 9229

# データベースディレクトリのパーミッションを設定
RUN mkdir -p /workspace/sqlite && chmod 777 /workspace/sqlite

# コンテナ起動時のコマンド
CMD ["sh", "-c", "chmod 777 /workspace/sqlite && if [ \"$DEVCONTAINER\" != \"true\" ]; then npm run start; else tail -f /dev/null; fi"]
