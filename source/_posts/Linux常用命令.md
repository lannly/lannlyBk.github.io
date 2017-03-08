---
title:  Linux常用命令
date: 2016-11-01 09:25:44
comments: true
categories: 学习笔记
tags: [linux]
keywords: linux, 命令
description: 以下是Linux常用命令等,随时更新补充~
---

### 1.ls命令
`ls命令是列出目录内容(List Directory Contents)的意思。运行它就是列出文件夹里的内容，可能是文件也可能是文件夹。`
	* “ls -l”命令以详情模式(long listing fashion)列出文件夹的内容。
	* "ls -a"命令会列出文件夹里的所有内容，包括以"."开头的隐藏文件。
### 2.sudo命令
`“sudo”(super user do)命令允许授权用户执行超级用户或者其它用户的命令。通过在sudoers列表的安全策略来指定。`
### 3.mkdir命令


---
#### 目录操作
| 命令名        | 功能描述              |  使用举例         |
| ------------- |:-------------:        |  -----:           |
| mkdir         | 创建一个目录          |  mkdir dirname    |
| rmdir         | 删除一个目录          |  rmdir dirname    |
| mvdir         | 移动或重命名一个目录  |  mvdir dir1 dir2  |
| pwd           | 显示当前目录的路径名  |  pwd              |
| ls            | 显示当前目录的内容    |  ls -l 或者 ls -a |
| dircmp        | 比较两个目录的内容    |  dircmp dir1 dir2 |


#### 文件操作
| 命令名        | 功能描述              |  使用举例         |
| ------------- |:-------------:        |  -----:           |
| cat           | 显示或连接文件        |  cat filename     |
| pg		    | 分页格式化显示文件内容|  pg filename      |
| more		    | 分屏显示文件内容      |  more filename    |
| od		    | 显示非文本文件的内容  |  od -c filename   |
| cp		    | 复制文件或目录        |  cp file1 file2   |
| rm		    | 删除文件或目录        |  rm filename      |
| mv		    | 改变文件名或所在目录  |  mv file1 file2   |
| rm		    | 删除文件或目录        |  rm filename      |
| ln		    | 联接文件              |  ln -s file1 file2|
| find		    | 使用匹配表达式查找文件| find . -name "*.c" -print    |
| file		    | 显示文件类型          |  file filename    |
| open		    | 使用默认的程序打开文件|  open filename    |

#### 时间操作
| 命令名        | 功能描述                  |  使用举例     |
| ------------- |:-------------:            |  -----:       |
| date          | 显示系统的当前日期和时间  |  date         |
| cal           | 显示日历                  | cal 8 1996    |
| time          | 统计程序的执行时间        |  time         |

