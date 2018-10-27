
title: tmux 





---------------------

## tmux
tmux 中直接通过默认前缀 ctrl + b 之后输入对应命令来操作
    session 会话：session是一个特定的终端组合。输入tmux就可以打开一个新的session
        'tmux new -s session_name' 创建一个叫做 session_name 的 tmux session
        'tmux attach -t session_name' 重新开启叫做 session_name 的 tmux session
        tmux switch -t session_name 转换到叫做 session_name 的 tmux session
        tmux list-sessions / tmux ls 列出现有的所有 session
        'tmux detach' 离开当前开启的 session
        tmux kill-server 关闭所有 session
    window 窗口：session 中可以有不同的 window（但是同时只能看到一个 window）
        tmux new-window 创建一个新的 window
        tmux list-windows
        tmux select-window -t :0-9 根据索引转到该 window
        tmux rename-window 重命名当前 window
    pane 面板：window 中可以有不同的 pane（可以把 window 分成不同的部分）
        tmux split-window 将 window 垂直划分为两个 pane
        tmux split-window -h 将 window 水平划分为两个 pane
        tmux swap-pane -[UDLR] 在指定的方向交换 pane
        tmux select-pane -[UDLR] 在指定的方向选择下一个 pane


### 基本操作
    ? 列出所有快捷键；按q返回
    d 脱离当前会话,可暂时返回Shell界面
    s 选择并切换会话；在同时开启了多个会话时使用
    'D 选择要脱离的会话；在同时开启了多个会话时使用'
    : 进入命令行模式；此时可输入支持的命令，例如 kill-server 关闭所有tmux会话
    [ 复制模式，光标移动到复制内容位置，空格键开始，方向键选择复制，回车确认，q/Esc退出
    ] 进入粘贴模式，粘贴之前复制的内容，按q/Esc退出
    ~ 列出提示信息缓存；其中包含了之前tmux返回的各种提示信息
    t 显示当前的时间
    ctrl + z 挂起当前会话
    '$ 重命名session'

### session
1. open session

$ tmux new-session -s basic
或者
$ tmux new -s basic

-s参数表示session名称，如果不加-s参数，那么Tmux默认会新建一个以数字(下标从0开始)命名的session，并默认打开一个window。打开一个session后，后续的所有控制Tmux本身的快捷键都需要加前缀，默认是 Ctrl+b ，以下把前缀按键称为Prefix。

2. detach session 
想要暂时离开Tmux，回到终端环境时，可以通过快捷键 Prefix+d (d for detach)。要注意的时，即使是detach的状态，Tmux中在运行的程序还会继续运行。想要回到Tmux session时，只需执行：

$ tmux attach -t basic

-t参数可以指定要attach的session。

3. list session 
终端中执行 tmux ls (ls for list session)可以列出当前有多少个session。如果已经在session中，执行 Prefix+s (s for session)可以列出当前有多少个session，并且可通过上、下键选择要进入的session。

4. kill session 
要真正关闭一个session，可以在终端下执行命令 'tmux kill-session -t basic' ，其中-t参数表示session名称。

###　窗口操作
c '创建新窗口'
& '关闭当前窗口'
, '重命名当前窗口，便于识别'
. 修改当前窗口编号，相当于重新排序
f 在所有窗口中查找关键词，便于窗口多了切换
[0-9] 数字键切换到指定窗口
p 切换至上一窗口
n 切换至下一窗口
l 前后窗口间互相切换
w 通过窗口列表切换窗口


### 面板操作
" '将当前面板上下分屏'（我自己改成了 |）
% '将当前面板左右分屏'（我自己改成了 -）
x '关闭当前分屏'
Ctrl-方向键 '调整分隔窗口大小'
    ! 将当前面板置于新窗口,即新建一个窗口,其中仅包含当前面板
    ctrl+方向键 以1个单元格为单位移动边缘以调整当前面板大小
    alt+方向键 以5个单元格为单位移动边缘以调整当前面板大小
    q 显示面板编号
    o 选择当前窗口中下一个面板
    方向键 移动光标选择对应面板
    { 向前置换当前面板
    } 向后置换当前面板
    alt+o 逆时针旋转当前窗口的面板
    ctrl+o 顺时针旋转当前窗口的面板
    z 最大化当前所在面板
    page up 向上滚动屏幕，q 退出
    page down 向下滚动屏幕，q 退出
Prefix+Space (空格键): 对当前窗口下的所有pane重新排列布局，每按一次，换一种样式。 
Prefix+z : 最大化当前pane。再按一次后恢复。

### 合并


