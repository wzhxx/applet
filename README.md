# 主包
## 样式
.wxss、.wxml文件中统一使用全局变量；.js文件中设计主题色值的统一使用公共公共工具类库（utils）中的配置。*除了这两个地方,其他地方不能出现对应的相同变量值。更新变量的值两个文件（/static/style/style.wxss、/utils/style.js）要同步更新*   
style 
新版ui的公共样式库
- 变量（常用字号、色值、内外边距等）  

  统一用小驼峰命名 *例：themeColor*  
  单位：rpx *例：28rpx*  
  色值：HEXA格式（字母大写），不得使用RGB格式 *例：#264AFFFF*  
- 类（常用样式类）  

  统一下划线命名 *例: class="page_content"*
- 图标库(iconfont.wxss)  

  文字不得出现在图标上，文字必须写在代码里，有的话要叫ui整改
  iconfont文件夹（需到[阿里巴巴矢量图标库](https://www.iconfont.cn/home/index?spm=a313x.7781069.1998910419.2)后台下载）;小程序.wxss引用需Base64 encode，[转换地址](https://transfonter.org/)  
  因为不能影响之前的图标库，所以新版图标库的font-family属性为new-iconfont

```html
<i class="new-iconfont icon-apply"></i>
```

```css
page {
    <!--颜色-->
    --themeColor: #264AFF;
    <!--字体-->
    --fontSize: 28rpx;
    --lineHeight: 40rpx;
    <!--边距-->
    --margin: 32rpx;
    --margin8: 8rpx;
}

.demo{
    font-size: var(--fontSize);
    color: var(--themeColor);
    padding: var(--margin);
    margin: var(--margin8);
}
```
样式变量统一style.wxss文件管理,style.wxss文件只能定义变量，不得写其他样式代码;公共class的样式统一写在common.wxss。app.wxss中引入
```css
<!--app.wxss-->
@import "/static/style/style.wxss";
@import "/static/style/common.wxss";
```

## 图标
### 方形：  

1、单色图标使用iconfont图标库（*单色*），图标颜色统一通过类名设置；开发过程中一定要设置字体图标的颜色，颜色只能在公共样式表/static/style/style.wxss中取，没有高保真对应的色值需反映   
2、多色图标使用iconfont图标库（*多色，需上传到服务器*），下载规格以三倍图为准（以免真机上失真）     
*蓝湖需切至IOS才能下载三倍图* 

### 其他形状：
在高保真图上切图（*需上传到服务器*） 切图规格以三倍图为准（以免真机上失真）  
*蓝湖需切至IOS才能下载三倍图* 

新版ui切图服务器访问地址
``` js
const newImgUrl = "https://ftp.u-zf.com/ftp40pb/new_wximg/" // 生产图标地址(新版ui)
```

## 模板
一切无事件操作的组件均按模板（而不是组件）开发  

  templates新版ui公共模板
  - template.wxml 模板内容
  - template.wxss 模板样式
  app.wxss中引入模板样式template.wxss
  ```css
  <!--app.wxss-->
  @import "/static/template/template.wxss";
  ```
  模板（template）[官方教程](https://developers.weixin.qq.com/miniprogram/dev/reference/wxml/template.html)


## 导航栏
所有页面一律要用自定义的导航栏组件<mp-navigation-bar>（<navigation-bar>） 不得使用官方的默认导航栏样式
```json
<!--page.json-->
{
  "usingComponents": {},
  "navigationStyle": "custom"
}
```
```html
<!-- page.wxml -->
 <!-- 不推荐
  <navigation-bar></navigation-bar>
 -->
 <!-- 或者（推荐） -->
 <mp-navigation-bar><mp-navigation-bar>
```

## 官方api
不能使用涉及到样式的官方api像wx.showModal应该开发公共组件

## 主包大小
开发过程有包大小的问题需反映平台，平台统一整改

## 扩展库
useExtendedLib
[weui](https://wechat-miniprogram.github.io/weui/docs/)