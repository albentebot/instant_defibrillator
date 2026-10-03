# Instant Defibrillator 0.1.0

把除颤器的使用读条和复活延迟都压到几乎为零，倒地队友一键拉起。真人幸存者和Bot同时生效，除颤器正常消耗，不赠送物品。

| 功能 | 默认值 |
| --- | --- |
| 除颤器使用读条 | 0.2 秒 |
| 除颤器复活延迟 | 0.0 秒 |

极简实现：启动时设置两个游戏内建变量，没有循环计时器、配置文件或聊天命令。

## 安装

退出游戏，把 `instant_defibrillator.vpk` 放到：

```text
/steamapps/common/Left 4 Dead 2/left4dead2/addons/
```

在"附加内容"启用 **Instant Defibrillator**。开启单机战役/写实，或自己作为房主的本地服务器。

只安装一份本Mod的VPK，源码文件夹无需放入游戏。不需要SourceMod、Metamod或其他脚本库。

## 实现说明

启动时执行两条 `Convars.SetValue`：

```text
defibrillator_use_duration         = 0.2
defibrillator_return_to_life_time  = 0.0
```

- `defibrillator_use_duration`：手持除颤器按E后的读条时长，原值2秒。
- `defibrillator_return_to_life_time`：读条完成后，倒地者回到站立状态的延迟，原值3秒。

除颤器仍须正常拾取和消耗，不影响其他治疗行为（急救包、扶人、回血）。只在服务端有意义——单机和本地服务器自动生效；加入官方或他人服务器时，仅本机安装无效。

## 兼容与关闭

仅修改两个游戏变量，启动时覆盖，关闭或移除VPK后重开地图即恢复游戏默认值。

与其他修改相同convar的Mod叠加时，以最后加载者为准。其他加速Mod或自定义地图可能改写同一变量，建议用控制台 `defibrillator_use_duration` 和 `defibrillator_return_to_life_time` 检查实际值。

完整卸载请退出游戏后移除其VPK并重启。
