FROM ruby:2.5
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs

# 時間設定
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get install -y tzdata
RUN ln -fs /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
RUN dpkg-reconfigure --frontend noninteractive tzdata

RUN mkdir /app
WORKDIR /app
ADD ./rails/Gemfile /app
ADD ./rails/Gemfile.lock /app
RUN bundle install
ADD ./rails /app

RUN mkdir -p tmp/sockets
RUN mkdir -p tmp/pids

COPY ./docker/ruby/httpd-foreground /usr/local/bin/
EXPOSE 80
EXPOSE 443
CMD ["httpd-foreground"]
