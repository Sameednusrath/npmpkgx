# npmpkgx  

---
![GitHub package.json version](https://img.shields.io/github/package-json/v/bitjerry/npmpkgx?style=flat-square)
[![NPM Version](https://img.shields.io/npm/v/npmpkgx?style=flat-square)](https://www.npmjs.org/package/npmpkgx)
![NPM](https://img.shields.io/npm/l/npmpkgx?style=flat-square)
![npm](https://img.shields.io/npm/dm/npmpkgx?style=flat-square)


为你的项目自动添加依赖模块

使用其他语言阅读：[English](./README.md) | 简体中文

### 它能干什么?

---
在python中有pip+pipreqs打包依赖的方式, 在nodejs中有npm+npmpkgx   
如果你fork了他人项目, 发现缺失模块无法运行, 那么在线模式将为你补全    
如果你的项目需要移植到其它环境, 那么本地模式会适合你  

### 它是如何工作的?

---
它有两种工作模式  
1. 本地模式, 扫描代码中引入模块->匹配全局模块->添加到项目的package.json  
2. 在线模式, 扫描代码中引入模块->匹配registry模块->添加到项目的package.json

### 安装

---
从npm全局安装npmpkgx
```shell
$ npm install npmpkgx -g
```  


### 用法

---
```shell
$ npmpkgx -h  
npmpkgx - Automatically add project dependencies to npm's package.json

Usage:
    npmpkgx [options] [<path>]

Arguments:
    <path>                      The path to the directory containing the application files for the package.json file
                                 generated by npm

Options:
    -s, --save                  Add package to dependencies(default)
    -d, --save-dev              Add package to devDependencies
    -o, --save-optional         Add package to optionalDependencies
    -p, --save-prefix <prefix>  Customize the prefix(^|~|<|>|=) for package version
    --encoding <charset>        Use encoding parameter for package.json write. The default value of charset is utf-8
                                 if not specified
    --registry <url?>           Switch online mode, it will search the nodejs registry. The default value of url is
                                'https://registry.npmjs.org' if not specified

```


### 示例

---
```shell
$ npmpkgx ./ --registry
The following packages have been added to the dependencies
{ 'npm-pkgs': '^2.0.1' }
The following packages are not added to the dependencies
{
  fs: '*',
  path: '*',
  https: '*',
  './cmd/command': '*',
  'npm-pkgxxx': '*'
}

$ npm install
...

```

### 注意

---
建议在power shell之下使用npmpkgx, 其中的prefix标识在cmd下需要转义  
目前仅支持 `require()` 方式引入的模块, 为了可能支持import  
添加方式为追加, 已有包不会被添加, nodejs原生模块不会被添加, 自定义模块不会被添加  
命令行参数不支持`=`

### 版权

---
MIT © [bitjerry](https://github.com/bitjerry/npmpkgx/blob/main/LICENSE)




