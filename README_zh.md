# decimal.js

decimal.js是一种用于JavaScript上的高精度数学库。

OpenHarmony上引入decimal.js主要用于高精度数学库计算。

## 主要目录结构

```
doc              #文档
test             #测试代码
decimal.mjs      #decimal源码
API              #接口说明
LICENSE          #版权补充说明
README.md        #软件说明
```

## OpenHarmony对于decimal.js的适配

decimal.js引入openharmony的thirdparty目录下，
使用OpenHarmony中依赖部件的方式进行编译。
1. 主干代码下载
   ```
   repo init -u https://gitee.com/openharmony/manifest.git -b master --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
2. 在使用的模块进行依赖
   ```
   deps = [ "//third_party/decimal.js:decimal" ]
   ```
3. 预处理
   ```
   ./build/prebuilts_download.sh
   ```
4. 编译
   ```
   ./build.sh --product-name rk3568 --ccache
   ```
编译生成物对应路径：`out/rk3568/thirdparty/decimal.js/libdecimal.z.so`。

## 许可证

本项目遵从[LICENSE](https://gitee.com/openharmony-sig/third_party_decimal.js/blob/master/LICENSE)中所描述的许可证。

## 相关仓
[decimal.js](https://gitee.com/openharmony-sig/third_party_decimal.js)
