* [Angular介绍](#fireAngular介绍)
* [Angular应用开发](#fireAngular应用开发)
* [项目目录结构](#fire项目目录结构)

* [TypeScript语法](#fireTypeScript语法)
* [Angular的架构及概念](#fireAngular的架构及概念)
    * [组件和模板](#组件和模板)： 组件数据绑定，数据请求，指令模块，管道操作(类似过滤器)
    * [表单](#表单)
    * [NgModules](#NgModules)
    * [依赖注入](#依赖注入)
    * [路由配置与操作](#路由)
    * [网络请求](#网络请求)
* [RxJS](#fireRxJS)
* [动画测试](#fire动画测试)
* [项目发布](#fire项目发布)

## :fire:Angular介绍
### 什么是AngularJs？
AngularJs是一个JavaScript framework，它能够创建Web，Mobile，Desktop Application。Google创建
* **优势**
    * Dependency Injection [依赖注入](#fire依赖注入)
    * Two Way Data-Binding [双向数据绑定](#双向数据绑定)
    * Test测试，可以对具体模块进行单元测试，便于后面模块整合
    * Model-View Controller 控制
    * 提供Directives 指令，Pipe 管道操作，service 服务，animate 动画等服务
    
### MVC
Model-View-Controller: 改变model，更新view；改变view，更新model
* M即数据模型: 可以将service服务层认为就是MVC中的M层
在angular中可以认为是从服务端获取的数据，因为angular提倡的是组件化、模块化开发。所以不建议将与后台交互的业务逻辑、数据请求与组件混合，而是专门放在服务即service中单独处理，通过依赖注入（DI）的形式将获取到的数据注入到所应用的组件。所以。
* V即视图层: 在angular中视图就是在@componet装饰器中组装的html模板
* C即控制器: 在angular中可以理解为组件。

### 版本
* **Angular1** = AngularJs，一个应用面非常广泛的JS框架
* **Angular2** = Angular，重构的JS框架，与Angular1基本没关系。
* **Angular4** = Angular2+，对Angular2的向下兼容性做的一些更新与改进（为了解决版本冲突，官方跳过了Angular3）

## :fire:Angular应用开发
### 准备
* **Angular CLI**
cli.angular.io
command-line-interface
因为Angular基于TypeScript，TypeScript不能被网页解析，所以需要有一套工具对程序进行预编译，将ts编译成浏览器可解析的js代码。之后angular项目的创建，组件的构建，项目的发布等操作都将有cli进行管理和操作。
Angular提供的一个命令行工具，让用户通过命令行创建和管理项目。
`npm install -g @angular/cli`
* **Node.js**
angular的CLI需要的NodeJs的环境基础
“https://nodejs.org/en/”
* **IDE：Visual Studio Code**
“https://code.visualstudio.com/download”
* **Debug: Visual Studio Code Chrome Debugger Extension**
"https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome"

* **Tip**: To test that you have Node.js and npm correctly installed on your machine, you can type node --version and npm --version.

### 步骤
1) **创建新的Angular项目**：ng new
`ng new XXX`
<br>第一次因为需要安装nodenode-modules，所以会很慢
2) **运行应用**：ng serve
<br>进入对应应用的文件夹`cd XXX`
<br>使用CLI命令启动服务器`ng serve --open`，运行刚刚创建的angular项目
<br>浏览器输入`http://localhost:4200`，运行地址
3) **停止运行**: Ctrl + c
`Ctrl + c`

## :fire:项目目录结构
命令行工具自动生成了很多文件和目录
* **e2e**: 端到端的测试目录，用来做自动测试
    * **protractor.conf.js**: 自动化测试的配置文件
* **node_modules**: 第三方依赖包存放目录 
* **src**: 应用源代码目录
    * **app**: 包含应用的组件与模块，我们需要系的代码都在这个目录
        <br>一个Angular程序至少需要一个模块和一个组件
        * **app.component.ts**: 组件，Angular应用的基本构件模块，可以理解为一段带有业务逻辑和数据的Html。typescript脚本文件
        * **app.component.css**：组件样式
        * **app.component.html**：组件模版
        * **app.component.spec.ts**：单元测试文件
        * **app.module.ts**: 模块，与AppComponent类似，模块也需要装饰器来装饰。数据模型定义的文件
    * **assets**: 资源目录，存储静态资源，比如图片
    * **environments**: 环境配置，Angular支持多环境开发，可以在不同的环境下共用一套代码
    * **index.html**: 应用的根html，程序启动就是访问这个页面
    * **main.ts**: 整个项目的（脚本）入口点，Angular通过这个文件来启动项目
    * **polyfills.ts**: 主要用来导入一些必要库，为了让Angular能正常运行在老版本下
    * **style.css**: 放全局样式
    * **test.ts**: 自动化测试用，单元测试入口文件
* **.editorconfig**: 编辑器的配置文件
* **.gitignore**: git代码版本管理忽略的配置文件
* **angular.json**:
* **karma.conf.js**: karma是单元测试的执行器，karma.conf.js是karma的配置文件
* **package-lock.json**:
* **package.json**: 标准的npm工具的配置文件，该文件中列出了应用程序所使用的第三方依赖包。刚开始建立项目的时候，因为下载第三方依赖包，所以会慢，下载完成放在node_modules这个目录中。后期可能会修改
* **README.md**: 说明文件
* **tsconfig.app.json**: TypeScript编译器的配置，添加第三方依赖的时候修改这些文件
* **tsconfig.json**: ts配置文件
* **tsconfig.spec.json**: 测试配置文件，不用管
* **tslint.json**: tslint的配置文件，用来定义TypeScript代码质量检查的规则，不用管。

### index.html
```javascript
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
### main.ts
```
import { enableProdMode } from '@angular/core';
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';

import { AppModule } from './app/app.module'; //引入子组件
import { environment } from './environments/environment';

if (environment.production) {
  enableProdMode();
}

platformBrowserDynamic().bootstrapModule(AppModule)
  .catch(err => console.error(err));
```
### app.module.ts模块
```javascript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component'; //操作的组件

//使用@NgModule来标记一个类，使之成为Angular模块类
@NgModule({
  //声明此NgModule模块中有什么东西，只能声明组件，指令，管道（(Component、Directive、Pipe)
  declarations: [
    AppComponent
  ],
  //引用其他NgModule来配合工作，声明模块所依赖的模块
  imports: [
    BrowserModule,
    AppRoutingModule
  ],
  // 依赖注入的Service。默认为空，只能声明模块中听过的服务
  providers: [],
  //声明模块中的主组件是什么，通常只有一个Component
  bootstrap: [AppComponent]
})
export class AppModule { }
```
### app.component.ts组件
```javascript
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
## :fire:TypeScript语法
## :fire:Angular的架构及概念
### 组件和模板
#### 组件数据绑定
从界面的操作能实时反映到数据，数据的变更能实时展现到界面
 [(x)]语法结合了属性绑定的方括号[x]和事件绑定的圆括号(x)。
 Angular 以 NgModel 指令为桥梁，允许在表单元素上使用双向数据绑定。

可以在开发时更关注业务结构和逻辑结构

#### 数据请求，指令模块，管道操作(类似过滤器)
### 表单
### NgModules](#NgModules)
### 依赖注入
### 路由配置与操作
### 网络请求
### 依赖注入
保证项目更加高性能和更加安全

## :fire:RxJS
## :fire:动画测试
## :fire:项目发布

