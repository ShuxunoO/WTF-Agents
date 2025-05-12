# Anaconda🐍 安装与使用

<img src="./assets/anaconda_logo.svg" alt="anaconda_logo" width="300" height="200">

## 简介

### Anaconda
Anaconda是一个开源的Python和R语言的发行版本，用于计算科学、数据科学、机器学习、大规模数据处理和预测分析。它包含了conda、Python以及超过1500个科学计算包。Anaconda的优势在于简化了包管理和部署，特别适合需要使用大量第三方库的数据科学工作。

### Miniconda
Miniconda是Anaconda的精简版，它仅包含conda、Python和一些必要的基础包。相比Anaconda，Miniconda安装更快、占用空间更小，用户可以根据需求自行安装所需的包，适合对磁盘空间有限制或只需要特定包的用户。

一句话概括就是：Anaconda是一个及其方便的Python包管理工具，Miniconda是Anaconda的精简版。

---

## Windows系统下安装Anaconda(OS:Windows)

### 1. 下载安装包
1. 访问[Anaconda官网下载页面](https://www.anaconda.com/products/distribution#Downloads)
2. 选择Windows版本的安装程序（选择适合您系统的32位或64位版本）

### 2. 安装
1. 双击下载的安装文件（如[Anaconda3-2024.10-1-Windows-x86_64.exe](https://repo.anaconda.com/archive/Anaconda3-2024.10-1-Windows-x86_64.exe)）启动安装程序
2. 点击"Next"进入安装向导
3. 阅读并同意许可协议，点击"Next"
4. 选择安装类型：
   - "Just Me"（推荐）：仅为当前用户安装
   - "All Users"：为系统上的所有用户安装
5. 选择安装位置，默认路径通常为`C:\Users\YourUsername\anaconda3`，可以根据需要修改
6. 高级选项配置：
   - 建议勾选"Add Anaconda to my PATH environment variable"（这样可以在命令行直接使用conda命令）
   - 建议勾选"Register Anaconda as my default Python"
7. 点击"Install"开始安装过程
8. 安装完成后，可以选择是否查看教程或加入邮件列表
9. 点击"Finish"完成安装

### 3. 验证安装
1. 启动Window终端输入`conda --version` 或者 `conda -V`，如显示版本号则表示安装成功

**✨注：安装Miniconda操作与上类似**

---

## 常用conda命令

### 环境管理
```bash
# 创建新环境
conda create --name myenv python=3.12 -y

# 激活环境
conda activate myenv

# 退出当前环境
conda deactivate

# 列出所有环境
conda env list

# 删除环境
conda remove --name myenv --all
```

### 包管理
```bash
# 安装包
conda install numpy

# 安装指定版本的包
conda install numpy=1.20.0

# 更新包
conda update numpy

# 删除包
conda remove numpy

# 列出已安装的包
conda list

# 在指定环境中安装包
conda install --name myenv numpy
```

### 系统管理
```bash
# 更新conda
conda update conda

# 更新anaconda
conda update anaconda

# 清理缓存
conda clean --all
```

### 从特定渠道安装包
```bash
# 从conda-forge安装包
conda install -c conda-forge package_name
```

### 导出和恢复环境
```bash
# 导出环境配置到文件
conda env export > environment.yml

# 从配置文件创建环境
conda env create -f environment.yml
```

---

## 一些使用建议💫

1. **使用国内镜像源**：为了可以丝滑地下载某些资源包，可以配置国内镜像源加速下载：
   ```bash
      conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
      conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
      conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r/
      conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/pro/
      conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2/
      conda config --set show_channel_urls yes
   ```

   或者使用阿里镜像源：
      ```bash
      conda config --add channels http://mirrors.aliyun.com/anaconda/pkgs/main
      conda config --add channels http://mirrors.aliyun.com/anaconda/pkgs/r
      conda config --add channels http://mirrors.aliyun.com/anaconda/pkgs/msys2
      conda config --add channels https://mirrors.aliyun.com/anaconda/cloud/conda-forge/
      conda config --add channels https://mirrors.aliyun.com/anaconda/cloud/msys2/
      conda config --set show_channel_urls yes
   ```

   配置完成后，运行`conda config --show channels`查看配置结果。

> channels:
     https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2/
     https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/pro/
     https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r/
     https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
     https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
     defaults

如果后面想去掉某一个镜像源，可以使用以下命令，例如：

```bash
conda config --remove channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --remove channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/

```


1. **定期更新**：定期运行`conda update --all`来更新所有包

2. **为不同项目创建独立环境**：为每个项目创建专用的conda环境，避免依赖冲突

