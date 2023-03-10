# switch
 A virtual network tool (VPN)

将不同网络下的多个设备虚拟到一个局域网下


### 示例：

- 在一台mac设备上运行，获取到ip 10.13.0.2：

  <img width="506" alt="图片" src="https://user-images.githubusercontent.com/49143209/210379090-a3f21007-5a12-44d3-81d6-a69495209ea7.png">

- 在另一台windows上运行，获取到ip 10.13.0.3：

  ![图片](https://user-images.githubusercontent.com/49143209/210380063-d02c5b46-8fef-4e21-aa9b-6c2defcb1412.png)

- 此时这两个不同局域网的设备之间就能用ip相互访问了

  <img width="437" alt="图片" src="https://user-images.githubusercontent.com/49143209/210380969-4a7c0f23-1e88-4ab6-9cc2-0c0f086848ac.png">

- 输入"list"查看其他已连接的设备(p2p表示NAT打洞成功，relay表示使用服务器中继转发),"status"查看当前设备状态

  <img width="461" alt="图片" src="https://user-images.githubusercontent.com/49143209/217267931-5f134337-6259-40fd-ab2c-882bed19c0cb.png">

- token的作用是标识一个虚拟局域网，当使用公共服务器时，建议使用一个唯一值当token(比如uuid)，否则有可能连接到其他人创建的虚拟局域网中
- 公共服务器目前的配置是2核4G 4Mbps，有需要再扩展~

### 使用须知
- 需要root/管理员权限
- 使用命令行运行
- Mac和Linux下需要加可执行权限(例如:chmod +x ./switch-macos)
- 暂时固定使用的10.13.0.1/24网段，需要避免和已有的路由冲突
## 编译
 前提条件:安装rust编译环境(https://www.rust-lang.org/zh-CN/tools/install)
 
 到项目根目录下执行 cargo build -p switch-desktop
 
### 支持平台
- Mac
- Linux
- Windows
  - 依赖 wintun.dll(https://www.wintun.net/)

### 特性
- IP层数据转发
  - tun虚拟网卡
- NAT穿透
  - 点对点穿透
  - 服务端中继转发
- Windows后台服务

### Todo
- 支持安卓
- 数据加密
- 客户端中继转发
