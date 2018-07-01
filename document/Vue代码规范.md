#Vue.js代码规范（Vue前端）
本文档参考[Vue.js风格指南](http://https://cn.vuejs.org/v2/style-guide)
以下内容基本是基于Vue.js的组件来规范的。
##1.组件名为多个单词
组件名应该始终是多个单词的，根组件 App 除外。
这样做可以避免跟现有的以及未来的 HTML 元素相冲突，因为所有的 HTML 元素名称都是单个单词的。
例如，
```
Vue.component('todo-item', {
  // ...
})
```
```
export default {
  name: 'TodoItem',
  // ...
}
```
而且，进一步的好处是利于代码阅读者对组件作用的理解。
##2.组件数据data 必须是一个函数
eg,
```
Vue.component('some-comp', {
  data: function () {
    return {
      foo: 'bar'
    }
  }
})
```
##3.组件Prop 定义应该尽量详细
理由：
1.它们写明了组件的 API，所以很容易看懂组件的用法；
2.在开发环境下，如果向一个组件提供格式不正确的 prop，Vue 将会告警，以帮助你捕获潜在的错误来源。
eg,
```
// 相对来说很好的做法！
props: {
  status: {
    type: String,
    required: true,
    validator: function (value) {
      return [
        'syncing',
        'synced',
        'version-conflict',
        'error'
      ].indexOf(value) !== -1
    }
  }
}
```

##4.总是用为 v-for 设置键值
在组件上总是必须用 key 配合 v-for，以便维护内部组件及其子树的状态。甚至在元素上维护可预测的行为。

eg,
```
<ul>
  <li
    v-for="todo in todos"
    :key="todo.id"
  >
    {{ todo.text }}
  </li>
</ul>
```

##5.应当避免 v-if 和 v-for 用在一起
为了过滤一个列表中的项目 (比如 v-for="user in users" v-if="user.isActive")。在这种情形下，请将 users 替换为一个计算属性 (比如 activeUsers)，让其返回过滤后的列表。
1.为了过滤一个列表中的项目 (比如 v-for="user in users" v-if="user.isActive")。在这种情形下，请将 users 替换为一个计算属性 (比如 activeUsers)，让其返回过滤后的列表。
2.为了避免渲染本应该被隐藏的列表 (比如 v-for="user in users" v-if="shouldShowUsers")。这种情形下，请将 v-if 移动至容器元素上 (比如 ul, ol)
eg,
```
<ul>
  <li
    v-for="user in activeUsers"
    :key="user.id"
  >
    {{ user.name }}
  </li>
</ul>
```
```
<ul v-if="shouldShowUsers">
  <li
    v-for="user in users"
    :key="user.id"
  >
    {{ user.name }}
  </li>
</ul>
```

##6.为组件样式设置作用域
对于应用来说，顶级 App 组件和布局组件中的样式可以是全局的，但是其它所有组件都应该是有作用域的。
一般此规则适用于单文件组件。
对于组件库，我们应该更倾向于选用基于 class 的策略而不是 scoped 特性。使用了常人可理解的 class 名称且没有太高的选择器优先级，而且不太会导致冲突。
在单文件组件中我们可以这样设置样式：
```
<template>
  <button :class="[$style.button, $style.buttonClose]">X</button>
</template>

<!-- 使用 CSS Modules -->
<style module>
.button {
  border: none;
  border-radius: 2px;
}

.buttonClose {
  background-color: red;
}
</style>
```
##7.私有属性名（因项目较小，所以在E-Order项目中为可选）
在插件、混入等扩展中始终为自定义的私有属性使用 $_前缀。并附带一个命名空间以回避和其它作者的冲突 (比如 $_yourPluginName_)。
建议写法：
```
var myGreatMixin = {
  // ...
  methods: {
    $_myGreatMixin_update: function () {
      // ...
    }
  }
}
```
##8.组件文件
只要有能够拼接文件的构建系统，就把每个组件单独分成文件。
##单文件组件文件的大小写
单文件组件的文件名应该要么始终是单词大写开头 (PascalCase)，要么始终是横线连接 (kebab-case)。

单词大写开头对于代码编辑器的自动补全最为友好，因为这使得我们在 JS(X) 和模板中引用组件的方式尽可能的一致。然而，混用文件命名方式有的时候会导致大小写不敏感的文件系统的问题，这也是横线连接命名同样完全可取的原因。
##9.紧密耦合的组件名
和父组件紧密耦合的子组件应该以父组件名作为前缀命名。

如果一个组件只在某个父组件的场景下有意义，这层关系应该体现在其名字上。因为编辑器通常会按字母顺序组织文件，所以这样做可以把相关联的文件排在一起。
##10.模板中的组件名大小写
对于绝大多数项目来说，在单文件组件和字符串模板中组件名应该总是PascalCase的。
##11.完整单词的组件名
组件名应该倾向于完整单词而不是缩写。
eg,
```
components/
|- StudentDashboardSettings.vue
|- UserProfileOptions.vue
```
##12.模板中简单的表达式
组件模板应该只包含简单的表达式，复杂的表达式则应该重构为计算属性或方法。

复杂表达式会让你的模板变得不那么声明式。我们应该尽量描述应该出现的是什么，而非如何计算那个值。而且计算属性和方法使得代码可以重用。
```
<!-- 在模板中 -->
{{ normalizedFullName }}
```
```
// 复杂表达式已经移入一个计算属性
computed: {
  normalizedFullName: function () {
    return this.fullName.split(' ').map(function (word) {
      return word[0].toUpperCase() + word.slice(1)
    }).join(' ')
  }
}
```
##13.指令缩写
指令缩写 (用 : 表示 v-bind: 和用 @ 表示 v-on:) 应该要么都用要么都不用。
应该保持一致性。