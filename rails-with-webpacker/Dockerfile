FROM ruby:2.7

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update -qq && apt-get install -y build-essential nodejs yarn  && rm -rf /var/lib/apt/lists/*

RUN mkdir /myapp
WORKDIR /myapp

COPY Gemfile /myapp/Gemfile
RUN bundle install
RUN yarn install --check-files

ADD . /myapp