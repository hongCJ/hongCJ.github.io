---
layout:     post
title:      "添加 less到react"
subtitle:   "less"
date:       2019-07-18
author:     "鸿"
header-img: "img/home-bg.jpg"
tags:
    - 日记
---



### 添加less支持到react

### 1、配置less文件

```javascript
const lessRegex = /\.less$/;
const lessModuleRegex = /\.module\.less$/;
```

### 2、配置webpack config

```javascript
// Less 解析配置
{
    test: lessRegex,
    exclude: lessModuleRegex,
    use: getStyleLoaders(
        {
            importLoaders: 2,
            sourceMap: isEnvProduction && shouldUseSourceMap,
        },
        'less-loader'
    ),
    sideEffects: true,
},
{
    test: lessModuleRegex,
    use: getStyleLoaders(
        {
            importLoaders: 2,
            sourceMap: isEnvProduction && shouldUseSourceMap,
            modules: true,
            getLocalIdent: getCSSModuleLocalIdent,
        },
        'less-loader'
    )
},
```

### 3、安装less

```powershell
npm install less less-loader --save
```




