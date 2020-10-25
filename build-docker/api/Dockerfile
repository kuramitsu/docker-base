FROM python:3.8-buster AS build-stage

WORKDIR /opt/app

# Pipfile.lock to requirements.txt
RUN pip install --upgrade pip && pip install pipenv
COPY api/ ./ 
RUN pipenv lock -r > requirements.txt
RUN pip install -r requirements.txt


FROM python:3.8-slim-buster

COPY --from=build-stage /usr/local/lib/python3.8/site-packages /usr/local/lib/python3.8/site-packages
COPY --from=build-stage /usr/local/bin/uwsgi /usr/local/bin/uwsgi

RUN apt-get update \
  && apt-get install -y libxml2 \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

RUN useradd -r -s /bin/false uwsgiuser
 
WORKDIR /opt/app
COPY build-docker/api/uwsgi.ini ./ 
COPY api/ ./

USER uwsgiuser

EXPOSE 8000
CMD ["uwsgi", "--ini", "/opt/app/uwsgi.ini"]
