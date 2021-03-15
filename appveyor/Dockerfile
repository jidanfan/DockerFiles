# FROM ubuntu:18.04  
# # WORKDIR /tmp
# # USER root
# RUN  sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
# RUN  apt-get clean

# RUN apt update
# RUN apt install wget -y
# RUN wget https://www.appveyor.com/downloads/appveyor-server/7.0/linux/appveyor-server_7.0.2184_amd64.deb -O appveyor-server.deb

FROM mcr.microsoft.com/dotnet/runtime-deps:5.0-focal
RUN  sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
RUN  apt-get clean
RUN apt update
RUN apt install libcap2-bin git -y

# Add Microsoft repository for .NET SDK
# RUN curl -sSL https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
# RUN apt-add-repository https://packages.microsoft.com/debian/9/prod/
# RUN apt install wget -y
# RUN wget https://www.appveyor.com/downloads/appveyor/appveyor-server.deb -O packages-microsoft-prod.deb
# ADD https://www.appveyor.com/downloads/appveyor/appveyor-server.deb .
COPY appveyor-server.deb .
# RUN  dpkg -i packages-microsoft-prod.deb 
RUN  dpkg -i appveyor-server.deb
# Install .NET SDK
# RUN  apt-get update; \
#     apt-get install -y apt-transport-https && \
#     apt-get update && \
#     apt-get install -y dotnet-sdk-5.0
# COPY --from=download /tmp/appveyor-server.deb /tmp/
# RUN dpkg -i /tmp/appveyor-server.deb
# RUN cd /tmp && rm -f *
WORKDIR /opt/appveyor/server
EXPOSE 80 443
VOLUME [ "/etc/opt/appveyor/server" ]
VOLUME [ "/var/opt/appveyor/server" ]
ENTRYPOINT [ "./appveyor-server" ]