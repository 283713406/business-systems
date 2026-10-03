ARG BASE_IMAGE=crpi-7a6qgvce1ic8faue.cn-hangzhou.personal.cr.aliyuncs.com/qinguangrui/golang:1.20-bookworm
FROM ${BASE_IMAGE}

ENV DEBIAN_FRONTEND=noninteractive \
    GO111MODULE=on \
    GOPROXY=https://goproxy.cn,direct \
    NPM_CONFIG_REGISTRY=https://registry.npmmirror.com \
    PLAYWRIGHT_DOWNLOAD_HOST=https://npmmirror.com/mirrors/playwright \
    PLAYWRIGHT_BROWSERS_PATH=.ms-playwright

RUN set -eux; \
    cat > /etc/apt/sources.list.d/debian.sources <<'EOF'
Types: deb
URIs: https://mirrors.tuna.tsinghua.edu.cn/debian
Suites: bookworm bookworm-updates bookworm-backports
Components: main contrib non-free non-free-firmware
Signed-By: /usr/share/keyrings/debian-archive-keyring.gpg

Types: deb
URIs: https://mirrors.tuna.tsinghua.edu.cn/debian-security
Suites: bookworm-security
Components: main contrib non-free non-free-firmware
Signed-By: /usr/share/keyrings/debian-archive-keyring.gpg
EOF

RUN set -eux; \
    apt-get update; \
    apt-get install -y --no-install-recommends \
      ca-certificates \
      curl \
      git \
      npm \
      nodejs \
      fonts-noto-cjk \
      fonts-liberation \
      procps; \
    rm -rf /var/lib/apt/lists/*

RUN mkdir -p /workspaces
