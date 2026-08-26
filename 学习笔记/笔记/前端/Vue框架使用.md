---
tags:
  - Vue
  - 前端
  - 框架
updated: 2026-07-18
---

# Vue 框架学习笔记

> **Vue**（发音 /vjuː/，类似 **view**）是一款用于构建用户界面的渐进式 JavaScript 框架。
> 目前主流版本是 **Vue 3**（使用 Composition API + `<script setup>` 语法），本笔记全部基于 Vue 3。

---

## 📋 学习路线图

```
JavaScript 基础（已有 ✅）
    ↓
Vue 核心概念（模板语法、响应式、组件）
    ↓
Vue 进阶（生命周期、路由、状态管理）
    ↓
项目实战
```

---

## 1. Vue 简介

### 1.1 为什么用 Vue？

|     | 特性       | 说明                                         |
| :-- | :------- | :----------------------------------------- |
|     | **渐进式**  | 可以逐步引入，从一个页面到整个项目                          |
|     | **响应式**  | 数据变化自动更新视图，不用手动操作 DOM                      |
|     | **组件化**  | 页面拆分成独立可复用的组件                              |
|     | **生态丰富** | 官方路由 (Vue Router)、状态管理 (Pinia)、构建工具 (Vite) |

### 1.2 与其他框架对比

|     | 框架          | 适用场景     | 特点            |
| :-- | :---------- | :------- | :------------ |
|     | **Vue**     | 中小型到大型应用 | 上手简单，文档友好，渐进式 |
|     | **React**   | 大型应用     | 更灵活自由，生态更庞大   |
|     | **Angular** | 企业级应用    | 全家桶，学习曲线陡     |

> **对小白来说，Vue 是最友好的前端框架**，没有之一。

---

## 2. 环境准备

### 2.1 方式一：CDN 直接使用（快速体验）
![[vue使用步骤.png]]
```html
<!-- 直接在 HTML 中引入 Vue -->
<script src="https://unpkg.com/vue@3/dist/vue.global.prod.js"></script>

<div id="app">{{ message }}</div>

<script>
  const { createApp, ref } = Vue;

  createApp({
    setup() {
      const message = ref('Hello Vue!');
      return { message };
    }
  }).mount('#app');
</script>
```

### 2.2 方式二：Vite 创建项目（推荐，正式开发用）

```bash
# 确保已安装 Node.js（>= 18）
node -v   # 检查 Node 版本

# 创建 Vue 项目
npm create vue@latest

# 根据提示：
# ✔ Project name: my-vue-app
# ✔ TypeScript? 新手先选 No
# ✔ 其他功能都先选 No

# 进入项目目录
cd my-vue-app

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

### 2.3 项目文件结构

```
my-vue-app/
├── index.html          # 入口 HTML
├── src/
│   ├── main.js         # 应用入口：创建 Vue 应用
│   ├── App.vue         # 根组件
│   ├── components/     # 组件目录
│   └── assets/         # 静态资源
├── package.json        # 依赖配置
└── vite.config.js      # Vite 配置
```

---

## 3. 核心概念

### 3.1 创建 Vue 应用

```javascript
// src/main.js
import { createApp } from 'vue'
import App from './App.vue'

createApp(App).mount('#app')
```

### 3.2 .vue 文件结构（单文件组件 SFC）

```vue
<script setup>
// JavaScript 逻辑（Composition API）
import { ref } from 'vue'

const count = ref(0)

function increment() {
  count.value++
}
</script>

<template>
  <!-- HTML 模板 -->
  <button @click="increment">点击了 {{ count }} 次</button>
</template>

<style scoped>
/* CSS 样式，scoped 表示样式只作用于当前组件 */
button {
  padding: 8px 16px;
  cursor: pointer;
}
</style>
```

> **`<script setup>`** 是 Vue 3 推荐的写法，语法更简洁，不需要写 `export default`。

---

## 4. 模板语法

### 4.1 文本插值

```vue
<template>
  <p>{{ message }}</p>          <!-- 普通文本 -->
  <p>{{ number + 1 }}</p>       <!-- 表达式 -->
  <p>{{ ok ? 'YES' : 'NO' }}</p> <!-- 三元运算 -->
  <p>{{ message.split('').reverse().join('') }}</p> <!-- 方法调用 -->
