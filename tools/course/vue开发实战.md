### 如何制作npm组件上传到npm
[npm常用命令、发布自己的npm、更新和删除npm包](https://www.jianshu.com/p/eabdc2871bd9)
- npmjs.com登陆注册验证邮箱

- 新建一个文件夹，初始化项目npm init,设置包的参数，

- 新建一个index.js（默认main.js） index.js里面导出一个函数 运行 npm install -g (查看代码有没有报错)

- npm link 可以对项目进行调试生成packjson-lock.json

- npm login 

- npm publish npm包发布成功

- 项目中引用 webpack npm 包
- npm i 项目名 --save-dev
- npm如何更新和上传包

```
npm version patch : 更新项目版本
npm publish: 此时项目更新上线版本（1.0.1-》1.0.2）
```
- 从npm删除对应的版本项目 ： npm unpublish 项目名@1.0.2