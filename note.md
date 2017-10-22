> 这个Demo做下来，首先组件的结构要清楚。

根组件App  
展示进度条的Header组件  
展示作业任务的QuoteGrid组件，和它的子组件Quote  
展示添加的NewQuote组件

# Quote.vue组件

这个组件就是现实作业内容，没别的，就是提供了slot供它的父组件来填充。

# QuoteGrid.vue组件

它的目的就是遍历数组把多个Quote.vue组件渲染出来。数据源是通过props属性从根组件中赋值过来的。另外，还提供了一个点击Quote.vue组件删除某个人物的功能。这里面需要注意的是：当我们在父组件中为子组件添加事件的时候，我们应该类似这么写：` @click.native="deleteQuote(index)"`。

# Header.vue组件

它用来动态显示精度条的宽度。通过对`:style="dynamicWidth"`的设置，就可以动态显示宽度了。而`dynamicWidth`就是`props`的一个属性，最终由根组件来赋值。

# NewQuote.vue组件

发生动作的时候广播出去并带上参数，最后在根组件中侦听事件并调用回调函数处理数组等。

# App.vue根组件

- Header.vue组件的`dynamicWidth`由这里的computed的自定义计算属性提供。
- QuoteGrid.vue组件的数据源由这里提供，删除事件在这里侦听并调用回调函数处理数组
- 定义NewQuote.vue组件添加回调函数，除了对数组进行操作，还设置用来表示总记录数的变量
- 定义NewQuote.vue组件删除回调函数，出了对数组进行操作，还要判断当前数组的数量是否是零，如果是零表示作业完成，重新设置表示总记录数的变量，以及弹出对话框
- reset是各项变量回归到初始值

> 通过本Demo,熟悉了子组件通过slot, props来挖模型让父组件来填，子组件通过$emit方法把事件和参数广播出去让父组件来侦听，v-if, v-else用来展示或隐藏某部分内容，computed把计算后的属性交出来用。