</template>
```

### 4.2 指令 (Directives)

指令是带有 `v-` 前缀的特殊属性：

|     | 指令                              | 缩写  | 作用                   |
| :-- | :------------------------------ | :-- | :------------------- |
|     | `v-bind`                        | `:` | 动态绑定属性               |
|     | `v-on`                          | `@` | 绑定事件                 |
|     | `v-if` / `v-else-if` / `v-else` | -   | 条件渲染                 |
|     | `v-show`                        | -   | 条件显示（切换 CSS display） |
|     | `v-for`                         | -   | 列表渲染                 |
|     | `v-model`                       | -   | 双向数据绑定（表单）           |
|     | `v-html`                        | -   | 渲染 HTML（小心 XSS）      |
|     | `v-once`                        | -   | 只渲染一次                |

#### 动态绑定 (`v-bind` / `:`)

```vue
<template>
  <img :src="imageUrl" :alt="description">
  <button :disabled="isLoading">提交</button>

  <!-- 动态绑定多个属性 -->
  <div v-bind="attrsObject"></div>
  <!-- attrsObject = { id: 'myId', class: 'myClass' } -->
</template>
```

#### 事件绑定 (`v-on` / `@`)

```vue
<template>
  <button @click="handleClick">点击</button>
  <button @click="count++">直接写表达式</button>
  <input @keyup.enter="submit">   <!-- 按回车触发 -->
  <div @click.stop="doThis">点击不冒泡</div>  <!-- 阻止冒泡 -->
  <a @click.prevent="doThat">点击不跳转</a>   <!-- 阻止默认行为 -->
</template>

<script setup>
function handleClick(event) {
  console.log(event.target)  // 原生 DOM 事件对象
}

function submit() {
  console.log('回车提交')
}
</script>
```

**事件修饰符**：

|     | 修饰符                                | 作用                     |
| :-- | :--------------------------------- | :--------------------- |
|     | `.stop`                            | 阻止事件冒泡                 |
|     | `.prevent`                         | 阻止默认行为                 |
|     | `.once`                            | 只触发一次                  |
|     | `.enter` / `.esc` / `.space` / ... | 按键修饰符                  |
|     | `.self`                            | 只有 event.target 是自身才触发 |
|     | `.capture`                         | 捕获阶段触发                 |

---

## 5. 响应式基础

> Vue 3 使用 **Composition API** 来管理响应式数据。

### 5.1 `ref` — 单个值

```vue
<script setup>
import { ref } from 'vue'

// 定义响应式数据
const count = ref(0)
const name = ref('小明')
const isActive = ref(true)

// 在 JS 中需要通过 .value 访问/修改
function increment() {
  count.value++
  console.log(count.value)
}

// 在模板中自动解包，不需要 .value
</script>

<template>
  <p>{{ count }}</p>
  <p>{{ name }} - {{ isActive ? '在线' : '离线' }}</p>
  <button @click="increment">+1</button>
</template>
```

### 5.2 `reactive` — 对象

```vue
<script setup>
import { reactive } from 'vue'

// 定义响应式对象
const user = reactive({
  name: '小红',
  age: 25,
  hobbies: ['读书', '跑步']
})

function addAge() {
  user.age++
}

function addHobby(hobby) {
  user.hobbies.push(hobby)
}
</script>

<template>
  <p>{{ user.name }} - {{ user.age }}岁</p>
  <ul>
    <li v-for="hobby in user.hobbies" :key="hobby">{{ hobby }}</li>
  </ul>
  <button @click="addAge">长大一岁</button>
</template>
```

### 5.3 `ref` vs `reactive`

|     | 特性     | `ref`                | `reactive`     |
| :-- | :----- | :------------------- | :------------- |
|     | 支持类型   | 任意类型（基本类型+对象）        | 仅对象/数组/Map/Set |
|     | JS 中访问 | 需 `.value`           | 直接访问           |
|     | 模板中访问  | 自动解包                 | 直接访问           |
|     | 重新赋值   | 直接 `.value = newVal` | 不能直接替换，需修改属性   |
|     | 推荐场景   | **绝大多数情况**           | 深层嵌套对象         |

> **推荐**：默认用 `ref`，遇到深层嵌套对象用 `reactive`。

---

## 6. 计算属性与侦听器

### 6.1 `computed` — 计算属性

```vue
<script setup>
import { ref, computed } from 'vue'

