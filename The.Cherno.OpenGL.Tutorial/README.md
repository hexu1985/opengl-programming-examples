### Ubuntu24.04 上安装glfw

**通过 apt 安装**

GLFW 的稳定版本通常包含在 Ubuntu 的仓库中：

```bash
$ sudo apt update
$ sudo apt install libglfw3 libglfw3-dev
```

安装后，头文件会保存在 /usr/include/GLFW/，库文件在 /usr/lib/x86_64-linux-gnu/。

### Ubuntu24.04 上安装glew

**通过 apt 安装**

Ubuntu 官方仓库提供了 GLEW 的开发包，安装命令如下：

```bash
$ sudo apt update
$ sudo apt install libglew-dev
```

libglew-dev 包含头文件（/usr/include/GL/glew.h）和库文件（/usr/lib/x86_64-linux-gnu/libGLEW.so）。
