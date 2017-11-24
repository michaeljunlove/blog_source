clearReading: true
thumbnailImage: http://7xid80.com1.z0.glb.clouddn.com/工大向日葵.jpg
thumbnailImagePosition: right
autoThumbnailImage: yes
metaAlignment: center
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大向日葵.jpg
coverCaption: "工大的向日葵"
coverMeta: out
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大向日葵.jpg
comments: false
title: oh-my-zsh
date: 2016-05-27 18:38:44
tags: [oh-my-zsh]
categories: [工具]

---
作为一个程序员，开发效率还是需要的，好的命令行工具是必备的。推荐使用这款。
<!-- more -->
***
# 学习网站

 * [oh-my-zsh](http://ohmyz.sh/)


# 安装

``` markdown
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

# 在mac中用命令行时用sublime打开文件

## 在默认shell下
``` markdown
sudo ln -s "/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl" /usr/bin/subl
```

## 使用zsh的可以使用以下命令
``` markdown
alias subl="'/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl'"
alias nano="subl"
export EDITOR="subl"
```
