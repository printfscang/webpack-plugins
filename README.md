# webpack-plugins
webpack4的常用插件
## sass-loader 依赖与node-sass
```
1. 因为sass-loader依赖以node-sass，因此要来一起安装，查看npm
2. style-loader和css-loader也是必须的依赖项
style-loader---将计算后的样式加入到页面中
css-loader---是的import css from ‘index.scss’或者require('./index.scss')在js文件中生效
引入外部样式
import './index.scss'
require('./index.scss')
在vue中使用
<style lang="scss">
</style>
3. 配置略...
```
## mini-css-extract-plugin 
`js，css分离`
## html-webpack-plugin
`提取html文件，并将js，css文件自动引入`
## uglifyjs-webpack-plugin
`压缩js代码`
## file-loader 以及url-loader
```
npm install file-loader css-loader --save-dev
1. 当我们同过webpack打包文件之后，如果文件中设置了img或background来引入图片等数据，那么打包后是不能正确访问到路径的
2. 这时我们去要url-loader来处理相关的路径引入问题
3. url-loader提供了一个limit参数，当图片大小超过限制后，url-loader会调用file-loader，同时也会将参数传给file-loader
4. 这里涉及到了4个属性
limit,name,outputPath,publicPath
limit---没超过设置值时将图片转为dataURL ，以base64的格式打包图片，减少请求的次数，当超过限制时，打包图片到相应的输出路径
name---输出的文件名规则，默认时文件哈希，一般书写格式如下：name:'[path]/[name].[ext]',表示打包后文件被放到了对应的path路径下，名字和原图片名字相同，后缀名与原图片后缀相同
outputPath---指定图片在输出文件夹的路径，比如outputPath:'img/',如果没有该文件则会自动创建，⚠️设置路径时，是相对与webpack的出口文件output的，设置错了则报路径错误
publicPath---指向自己的线上地址，或则cdn
 
```
