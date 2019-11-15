### 快捷键

> 截图

#### shift(⬆️)+command +4。再按空格截当前窗口。

#### shift+command+3,截全屏。

> 设置 DOCK 栏的隐藏速度

```
//这里设置为0，也可以设置0.1，0.5等。
 defaults write com.apple.dock autohide-time-modifier -int 0;killall Dock

```

> 恢复 DOCK 栏的隐藏速度

```
defaults delete com.apple.dock autohide-time-modifier;killall Dock

```
