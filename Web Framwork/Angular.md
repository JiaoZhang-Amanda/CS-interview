* [Angular介绍](#fireAngular介绍)
* [Angular应用开发](#fireAngular应用开发)
* [项目目录结构](#fire项目目录结构)

* [模版语法](#fire模版语法)

## :fire:Angular介绍
### 什么是AngularJs？
AngularJs是一个JavaScript framework，它能够创建Web，Mobile，Desktop Application。Google创建
* **优势**
    * Dependency Injection依赖注入
    * Two Way Data-Binding 双向数据绑定
    * Test测试
    * Model-View Controller 控制
    * Directives 指令，Pipe 管道操作，service 服务，animate 动画等
    
### MVC
Model-View-Controller
改变model，更新view；改变view，更新model

### 版本
* **Angular1** = AngularJs，一个应用面非常广泛的JS框架
* **Angular2** = Angular，重构的JS框架，与Angular1基本没关系
* **Angular4** = Angular2+，对Angular2的向下兼容性做的一些更新与改进（为了解决版本冲突，官方跳过了Angular3）

## :fire:Angular应用开发
### 准备
* Node.js
angular的CLI需要的NodeJs的环境基础
“https://nodejs.org/en/”
* Angular CLI
Angular提供的一个命令行工具，让用户通过命令行创建和管理项目。
`npm install -g @angular/cli`
* IDE：Visual Studio Code
“https://code.visualstudio.com/download”
* Debug: Visual Studio Code Chrome Debugger Extension
"https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome"

* Tip: To test that you have Node.js and npm correctly installed on your machine, you can type node --version and npm --version.

### 步骤
1) 创建新的Angular项目：ng new
`ng new XXX`
<br>第一次因为需要安装nodenode-modules，所以会很慢
2) 运行应用：ng serve
<br>进入对应应用的文件夹`cd XXX`
<br>使用CLI命令启动服务器`ng serve --open`，运行刚刚创建的angular项目
<br>浏览器输入`http://localhost:4200`，运行地址
3) 停止运行: Ctrl + c
`Ctrl + c`

## :fire:项目目录结构
命令行工具自动生成了很多文件和目录
* **e2e**: 端到端的测试目录，用来做自动测试
* **node_modules**: 第三方依赖包存放目录 
* **src**: 应用源代码目录
    * **app**: 包含应用的组件与模块，我们需要系的代码都在这个目录
        <br>一个Angular程序至少需要一个模块和一个组件
        * **app.component.ts**: 组件，Angular应用的基本构件模块，可以理解为一段带有业务逻辑和数据的Html
        * **app.component.css**
        * **app.component.html**
        * **app.component.spec.ts**
        * **app.module.ts**: 模块，与AppComponent类似，模块也需要装饰器来装饰。
    * **assets**: 资源目录，存储静态资源，比如图片
    * **environments**: 环境配置，Angular支持多环境开发，可以在不同的环境下共用一套代码
    * **index.html**: 应用的根html，程序启动就是访问这个页面
    * **main.ts**: 整个项目的入口点，Angular通过这个文件来启动项目
    * **polyfills.ts**: 主要用来导入一些必要库，为了让Angular能正常运行在老版本下
    * **style.css**: 放全局样式
    * **tsconfig.app.json**: TypeScript编译器的配置，添加第三方依赖的时候修改这些文件
    * **tsconfig.spec.json**: 不用管
    * **test.ts**: 自动化测试用
    * **typings.d.ts**: 不用管
* **.angular-cli.json**: Angular命令行工具的配置文件，引入一些第三方包会修改它，比如jQuery
* **karma.conf.js**: karma是单元测试的执行器，karma.conf.js是karma的配置文件
* **package.json**: 标准的npm工具的配置文件，该文件中列出了应用程序所使用的第三方依赖包。刚开始建立项目的时候，因为下载第三方依赖包，所以会慢，下载完成放在node_modules这个目录中。后期可能会修改
* **protractor.conf.js**: 自动化测试的配置文件
* **README.md**: 说明文件
* **tslint.json**: tslint的配置文件，用来定义TypeScript代码质量检查的规则，不用管。
### app.component.ts组件
```
//导入依赖：从Angular核心模块里面引入了component装饰器
import { Component } from '@angular/core';

//声明创建组件
@Component({
  selector: 'app-root', //定义一个新的HTML标签：这个标签表示我们希望在HTML中使用该组件。
  templateUrl: './app.component.html', //添加模板，当Angular加载该组件时，就会读取此文件的内容作为组件的模板。
  styleUrls: ['./app.component.css'] //添加CSS样式，在特定组件中指定的样式只会应用于该组件本身
})

export class AppComponent {
  title = 'XXX';
}
```
### app.module.ts模块
```
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { FormsModule } from '@angular/forms'; // <-- NgModel lives here

import { AppComponent } from './app.component';
import { HeroesComponent } from './heroes/heroes.component';

//使用@NgModule来标记一个类，使之成为Angular模块类
@NgModule({
  //声明此NgModule模块中有什么东西，只能声明组件，指令，管道（(Component、Directive、Pipe)
  declarations: [
    AppComponent,
    HeroesComponent
  ],
  //引用其他NgModule来配合工作，声明模块所依赖的模块
  imports: [
    BrowserModule,
    FormsModule
  ],
  // 依赖注入的Service。默认为空，只能声明模块中听过的服务
  providers: [],
  //声明模块中的主组件是什么，通常只有一个Component
  bootstrap: [AppComponent]
})
export class AppModule { }
```
### index.html
```
<!doctype html>
<html lang="en">
//声明了页面的字符集（charset）、标题（title）和基础URL（base href）。
<head>
  <meta charset="utf-8">
  <title>XXX</title>
  <base href="/">

  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="icon" type="image/x-icon" href="favicon.ico">
</head>
<body>
  //加载组件：我们的应用将会在app-root标签处进行渲染
  <app-root></app-root>
</body>
</html>
```
## :fire:模版语法
