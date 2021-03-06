# SAAS产品线多项目前端架构

架构的目的是制定标准，提升质量和效率，构建一个易维护，代码简洁，性能优化程度高的项目。

架构是个不断完善的过程，而把架构尤其是跟规范相关的部分落实到具体业务系统里面更是个团队不断磨合的过程。

## 代码规范化

项目目录结构清晰，当进行开发的时候，哪些代码应该放到哪里都进行了明确的规定，并且每个文件的功能都尽量清晰并且单一，方便维护及新成员快速上手。

- 代码风格遵循[angular风格指南](https://github.com/johnpapa/angular-styleguide)
- 目录规范：按业务划分
- 文件规范：单一职责
- 使用代码风格检查工具 csslint eslint
- 使用 es6 编写最新业务组件，并持续优化遗留业务组件

## 核心模块

- 路由动态管理中心模块
- 菜单动态管理中心模块
- 鉴权认证中心模块
- 公共框架样式
- 公共组件
- 公共服务模块 genedock_sdk
- 全局变量配置模块
- 依赖插件默认配置

## 前端路由控制

- 公共路由管理（401，403，404，500等）
- 默认路由管理（a项目默认/patients，b项目默认/projects...）
- 模块路由动态注入

## 权限控制

- UI控制(根据用户拥有的权限,判断页面上的一些内容是否显示、导航菜单控制、新增编辑等操作按钮的显示隐藏等...)
- 前端路由控制(当用户访问一个它没有权限访问的url时,跳转到一个错误提示的页面)
- HTTP请求控制(当我们发送一个数据请求,如果返回的status是401或者403,则通常重定向到一个错误提示的页面)
- 模块policy动态注入

## 样式展现

- 统一公共UI框架 bootstrap
- 多项目根据配置样式动态切换
- 组件样式独立性（不受其他组件影响）

## 开发

- 通过 npm script 统一管理前端脚本
- 实时编译、页面热加载
- 业务组件通过entry导入来控制
- 使用json模拟数据快速开发产品原型
- 多项目代码分离，方便新进人员快速理清业务模块

## 前端部署

- 多项目切换（如根据配置动态切换数据库、配置项、API、前端模块）
- 模块安装速度及稳定性优化（nvm yarn npmrc）
- 统一构建工具 webpack，gulp仅负责静态文件拷贝及任务流程控制
- webpack 编译打包优化
- 静态资源缓存控制及CDN部署
- 使用 webpack 按需加载

## 前后端联调

- 前后端使用公共测试环境快速联调
- 前端flask路由清理，仅保留入口路由及用户登录控制
- API文档化
- API风格调整，整体基于RESTful，清理路由末尾斜杠/
- API访问认证自动注入
- 某些API不需要认证（登录控制、开放数据）

## 整体医疗业务线项目部署

- docker compose：使用 Docker Compose 编排容器集群，快速在集群中部署分布式应用。一个文件可以列出所有依赖的服务，并显式声明依赖（例如web依赖account、 api 依赖backend 等），配置灵活，透明，可控 (仅需要关注一个配置文件)，操作方便（cli命令行操作，--help查看帮助，可对单个容器进行操作等），安全 （网络隔离、文件挂载保护等），docker官方维护更新，文档齐全。
- docker ignore： node_modules 小文件太多，挂载效率太慢，通过忽略大文件，加快 build 速度
- Travis Ci：通过 Travis Ci 运行测试代码来做构建集成测试，后续会考虑进行测试环境自动部署
- 多项目部署切换：通过项目根目录下 config.yml 配置文件或对应的环境变量切换项目

## 痛点问题解决方案

- 公共模块通过私有 npm registry 解决版本依赖问题，通过 yarn.lock 锁定版本依赖
- webpack 编译后端模版问题（通过抽离用户登录为API请求，做到前后端完全分离）
- 编写公共模块使用文档解决公共模块团队使用问题
- 服务器端渲染解决SEO问题
