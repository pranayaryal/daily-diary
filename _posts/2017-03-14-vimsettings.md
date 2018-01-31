---
layout: post
title:  Configuring Vim
---

These are steps you can take to configure your vim to make it look prettier and improve file browsing. You will also find tips on how to set up your .vimrc file plugins.vim file.

## 1. Making Vim Prettier
These are some of the settings to configure Vim to make it look prettier. And then wget atom-dark-256.vim

Inside your .vim directory make a folder named 'colors'
```
cd ~/.vim
mkdir colors
cd colors
wget https://raw.githubusercontent.com/gosukiwi/vim-atom-dark/master/colors/atom-dark-256.vim
#if you do ls you should see the newly installed file
```


## 2. Your .vimrc file
Paste <a href="https://gist.githubusercontent.com/pranayaryal/95cd000b91c7b841cbf0b63d82f7f588/raw/577817f3222f976642bdac9da2812c9497640869/new_gist_file_0" target="_blank">this code</a> inside your .vimrc file

## 3. Make a file inside ~/.vim named plugins.vim
```
cd ~/.vim
touch plugins.vim
```

## 4. Install a Plugin Manager like Vundle
Type this in your terminal
```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

## 5. Your ~/.vim/plugins.vim file
Paste  <a href="https://gist.githubusercontent.com/pranayaryal/010cdee74b705092fb0b516fe880e472/raw/d1546ae6611e80e195d389859e5700effa24833f/new_gist_file_0" target="_blank">this code</a> inside plugins.vim

Then install the plugins using this command inside the ~/.vim/plugins.vim file
```
:PluginInstall
```

This should install all your plugins

## 6. Download ctags
Then type this in the project you want to be searchable. You might have to create a tags/ directory in your project
{% highlight ruby %}
ctags -R
{% endhighlight %}

I hope this helps
