FROM ubuntu:16.04
RUN apt-get update \
&& apt-get install -y ruby-full ruby-dev build-essential iputils-ping \
&& gem install bundler --no-ri --no-rdoc
RUN apt-get install -y iputils-ping
ENV APP_HOME /app
RUN mkdir $APP_HOME
WORKDIR $APP_HOME
ADD Gemfile* $APP_HOME/
RUN gem install bson_ext -v '1.12.5' --source 'https://rubygems.org/'
RUN gem install unf_ext -v '0.0.7.4' --source 'https://rubygems.org/'
RUN gem install puma -v '3.10.0' --source 'https://rubygems.org/'
RUN bundle install
ADD . $APP_HOME
ENV POST_SERVICE_HOST post
ENV POST_SERVICE_PORT 5000
ENV COMMENT_SERVICE_HOST comment
ENV COMMENT_SERVICE_PORT 9292
CMD ["puma"]
