## Hysteria使用教程
Hysteria协议限制，无法使用中转，只能直连，但是速度可能比中转还快。  

**注意：** 因为Hysteria使用udp传输，不同运营商、地区的QoS优先级或者限速级别均不同，未必比Trojan更好，请自行测试。

### Windows:
**必要步骤:** 打开文件扩展名显示，[打开方法](https://support.microsoft.com/zh-cn/windows/windows-%E4%B8%AD%E7%9A%84%E5%B8%B8%E8%A7%81%E6%96%87%E4%BB%B6%E6%89%A9%E5%B1%95%E5%90%8D-da4a4430-8e76-89c5-59f7-1cdbbc75cb01)
* v2rayN:
1. 下载[v2rayN.zip](https://github.com/2dust/v2rayN/releases/download/5.29/v2rayN.zip),以及[Hysteria核心](https://github.com/HyNetwork/hysteria/releases/download/v1.1.0/hysteria-tun-windows-6.0-amd64.exe)。
2. 解压v2rayN.zip到任意目录，重命名下载的Hysteria核心(hysteria-tun-windows-6.0-amd64.exe)为**hysteria.exe**,并复制到v2rayN根目录。  
3. 启动v2rayN
4. 在v2rayN目录内右键新建一个文本文档，重命名为hysteria_config.json，复制下面配置进去修改对应参数并保存。  
    ``` json
    {
        "server": "服务器地址:8443",   //服务器地址自行修改
        "up_mbps": 120,
        "down_mbps": 1200,
        "auth_str": "密码",  //自行修改
        "socks5": {
            "listen": "0.0.0.0:端口"   //此处端口自行设置为v2rayN的socks端口(v2rayN左下角有显示)
        },
        "http": {
            "listen": "0.0.0.0:端口"  //此处端口自行设置为v2rayN的http端口(v2rayN左下角有显示)
        },
        "recv_window_conn": 50331648, 
        "recv_window": 201326592
    }
    ```  
5. v2rayN 服务器->添加自定义配置服务器，别名自行修改，地址点击浏览，选择hysteria_config.json，core类型选择hysteria，确定。  
**提示:如需修改配置，只需要双击节点然后点击编辑，修改对应参数即可**  
**如需导入多个节点，只需右键已有节点，选择克隆所选服务器，并双击进入编辑修改即可，不需要重复导入**  

### macOS or Linux(需有基础命令行知识):
1. 下载[Hysteria核心](https://github.com/tobyxdd/hysteria/releases)(macOS:hysteria-tun-darwin, intel架构选择amd64, Apple Silicon选择arm64, Linux: 自行选择对应架构)，修改文件名为hysteria，并新建一个文件夹存放。
2. 新建一个文本文件，命名为config.json，并复制配置文本进去，同Windows配置(端口自行设置，一般socks:1080，http:8123)。
3. 启动终端，切换到hysteria目录下，```chmod +x ./hysteria```
4. 终端输入 ```./hysteria -c ./config.json client```  (运行期间需保持终端运行)

### iOS:
* Shadowrocket:
1. 点击右上角+
2. 类型选择Hysteria  
地址: 服务器地址  
端口: 8443  
密码: 密码  
上行速度: 120  
下行速度: 1200  
备注自行填写  
**其余选项保持默认**
3. 右上角完成即可

### Android:
* SagerNet 配合 hysteria-plugin:
1. 安装[SagerNet](https://github.com/SagerNet/SagerNet)以及[hysteria-plugin](https://github.com/SagerNet/SagerNet/releases/tag/hysteria-plugin-1.1.0)
2. 打开SagerNet，右上角添加->手动输入->Hysteria
3. 配置名称:自己填  
服务器:服务器地址  
服务器端口: 8443  
认证类型: STRING  
认证载荷: 密码  
最大上行: 120  
最大下行: 1200  
QUIC连接接收窗口: 50331648  
QUIC流接收窗口: 201326592  
**其余选项保持默认**  
**混淆密码请勿设置 混淆密码请勿设置 混淆密码请勿设置**  
4.保存


## 测速
* 测试环境统一为speedtest.net单线程测试(多线程测试无意义，只有下载时有用)，每个地区测试节点都一样
* 广州移动家宽(500M)  
Hysteria:  
![cmjp2_hy.png](https://github.com/SamuelW9527/hy_manuel/raw/main/cmjp2_hy.png)  
Trojan:  
![cmjp2_trojan.png](https://github.com/SamuelW9527/hy_manuel/raw/main/cmjp2_trojan.png)
* 广州电信家宽(1000M)  
Hysteria:  
![ctjp2_hy.png](https://github.com/SamuelW9527/hy_manuel/raw/main/ctjp2_hy.png)  
Trojan:  
![ctjp2_trojan.png](https://github.com/SamuelW9527/hy_manuel/raw/main/ctjp2_trojan.png)
