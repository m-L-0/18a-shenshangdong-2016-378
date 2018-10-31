### 作业总结

#### 1.总结name_scope与variable_scope的作用以及异同点

##### 使用name_scope与variable_scope的优点

使用`name_scope`与`variable_scope`可以较好的解决图中的节点命名时所出现的问题。比如可以解决功能近似的节点`name`也极其相似难以区分的问题，而且使用name_scope后如果可视化图可以较为整洁的将全部节点展示出来。`name_scope`可以通过划分操作范围来组织图结构，并能服务于得可视化。

##### name_scope的作用

`name_scope`可以为其作用域中的节点的`name`添加一个或多个前缀，并使用这些前缀作为划分内部与外部`op`范围的标记。同时在TensorBoard可视化时可以作为一个整体出现（也可以展开）。并且`name_scope`可以嵌套使用，代表不同层级的功能区域的划分。

##### name_scope的创建

`name_scope`使用`tf.name_scope()`创建，返回一个上下文管理器。`name_scope`的参数`name`可以是字母、数字、下划线，不能以下划线开头。类似于`Op`的`name`的命名方式。

##### name_scope使用的注意事项

使用`name_scope`可以给operation的name加前缀，但不包括tf.get_variable()创建的变量。

这是因为`tf.get_variable`是一种特殊的操作，其只能与`variable_scope`配合完成相应功能。

##### variable_scope的作用

`variable_scope`主要用于管理变量作用域以及与变量相关的操作，同时`variable_scope`也可以像`name_scope`一样用来给不同操作区域划分范围（添加`name`前缀）。`variable_scope`功能也要更丰富，最重要的是可以与`tf.get_variable()`等配合使用完成对变量的重复使用。

##### variable_scope的创建

```
variable_scope`使用`tf.variable_scope()`创建，返回一个上下文管理器。`variable_scope`包含了`name_scope`的全部功能，即在`variable_scope`下也可以给`Op`与`Tensor`加上`name_scope
```

variable_scope的使用注意事项

`variable_scope`的最佳搭档是`tf.get_variable()`函数。一般的，我们会在`variable_scope`中使用`tf.get_variable()`创建与获取模型的变量。

`tf.get_variable()`还有一个特点是必须提供独一无二的`name`（在当前变量作用域下)。

`tf.get_variable()`的用法是随着`reuse`的状态而改变的

- 在变量作用域中，如其属性`reuse=None`时，`tf.get_variable`不能获得变量；
- 在变量作用域中，如其属性`reuse=True`时，`tf.get_variable`不能创建变量；
- 在变量作用域中，`scope.reuse_variables()`可以改变下文的`reuse`属性值为`True`；
- 同名的多个变量作用域所处的上下文中的名字作用域不同。