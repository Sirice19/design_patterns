## State模式与Strategy模式相同与不同

### 相似之处

如果你看看状态模式和策略模式的UML图，就会发现它们的结构非常相似。使用State对象改变自己行为的对象被称为Context对象；相似的，使用Strategy对象改变自己行为的对象叫Context对象。记住，Client和Context打交道。在状态模式中，Context把方法调用委托给当前的状态对象，而在策略模式中，Context使用的Strategy对象，是被当做参数传递过来的，或在Context对象被创建时就被提供的

让我们来看看它们之间更多的相似之处：

1. 添加新的状态或策略都很容易，而且不需要修改使用它们的Context对象。
2. 它们都让你的代码符合OCP原则。在状态模式和策略模式中，Context对象对修改是关闭的，添加新的状态或策略，都不需要修改Context。
3. 正如状态模式中的Context会有初始状态一样，策略模式同样有默认策略。
4. 状态模式以不同的状态封装不同的行为，而策略模式以不同的策略封装不同的行为。
5. 它们都依赖子类去实现相关行为。

### 不同之处

现在我们知道，状态模式和策略模式的结构是相似的，但它们的意图不同。让我们重温一下它们的主要不同之处：

1. 策略模式封装了一组相关算法，它允许Client在运行时使用可互换的行为；状态模式帮助一个类在不同的状态显示不同的行为。
2. 状态模式封装了对象的状态，而策略模式封装算法或策略。因为状态是跟对象密切相关的，它不能被重用；而通过从Context中分离出策略或算法，我们可以重用它们。
3. 在状态模式中，每个状态通过持有Context的引用，来实现状态转移；但是每个策略都不持有Context的引用，它们只是被Context使用。
4. 策略实现可以作为参数传递给使用它的对象，例如Collections.sort()，它的参数包含一个Comparator策略。另一方面，状态是Context对象自己的一部分，随着时间的推移，Context对象从一个状态转移到另一个状态。
5. 虽然它们都符合OCP原则，策略模式也符合SRP原则（单一职责原则），因为每个策略都封装自己的算法，且不依赖其他策略。一个策略的改变，并不会导致其他策略的变化。
6. 另一个理论上的不同：策略模式定义了对象“怎么做”的部分。例如，排序对象怎么对数据排序。状态模式定义了对象“是什么”和“什么时候做”的部分。例如，对象处于什么状态，什么时候处在某个特定的状态。
7. 状态模式中很好的定义了状态转移的次序；而策略模式并无此需要：Client可以自由的选择任何策略。
8. 一些常见的策略模式的例子是封装算法，例如排序算法，加密算法或者压缩算法。如果你看到你的代码需要使用不同类型的相关算法，那么考虑使用策略模式吧。而识别何时使用状态模式是很简单的：如果你需要管理状态和状态转移，但不想使用大量嵌套的条件语句，那么就是它了。
9. 最后但最重要的一个不同之处是，策略的改变由Client完成；而状态的改变，由Context或状态自己。