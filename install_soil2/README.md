
### SOIL2编译安装
#### **1. 安装依赖**
首先，确保系统安装了必要的开发工具和依赖库：
```bash
sudo apt update
sudo apt install -y build-essential cmake git libgl1-mesa-dev
```

#### **2. 下载 SOIL2 源码**
从 GitHub 克隆官方仓库：
```bash
git clone https://github.com/SpartanJ/SOIL2.git
cd SOIL2
```

#### **3. 使用 CMake 编译**
SOIL2 支持 CMake 构建，执行以下命令：
```bash
mkdir build && cd build
cmake ..
make
```

#### **4. 安装到系统**
编译完成后，安装库文件和头文件：
```bash
sudo make install
```
默认会安装到 `/usr/local/lib` 和 `/usr/local/include/SOIL2`。

#### **5. 验证安装**
检查是否成功安装：
```bash
ls /usr/local/lib/libSOIL2.*  # 应该能看到 .so 或 .a 文件
ls /usr/local/include/SOIL2   # 应该能看到 SOIL2.h
```

