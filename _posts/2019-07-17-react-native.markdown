---
layout:     post
title:      "react-native and mobx"
subtitle:   "mobx"
date:       2019-07-17
author:     "鸿"
header-img: "img/home-bg.jpg"
tags:
    - 日记
---

### React-Native 集成 Mobx



#### 1. 安装Mobx

当前的React 和 React-Native版本是

> "react": "16.8.6",

> "react-native": "0.60.3"

不能安装最新的mobx 版本， 或者@inject 会出错

```powershell
yarn add mobx@5.9.4 --save
yarn add mobx-react@5.4.3 --save
```

#### 2. 安装babel 插件

```powershell
   yarn add nis @babel/plugin-proposal-decorators --save
```

#### 3. 修改babel.config.js

```json
module.exports = {
  presets: ['module:metro-react-native-babel-preset'],
  plugins: [
    [
      '@babel/plugin-proposal-decorators',
      {
        'legacy': true
      }
    ]
  ]
};
```




