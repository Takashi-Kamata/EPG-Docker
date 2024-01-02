FROM ubuntu:latest
WORKDIR /app
RUN apt-get update
RUN apt-get install --yes curl
RUN curl -SLO https://deb.nodesource.com/nsolid_setup_deb.sh 
RUN chmod 500 nsolid_setup_deb.sh
RUN ./nsolid_setup_deb.sh 21
RUN apt-get install nodejs -y
RUN apt-get install -y git
WORKDIR /app/epg
CMD ["npm", "run", "grab", "--", "--site=tvguide.myjcom.jp", "--cron=* */6 * * *"]
