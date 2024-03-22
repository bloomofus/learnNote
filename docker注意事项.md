# Docker注意事项

## 1、docker在ubuntu server上的安装

在Ubuntu服务器上安装Docker相当简单，只需按照以下步骤操作：

1. **更新软件包列表**： 在终端中执行以下命令，确保您的软件包列表是最新的：

   ```
   sudo apt update
   ```
   
2. **安装依赖包**： 安装一些必要的依赖包，以确保安装过程顺利进行：

   ```
   sudo apt install apt-transport-https ca-certificates curl software-properties-common
   ```
   
3. **添加 Docker 官方 GPG 密钥**： 使用以下命令来添加 Docker 官方 GPG 密钥：

   ```
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   ```
   
4. **添加 Docker APT 仓库**： 添加 Docker 的 APT 仓库，以便您可以从中安装 Docker：

   ```
   sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
   ```
   
5. **更新软件包列表**： 再次更新软件包列表，以确保新添加的 Docker 仓库已被识别：

   ```
   sudo apt update
   ```
   
6. **安装 Docker**： 最后，使用以下命令安装 Docker：

   ```
   sudo apt install docker-ce
   ```
   
7. **验证 Docker 安装**： 安装完成后，您可以执行以下命令来验证 Docker 是否已成功安装：

   ```
   sudo docker --version
   ```
   
如果一切顺利，您应该能够看到 Docker 的版本信息。

## 2、

