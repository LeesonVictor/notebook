# vscode使用

标签： vscode 插件 配置

---

- [vscode使用](#vscode使用)
  - [常用前端开发插件](#常用前端开发插件)
    - [通用](#通用)
    - [HTML](#html)
    - [JS](#js)
    - [VUE](#vue)
  - [常用markdown插件](#常用markdown插件)
  - [用户设置和工作区设置的区别](#用户设置和工作区设置的区别)

---

## 常用前端开发插件

### 通用

- chinese(simplified) langwage pack for visual studio code ：中文语言包
- code runner : 跑各种语言的代码（可用于写小Demo测试）
- vscode-pdf ：查看pdf
  
### HTML

- auto close tag ：帮助自动补齐html闭合标签  
- auto rename tag ：重命名标签时，自动重命名闭合标签
- open in browser : 在默认浏览器中打开html文件
  
### JS
  
- eslint ：es语法检查工具，带部分代码风格检查（一般会禁用，而用prettier代码风格）。
  注：一般有三种代码风格：standard、airbnb、prettier,其中prettier用得最多。
- javascript(es6) code snippets ：es6常用代码段

### VUE

- vetur ：vue常用代码段，集成prettier代码风格

## 常用markdown插件

- markdown all in one  ：
  - 生成/更新目录（命令Create/Update  Table of Contents,若要生成的目录兼容github,需勾选设置里的githubCompatibility）
  - 常用快捷键加粗、斜体等
  - 格式化table。alt+shift+f
  - 支持特殊数学符号渲染
  - 一边书写一边预览(Ctrl + Shift + V or Ctrl + K V) (markdown preview enhanced有此功能)
  - 导出html，命令Print current document to HTML（markdown pdf有此功能，且可以导出pdf、json等）
  - ...
- markdown preview enhanced ：优化markdown预览
- markdown pdf ：支持将.md文件导出为pdf、html等多种格式
- markdownlint ：markdown的格式检查
- ~~markdown toc~~(markdown all in one已带此功能) ：右键可自动生成目录，若生成中有aoto等乱码，需将vscode的默认行尾字符（Eol）设为\n。

## 用户设置和工作区设置的区别

用户设置全局生效。工作区设置只在该工作区生效。
工作区的存在可以避免加载过多无用的插件。特定工作去只加载特定的插件。比如java工作区只加载jiava相关的插件。
要新建一个工作区通过文件菜单下将工作区另存为即可。

     "files.autoSave": "onFocusChange" //当失去焦点时自动保存

[添加代码段](https://www.cnblogs.com/summit7ca/p/5225494.html)