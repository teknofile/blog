FROM alpine:3.15

RUN apk update && apk add \
  build-base \
  ruby \
  ruby-dev \
  ruby-libs \
  ruby-jekyll-watch \
  ruby-bundler \
  ruby-test-unit \
  ruby-liquid \
  ruby-builder \
  ruby-rake-compiler \
  ruby-ffi \
  ruby-rss \
  ruby-rake 

RUN gem install jekyll bundler

#RUN chmod 777 /usr/lib/ruby/gems/3.0.0/cache /usr/lib/ruby/gems/3.0.0 /usr/lib/ruby/gems /usr/lib/ruby/gems/3.0.0/gems /usr/lib/ruby/gems/3.0.0/plugins
RUN chown -R 113 /usr/lib/ruby
