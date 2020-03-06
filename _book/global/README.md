# 国际化

1. 本项目需要做国际化处理，由locales下的zh-CN.js统一管理，位于src下的locales的zh-Cn目录下，由zh-CN.js统一导入。
2. zh-CN下推荐命名：模块_模块_模块.js，用下划线“_”隔开，里面的内容则为导出对象，具体参考目录文件



```javascript
export default {
    'userList.searchOptions.nickName': '昵称',
    'userList.searchOptions.nickName.placeholder': '请输入昵称',
}
```









