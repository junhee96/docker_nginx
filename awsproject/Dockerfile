FROM python:3.8.5

ENV PATHONUNBUFFERED 1

RUN apt-get -y update
RUN apt-get -y install vim

RUN mkdir /srv/docker-server
ADD . /srv/docker-server

WORKDIR /srv/docker-server

RUN pip3 install --upgrade pip
RUN pip3 install -r requirements.txt

#EXPOSE 8000
#CMD ["python3", "manage.py", "runserver", "0.0.0.0:8000"]


