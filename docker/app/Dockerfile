FROM python:3.8

RUN apt-get update
RUN apt-get upgrade -y

# mecab
RUN apt-get install -y libmecab2 libmecab-dev mecab mecab-utils nkf

# pipenv
RUN pip install --upgrade pip && pip install pipenv

# yarn
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update
RUN apt-get install -y yarn nodejs npm 
