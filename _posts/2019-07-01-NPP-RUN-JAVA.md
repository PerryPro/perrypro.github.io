---
layout: post
title: NPPExec编译运行C++、JAVA和Python代码
subtitle: 
tags: [NPP]
---    

适用于NotePad++的NPPExec插件    

运行JAVA代码     
```
npp_save 
cd $(CURRENT_DIRECTORY) 
javac -encoding utf8  $(NAME_PART).java 
java $(NAME_PART) 
```
运行C++代码    
```
npp_save 
cd $(CURRENT_DIRECTORY) 
g++ -o "$(NAME_PART).exe" "$(FULL_CURRENT_PATH)" 
"$(NAME_PART)".exe 
```
运行Python代码
```
npp_save
cd   $(CURRENT_DIRECTORY)
python $(NAME_PART).py
```
