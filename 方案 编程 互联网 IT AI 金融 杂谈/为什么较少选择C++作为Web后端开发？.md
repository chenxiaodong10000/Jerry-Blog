﻿# 【为什么较少选择C++作为Web后端开发？】

> 特别说明：以下内容来自知乎！

---

同样面向对象，为什么 Web 后端开发中 Java 应用的很广泛，C++ 用的却很少呢？
目前想到的可能问题有：

1. 是 C++ 本身的语言特性问题？
2. 没有一个像 Oracle 一样的公司推动 C++ 的 Web 开发标准指定以及相关库的开发？
3. C++ 学习成本太高？
4. 还是其他？

原因很多：

- 相比于 Java、.net、PHP 等开发效率低太多，低到无法忍受，不符合互联网的短平快、快速迭代、灰度发布
- Web 后端开发中大多数情况下语言本身带来的性能提升并没有那么重要，绝大多数时候系统的瓶颈在于 `架构` 和 `数据库` 上
- Web 项目通常要敏捷开发，好占据先机， 所以性能不是很重要（至少前期是）， 更需要入门快，上手快
- Web 需求变化多端且朝令夕改，所以性能无法顾忌， 需要更容易重构，有一定动态能力的
- C++ 很灵活，但同时开发成本也高，招人难， 所以对于大部分公司只能将其用在刀刃上，比如少量对性能要求高的地方（其实，绝大多数情况下是直接使用第三方写好的 C/C++ 中间件）