'''试想这样一个场景：当你打开多个窗口后，然后想将其中几个窗口合并到当前窗口中，以便对比观察输出。

实际上，你的要求就是将其它窗口变成面板，然后合并到当前窗口中。对于这种操作，我们可以在当前窗口，按下prefix + :，打开命令行，然后输入如下命令：

join-pane -s window01 # 合并名称为window01的窗口的默认（第一个）面板到当前窗口中
join-pane -s window01.1 # .1显式指定了第一个面板，.2就是第二个面板(我本地将面板编号起始值设置为1，默认是0)

每次执行join-pane命令都会合并一个面板，并且指定的窗口会减少一个面板，直到面板数量为0，窗口关闭。

除了在当前会话中操作外，join-pane命令甚至可以从其它指定会话中合并面板，格式为join-pane -s [session_name]:[window].[pane]，如join-pane -s 2:1.1 即合并第二个会话的第一个窗口的第一个面板到当前窗口，当目标会话的窗口和面板数量为0时，会话便会关闭。


### 自定义配置
如果没有配置文件的话先创建: touch ~/.tmux.conf
```
# Send prefix 
set-option -g prefix C-a
unbind-key C-a 
bind-key C-a send-prefix 

# Use Alt-arrow keys to switch panes 
bind -n M-Left select-pane -L 
bind -n M-Right select-pane -R 
bind -n M-Up select-pane -U 
bind -n M-Down select-pane -D

# Shift arrow to switch windows 
bind -n S-Left previous-window 
bind -n S-Right next-window 

# Mouse mode 
set -g mouse on 

# Set easier window split keys 
bind-key v split-window -h 
bind-key h split-window -v 

# Easy config reload 
bind-key r source-file ~/.tmux.conf \; display-message "tmux.conf reloaded"

# key bindings for horizontal and vertical panes
unbind %
bind | split-window -h # 使用|竖屏，方便分屏
unbind '"'
bind - split-window -v # 使用-横屏，方便分屏

#-- statusbar --#
set -g status-justify centre
set -g status-left "#[fg=red]s#S:w#I.p#P#[default]"
set -g status-right '[#(whoami)#(date +" %m-%d %H:%M ")]'
set -g status-left-attr bright
set -g status-left-length 120
set -g status-right-length 120
set -g status-utf8 on
set -g status-interval 1
set -g visual-activity on
setw -g monitor-activity on
setw -g automatic-rename off
# default statusbar colors
set -g status-bg colour235 #base02
set -g status-fg colour136 #yellow
set -g status-attr default
# default window title colors
setw -g window-status-fg colour244
setw -g window-status-bg default
#setw -g window-status-attr dim
# active window title colors
setw -g window-status-current-fg colour166 #orange
setw -g window-status-current-bg default
#setw -g window-status-current-attr bright
# window title string (uses statusbar variables)
set -g set-titles-string '#T'
set -g status-justify "centre"
set -g window-status-format '#I #W'
set -g window-status-current-format ' #I #W '
# pane border
set -g pane-active-border-fg '#55ff55'
set -g pane-border-fg '#555555'
# message text
set -g message-bg colour235 #base02
set -g message-fg colour166 #orange
# pane number display
set -g display-panes-active-colour colour33 #blue
set -g display-panes-colour colour166 #orange
# clock
setw -g clock-mode-colour colour64 #green


Send prefix
把prefix的ctrl+b变为了ctrl+a，因为这样按起来方便些。基本上用tmux的都改了这个。

Use Alt-arrow keys to switch panes
不用按prefix，直接用alt+箭头在pane之间switch。实际用过之后才发现真是太方便了！

Shift arrow to switch windows
不用按prefix，直接用shift+箭头在window之间switch。太方便了！

Mouse mode
开启鼠标模式。用鼠标就能切换window，pane，还能调整pane的大小，方便！

Set easier window split keys
这一部分是用来更方便切分pane的。prefix + v 代表竖着切，prefix + h 代表横着切。比起默认的切割方法不仅直观而且方便。

首先，在更改了.tmux.conf后，在tmux里的快捷键没有变化。查找后发现是tmux只有在新建session的时候，才会去找tmux.conf文件。所以说，之前创建的那些session都没有参考tmux.conf. 就用tmux ls  tmux kill-session -a只保留当前session。再删除当前session 'tmux kill-session -t XX'。这下删除了所有创建好的session。


## 放大字体

Ctrl+shift+“+”

## 黏贴
要按住shift,再右键
## 参考文献


https://blog.csdn.net/u011138533/article/details/53109247
https://www.cnblogs.com/piperck/p/4992159.html
