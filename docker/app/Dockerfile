# Base image:
FROM ruby:2.7-alpine
# Install dependencies
RUN apk --update add --virtual build-dependencies \
                               build-base \
                               libxml2-dev \
                               libxslt-dev \
                               postgresql-dev \
                               nodejs \
                               yarn \
                               tzdata \
                               bash \
                               vim \
                               && rm -rf /var/cache/apk/*
# create application directory
RUN mkdir /myapp
# Set our working directory inside the image
WORKDIR /myapp
ADD Gemfile /myapp/Gemfile
ADD Gemfile.lock /myapp/Gemfile.lock
RUN bundle install
ADD . /myapp
EXPOSE 3000
CMD [ "bundle", "exec", "puma", "-C", "config/puma.rb" ]
