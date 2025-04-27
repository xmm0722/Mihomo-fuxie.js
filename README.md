# 备份自用的一些配置文件


```
.
├── clash
│   ├── clash-mihomo.yaml   # mihomo part覆写的配置文件
│   ├── clash-script.js     # 修改自dahaha-365大佬的脚本，细微改动，修复dns泄露
│   └── clash.js            # Clash Verge Rev 全局扩展脚本（懒人配置）/ Mihomo Party 覆写脚本
│   └── clash.yaml          # Clash 裸核配置文件
├── mac
│   └── install.sh
└── README.md
```

# MacBook 裸核教程
```bash
# 进入到用户目录的启动项管理
cd ~/Library/LaunchAgents
# 创建启动项文件
touch mihomo.plist
```

## 将文件内容写入`mihomo.plist`，需要自己修改路径

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>mihomo</string>
    <key>ProgramArguments</key>
    <array>
        <!-- 替换为你的 mihomo 可执行文件路径 -->
        <string>/path/mihomo</string>
        <!-- 可选：指定配置路径 -->
        <string>-d</string>
        <string>/path/mihomo/</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>KeepAlive</key>
    <true/>
    <key>StandardOutPath</key>
    <!-- 日志存路径，自己设置 -->
    <string>/tmp/mihomo/clash-meta.log</string>
    <key>StandardErrorPath</key>
    <string>/tmp/mihomo/cmihomo/clash-meta.error.log</string>
</dict>
</plist>
```
## 启动
```bash
launchctl start mihomo
```
## 配置文件
（config.yaml）会在启动后自动生成
修改config.yaml，自己配置，或者用我的路径在clash/config.yaml
修改完之后执行`launchctl stop mihomo`会自动重启内核，重新加载配置文件