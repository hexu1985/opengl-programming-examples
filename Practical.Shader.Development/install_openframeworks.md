好的，在 Ubuntu 上安装和使用 OpenFrameworks 是一个非常棒的选择。Linux 是 OF 开发的一等公民，运行效率很高。

下面我将为您提供一个从安装到运行第一个程序的详细、分步指南。

### 第一阶段：安装必需的依赖项

OpenFrameworks 需要一些基础的开发工具和库。首先打开终端 (`Ctrl+Alt+T`)，然后执行以下命令来安装这些依赖。

1.  **更新软件包列表**：
    ```bash
    sudo apt update
    ```

2.  **安装编译工具和核心依赖**：
    这是一条较全的依赖安装命令，复制粘贴即可。
    ```bash
    sudo apt install -y build-essential pkg-config libasound2-dev libgl1-mesa-dev libglu1-mesa-dev libglew-dev libglfw3-dev libxmu-dev libxi-dev libopenal-dev libcurl4-openssl-dev libfreetype6-dev libfontconfig1-dev libboost-all-dev libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev gstreamer1.0-libav gstreamer1.0-plugins-bad gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly liburiparser-dev libssl-dev libopencv-dev libassimp-dev freeglut3-dev
    ```

    **说明**：这些包包括了编译器 (`gcc`, `g++`)、链接器 (`make`)、音频(Alsa)、图形(GLEW, GLFW, OpenGL)、多媒体(GStreamer)、字体处理等必要的开发库。

3.  **（可选但推荐）安装代码编辑器**
    *   **VS Code**: 从 [官网](https://code.visualstudio.com/) 下载 `.deb` 包安装，然后安装 C++ 扩展。
    *   **Qt Creator**: 一个非常好的 C++ IDE，对 OF 项目支持很好。
        ```bash
        sudo apt install qtcreator
        ```
    *   **其他**: Sublime Text, CLion 等也是不错的选择。

---

### 第二阶段：下载和设置 OpenFrameworks

1.  **下载 OpenFrameworks**：
    访问 [OpenFrameworks 下载页面](https://openframeworks.cc/download/)。在 **Linux** 栏目下，选择下载 **稳定版** 的压缩包。通常文件名类似 `of_vX.X.X_linux64gcc6_release.tar.gz`。

2.  **解压文件**：
    建议将 OF 解压到你的家目录 (`~`) 或者某个容易访问的路径。
    ```bash
    # 假设你下载到了 'Downloads' 文件夹
    cd ~/Downloads
    tar -xvzf of_vX.X.X_linux64gcc6_release.tar.gz -C ~/
    # 这会将文件夹解压到你的家目录
    ```
    现在，你的家目录下应该会有一个 `of_vX.X.X_linux64gcc6_release` 文件夹。为了便于管理，你可以将其重命名为 `openFrameworks`：
    ```bash
    mv ~/of_vX.X.X_linux64gcc6_release ~/openFrameworks
    ```

3.  **运行安装脚本**：
    OpenFrameworks 提供了一个脚本，用于下载和编译它所依赖的一些特定库（如 OpenCV，Assimp 等）。
    ```bash
    cd ~/openFrameworks
    # 运行脚本（这需要一段时间，请耐心等待）
    ./scripts/linux/install_dependencies.sh
    ```

4.  **编译项目生成器（可选，但推荐）**：
    OF 自带一个名为 `projectGenerator` 的工具，它可以帮你快速、正确地创建新项目，自动生成 Makefile，非常方便。
    ```bash
    cd ~/openFrameworks/libs/projectGenerator
    make -j4 # 使用4个CPU核心进行编译，数字可以根据你的CPU核心数修改
    cd frontend
    make -j4
    ```
    编译完成后，你可以在 `~/openFrameworks/libs/projectGenerator/frontend/bin` 找到 `projectGenerator` 可执行文件。你可以为其在桌面或应用菜单中创建快捷方式。

---

### 第三阶段：编译并运行一个示例程序

让我们通过编译一个示例来验证你的安装是否成功。

1.  **定位到示例项目**：
    我们以 `examples/graphics/polygonExample` 为例。
    ```bash
    cd ~/openFrameworks/examples/graphics/polygonExample
    ```

2.  **编译项目**：
    每个 OF 项目都自带一个 `Makefile`。使用 `make` 命令进行编译。
    ```bash
    # 先清理（可选）
    make clean
    # 然后编译。使用 -j4 参数可以加速编译（4代表并行任务数，可根据你的CPU调整）
    make -j4
    ```
    第一次编译会花费一些时间，因为它需要先编译整个 OF 核心库。

3.  **运行程序**：
    编译成功后，会在 `bin` 目录下生成可执行文件。
    ```bash
    ./bin/polygonExample
    ```
    如果一切顺利，你应该能看到一个带有旋转彩色图形的窗口弹出！恭喜你，安装成功了。

---

### 第四阶段：创建你自己的第一个项目

使用 `projectGenerator` 是最简单的方法。

1.  **启动 projectGenerator**：
    导航到之前编译生成的目录，并运行它。
    ```bash
    ~/openFrameworks/libs/projectGenerator/frontend/bin/projectGenerator
    ```

2.  **创建新项目**：
    *   在界面中，将 **项目路径** 设置为你希望放置新项目的目录（例如 `~/ofApps`）。
    *   在 **项目名称** 中输入 `myFirstApp`。
    *   确保 **Addons** 栏是空的（暂时不需要）。
    *   点击 **生成** 按钮。

3.  **打开并编辑项目**：
    项目生成后，你可以在 `~/ofApps/myFirstApp/src` 目录下找到 `main.cpp` 和 `ofApp.h`/`ofApp.cpp`。
    用你喜欢的代码编辑器（如 VS Code）打开 `ofApp.cpp` 文件。

4.  **添加一些简单代码**：
    在 `ofApp::draw()` 函数里添加一行代码，例如画一个圆：

    ```cpp
    void ofApp::draw(){
        ofBackground(0); // 设置背景为黑色
        ofSetColor(255, 0, 0); // 设置绘制颜色为红色
        ofDrawCircle(ofGetWidth()/2, ofGetHeight()/2, 100); // 在窗口中心画一个半径为100的圆
    }
    ```

5.  **编译和运行**：
    回到终端，导航到你的新项目目录，使用 `make` 命令。
    ```bash
    cd ~/ofApps/myFirstApp
    make -j4
    ./bin/myFirstApp
    ```
    你应该会看到一个红色的圆圈出现在黑色窗口的中央！

### 常见问题与解决 (Troubleshooting)

*   **编译错误：找不到 `ofMain.h` 等头文件**：
    这通常是因为 `Makefile` 路径错误。**务必**在项目根目录（包含 `Makefile` 和 `src` 文件夹的目录）下运行 `make` 命令。

*   **权限错误**：
    如果你在连接硬件（摄像头、Arduino）时遇到权限问题，通常需要将用户添加到 `video`、`dialout` 等用户组。
    ```bash
    sudo usermod -a -G video,dialout $USER
    ```
    **注销并重新登录**后生效。

*   **音频不工作**：
    确保已安装 `libasound2-dev`（我们在第一步已经安装了）。

*   **更新或重装后问题**：
    如果想彻底重新编译 OF 本身，可以进入 `openFrameworks/libs/openFrameworksCompiled/project` 目录运行 `make clean` 和 `make`。

现在你已经成功在 Ubuntu 上搭建了 OpenFrameworks 开发环境，可以开始探索创意编程的世界了！官方文档和论坛是非常好的学习资源。
