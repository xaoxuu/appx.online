---
type: 书签
order: 1
title: macOS常用终端命令
---


## <i class="fa fa-file fa-fw"></i>显示隐藏文件

### <i class="fa fa-eye fa-fw"></i>显示
```bash
defaults write com.apple.finder _FXShowPosixPathInTitle -bool TRUE;
killall Finder
```

### <i class="fa fa-eye-slash fa-fw"></i>隐藏
```bash
defaults delete com.apple.finder _FXShowPosixPathInTitle;
killall Finder
```

## 安装包已损坏的解决办法

```bash
sudo spctl --master-disable
```

## <i class="fa fa-folder-open fa-fw"></i>外置磁盘路径

```bash
/volume/磁盘路径/~~~
```
例如一个名称为"Files"的磁盘里的文件夹"Projects"路径是:
```bash
/Volumes/Files/Projects/
```


## <i class="fa fa-exchange fa-fw"></i>使用终端将 json 文件转为 plist 文件

```bash
plutil -convert xml1 data.json -o data.plist
```

其中`data.json`、`data.plist`分别对应转换前后的文件路径。


## sudo依然没有权限的解决办法

### 查询SIP状态

```bash
csrutil status
```

如果输出：
```bash
System Integrity Protection status: enabled.
```
说明SIP保护开启，需要暂时关闭SIP。

### 关闭SIP保护

重启Mac，按住【⌘】+【R】直到出现开机logo，此时会进入Recovery模式，选择实用工具菜单中的终端（Terminal）
输入以下命令：

```bash
csrutil disable
```

然后重新启动电脑即可关闭SIP保护。

### 开启SIP保护

重启Mac，按住【⌘】+【R】直到出现开机logo，此时会进入Recovery模式，选择实用工具菜单中的终端（Terminal）
输入以下命令：

```bash
csrutil enable
```

然后重新启动电脑即可开启SIP保护。