const todos = ref([
  { text: '学习 Vue', done: false },
  { text: '做项目', done: true },
  { text: '写笔记', done: false }
])

// 计算属性——根据已有数据派生新数据
const activeTodos = computed(() => {
  return todos.value.filter(t => !t.done)
})

const doneCount = computed(() => {
  return todos.value.filter(t => t.done).length
})
</script>

<template>
  <p>已完成: {{ doneCount }} / {{ todos.length }}</p>
  <ul>
    <li v-for="todo in activeTodos" :key="todo.text">
      {{ todo.text }}
    </li>
  </ul>
</template>
```

> **`computed` vs `methods`**：`computed` 有缓存，只有依赖变化时才重新计算；方法每次渲染都会调用。

### 6.2 `watch` — 侦听器

```vue
<script setup>
import { ref, watch } from 'vue'

const searchQuery = ref('')
const results = ref([])

// 监听单个数据源
watch(searchQuery, (newVal, oldVal) => {
  console.log(`搜索词从 "${oldVal}" 变为 "${newVal}"`)
  // 可以在这里发起 API 搜索
  fetchResults(newVal)
})

// 监听多个数据源
const page = ref(1)
watch([searchQuery, page], ([newQuery, newPage], [oldQuery, oldPage]) => {
  console.log('搜索条件变了', newQuery, newPage)
})

// 立即执行一次（默认是懒执行的）
watch(searchQuery, (newVal) => {
  fetchResults(newVal)
}, { immediate: true })
</script>

<template>
  <input v-model="searchQuery" placeholder="搜索..." />
</template>
```

|     | 选项                | 作用                           |
| :-- | :---------------- | :--------------------------- |
|     | `immediate: true` | 创建时立即执行一次回调                  |
|     | `deep: true`      | 深度监听对象内部变化（reactive 默认 deep） |
|     | `once: true`      | 只监听一次                        |

---

## 7. 条件渲染与列表渲染

### 7.1 条件渲染

```vue
<template>
  <!-- v-if 系列：条件渲染（真正的创建/销毁） -->
  <div v-if="status === 'loading'">加载中...</div>
  <div v-else-if="status === 'error'">出错了</div>
  <div v-else>加载完成！</div>

  <!-- v-show：只是切换 display（适合频繁切换） -->
  <div v-show="isVisible">这个只是隐藏/显示</div>

  <!-- v-if vs v-show -->
  <!-- v-if：惰性——条件为假时不渲染，切换时有创建/销毁开销 -->
  <!-- v-show：总是渲染，仅切换 CSS display -->
</template>
```

### 7.2 列表渲染

```vue
<script setup>
import { ref } from 'vue'

const items = ref([
  { id: 1, name: '苹果' },
  { id: 2, name: '香蕉' },
  { id: 3, name: '橘子' }
])

function removeItem(id) {
  items.value = items.value.filter(item => item.id !== id)
}

function addItem() {
  const newId = items.value.length + 1
  items.value.push({ id: newId, name: `水果 ${newId}` })
}
</script>

<template>
  <ul>
    <li v-for="(item, index) in items" :key="item.id">
      {{ index + 1 }}. {{ item.name }}
      <button @click="removeItem(item.id)">删除</button>
    </li>
  </ul>
  <button @click="addItem">添加</button>
</template>
```

> **`:key` 很重要！** Vue 用 key 来跟踪每个节点的身份，实现高效的列表更新。**永远不要用 `index` 当 key**（除非列表是静态的不会增删）。

---

## 8. 表单绑定 `v-model`

### 8.1 各种表单控件

```vue
<script setup>
import { ref } from 'vue'

const form = ref({
  name: '',
  email: '',
  gender: '',        // radio
  hobbies: [],       // checkbox 多选
  agree: false,      // checkbox 单选
  city: '',          // select
  message: ''        // textarea
})

function submitForm() {
  console.log(form.value)
}
</script>

