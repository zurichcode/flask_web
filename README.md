# flask_web
Ein erster Webserver mit Flask im Container

Wir benutzen das Python Programm app.py

Siehe
https://runnable.com/docker/python/dockerize-your-flask-application

Wir setzen auf Google Cloud in Zurich eine CentOs-8 Linux Maschine auf:

#superuser werden , damit man Installieren darf

sudo su -

#Neueste Software holen

yum update

#docker installieren

yum install -y docker

#git installieren

yum install -y git

#Docker als Service freischalten

systemctl enable docker

#Kontrolle ob Docker läuft

docker ps

#Und das Linux-Betriebssystem, das wir im Container brauchen, Ubuntu, runterladen.

docker pull ubuntu:16.04

#Kontrolle, ob das läuft. Wir starten den Container, um das Datum auszugeben.

docker run --rm ubuntu:16.04 date

#Emulate Docker CLI using podman. Create /etc/containers/nodocker to quiet msg.
$Sat Dec  7 05:41:14 UTC 2019

#Jetzt wird unser Sourcecode geklont

git clone https://github.com/zurichcode/flask_web

#in das Directory gehen

cd flask_web/

#Den Container bauen

docker build -t flask-tutorial:latest -f dockerfile  .

#Ist der Container da?

docker images

#Den Container starten

docker run -d -p 80:5000 flask-tutorial

#man kann nun mit

curl localhost

#den output des webservers sehen. In Google Cloud muss man das Netzwerk freischalten, falls man es 
#im Internet sehen möchte.







