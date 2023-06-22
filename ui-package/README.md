# 分包（ui-package）
目录结构  
- components 组件库
- lib 第三方组件库
- pages 页面

*暂时使用ui-package,后续逐步组件替换，代各模块都完成改版，进行分包整改，废除主包无用文件，用ui-package的文件将主包的文件逐一替换*
## components
新版组件库文件夹，引用方式，参考[跨分包自定义组件引用](https://developers.weixin.qq.com/miniprogram/dev/framework/subpackages/async.html)
示例代码
```json
// xxx-package/pages/index.json
{
  "usingComponents": {
    "demo-component": "../../ui-package/components/demo-component",
    "demo": "../components/demo"
  },
  "componentPlaceholder": {
    "demo-component": "demo"
  }
}
```
componentPlaceholder为[占位组件](https://developers.weixin.qq.com/miniprogram/dev/framework/custom-component/placeholder.html)，即当组件引用失败时的替代组件

组件设计开发过程中，不得加入组件功能无关的业务逻辑，设计时必要性地增加组件的[插槽位、外部样式类](https://developers.weixin.qq.com/miniprogram/dev/framework/custom-component/wxml-wxss.html)，提高可扩展性；组件的属性必须有注释说明，方便对接。

## libs
新版第三方组件库，基于[vant weapp](https://vant-contrib.gitee.io/vant-weapp/#/home)组件库按需引入（基于版本一定，只能引入指定版本的组件库组件,防止版本差异带来的编译问题）
vant weapp项目地址
## pages
新版ui需平台提供的相关页面