FROM debian

RUN apt-get update -y && apt-get upgrade -y

RUN apt-get install -y sudo git wget

RUN sudo adduser --disabled-login --gecos 'Gogs' git

RUN sudo su - git
RUN mkdir /home/local
WORKDIR $HOME/local

RUN wget https://storage.googleapis.com/golang/go1.7.linux-amd64.tar.gz
RUN tar -xvzf go1.7.linux-amd64.tar.gz

ENV GOROOT=$HOME/local/go
ENV GOPATH=$HOME/gogs
ENV PATH=$PATH:$GOROOT/bin:$GOPATH/bin

WORKDIR $GOPATH/src/github.com/gogs
RUN git clone --depth=1 -b develop https://github.com/gogs/gogs
RUN go get -u github.com/gogs/gogs

WORKDIR $GOPATH/src/github.com/gogs/gogs
RUN go build

EXPOSE 3000

ENTRYPOINT ./gogs web

# docker build -t ex03 .
# docker run -it -p 3000:3000 ex03