> 作者：dwing
来源：[知乎](https://www.zhihu.com/question/26782196/answer/975604841)
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

---

世界上主要的 Web 后端，都是用 C/C++ 编写的，比如目前谷歌、百度、腾讯、脸书、Youtube 等公司的后端，主要是 C++。

另外一些商务型公司，则采用 Java，比如：阿里巴巴。

其次，大部分互联网底层平台（操作系统、Web 服务器、数据库等），编程语言、相关扩展库，也大都是 C/C++ 开发的。

当然，这些基础平台的开发国内很少涉及，几乎是用国外 C/C++ 程序员开发好的产品（开源或商业收费）。一般都没有中国开发者参与，所以导致被完全忽视。

C/C++ 编写的程序，占互联网后台 90% 以上的运算能力。C/C++ 性能最好，但是开发效率最低。因此除了基础部件、调用频繁的库之外，普通网站大部分业务逻辑都会用开发效率更高的语言来编写。

C/C++ 占互联网后台运算能力统计：按平台算约 100%：C/C++ 几乎包揽了全部 Web 后台的运算能力。操作系统、Web服务器、数据库、大部分编程语言、扩展库全都囊括在内。包括 API 和 库调用 来算占 90% 以上。

除其他高级语言代码，C/C++ 占用了互联网后台 90% 以上的运算能力。其他低性能语言直接承载的运算较少，大部分运算是调用的 C/C++ 编写的系统 API 和 库。只按后端语言计算（大家常见的）：C/C++ 后端几大巨头在用，还有一些局部领域应用，总量确实较少，但权重有半壁江山也毫不夸张。并且因为通常有封装，所以前端直接看不到。谷歌后台内核主要是 C/C++，代码量是 Windows 的 30 倍。Python 运算性能比 C/C++ 慢 200 倍以上，只用于周边和大数据 AI 的胶水语言。目前到处在误传谷歌后端用 Python（来支撑大家常见的业务）。当然，Python Web 服务器性能可以达到 C/C++ 的 1/10，可以承载一些负载较轻、或原型性质的业务。为什么比 C++ 慢200 多倍的 Python，服务器性能却能达到 C++ 的 1/10 呢？因为 Python 大部分时间都是在运行 C 编写的扩展库以及系统 IO，本身 py 代码运力占比只有 5%。【这是一道小学奥数题】：已知 C/C++（C、C++速度几乎相等，可忽略差异）的速度是 Python 的 200 倍。Python 和 C++ 走过同样一段路程。Python 中间有乘坐 C，总耗时是C++ 的 10 倍。求 Python 独立行走的路程占整段路程的百分比？

答案为：大约 5%。

只有那些巨头网站，才有资源和能力用 C++ 来写后台。因为海量服务器的成本差异，远远超过 C++ 开发成本的增长。比如某服务 Python 要用 1000 万台服务器，PHP用 300 万台，Java 用 200 万台，C++ 用 100 万台。肯定选C++，节省几十几百亿。

比如脸书已经全面从PHP迁移到C++（70% C++ 和 30% PHP 转译 C++），服务器减少到原来的三分之一。 而 Python 最具盛名的网站 Youtube 也已迁移到 C++，此前用 C 来优化 Python 依然不能满足。

对于小型网站，如果 Python 用 10 台服务器、PHP 用 3 台、Java 用 2 台、C++ 用 1 台服务器。甚至起初任何语言一台服务器都够用。这时肯定不会选 C++，因为开发成本比服务器贵的多。通常我们粗略估算 C++ 需要两倍的开发成本，一个普通开发约 30-50 万总成本每年，能节省上百台服务器时才划算。而且 C++ 直接写 Web 痛苦指数高、快速反应能力低、大量熟手招聘困难，需要有更大成本优势时（成千上万台服务器），才会被采用。互联网 C/C++ 的替代品：Go 。

C/C++入门并不难学。但因为和硬件底层更近，所以程序形态与自然语言距离更远，需要写更多行语句和花更多时间去掌握。而夺命指针，即是性能飙升的利器，也是程序崩坏的元凶。因此，C++要更多时间去编译、测试和检查程序，才能保证稳定，不适合快速开发更迭。实际上是后端开发语言太方便、灵活、稳定了，倒逼 C++ 只能去做内核了。互联网光一般的更迭速度，C++ 的缓慢接近凝滞的身段，令人没法提起改进C++ 直接 Web 开发的兴趣。索性直接写出了 PHP、ASP.NET、JSP 等支持高效开发的产品。但当网站规模增大的时候，高并发和密集运算部分 C/C++ 又成为了必须的选择。Go 就是谷歌为了解决这些痛点，应运而生的。具备接近 C 的性能，但更安全快速、更具备互联网基因，目前在后端增长最快。

> 作者：无缺草
> 来源：[知乎](https://www.zhihu.com/question/26782196/answer/968086477?utm_source=wechat_session)
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

---

业务迭代效率互联网的 Web 后端追求短平快，这里倒不是说 C++ 效率不高，C++ 在多范式上结合了 oop 和 fp，同时保留了 c 的过程式，拥有几乎所有的语言特性。因此 C++ 是很强大的，但也就是因为这些特性，再加上特有的 pointer，reference 与之叠加起来，C++ 是非常非常复杂的，所以一般的公司是很难把控 C++ 写出来的质量的，这点 Java 虽然死板，但在工程上来说更可控。

还有后端最重要的一个技能就是使用轮子，面向 github/stackoverflow/google 编程，这点 Java 有很多顶级的后端的轮子，而 C++ 相对来说没有那么多。当然大厂有很多封装好的轮子，譬如 google/tencent 等，但对于一般的公司来说，一是没有造这种顶级轮子的实力，二是业务迭代也不允许去造。所以 Java、Python 这种能直接 import package 对大多数公司来说会更合适。

Web 后端的特点 Web 后端大多数是和 db 以及 cache 打交道，操作数据的时候嵌套业务逻辑，这一特点决定 Web 后端是重 io，轻计算的，因此好的 IO 并发模型，好的缓存设计才是关键。因此语言层面带来的性能提升面对磁盘寻道可以忽略不计。

> 作者：威士忌的碎冰
来源：[知乎](https://www.zhihu.com/question/26782196/answer/993217316)
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
