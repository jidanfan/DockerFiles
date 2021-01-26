# FROM stulzq/dotnet:2.2.0-aspnetcore-runtime-with-image  
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim 
# EXPOSE 80  
# WORKDIR /filestorage
# WORKDIR /filestorage/avatar
# WORKDIR /video
#设置时间为中国上海
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
WORKDIR /app
#设置语言  否则swagger.xml中文会有乱码，也可以再docker-compose中设置
ENV LANG C.UTF-8
RUN apt-get update -y && apt-get install -y libgdiplus && apt-get clean && ln -s /usr/lib/libgdiplus.so /usr/lib/gdiplus.dll
RUN sed -i "s|DEFAULT@SECLEVEL=2|DEFAULT@SECLEVEL=1|g" /etc/ssl/openssl.cnf 
COPY "ca.crt" "/usr/local/share/ca-certificates"
COPY "mid.crt" "/usr/local/share/ca-certificates"
RUN update-ca-certificates 
# COPY . .
# ENTRYPOINT ["dotnet", "CodePlateform.dll"]