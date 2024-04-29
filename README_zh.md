# decimal.js

decimal.js是JavaScript的一个高精度数学库，它具有以下特性

- 可以进行128位的高精度计算和表示数据

- 简单但功能齐全的API

- 复用了许多JavaScript的 `Number.prototype` 和 `Math` 对象的方法

- 可以转换为二进制、八进制和十六进制值

- 比Java的BigDecimal的JavaScript版本更快、更小，也更容易使用

- 广泛的平台兼容性：仅使用JavaScript 1.5（ECMAScript 3）特性

- 添加了三角函数，非整数幂等数学计算方法

  

OpenHarmony上引入decimal.js主要用于高精度数学库计算。

## 主要目录结构

```
doc/             #文档
test/            #测试代码
decimal.mjs      #decimal源码
LICENSE          #版权补充说明
README.md        #软件说明
```

## OpenHarmony如何集成decimal.js

decimal.js被引入在OpenHarmony的third_party目录下，使用OpenHarmony中依赖部件的方式进行编译。

1. 主干代码下载

   ```
   repo init -u https://gitee.com/openharmony/manifest.git -b master --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

2. 在需要使用该库的模块中添加依赖

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

   编译生成的文件对应路径：`out/rk3568/thirdparty/decimal.js/libdecimal.z.so`。

5. 运行

   ```ts
   // Decimal功能需要在ArkTs中使用
   // Index.ets
   import { Decimal } from '@kit.ArkTS';
   @Entry
   @Component
   struct Index {
     build() {
       Row() {
         Column() {
           Text("Test")
             .fontSize(50)
             .fontWeight(FontWeight.Bold)
             .onClick(() => {
             	let a0 : Decimal = Decimal.abs(-0.5);
               console.log("test Decimal abs:"+a0.toString()); // '0.5'
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   
   ```

   

## decimal.js官方文档

API官方文档 [https://mikemcl.github.io/decimal.js/](https://mikemcl.github.io/decimal.js/)



## 许可证

本项目遵从[LICENSE](https://gitee.com/openharmony-sig/third_party_decimal.js/blob/master/LICENCE.md)中所描述的许可证。