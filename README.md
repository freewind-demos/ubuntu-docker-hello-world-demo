Ubuntu Docker Hello World Demo
==============================

在Ubuntu上安装和执行docker，比在Mac下要简单一点，
主要是因为Ubuntu本身就是Linux，docker必须的某些底层支持就已经具备，
所以我们下载安装完docker后，就直接可以使用`docker`命令了。

安装Docker-CE
-------------

CE是社区版的意思。

在Bash下执行：

```
curl -fsSL get.docker.com | CHANNEL=stable sh
```

如果需要在非root用户下使用docker，需要执行：

```
sudo usermod -aG docker your-user
```

测试:

```
$ docker --version
Docker version 18.06.1-ce, build e68fc7a
```

运行hello world
-------------

```
docker run hello-world
```

它会下载`library/hello-world`并运行：

```
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
9db2ca6ccae0: Pull complete
Digest: sha256:4b8ff392a12ed9ea17784bd3c9a8b1fa3299cac44aca35a85c90c5e3c7afacdc
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.
```

可以看到最后输出的`Hello from Docker!`，说明正常。

它同时还说明了这个信息是怎么打出来的：

```
To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.
```

以及更多信息：

```
To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/
```

执行docker容器里的命令
--------------

在前面的更多信息中，它提到了可以使用`run -it`命令，执行docker容器里的命令：

```
docker run -it ubuntu bash
```

它将会下载最新的`ubuntu:latest`，然后进入它的bash:

```
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
124c757242f8: Pull complete
9d866f8bde2a: Pull complete
fa3f2f277e67: Pull complete
398d32b153e8: Pull complete
afde35469481: Pull complete
Digest: sha256:b5309340de7a9a540cf6c0cba3eabdfb9c9bc5153026d37991fd0028180fc725
Status: Downloaded newer image for ubuntu:latest
root@a03dc7582e87:/#
```

注意到最后一行，我们已经进入了该ubuntu容器！可以执行更多命令了：

```
# uname --all
```

输出为：

```
Linux a03dc7582e87 4.4.0-128-generic #154-Ubuntu SMP Fri May 25 14:15:18 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```
