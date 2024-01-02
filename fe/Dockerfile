FROM ubuntu:latest
WORKDIR /app
RUN apt-get update
RUN apt-get install --yes curl
RUN curl -SLO https://deb.nodesource.com/nsolid_setup_deb.sh 
RUN chmod 500 nsolid_setup_deb.sh
RUN ./nsolid_setup_deb.sh 21
RUN apt-get install nodejs -y
RUN apt-get install -y git
RUN git clone --depth 1 -b master https://github.com/iptv-org/epg.git
WORKDIR /app/epg
RUN npm install
RUN npm install -g serve
EXPOSE 4000
CMD serve -s . -p 4000