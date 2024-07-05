FROM ruby:3.1.6-alpine3.20

COPY . /app

WORKDIR /app

RUN apt update && \
    apt install build-base && \
    apt install libxml2-dev && \
    bundle config build.nokogiri --use-system-libraries && \
    bundle install --clean --no-cache --without development && \
    apt install --no-cache-dir -r requirements.txt

CMD [bundle exec rake db:migrate && \
     bundle exec puma -b unix:///var/run/puma.sock -e $RAILS_ENV config.ru]

