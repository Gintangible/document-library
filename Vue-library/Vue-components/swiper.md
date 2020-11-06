## swiper组件

`swiper`组件在网上有很多封装好的，可以直接使用。这里使用`vue-awesome-swiper`。

[gitHub](https://github.com/surmon-china/vue-awesome-swiper)

### 1. 安装

`npm`安装

`npm i vue-awesome-swiper --save`

### 2. 引用

根据项目中的对`vue-awesome-swiper`的使用情况，如果使用不多，可以直接在相应组件内引用；反之，在全局中引用。

#### 2.1 全局引用

```
import Vue from 'vue';
import VueAwesomeSwiper from 'vue-awesome-swiper';

// require styles
import 'swiper/dist/css/swiper.css';

Vue.use(VueAwesomeSwiper);
```

#### 2.2 组件内使用

```
3、组件中使用 
import 'swiper/dist/css/swiper.css';

import { swiper, swiperSlide } from 'vue-awesome-swiper';

export default {
  components: {
    swiper,
    swiperSlide
  }
}
```

