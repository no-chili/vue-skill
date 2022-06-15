#### auto-import

安装插件

```
pnpm add unplugin-auto-import -D
```

vite.config.js中配置插件

```
import AutoImport from 'unplugin-auto-import/vite'

export default defineConfig({
  plugins: [
    AutoImport({
      // 在哪些文件下有效
      include: [
        /\.[tj]sx?$/, 
        /\.vue$/, 
        /\.vue\?vue/, 
        /\.md$/,
      ],

      // 自动导入内容
      imports: [
        // 插件预设支持导入的api
        'vue',
        'vue-router',
        'pinia'
        // 自定义导入的api
      ],
		//生成eslint配置文件
      eslintrc: {
        enabled: false, // 第一次设为true，生成|更新配置文件
        filepath: './.eslintrc-auto-import.json', // 配置文件生成路径
        globalsPropValue: true, //
      },

      // 生成导入文件
      dts: './auto-imports.d.ts',
    })
  ],
})
```

修改tsconfig.json

```
// 解决使用api时ts提示未定义
{
    "include": [
        "./auto-imports.d.ts"
      ]
}
```

