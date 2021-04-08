FROM mcr.microsoft.com/dotnet/sdk:5.0-focal
# USER root
# RUN  sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
RUN sed -i 's/archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list

RUN  apt-get clean

RUN apt update 
RUN apt install libcap2-bin git ssh  -y 
RUN apt install nodejs npm -y 
# RUN apt install nuget
# RUN apt install wget -y
# RUN wget https://www.appveyor.com/downloads/appveyor/appveyor-server.deb -O appveyor-server.deb
# ADD https://www.appveyor.com/downloads/appveyor/appveyor-server.deb .
COPY appveyor-server.deb . 
RUN  dpkg -i appveyor-server.deb 
RUN rm appveyor-server.deb 
WORKDIR /opt/appveyor/server
EXPOSE 80 443
VOLUME [ "/etc/opt/appveyor/server" ]
VOLUME [ "/var/opt/appveyor/server" ]
ENTRYPOINT [ "./appveyor-server" ] 