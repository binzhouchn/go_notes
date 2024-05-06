FROM golang 

ENV GO111MODULE=on \
    GOPROXY=https://goproxy.cn,direct \
    CGO_ENABLED=1 \
    GOOS=linux

# 安装基础包
RUN apt-get update && \
    apt-get install -y \
        wget build-essential iputils-ping net-tools vim openssh-server && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# 解决vim中文乱码
RUN echo 'set fileencodings=utf-8,ucs-bom,gb18030,gbk,gb2312,cp936 \n\
set termencoding=utf-8 \n\
set encoding=utf-8' >> ~/.vimrc

WORKDIR /go/src/red
COPY . .
RUN go mod download
RUN go build -o main .

# 暴露端口 8080
EXPOSE 8080