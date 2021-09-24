### DSM 7.0.1 编译
1. 安装DOCKER
```
sudo apt-get update
sudo apt install docker.io
```
2. 安装依赖
```
sudo apt install jq
sudo apt install curl
```
3. 下载编译工具链
    redpill-tool-chain_x86_64_v0.10 
    [https://xpenology.com/forum/applications/core/interface/file/attachment.php?id=13072](/uri)
4. 去文件夹配置权限
```
cd redpill-tool-chain_x86_64_v0.10
chmod +x redpill_tool_chain.sh
```
5. 如果你要编辑 vid,pid,sn,mac信息请编译对应文件:
```
#edit apollolake
vi apollolake_user_config.json
#edit bromolow
vi bromolow_user_config.json
```
- 配置文件模板
```
{
  "extra_cmdline": {
    "vid": "0x46f4",
    "pid": "0x0001",
    "sn": "1236PDN123456",
    "mac1": "E1C42CC3EEEE"
  },
  "synoinfo": {},
  "ramdisk_copy": {}
}
```

6. 编译镜像文件
```
#for apollolake
./redpill_tool_chain.sh build apollolake-7.0.1-42214 && ./redpill_tool_chain.sh auto apollolake-7.0.1-42214
#for bromolow
./redpill_tool_chain.sh build bromolow-7.0.1-42214 && ./redpill_tool_chain.sh auto bromolow-7.0.1-42214
```
完成后文件会保存在 redpill-tool-chain_x86_64_v0.10/images目录下
7. 对于VMWare，我用StarWind V2V转换器将.img转换为.vmdk，然后像sata一样添加到虚拟机。另外，将ethernet0.VirtualDeb="e1000 "改为.vmx文件中的e1000e。

原文链接

[https://xpenology.com/forum/topic/45795-redpill-the-new-loader-for-624-discussion/page/76/](/uri)
