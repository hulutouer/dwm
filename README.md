---
date created: 2022-10-28 06:23
date updated: 2022-10-28 07:07
转载请注明出处，有错误欢迎指出
---

## 预览
![screenshot](https://github.com/hulutouer/dwm/blob/main/screenshot.png)

## `X server` 或者其他

安装`x server`

```bash
sudo pacman -S xorg-server xorg-xinit
sudo cp /etc/X11/xinit/xinitrc ~/.xinitrc
```

## 下载`alacritty` 、`rofi`

```bash
sudo pacman -S alacritty rofi
```

### 编辑 `.xinitrc`

#### 需要注释掉的内容

```
# twm &
# xclock -geometry 50x50-1+1 &
# xterm -geometry 80x50+494+51 &
# xterm -geometry 80x20+494-0 &
# exec xterm -geometry 80x66+0+0 -name login
```

#### 需要追加的内容

```
# 在不登出和退出程序程序的情况下重启dwm
while true; do
    dwm 2> ~/.dwm.log
done
```

### 编辑 `.bashrc` 追加以下

追加

```
if [[ ! $DISPLAY && $XDG_VTNR -eq 1 ]]; then
  exec startx
fi
```

## 下载此存储库

```bash
git clone https://github.com/hulutouer/dwm.git 
```

## 字体

### 离线安装字体

```bash
cd dwm/fonts
cp -r fonts/* /usr/share/fonts
cd /usr/share/fonts
mkfontscale
mkfontdir
fc-cache -v

```

### 在线安装字体(安装时间不同，名字可能会有变化)

```bash
sudo pacman -S  wqy-microhei ttf-jetbrains-mono ttf-nerd-fonts-symbols-2048-em-mono
```

## 安装dwm

```bash
cd dwm/
sudo make clean install 
```

## 第一次启动dwm

```bash
startx
```

## 快捷键速览

|组合键| 功能|
|---|---|
|super + r| 程序启动器（rofi）|
|super + enter| 启动termcmd(alacritty)|
|super + b| 显示&隐藏bar|
|super + j| 切换活动窗口（多窗口下）|
|super + k| 切换活动窗口（多窗口下）|
|super + h| 增加活动窗口的显示面积（多窗口下）|
|super + l| 减少活动窗口的显示面积（多窗口下）|
|super + shift +c| 关闭当前程序|
|super + t| 切换layout为动态布局|
|super + f| 切换layout为层叠布局|
|super + m| 切换layout为全屏层叠布局|
|super + space| 切换上一次layout|
|super + 1,2,3...| 切换标签页|
|super + shift + q| 退出dwm （刷新dwm配置时使用）|
|super + shift + 2| 将当前活动窗口移动到第二个标签页|

## 设置分辨率(如果需要)

主要通过xrandr 命令设置

终端输入`xrandr`查看支持的`显示器接口`和`分辨率`

```bash
xrandr --output eDP-1 --mode 1920x1080 --rate 60  # 设置eDP-1接口的显示器分辨率为1920x1080 刷新率60hz
```

## 可选的快捷键(截图、屏幕亮度、音量控制)

### 安装依赖

```bash
sudo pacman -S flameshot light alsa-utils
```

|组合键|功能|
|---|---|
|super + shift + a| 截图|
|super + F1| 静音|
|super + F2| 音量减小5%|
|super + F3| 音量增加5%|
|super + F5| 背光增加10%|
|super + F6| 背光减少10%|

> 如果不能控制背光请尝试:
- `fn + 组合键`
- 将当前用户添加到video组并且重启电脑`usermod -G video YourUserName`

## 锁屏

参看
