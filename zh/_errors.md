
# 警告和错误

如果提到经常被开发者忽略的特性，那应该就是动态输出错误和提醒的功能了。事实上，Sass 自带三条自定义指令从标准输出系统（CLI，编译程序……）中打印内容：

* `@debug`;
* `@warn`;
* `@error`.

先让我们把 `@debug` 放一边，毕竟它主要是用作调试 SassScript，而这并不是我们的重点。然后我们就剩下了相互间没有明显差异的 `@warn` 和 `@error`，唯一的不同是其中一个可以中断编译器的工作，而另一个不能。我想让你猜猜具体每一个都是做什么的。

现在，在一个 Sass 项目中往往存在大量的错误和提醒。基本上任何混合宏和函数出错都会发生特定类型或参数的错误，或者显示假设的提醒。

###### 扩展阅读

* [An Introduction To Error Handling](http://webdesign.tutsplus.com/tutorials/an-introduction-to-error-handling-in-sass--cms-19996)
* [Building a Logger Mixin](http://webdesign.tutsplus.com/tutorials/building-a-logger-mixin-in-sass--cms-22070)
* [SassyLogger](https://github.com/HugoGiraudel/SassyLogger)

## 警告

使用 [Sass-MQ](https://github.com/sass-mq/sass-mq) 中的这个函数可以转换 `px` 为 `em`，展示如下：

{% include snippets/errors/01/index.html %}

如果碰巧值是无单位的，这个函数就会默认单位是像素。就这一点而论，一个假设可能会带来风险，所以软件应该能够预测风险并提醒使用者。

## 错误

错误，与提示有所不同，将会中断编译器的下一步进程。基本上，它们中断编译并像堆栈跟踪一样在输出流中显示相关信息，这对调试很有帮助。因此，如果程序无法继续执行就应该抛出错误。如有可能，尝试解决这个问题并以显示提醒的方式代替。

举个例子，假设你创建了一个 getter 函数来从特定 map 中获取值。如果想要获取的值并不在 map 中，就可能会抛出错误。

{% include snippets/errors/02/index.html %}
