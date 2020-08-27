FROM ruby:2.6.0
WORKDIR /mydir
COPY rails-example-project/ .
RUN apt-get update && apt-get install -y nodejs
RUN bundle install && rails db:migrate
EXPOSE 3000
CMD ["rails","s"]
