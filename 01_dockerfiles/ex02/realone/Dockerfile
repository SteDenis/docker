FROM ruby:2.3
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y sqlite3 nodejs
RUN gem install rails
ONBUILD COPY ./app /opt/app
ONBUILD WORKDIR /opt/app
ONBUILD RUN gem update --system
ONBUILD RUN gem install bundler
ONBUILD RUN bundler update --bundler
ONBUILD RUN bundle install
ONBUILD RUN rails db:migrate
ONBUILD RUN rails db:seed
