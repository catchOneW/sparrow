
vue api

slot加任何东西没用的，只有内容有用
:class的{}代表单选，[]代表多选,class和:class会合并

VueComponent是一个单位件，是一个{}配置而已
vue.component返回一个函数fn里面引用了VueComponent
$children里全是配置好的组件配置VueComponent对象{}，$el.children里全是dom


原则
1props>slot,用户传的时候props更简洁,slot适合大众习惯如按钮中的文字
2class>v-if
3