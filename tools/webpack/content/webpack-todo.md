# 如何查找webpack版本
> 答：package.json中"devDependencies": {"webpack": "^3.11.0",}
## 通过配置文件来使用Webpack
> 定义一个配置文件，这个配置文件其实也是一个简单的JavaScript模块，我们可以把所有的与打包相关的信息放在里面
>[入门 Webpack，看这篇就够了](https://segmentfault.com/a/1190000006178770)
## 技术胖Webpack
- [技术胖Webpack](http://jspang.com/post/webpack3x.html)
- npm init
- npm uninstall webpack -g
- npm install webpack@3.5.2 -g
- import _css from './css/index.css'; 
>css is declared but its value is never read
- Can't resolve 'css-loader'
    npm install --save-dev style-loader并npm install --save-dev css-loader使其为我工作。看起来这些模块不再是标准捆绑的一部分。
- webpack-dev-server如果是3.x的话，webpack必须是4.x才不会报此TypeError: Cannot read property 'compile' of undefined错误, 同理如果webpack是3.x，则webpack-dev-server必须是2.x 
- 
    1.先安装全局webpack:npm install webpack
    2.再安装项目中webpack:npm install webpack -D
    相当于 npm install webpack --save-dev
    3.再安装 webpack-dev-serve npm install webpack
    4.上述安装的都是最新的版本
    如果找对应的版本。则在下载名后面加@ webpack@3
    webpack-dev-server@2

- 开发环境，什么是生产环境
1. 开发环境中是基本不会对js进行压缩的，在开发预览时我们需要明确的报错行数和错误信息，所以完全没有必要压缩JavasScript代码。而生产环境中才会压缩JS代码，用于加快程序的工作效率。devServer用于开发环境而压缩JS用于生产环境，在开发环境中作生产环境的事情所以Webpack设置了冲突报错
- file-loader url-loader
1. file-loader：解决引用路径的问题，拿background样式用url引入背景图来说，我们都知道，webpack最终会将各个模块打包成一个文件，因此我们样式中的url路径是相对入口html页面的，而不是相对于原始css文件所在的路径的。这就会导致图片引入失败。这个问题是用file-loader解决的，file-loader可以解析项目中的url引入（不仅限于css），根据我们的配置，将图片拷贝到相应的路径，再根据我们的配置，修改打包后文件引用路径，使之指向正确的文件。

2. url-loader：如果图片较多，会发很多http请求，会降低页面性能。这个问题可以通过url-loader解决。url-loader会将引入的图片编码，生成dataURl。相当于把图片数据翻译成一串字符。再把这串字符打包到文件中，最终只需要引入这个文件就能访问图片了。当然，如果图片较大，编码会消耗性能。因此url-loader提供了一个limit参数，小于limit字节的文件会被转为DataURl，大于limit的还会使用file-loader进行copy。

- [html-webpack-plugin](https://www.jianshu.com/p/2c849a445a91)
- [html-webpack-plugin详解](https://www.cnblogs.com/wonyun/p/6030090.html)
-[webpack-dev-server使用方法，看完还不会的来找我~](https://segmentfault.com/a/1190000006670084)
    
- 如何查看打包成功？
1. 跑跑静态文件就知道了
2. npm 安装一个全局模块 live-server
3. 然后进入 dist 目录 执行 live-server
4. npm run server 这个跑的是打包前的代码