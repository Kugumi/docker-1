FROM ruby
RUN apt-get update && apt-get -y upgrade && \
	apt-get -y install sqlite3 nodejs && \
	gem install rails && \
	rails new app
ONBUILD RUN cp -r app /opt/app
ONBUILD WORKDIR /opt/app
ONBUILD EXPOSE 3000
ONBUILD RUN bundler install
ONBUILD RUN	rails db:migrate
ONBUILD RUN	rails db:seed
