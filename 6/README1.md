​								**流程控制总结**

1.比较运算

- tf.equal   **不支持`==`运算符重载**。

- tf.not_equal    **不支持`!=`运算符重载**。

- tf.less

- tf.less_equal

- tf.greater

- tf.greater_equal

- tf.where    是一种特殊的比价运算符，他根据判别条件，分别从两个张量中抽取子元素组成新的张量

2.张量拷贝

tf.identity

3.张量结组

tf.group

4.双分支选择结构

tf.cond 用来构建选择结构，类似于if  else  语句

5.多分路分支选择结构

- 可用两个两路分支来实现   ，类似于if    elif   else
- tf.case

6.循环结构

tf.while_loop





