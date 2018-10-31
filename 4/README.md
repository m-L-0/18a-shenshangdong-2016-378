**总结**

本章主要讲了常量、变量、占位符

**1.常量**

​	常量是一块只读的内存区域，常量在**初始化时就必须赋值**，并且之后值将不能被改变。Python并无内置常量关键字，需要用到时往往需要我们去实现，而Tensorflow内置了常量方法 `tf.constant()`。

​	普通常量：tf.constant()

​	序列常量：tf.linspace()    tf.range()     

​	随机数常量：tf.random_normal()    tf.truncated_normal()    tf.random_uniform()     tf.random_shuffle()   tf.random_crop()

​	特殊常量：tf.zeros()    tf.zeros_like()   tf.ones()   tf.ones_like()

**2.变量**

​	变量用于存取张量，在Tensorflow中主要使用类`tf.Variable()`来实例化一个变量对象，作用类似于Python中的变量。需要注意的是，使用`tf.get_variable()`方法生成一个变量时，其**name不能与已有的name重名**。变量作为操作的一种，是可以参与图的构建与运行的，但变量在会话中运行时必须在之前进行初始化操作。

​	（1）变量初始化

- 使用变量的属性`initializer`进行初始化

- 使用`tf.variables_initializer()`初始化一批变量

- 使用`tf.global_variables_initialize()`与`tf.local_variables_initializer()`即可初始化全部变量

  ##### （2）变量赋值

- 定义时进行赋值

- 运行时修改变量的值

3. **占位符**

   使用TensorFlow定义图，类似于定义了一个算式。但这是不方便的，为了能够在复杂问题中能够流畅构建运算逻辑，我们还需要引入“未知数”来参与构建图，就像代数中的方程中引入未知数一样。在TensorFlow中，我们称之为**占位符（placehoders）**。