<template>
  <form @submit.prevent="submitForm">
    <!-- 文本输入 -->
    <input v-model="form.name" placeholder="姓名" />

    <!-- 邮箱 -->
    <input v-model="form.email" type="email" placeholder="邮箱" />

    <!-- 单选框 -->
    <input type="radio" v-model="form.gender" value="male" /> 男
    <input type="radio" v-model="form.gender" value="female" /> 女

    <!-- 多选框 -->
    <input type="checkbox" v-model="form.hobbies" value="reading" /> 读书
    <input type="checkbox" v-model="form.hobbies" value="sports" /> 运动

    <!-- 单个复选框（绑定 boolean） -->
    <input type="checkbox" v-model="form.agree" /> 同意条款

    <!-- 下拉选择 -->
    <select v-model="form.city">
      <option value="">请选择城市</option>
      <option value="beijing">北京</option>
      <option value="shanghai">上海</option>
    </select>

    <!-- 多行文本 -->
    <textarea v-model="form.message" placeholder="留言"></textarea>

    <button type="submit">提交</button>
  </form>
</template>
```

### 8.2 `v-model` 修饰符

|     | 修饰符       | 作用                    | 示例                     |
| :-- | :-------- | :-------------------- | :--------------------- |
|     | `.lazy`   | 在 change 事件后同步（失去焦点时） | `v-model.lazy="val"`   |
|     | `.number` | 自动转为数字类型              | `v-model.number="age"` |
|     | `.trim`   | 去除首尾空格                | `v-model.trim="name"`  |

---

## 9. 组件基础

> 组件是 Vue 的核心概念——将 UI 拆分成独立、可复用的块。

### 9.1 定义和使用组件

```vue
<!-- src/components/MyButton.vue -->
<script setup>
// 通过 defineProps 接收父组件传值
const props = defineProps({
  color: {
    type: String,
    default: 'blue'
  },
  size: {
    type: String,
    default: 'medium'
  }
})

// 通过 defineEmits 声明事件
const emit = defineEmits(['click'])

function handleClick() {
  emit('click', '按钮被点击了')
}
</script>

<template>
  <button
    :class="['btn', `btn-${color}`, `btn-${size}`]"
    @click="handleClick"
  >
    <!-- 插槽：父组件可以插入内容 -->
    <slot />
  </button>
</template>

