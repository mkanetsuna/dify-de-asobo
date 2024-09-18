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

# Google Cloud SDKのリポジトリを追加
RUN echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list > /dev/null \
    && curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - \
    && apt-get update -y \
    && apt-get install -y google-cloud-sdk

# 不要なファイルをクリーンアップ
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# デフォルトのシェルをbashに設定
CMD ["bash"]
