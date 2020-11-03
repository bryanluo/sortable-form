# table-sortable

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### use elementui

```
npm i element-ui -S
```

### use Sortable

```
npm install sortablejs --save
```

main.js

```
import Vue from 'vue'
import App from './App.vue'
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';

Vue.use(ElementUI);
Vue.config.productionTip = false

new Vue({
  render: h => h(App),
}).$mount('#app')

```

import Sortablejs:

```
import Sortable from 'sortablejs'
```