<style scoped>
.btn { border: none; border-radius: 4px; cursor: pointer; padding: 8px 16px; }
.btn-blue { background: #42b883; color: white; }
.btn-red { background: #e74c3c; color: white; }
.btn-small { font-size: 12px; padding: 4px 8px; }
.btn-large { font-size: 18px; padding: 12px 24px; }
</style>
```

```vue
<!-- 使用组件 -->
<script setup>
import MyButton from './components/MyButton.vue'

function onButtonClick(msg) {
  alert(msg)
}
</script>

<template>
  <MyButton color="blue" size="large" @click="onButtonClick">
    点击我
  </MyButton>
</template>
```

### 9.2 Props 传递数据

|     | 方向        | 方式                              |
| :-- | :-------- | :------------------------------ |
|     | **父 → 子** | 父组件通过属性传递，子组件用 `defineProps` 接收 |
|     | **子 → 父** | 子组件用 `defineEmits` 触发事件，父组件监听   |
|     | **兄弟之间**  | 通过共同的父组件传递，或使用状态管理 Pinia        |

### 9.3 插槽 (Slots)

```vue
<!-- 基础插槽 -->
<script setup>
// BaseCard.vue
</script>

<template>
  <div class="card">
    <slot />
  </div>
</template>

<!-- 具名插槽 -->
<script setup>
// PageLayout.vue
</script>

<template>
  <header><slot name="header" /></header>
  <main><slot /></main>
  <footer><slot name="footer" /></footer>
</template>

<!-- 使用具名插槽 -->
<template>
  <PageLayout>
    <template #header>页面标题</template>
    <p>主体内容</p>
    <template #footer>版权信息</template>
  </PageLayout>
</template>
```

### 9.4 组件间通信总结

|     | 方式                   | 场景               |
| :-- | :------------------- | :--------------- |
|     | `props` / `emits`    | 父子组件通信           |
|     | `v-model`            | 父子组件双向绑定         |
|     | `defineExpose`       | 父组件调用子组件的方法/属性   |
|     | `provide` / `inject` | 祖先 → 后代（跨多层）     |
|     | Pinia                | 任意组件通信（推荐作为全局状态） |

---

## 10. 组件进阶

### 10.1 生命周期

Vue 组件从创建到销毁的过程：

```
创建 → 挂载 → 更新 → 卸载
```

```vue
<script setup>
import { onMounted, onUnmounted, onUpdated } from 'vue'

// 组件挂载到 DOM 后（最常用——发请求、操作 DOM）
onMounted(() => {
  console.log('组件已挂载')
})

// 组件更新后
onUpdated(() => {
  console.log('组件已更新')
})

// 组件卸载前（清理工作——清除定时器、取消订阅）
onUnmounted(() => {
  console.log('组件已卸载')
})
</script>
```

|     | 生命周期钩子        | 触发时机        | 常用场景             |
| :-- | :------------ | :---------- | :--------------- |
|     | `onMounted`   | 组件挂载到 DOM 后 | 发 HTTP 请求、操作 DOM |
|     | `onUpdated`   | 组件更新后       | 依赖更新后 DOM 的操作    |
|     | `onUnmounted` | 组件卸载前       | 清理定时器、取消事件监听     |

### 10.2 `provide` / `inject`（跨层级传值）

```vue
<!-- 祖先组件 -->
<script setup>
import { ref, provide } from 'vue'

const theme = ref('dark')
// 提供给所有后代组件
provide('theme', theme)

function toggleTheme() {
  theme.value = theme.value === 'dark' ? 'light' : 'dark'
}
</script>

<template>
  <button @click="toggleTheme">切换主题</button>
  <DeepChild />
</template>
```

```vue
<!-- 任意后代组件 -->
<script setup>
import { inject } from 'vue'

// 注入祖先提供的数据
const theme = inject('theme')
</script>

<template>
  <p>当前主题: {{ theme }}</p>
</template>
```

---

## 11. Vue Router（路由）

> Vue Router 是 Vue 官方的路由管理器，实现单页应用（SPA）的页面切换。

### 11.1 安装与配置

```bash
npm install vue-router@4
```

```javascript
// src/router/index.js
import { createRouter, createWebHistory } from 'vue-router'
import Home from '../views/Home.vue'
import About from '../views/About.vue'

const routes = [
  { path: '/', name: 'home', component: Home },
  { path: '/about', name: 'about', component: About },
  { path: '/users/:id', name: 'user', component: () => import('../views/User.vue') }
  // 动态导入 → 懒加载
]

const router = createRouter({
  history: createWebHistory(),  // HTML5 历史模式（URL 不带 #）
  routes
})

export default router
```

```javascript
// src/main.js
import { createApp } from 'vue'
import App from './App.vue'
import router from './router'

const app = createApp(App)
app.use(router)  // 安装路由插件
app.mount('#app')
```

### 11.2 路由视图与导航

```vue
<!-- App.vue -->
<template>
  <!-- 导航链接（会渲染为 <a> 标签，自动处理高亮） -->
  <nav>
    <router-link to="/">首页</router-link>
    <router-link to="/about">关于</router-link>
    <router-link :to="`/users/${userId}`">用户详情</router-link>
  </nav>

  <!-- 路由出口——当前路由对应的组件会渲染在这里 -->
  <router-view />
</template>

<script setup>
import { useRouter, useRoute } from 'vue-router'

const router = useRouter()  // 路由实例（用于编程式导航）
const route = useRoute()    // 当前路由信息

// 编程式导航
function goToAbout() {
  router.push('/about')
}

function goToUser(id) {
  router.push({ name: 'user', params: { id } })
}

// 获取路由参数
console.log(route.params.id)   // URL 中的 /users/123 → "123"
console.log(route.query)       // URL 中的 ?keyword=vue → { keyword: "vue" }
</script>
```

### 11.3 路由守卫

```vue
<script setup>
import { onBeforeRouteLeave } from 'vue-router'

// 离开当前页面前
onBeforeRouteLeave((to, from) => {
  const answer = window.confirm('有未保存的更改，确定离开吗？')
  if (!answer) return false  // 取消导航
})
</script>
```

---

## 12. Pinia（状态管理）

> Pinia 是 Vue 3 推荐的官方状态管理库，替代 Vuex。

### 12.1 安装与配置

```bash
npm install pinia
```

```javascript
// src/main.js
import { createApp } from 'vue'
import { createPinia } from 'pinia'
import App from './App.vue'

const app = createApp(App)
app.use(createPinia())
app.mount('#app')
```

### 12.2 定义 Store

```javascript
// src/stores/counter.js
import { ref, computed } from 'vue'
import { defineStore } from 'pinia'

// 定义 store
export const useCounterStore = defineStore('counter', () => {
  // state：响应式状态
  const count = ref(0)
  const name = ref('计数器')

  // getter：计算属性（派生状态）
  const doubleCount = computed(() => count.value * 2)

  // action：操作方法
  function increment() {
    count.value++
  }

  function reset() {
    count.value = 0
  }

  // 暴露给外部
  return { count, name, doubleCount, increment, reset }
})
```

### 12.3 在组件中使用

```vue
<script setup>
import { useCounterStore } from './stores/counter'

const counter = useCounterStore()

// 也可以解构（但要保持响应性需要用 storeToRefs）
// import { storeToRefs } from 'pinia'
// const { count, doubleCount } = storeToRefs(counter)
</script>

<template>
  <p>{{ counter.count }} × 2 = {{ counter.doubleCount }}</p>
  <button @click="counter.increment()">+1</button>
  <button @click="counter.reset()">重置</button>
</template>
```

---

## 13. 常用工具函数

### 13.1 `nextTick` — 等待 DOM 更新

```vue
<script setup>
import { ref, nextTick } from 'vue'

const count = ref(0)

async function increment() {
  count.value++
  console.log(document.querySelector('p')?.textContent)  // 可能是旧值

  // 等待 Vue 完成 DOM 更新
  await nextTick()
  console.log(document.querySelector('p')?.textContent)  // 新值
}
</script>
```

### 13.2 `watchEffect` — 自动追踪依赖

```vue
<script setup>
import { ref, watchEffect } from 'vue'

const userId = ref(1)
const userData = ref(null)

// 自动追踪内部用到的响应式数据
watchEffect(async () => {
  // 当 userId 变化时自动重新执行
  const res = await fetch(`https://api.example.com/users/${userId.value}`)
  userData.value = await res.json()
})
</script>
```

---

## 14. 开发工具

|     | 工具                  | 说明                          |
| :-- | :------------------ | :-------------------------- |
|     | **Vite**            | 构建工具，极快的热更新（HMR）            |
|     | **Vue DevTools**    | 浏览器插件，调试组件/状态/路由            |
|     | **VS Code + Volar** | 官方推荐的编辑器 + Vue 扩展（替代 Vetur） |
|     |                     |                             |

> 🛠️ **必装**：VS Code 装 **Vue - Official** 扩展（原名 Volar），获得完整的模板语法高亮和类型提示。

---

## 15. 常见问题与陷阱

|     | 问题                | 原因                      | 解决                           |
| :-- | :---------------- | :---------------------- | :--------------------------- |
|     | `ref` 忘记 `.value` | JS 中访问 ref 必须用 `.value` | 模板中不用 `.value`               |
|     | `v-for` 缺少 `:key` | Vue 无法高效更新列表            | 始终使用唯一 id 作为 key             |
|     | 直接修改数组/对象不更新      | 响应式丢失                   | 用 `push/map/spread` 等触发更新的方法 |
|     | 模板中调用函数过度         | 每次渲染都执行，性能差             | 用 `computed` 替代              |
|     | `reactive` 直接赋值   | 整个替换对象会丢失响应性            | 用 `ref` 或直接修改属性              |

---

## 课外扩展笔记

- [[JavaScript笔记]] — Vue 的前置知识
- [[前后端技术介绍]] — 前后端交互概念
- 进阶：Vue Router 深入、组件设计模式、性能优化、测试

---

## 📚 学习路径建议

```
第一阶段（第1-3天）
├── 看官方教程：https://cn.vuejs.org/tutorial/#step-1
├── 掌握模板语法、ref/reactive、v-if/v-for
└── 做一个 Todo List 小项目

第二阶段（第4-7天）
├── 组件化开发
├── 计算属性与侦听器
├── 生命周期
└── 模仿写一个简单的后台管理页面

第三阶段（第8-14天）
├── Vue Router 路由
├── Pinia 状态管理
├── 前后端联调（fetch API）
└── 完成一个小型完整项目（如博客/备忘录）

第四阶段（持续）
├── 组件设计模式
├── 性能优化
└── 学习 TypeScript + Vue
```
