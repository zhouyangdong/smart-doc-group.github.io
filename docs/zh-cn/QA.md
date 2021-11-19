<h1 align="center">Smart-Doc使用问题集</h1>

我们整理该文档的目的是减少萌新和菜鸟的一些疑惑，如有问题请仔细查看。当然看在我们辛苦整理文档的份上，
如果你喜欢smart-doc，也请推荐给你的同事或者朋友，好的东西要分享给大家。也请记得给我点点star.

# Smart-doc组件最新版本是多少？
对于开源软件的版本获取，有好几种方式可以查到：

- [Maven Repository](https://mvnrepository.com)：但是这个并不是没个都能直接通过artifactId搜索到，
原因是这取决与这个java开发组件的搜索率已经这个站点的搜索算法，一般都是非常流行的才能直接搜索到。 
  如果你搜索不到可以换成group去搜索。
  
- [Maven Central Repository](https://search.maven.org)：这才是正儿八经发布公有组件的仓库，大部分JAVA
开源都是从这个站点发布后被其它仓库同步过去，因此这里一定能搜索到。
  
- [阿里云Maven仓库](https://maven.aliyun.com)：国内阿里云提供的仓库，也是从Maven Central同步过来。
  这里也可以去也可以搜索到。

- **项目仓库首页徽标：** 你打开smart-doc或者是smart-doc-maven-plugin以及smart-doc-gradle插件代码仓库的首页都能看到
  最新版的版本徽标。这也是大多数标准开源项目的做法。
  
- **项目的tag列表：** 一般项目开源项目发布版本的时候作者都会给代码打上tag。即便是作者不把tag做release写release日志。
  但是这个也是可以参考的。
  
只要你掌握了上面几种方法什么开源软件版本查找都难不倒你。

你GET到了吗？GET到了请给我们一键三连，快去给我们点点star吧！

# 注释怎么提取不到啊？
这个往往是一些萌新提出的问题。smart-doc的原理是使用源代码中的注释和泛型来分析生成文档。
因此使用smart-doc时要明白几个基础知识点：

- JAVA注释只存在于源代码中，一旦代码经过编译后注释就被编译器擦除了，不信你自己解压一个编译过的jar包看看里面的class还有没有注释。
- JAVA的泛型也是后来才添加的，也并不是从一开始底层就支持泛型的，因此源代码编译后泛型也会被擦除。

明白了上面原理后，你就知道为什么smart-doc官方要求你如果把代码作为公用库被其他项目使用是要发布一个resource jar的原因了。

当然你可以能存在两种原因加载不到源代码：

- 发布了源代码jar到私服，但是使用插件是胡乱拷贝官方文档中的配置并没有注意到官方文档中每个配置项的注释说明，
  各种补丁在暗中提示也没有注意到，因此请建议回头再看看插件部分配置文档。不易轻易问简单问题被打脸。
  
- maven多模块项目无法加载公用模块中的注释：首先检查自己项目结构是否符合多模块的做法。smart-doc插件依赖底层maven api来处理，
如果项目做得不好可能就无法自动去追溯你工程的依赖结构。
  建议去参考官方的[多模块demo](https://gitee.com/smart-doc-team/spring-boot-maven-multiple-module.git)。
  当然官方的插件也不是万能的，毕竟很多奇怪的工程搭建官方人员也没见识过，因此如果有问题始终无法解决，
  那请给官方提供一个完整模拟你项目结构的工程，并不要求写什么代码，每个模块写一个测试类即可。
  不要觉得你能随便就能描述清楚，记住`show me your code`.
  