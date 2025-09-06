## OpenGL 随书示例代码

- [The Cherno OpenGL(video lesson)](The.Cherno.OpenGL.Tutorial)
- [计算机图形学编程(使用OpenGL和C++)](Computer.Graphics.Programming.In.OpenGL.With.Cpp)
- [Shader开发实战](Practical.Shader.Development)
- [OpenGL编程指南](OpenGL.Programming.Guide)


**Ubuntu安装 OpenGL及相关依赖**

```bash
$ sudo apt -y install build-essential libgl1-mesa-dev
$ sudo apt -y install freeglut3-dev
$ sudo apt -y install libglew-dev libsdl2-dev libsdl2-image-dev libglm-dev libfreetype6-dev
$ sudo apt -y install glew-utils libglew-dev libglew2.0 # for glew
$ sudo apt -y install libglfw3-dev # for glfw
```


**查看OpenGL版本信息**

```bash
$ sudo apt install mesa-utils
$ glxinfo | grep -i opengl
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: NVIDIA GeForce RTX 2060/PCIe/SSE2
OpenGL core profile version string: 4.6.0 NVIDIA 535.179
OpenGL core profile shading language version string: 4.60 NVIDIA
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.6.0 NVIDIA 535.179
OpenGL shading language version string: 4.60 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 535.179
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:
```

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

### Ubuntu24.04 上安装glm

**通过 apt 安装**

通过包管理器安装：

```bash
$ sudo apt update
$ sudo apt install libglm-dev
```

安装后，头文件默认位于 /usr/include/glm/。
