## 在vue项目中使用Mockjs

```
import { Random, mock } from "mockjs";

//一个mock的格式
mock(path，type，template)

```

### 例子

```
mock('/\api\/chili/',get,()=>{
	return{
		title:Random.Random.ctitle()
	}
})
```

### 使用

```
//main.js
import 'mock.js'
```

正式上线，注释掉即可