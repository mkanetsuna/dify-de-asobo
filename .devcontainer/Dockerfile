# ベースイメージとして公式のUbuntuを使用
FROM mcr.microsoft.com/vscode/devcontainers/base:ubuntu

# 必要な依存パッケージをインストール
RUN apt-get update && apt-get install -y \
    curl \
    gnupg \
    lsb-release \
    sudo \
    apt-transport-https \
    ca-certificates \
    git

# Google Cloud SDK のリポジトリを追加し、GPG 公開鍵を適切に設定
RUN mkdir -p /usr/share/keyrings \
    && curl -fsSL https://packages.cloud.google.com/apt/doc/apt-key.gpg | gpg --dearmor -o /usr/share/keyrings/cloud.google.gpg \
    && echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | tee /etc/apt/sources.list.d/google-cloud-sdk.list

# パッケージリストを更新し、Google Cloud SDK をインストール
RUN apt-get update -y && apt-get install -y google-cloud-sdk

# クリーンアップ
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# デフォルトのシェルをbashに設定
CMD ["bash"]