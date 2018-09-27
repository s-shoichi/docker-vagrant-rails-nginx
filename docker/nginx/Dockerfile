FROM nginx:1.13.3

RUN apt-get update -qq && apt-get install -y -q nginx

# インクルード用のディレクトリ内を削除
RUN rm -f /etc/nginx/conf.d/*

# Nginxの設定ファイルをコンテナにコピー
ADD ./docker/nginx/nginx.conf /etc/nginx/conf.d/app.conf

# ssl証明書をコンテナにコピー
ADD ./docker/ssl /etc/nginx/cert

# ビルド完了後にNginxを起動
CMD /usr/sbin/nginx -g 'daemon off;'
