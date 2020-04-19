title: React使用styled-components出现'injectGlobal' was not found in 'styled-components'错误
date: 2020-04-19 21:20:00
tags:

 - React
 - styled-components

---

# 'injectGlobal' was not found in 'styled-components'

​	想在react中用reset.css的时候借助了`styled-components`，为全局添加reset.css的时候，报了这个错误。

```javascript
import { injectGlobal } from 'styled-components';

injectGlobal`
	reset.css
`;
```

# 解决

​	查了下，`styled-components`更新了新的使用方法，如下：

```javascript
import { creatGlobalStyle } from 'styled-components';

export const GlobalStyle = creatGlobalStyle`
	reset.css;
`;
```

​	在入口文件引入：

```javascript
...
import { GlobalStyle } from './style';

...
  render() {
    return (
      <GlobalStyle />
    );
  }
```

# 自动补全

​	在使用了`styled-components`后，会发现在其中写css代码不会自动补全了，这里只要给IDE装一个插件就好了，我用的是vsc，直接搜索：

![插件](http://img.ruyuelee.com/styled-components.png)

​	这样就可以自动补全啦。