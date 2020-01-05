FROM mcr.microsoft.com/mssql/server:2017-latest
 #设置时间为中国上海
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
ENTRYPOINT ["/opt/mssql/bin/sqlservr"]
