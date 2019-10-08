FROM microsoft/aspnetcore:latest
#把当前目录复制到镜像的 app目录
COPY . /app
#指定工作目录
WORKDIR /app
#暴露的端口 是之前准备asp.net core应用设置的端口一致 UseUrls("http://*:5000")
EXPOSE 5000
#最后设置启动的dll
ENTRYPOINT ["dotnet", "dotnet2docker.dll"]