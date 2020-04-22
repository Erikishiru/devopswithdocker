FROM ruby:2.6.0

WORKDIR /rails-example-project

RUN apt update && apt install -y curl 
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash && apt install -y nodejs && npm install
RUN gem install bundler

COPY . .
RUN bundle install
RUN rails db:migrate 

ENTRYPOINT rails s 