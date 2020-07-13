# fed-e-task-02-01

### 简答题
- 1、谈谈你对工程化的初步认识，结合你之前遇到过的问题说出三个以上工程化能够解决问题或者带来的价值。
  - 工程化认识：
    - 遵循一定的标准与规范，通过工具取提高开发效率的一种手段
  - 解决的问题：
    - 以前使用在线网站压缩混淆js文件，现在工程化工具直接将项目中所有文件压缩js转换，解决重复性机械式的工作
    - 使用工程化可快速创建项目，并进行统一架构、代码风格等
    - 前端在开发预览阶段，可提供一个基础的web服务使项目运行起来，同时可支持热更新等功能提高开发效率
    - 团队协作开发时，传统开发方式会导致代码风格不统一，代码review困难，工程化项目中提供钩子可在提交前进行风格检测
    - 工程化可实现自动化部署，避免手动部署出错带来服务宕机等重大事件
- 2、你认为脚手架除了为我们创建项目结构，还有什么更深的意义？
  - 脚手架不仅是为了创建项目结构，它是对项目的整体的规划或架构，一个脚手架是一个集成式工程化方案

### 编程题
- 1、概述脚手架实现的过程，并使用 NodeJS 完成一个自定义的小型脚手架工具
  - 实现目标
  - 在终端中使用 ```xwatson init xxx``` 命令自动创建项目
    - 询问用户项目名称、版本号、描述信息
    - 下载远程GitHub模板生成项目结构
  - 使用的插件
    - commander - 处理命令行参数
    - inquirer - 命令行交互
    - ejs - 模板引擎
    - download-git-repo - 下载远程git仓库
    - metalsmith - 静态站点生成器
    - glob - 获取文件夹下所有文件
  - 实现思路
    - 基于commander获取到用户命令行输入项目目录名称
    - 使用promise分步骤执行异步操作
    - 使用glob获取当前执行命令目录文件，用于检测项目是否存在
    - 创建项目目录后，使用download-git-repo插件开始下载远程目录，远程目录配置在package.json中的tempUrl字段
    - 将模板下载到项目.download-temp文件夹下临时保存
    - 使用inquirer命令行交互，询问用户项目名、版本号、描述
    - 将询问后的答案，传递给metalsmith插件，metalsmith插件将读取下载的模板临时目录文件，并使用ejs.render将用户答案渲染到文件中
    - 文件输出后删除临时目录
    - 完成项目自动创建
  - 安装
    - 克隆项目
      ```bash
      git clone https://github.com/Xwatson/cli-demo.git
      yarn 或 npm install
      ```
    - link
      ```bash
      yarn link 或 npm link
      ```
    - 运行
      ```bash
      xwatson init [your project name]
      ```
    - [脚手架工具项目地址](https://github.com/Xwatson/cli-demo)

- 2、尝试使用 Gulp 完成项目的自动化构建
  - [代码地址](https://github.com/Xwatson/pages-boilerplate-gulp)
- 3、使用 Grunt 完成项目的自动化构建
  - [代码地址](https://github.com/Xwatson/pages-boilerplate-grunt)