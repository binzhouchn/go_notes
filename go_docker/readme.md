# docker构建[go] gin web framework

```shell
docker build -t my-gin-app .

docker run -d -p 8080:8080 my-gin-app:latest ./main
```

# 镜像优化

这样构建的镜像大概在1.28G左右还是有点大，如果想要更小的镜像，则可以参考Dockerfile_small文件的写法（即编译好文件后，移植到更小的alpine镜像去执行）

```shell
docker run -d -p 8080:8080 my-gin-app:latest
```