## Think in java

### 第一章、对象导论

#### 1.1 抽象过程

​	所有的编程语言都提供抽象机制。可以认为，人们所能够解决问题的复杂性直接取决于抽象的类型和质量。

​	面向对象方式通过向程序员提供表示问题空间中的元素而更近了一步。这种表示方式非常通用，使得程序员不会受限于任何特定类型的问题。我们将问题空间中的元素及其在解空间中的表示称为“对象”。这种思想的实质是：程序可以通过添加新类型的对象使自身适用于某个特定问题。因此，当你在阅读描述解决方案的代码的同时，也是在阅读问题的表述。相比以前我们所使用的语言，这是一种更加灵活和更强有力的语言抽象。所以，OOP允许根据问题来描述问题，而不是根据运行解决方案的计算机来描述问题。但是它仍然与计算机有联系：每个对象看起来都有点像一台微型计算机——它具有状态，还具有操作，用户可以要求对象执行这些操作。如果要对现实世界的对象作为类比，那么说它们都具有特性和行为似乎不错。

​	Alan Kay曾经总结了第一个成功的面向对象语言、同时也是Java所基于的语言之一的Smalltalk的五个基本特性，这些特性表现了一种纯粹的面向对象程序设计方式：

​	1）**万物皆为对象。**将对象视为奇特的变量，它可以存储数据，除此之外，你还可以要求它在自身上执行操作。理论上讲，你可以抽取待求解的问题的任何概念化构件（狗、建筑物、服务等），将其表示为程序中的对象。

​	2）**程序是对象的集合，它们通过发送消息来告知彼此所要做的。**要想请求一个对象，就必须对该对象发送一条消息。更具体的说，可以把消息想象为对某个特定对象的方法的调用请求。

​	3）**每个对象都有自己的由其它对象所构成的存储。**换句话说，可以通过创建包含现有对象的包的方式来创建新类型的对象。因此，可以在程序中构建复杂的体系，同时将其复杂性隐藏在对象的简单性背后。

​	4）**每个对象都拥有其类型。**按照通用的说法，“每个对象都是某个类（class）的一个实例（instance）”，这里“类”就是“类型”的同义词。每个类最重要的区别于其它类的特性就是“可以发送什么样的消息给它”。

​	5）**某一特定类型的所有对象都可以接收同样的消息。**这是一句意味深长的表述，你在稍后便会看到。因为“圆形”类型的对象同时也是“几何形”类型的对象。所以一个“圆形”对象必能接受发送给“几何形”对象的消息。这意味着可以编写与“几何形”交互并自动处理所有与几何性质相关的事物的代码。这种可替代性（substitutability）是OOP中最强有力的概念之一。

Booch对对象提出了一个更加简洁的描述：对象具有状态、行为和标识。这意味着每一个对象都可以拥有内部数据（它们给出了该对象的状态）和方法（它们产生行为），并且每一个对象都可以唯一地与其它对象区分开来，具体说来，就是每一个对象在内存中都有一个唯一的地址（在Java中为对象的hashCode()）。

#### 1.2 每个对象都有一个接口

​	所有的对象都是唯一的，但同时也是具有相同的特性和行为的对象所归属的类的一部分。这种思想被直接应用于第一个面向对象语言Simula-67，它在程序中使用基本关键字class来引入新的类型。

​	Simula，就像其名字一样，是为了开发诸如经典的“银行出纳员问题”（bank teller problem）这样的仿真程序而创建的。在银行出纳员问题中，有出纳、客户、账户、交易和货币单位等许多“对象”。**在程序执行期间具有不同的状态而其他方面都相似的对象会被分组到对象的类中，这就是关键字class的由来**。创建抽象数据类型（类）是面向对象程序设计的基本概念之一。抽象数据类型的运行方式与内置（built-in）类型几乎完全一致：你可以创建某一个类型的变量（按照面向对象的说法，称其为对象或实例），然后操作这些变量（称其为发送消息或请求；发送消息，对象就知道要做什么）。每个类的成员或元素都具有某种共性：每个账户都有结余金额，每个出纳都可以处理存款请求等。同时，每个成员都有其自身的状态：每个账户都有不同的结余金额，每个出纳都有自己的姓名。因此，出纳、客户、账户、交易等都可以在计算机程序中被表示成唯一的实体。这些实体就是对象。每一个对象都属于定义了特性和行为的某个特定的类。

​	所以，尽管我们在面向对象程序设计中实际上是进行的是创建新的数据类型，但事实上所有的面向对象程序设计语言都是用class这个关键词来表示数据类型。当看到类型一词时，可将其作为类来考虑，反之亦然。

​	因为**类描述了具有相同特性（数据元素）和行为（功能）的对象集合**。所以一个类实际上就是一个数据类型，例如所有的浮点型数字具有相同的特性和行为集合。两者的差异在于，程序员通过定义类来适应问题，而不再被迫只能使用现有的用来表示机器中的存储单元的数据类型。可以根据需求，通过添加新的数据类型来扩展编程语言。编程系统欣然接受新的类，并且像对待内置类型一样地照管它们和进行类型检查。

​	面向对象方法并不是仅局限于构建仿真程序。无论你是否赞成以下观点，即任何程序都是你所设计的系统的一种仿真，面向对象技术的应用确实可以将大量问题很容易地降解为一个简单的解决方案。

​	一旦类被建立，就可以随心所欲地创建类的任意个对象，然后去操作它们，就像它们是存在于你的待求解问题中的元素一样。事实上，面向对象程序设计的挑战之一，就是在问题空间的元素和解空间的对象之间创建一对一的映射。

​	接口确定了对某一特定对象所能发出的请求。但是，在程序中必须有满足这些请求的代码。这些代码与隐藏的数据一起构成了实现。

#### 1.3 每个对象都提供服务

​	当正在试图开发或理解一个程序设计时，最好的方法之一就是将对象想象为“服务提供者”。程序本身将向用户提供服务，它将通过调用其它对象提供的服务来实现这一目的。你的目标就是去创建（或者最好是在现有的代码库中寻找）能够提供理想的服务来解决问题的一系列对象。

#### 1.4 被隐藏的具体实现



#### 1.5 复用具体实现



#### 1.6 继承



#### 1.7 伴随多态的可互换对象



#### 1.8 单根继承结构



#### 1.9 容器



#### 1.10 对象的创建和生命期



#### 1.11 异常处理：处理错误



#### 1.12 并发编程



#### 1.13 Java与Internet



#### 1.14 总结



### 第二章、一切都是对象

​	**尽管Java是基于C++的，但是相比之下，Java是一种更“纯粹”的面向对象程序设计语言。**

​	Java语言假设我们只进行面向对象的程序设计。也就是说，在开始用Java进行设计之前，必须将思想转换到面向对象的世界中来。这个入门基本功，可以使你具备使用这样一种编程语言编程的能力，这种语言学习起来更简单，也比许多其它OOP语言更易用。在本章，我们将看到Java程序的基本组成部分，并体会到在Java中（几乎）一切都是对象。

#### 2.1 用引用操纵对象

​	每种编程语言都有自己的操纵内存中元素的方式。有时候，程序员必须注意将要处理的数据是什么类型。你是直接操纵元素，还是用某种基于特殊语法的间接表示（例如C和C++里的指针）来操纵对象？

​	所有这一切在Java中都得到了简化。一切都被视为对象，因此可采用单一固定的语法。尽管一切都看作对象，但操纵的标识符实际上是对象的一个“引用”（reference）。可以将这一情形想象成用遥控器（引用）来操纵电视机（对象）。只要握住这个遥控器，就能保持与电视机的连接。当有人想改变频道或者减小音量时，实际上操纵的是遥控器（引用），再由遥控器来调控电视机（对象）。如果想在房间里四处走走，同时仍能调控电视机，那么只需携带遥控器（引用）而不是电视机（对象）。

​	此外，即使没有电视机，遥控器亦可独立存在。也就是说，你拥有一个引用，并不一定需要有一个对象与它关联。因此，如果想要操纵一个词或者句子，则可以创建一个String引用：

```java
	String s;
```

​	但这里所创建的只是**引用**，并不是对象。如果此时向s发送一个消息，就会返回一个运行时异常（NullPointerException）。这是因为此时s实际上没有与任何事物相关联（即，没有电视机）。因此，一种安全的做法是：创建一个引用的同时便进行初始化。

```java
	String s = "asdf";
```



#### 2.2 必须由你创建所有对象

​	一旦创建了一个引用，就希望它能与一个新的对象相关联。通常使用**new**操作符来实现这一目的。**new**关键字的意思是“给我一个新对象。”所以前面的例子可以写成：

```java
	String s = new String("asaf");
```

##### 2.2.1 存储到什么地方

​	程序运行时，对象是怎么进行放置安排的呢？特别是内存是怎样分配的呢？对这些方面的了解会对你有很大的帮助，有五个不同的地方可以存储数据：

​	1）

​	2）

​	3）

​	4）

​	5）

### 第三章、操作符

#### 3.6 自动递增和自动递减

​	++i和i++的不同之处在于：

​		++i会先运算，再赋值
​		i++会先赋值，再运算

#### 3.9 直接常量

​	一般来说，如果在程序中使用了"**直接常量**"，编译器可以准确地知道要生成什么样的类型，但有时候却是摸棱两可的。如果发生这种情况，必须对编译器加以适当的“**指导**”，用与直接量相关的某些字符来额外增加一些信息。

​	

```java
	@Test
    public void literalTest() {
        int one = 0x2f;
        logger.info("one:" + Integer.toBinaryString(one));
        int two = 0X2F;
        logger.info("two:" + Integer.toBinaryString(two));
        int three = 0177;
        logger.info("three:" + Integer.toBinaryString(three));
        char c = 0xffff;
        logger.info("c:" + Integer.toBinaryString(c));
        byte b = 0x7f;
        logger.info("b:" + Integer.toBinaryString(b));
        short s = 0x7fff;
        logger.info("s:" + Integer.toBinaryString(s));
    }
```



​	直接常量后面的后缀字符标志了它的类型。若为大写（或小写）的L，代表long。大写（或小写）字母F，代表float；大写（或小写）字母D，代表double。

​	十六进制数适用于所有整数数据类型，以前缀**0x（或0X），后面跟随0-9或小写（或大写）a-f**来表示。**如果试图将一个变量初始化成超出自身范围的值（无论这个值的数值形式如何），编译器都会向我们报告一条错误信息**。注意在前面的代码中，已经给出了char、byte和short所能表示的最大的十六进制值。如果超出范围，编译器会将值自动转成int型，并告诉我们需要对这次赋值进行**窄化转型**（**向下转型：将能容纳更多信息的数据类型转换为无法容纳那么多信息的类型**），这样我们就可清楚地知道自己的操作是否越界了。

​	**八进制数由前缀0以及后续的0~7的数字来表示**。

​	在C、C++或者Java中，二进制数没有直接常量表示方法。但是，在使用十六进制和八进制计数法时，以二进制形式显示结果将非常有用。通过使用Integer和Long类的静态方法toBinaryString()方法可以很容易实现这一点。请注意，如果将比较小的类型（byte、char、short）传递给Integer.toBinaryString()方法，则该类型将自动被转换int。

##### 	3.9.1 指数计数法

​		Java中采用了一种很不直观的计数法来表示指数，例如：

​			

```java
    public static void main(String[] args) {
            double expDoubleOne = 47e47d;
            double expDoubleTwo = 47e47;
            logger.info("expDoubleOne:" + expDoubleOne);
            logger.info("expDoubleTwo:" + expDoubleTwo);
     }
```

 	

​	在科学与工程领域，“e”代表自然数对数的基数，约等于2.718（Java中的Math.E给出了更精确的double类型值）。例如1.39 * e<sup>-43</sup>这样的指数表达式意味着1.39 * 2.718<sup>-43</sup>。然而，设计FORTRAN语言的时候，设计师们很自然地决定e代表“10的幂次”。这种做法很奇怪，因为FORTRAN最初是面向科学与工程设计领域的，它的设计者们对引入这样容易令人混淆的概念应该很敏感才对。但不管怎样，这种惯例在C、C++以及Java中被保留了下来。所以倘若习惯将e作为自然对数的基数使用，那么在Java中看到像**1.39e<sup>43</sup>f**这样的表达式时，请转换思维，它真正的含义是1.39 * 10<sup>43</sup>。



#### 3.10 按位操作符

​	按位操作符用来操作**整数基本数据类型**中的单个“比特”（bit），即二进制位。按位操作符会对两个参数中对应的位执行布尔代数运算，并最终生成一个结果。

​	按位操作符来源于C语言面向底层的操作，在这种操作中经常需要直接操纵硬件，设置硬件寄存器内的二进制位。Java的设计初衷是嵌入电视机机顶盒内，所以这种面向底层的操作仍被保留了下来。但是，人们可能不会过多地用到位操作符。

​	如果两个输入位都是1，则按位与操作符（&）生成一个输出位1；否则生成一个输出位0。

​	如果两个输入位里只要有一个是1，则按位或操作符（|）生成一个输出位1；只有在两个输出位都是0的情况下，它才会生成一个输出位0。

​	如果输入位的某一个是1，但不全都是1，那么按位异或操作符（^）生成一个输出位1（两个操作数的位中，相同则结果位0，不同则结果为1）。

​	按位非操作符（~），也称为取反操作符，它属于一元操作符，只对一个操作数进行操作（其它按位操作符是二元操作符）。按位非生成与输入位相反的值（逐位取反）——若输入0，则输出1；若输入1，则输出0（输出为负数+1，输出为整数-1）。

​	按位操作符可与等号（=）结合使用，以便**合并运算和赋值**：&=、|=、^=都是合法的（由于“~”是一元操作符，所以不可与“=”联合使用）。

​	我们将布尔类型作为一种单比特值对待，所以它多少有些独特。我们可对它执行按位与、或、异或运算。但不能执行按位非（大概是为了避免与逻辑NOT混淆）。**对于布尔值，按位操作符具有与逻辑操作符相同的效果，只是它们不会中途“短路”**。此外，针对布尔值进行的按位运算为我们新增了一个“异或”逻辑运算符，他并未包括在“逻辑”操作符的列表中。在移位表达式中，不能使用布尔运算。



```java
	@Test
    public void bitTest() {
        OperationDemo operationDemo = new OperationDemo();
        logger.info("countOne:" + Integer.toBinaryString(operationDemo.countOne));
        logger.info("countTwo:" + Integer.toBinaryString(operationDemo.countTwo));
        // 00010011011110011
        // 10010100110110000
        logger.info("==========================按位操作符==========================");
        System.out.println(operationDemo.countOne & operationDemo.countTwo);
        logger.info("按位操作符,& result:" + Integer.parseInt("00010000010110000", 2));
        System.out.println(operationDemo.countOne | operationDemo.countTwo);
        logger.info("按位操作符,| result:" + Integer.parseInt("10010111111110011", 2));
        System.out.println(operationDemo.countOne ^ operationDemo.countTwo);
        logger.info("按位操作符,^ result:" + Integer.parseInt("10000111101000011", 2));
        
        logger.info("============================================================");
        System.out.println(~operationDemo.countThree);
        System.out.println(~operationDemo.countFour);
        logger.info("=============================================================");
        
        System.out.println(operationDemo.countOne &= operationDemo.countTwo);
        logger.info("按位操作符,&= result:" + Integer.parseInt("00010000010110000", 2));

        // 00010000010110000
        // 10010100110110000
        System.out.println(operationDemo.countOne |= operationDemo.countTwo);
        logger.info("按位操作符,|= result:" + Integer.parseInt("10010100110110000", 2));

        // 10010100110110000
        // 10010100110110000
        System.out.println(operationDemo.countOne ^= operationDemo.countTwo);
        logger.info("按位操作符,^= result:" + Integer.parseInt("00000000000000000", 2));
    }
```



#### 3.11 移位操作符

 	移位操作符操作的运算对象也是二进制的“位”。移位操作符只可用来处理**整数类型**（基本数据类型的一种）。左移运算符（<<）能按照操作符右侧指定的位数将操作符左边的操作数向左移动（在低位补0）。“有符号”右移位操作符（>>）则按照操作符右侧指定的位数将操作符左边的操作数向右移动。 “有符号”右移位操作符使用“符号扩展”；若符号为正，则在高位插入0；若符号为负，则在高位插入1。Java中增加了一种“无符号”右移位操作符（>>>）,它使用“零扩展”；无论正负，都在高位插入0。这一操作符是C和C++中所没有的。

​	如果对**char、byte**和**short**类型的数值进行移位处理，那么在移位进行之前，它们会被转换为int类型，并且得到的结果也是一个int类型的值。只有数值右端的低5位才有用。这样可以防止我们移位超过int型值所具有的位数。（译注：因为2的5次方为32，而int型值只有32位）。若对一个long类型的数值进行处理，最后得到的结果也是long。此时只会用到数值右端的低6位，以防止移位超过long型数值具有的位数。

​	“移位”可与“等号”（<<=、>>=、>>>=）组合使用。此时，操作符左边的值会移动由右边的值指定的位数，再将得到的结果赋给左边的变量。但在进行"无符号"右移位结合赋值操作时，可能会遇到一个问题；如果对byte或short值进行这样的移位运算，得到的可能不是正确的结果。它们会先被转换为int类型，在进行右移操作，然后被截断，赋值给原来的类型，在这种情况下可能得到-1的结果。



```java
	@Test
    public void binShiftingTest() {
        logger.info("==========================移位操作符==========================");
        int i = -1;
        System.out.println(Integer.toBinaryString(i));
        System.out.println(Integer.toBinaryString(i >>>= 10));
        long l = -1;
        System.out.println(Long.toBinaryString(l));
        l >>>= 10;
        System.out.println(Long.toBinaryString(l));
        short s = -1;
        System.out.println(Integer.toBinaryString(s));
        s >>>= 10;
        System.out.println(Integer.toBinaryString(s));
        byte b = -1;
        System.out.println(Integer.toBinaryString(b));
        b >>>= 10;
        System.out.println(Integer.toBinaryString(b));
        b = -1;
        System.out.println(Integer.toBinaryString(b));
        System.out.println(Integer.toBinaryString(b >>> 10));
    }

    @Test
    public void binShiftingTestTwo() {
        logger.info("==========================移位操作符==========================");
        int num = 2147483647;
        System.out.println(num <<= 3);
        System.out.println(Integer.toBinaryString(num));
        for (int i = 1; i <= 32; i++) {
            System.out.println(Integer.toBinaryString(num >>> i));
        }
    }
```



#### 3.13 字符串操作符+和+=

​	这个操作符在Java中有一项特殊用途：连接不同的字符串。

#### 3.15 类型转换操作符

​	**类型转换**（case）的原意是“模型铸造”。在适当的时候，Java会将一种数据类型自动转换为另一种。例如，假设我们为某浮点变量赋以一个整数值，**编译器会将int自动转换为float**。类型转换运算允许我们显式地进行这种类型的转换，或者在不能自动进行转换的时候强制进行类型转换。

​	要想执行类型转换，需要将希望得到的数据类型置于圆括号内，放在要进行类型转换的值的左边。



```java
	@Test
    public void caseDemo() {
        double num = 20.243;
        System.out.println((int) num);
    }
```

​	

​	正如所看到的，即可对数值进行类型转换，亦可对变量进行数据转换。请注意，这里可能会引入“多余的”转型，例如，**编译器在必要的时候会自动进行int值到long值的提升**。但是你仍然可以做这样“多余的”事，以提醒自己需要留意，也可以使代码更清楚。在其它情况下，可能只有先进行类型转换，代码编译才能通过。

​	在C和C++中，类型转换有时会让人头痛。但是在Java中，类型转换则是一种比较安全的操作。然而，如果要执行一种名为**窄化转换**（narrowing conversion）的操作（也就是说，**将能容纳更多信息的数据类型转换为无法容纳那么多信息的类型**），就有可能面临信息丢失的危险（**数据精度丢失**）。此时，编译器会强制我们进行类型转换，这实际上是说：”这可能是一件危险的事情，如果无论如何要这么做，必须显式地进行类型转换“。而对于**扩展转换**（widening  conversion）（也就是说，**将无法容纳那么多信息的类型转换为能容纳更多信息的数据类型**），则不必显式地进行类型转换，因为新类型肯定能容纳原来类型的信息，不会造成任何信息的丢失（**数据精度丢失**）。

​	Java允许我们把任何基本数据类型转换为别的基本数据类型，但boolean型除外，后者根本不允许进行任何类型的转换处理。”类“数据类型不允许进行类型转换。为了将一种类转换为另一种，必须采用特殊的方法（本书后面会讲到，对象可以在其所属类型的类族之间可以进行类型转换；例如，”橡树“可以转型为”树“；反之亦然。但不能把它转换成类族以外的类型，如”岩石“）（**父类与子类之间、接口与实现类之间的类型转换**）。



##### 3.15.1 截尾和舍入

​		在执行窄化转换时，必须注意截尾和舍入问题。例如，如果将一个浮点值转换为整型值，Java会如何处理呢？例如，将29.7转换为int，结果是30还是29？



```java
	@Test
    public void castingNumber() {
        double above = 0.7;
        double below = 0.4;
        float fabove = 0.7f;
        float fbelow = 0.4f;
        System.out.println("above:" + (int) above);
        System.out.println("below:" + (int) below);
        System.out.println("fabove:" + (int) fabove);
        System.out.println("fbelow:" + (int) fbelow);
    }
```

​	

​	因此答案是在将float或double转型为整形值时，总是对该数字进行截尾。如果想要得到舍入的结果，就需要使用java.lang.Math中的round()方法。



```java
	@Test
    public void roundingNumber() {
        double above = 0.7;
        double below = 0.4;
        float fabove = 0.7f;
        float fbelow = 0.4f;
        System.out.println("above:" + Math.round(above));
        System.out.println("below:" + Math.round(below));
        System.out.println("fabove:" + Math.round(fabove));
        System.out.println("fbelow:" + Math.round(fbelow));
    }
```



##### 	3.15.2 提升

​		如果对基本数据类型执行算数运算或者按位运算，大家会发现，只要类型比int小（即char、byte或者short），那么在运算之前，这些值会自动转换为int。这样一来，最终生成的结果就是int类型。如果想把结果赋值给较小的类型，就必须使用类型转换（既然把结果赋给了较小的类型，就可能出现信息丢失（**精度丢失**）)。通常，表达式中出现的最大的数据类型决定了表达式中最终结果的数据类型。如果将一个float值与一个double值相乘，结果都是double；如果将一个int和一个long值相加，则结果为long。



#### 3.16 Java没有sizeof

​	在C和C++中，**sizeof**()操作符可以告诉你为数据项分配的字节数。在C和C++中，需要使用**sizeof**()的最大原因是为了“**移植**”。不同的数据类型在不同的机器上可能有不同的大小，所以在进行一些与存储空间有关的运算时，程序员必须获悉那些数据类型具体有多大。例如，一台计算机可用32位来保存整数，而另一台计算机只用16位程序。显然，在第一台计算机中，程序可保存更大的值。可以想象，移植是令C和C++程序员颇为头痛的问题。

​	Java不需要sizeof()操作符来满足这方面的需要，因为所有数据类型在所有机器中的大小都是相同的。我们不必考虑移植问题——**它已经被设计在语言中了**。



### 第五章、初始化和清理

​	**随着计算机革命的发展，“不安全”的编程方式已逐渐成为编程代价高昂的主因之一。**

​	初始化和清理（cleanup）正是涉及安全的两个问题。许多C程序的错误都源于程序员忘记初始化变量。特别是在使用程序库时，如果用户不知道如何初始化库的构件（或者是用户必须进行初始化的其它东西），更是如此。清理也是一个特殊问题，当使用完一个元素时，它对你也就不会产生什么影响了，所以很容易把它忘记。这样一来，这个元素占用的资源就会一直得不到释放，结果就是资源（尤其是内存）用尽。

​	C++引入了构造器（constructor）的概念，这是一个在创建对象时被自动调用的特殊方法，Java中也采用了构造器，并额外提供了“垃圾回收器”。对于不再使用的内存资源，垃圾回收器能自动将其释放。

#### 5.1 用构造器确保初始化

​	在Java中，通过提供构造器，类的设计者可确保每个对象都会得到初始化。创建对象时，如果其类具有构造器，Java就会在用户有能力操作对象之前自动调用相应的构造器，从而保证了初始化的进行。

​	接下来的问题就是如何命名这个方法。有两个问题：第一、所取的任何名字都可能与类的某个成员名称相冲突；第二、调用构造器是编译器的责任，所以必须让编译器知道应该调用哪些方法。C++语言中采用的解决方案看来最简单且更符合逻辑，所以在Java中也采用了这种方案：即构造器和采用与类相同的名称。

​	以下就是一个带有构造器的简单类：

​		

```java
	public class Rock {
        // This is a constructor
		public Rock() {
            System.out.println("Rock");
        }
	}

	public class SimpleConstructor {
        public static void main(String[] args) {
            for(int i = 0; i < 10;i++) {
                new Rock();
            }
        }
    }
```

​	

​	现在，在创建对象时：

```java
	new Rock();	// 实例化Rock对象时，会调用该类的构造方法
```

​	将会为对象分配存储空间，并调用相应的构造器。这样就确保了在你能操作对象之前，它已经被恰当的初始化了。

​	请注意，**由于构造器的名称必须与类名完全相同，所以“每个方法首字母小写”的编码风格并不适用于构造器**。

​	不接受任何参数的构造器叫做**默认构造器**，Java文档中通常使用术语**无参构造器**，但是默认构造器在Java出现之前已经使用许多年了，所以我仍旧倾向使用它。但是和其他方法一样，构造器也能带有形式参数，以便指定如何创建对象。对上述例子稍加修改，即可使构造器接受一个参数：

​	

```java
	public class RockTwo {	
		public RockTwo(int i) {
			System.out.println("Rock" + i);
		}
	}
	
	public class SimpleConstructorTwo {
        public static void main(String[] args) {
            for(int i = 0; i < 8;i++) {
                new Rock(i);
            }
        }
    }
```

​	

​	有了构造器形式参数，就可以在初始化对象时提供实际参数。例如，假设类Tree有一个构造器，它接受一个整型变量来表示树的高度，就可以这样创建一个Tree对象：

```java
	Tree tree = new Tree(12);
```

​	如果**Tree(int)是Tree类中唯一的构造器**，那么编译器将不会允许你以其他任何方式创建Tree对象（除非在Tree类中再创建一个构造器方法）。

​	构造器是一种特殊类型的方法，因为它没有返回值。这与返回值为空（void）明显不同。对于空返回值，尽管方法本身不会自动返回什么，但仍可选择让它返回别的东西（return;和Exception）。构造器则不会返回任何东西，你别无选择（new表达式确实返回了对新建对象的引用，但构造器本身并没有任何返回值）。假如构造器具有返回值，并且允许人们自行选择返回类型，那么势必得让编译器知道该如何处理此返回值。

#### 5.2 方法重载

​	任何程序设计语言都具备的一项重要特性就是对名字的运用。当创建一个对象时，也就给此对象分配到的存储空间取了一个名字。所谓方法则是给某个动作取得名字。通过使用名字，你可以引用所有的对象和方法。名字起的好可以使系统更易于理解和修改。就好比写散文——目的是让读者易于理解。

​	大多数程序设计语言（尤其是C）要求为每个方法（在这些语言中经常称为函数）都提供一个独一无二的标识符。所以绝不能用名为print()的函数显示了整数之后，又用一个名为print()的函数显示浮点数——每个函数都要有唯一的名称。

​	在Java（和C++）里，构造器是强制重载方法名的另一个原因。既然构造器的名字已经由类名所决定，就只能有一个构造器名。那么要想用多种方式创建一个对象该怎么办呢？假设你要创建一个类，既可以用标准的方式初始化，也可以从文件里读取信息来初始化。这就需要两个构造器：一个默认构造器，另一个取字符串作为形式参数——该字符串表示初始化对象所需的文件名称（或路径），由于都是构造器，所以它们必须有相同的名称，即类名。**为了让方法名相同而形式参数不同的构造器同时存在，必须使用方法重载**。

	##### 5.2.1 区分重载方法

​	要是几个方法都有相同的名称，Java如何才能知道你指的是哪一个呢？其实规则很简单：每一个重载的方法都必须有一个独一无二的参数类型列表。

​	稍加思考，就会觉得这是合理的。毕竟，对于名字相同的方法，除了参数类型的差异以外，还有什么办法能把它们区别开呢（访问修饰符的不同，返回值的不同，抛出的异常类型不同）？

​	甚至参数列表顺序的不同也足以区分两个方法。不过，一般情况下别这么做，因为这会使代码难以维护：

​			

```java
public class OverloadingOrder {
    public static void f(String str, int num) {
        System.out.println("str:" + str + ",num:" + num);
    }

    public static void f(int num, String str) {
        System.out.println("num:" + num + ",str:" + str);
    }

    public static void main(String[] args) {
        f("String first", 11);
        f(99, "Int first");
    }
}
```

​		

​	上例中两个print()方法虽然声明了相同的参数，但顺序不同，因此得以区分。

##### 5.2.2 涉及基本类型的重载

​	基本类型能从一个”较小“的类型自动提升至一个”较大“的类型，此过程中一旦涉及到重载，可能会造成一些混淆。

​		

```java
	package com.github.initandclean;

    public class OverloadingOrder {

        public void f1(char c) {
            System.out.println("f1(char)");
        }

        public void f1(byte b) {
            System.out.println("f1(byte)");
        }

        public void f1(short s) {
            System.out.println("f1(short)");
        }

        public void f1(int i) {
            System.out.println("f1(int)");
        }

        public void f1(long l) {
            System.out.println("f1(long)");
        }

        public void f1(float f) {
            System.out.println("f1(float)");
        }

        public void f1(double d) {
            System.out.println("f1(double)");
        }

        public void f2(byte b) {
            System.out.println("f2(byte)");
        }

        public void f2(short s) {
            System.out.println("f2(short)");
        }

        public void f2(int i) {
            System.out.println("f2(int)");
        }

        public void f2(long l) {
            System.out.println("f2(long)");
        }

        public void f2(float f) {
            System.out.println("f2(float)");
        }

        public void f2(double d) {
            System.out.println("f2(double)");
        }

        public void f3(short s) {
            System.out.println("f3(short)");
        }

        public void f3(int i) {
            System.out.println("f3(int)");
        }

        public void f3(long l) {
            System.out.println("f3(long)");
        }

        public void f3(float f) {
            System.out.println("f3(float)");
        }

        public void f3(double d) {
            System.out.println("f3(double)");
        }

        public void f4(int i) {
            System.out.println("f4(int)");
        }

        public void f4(long l) {
            System.out.println("f4(long)");
        }

        public void f4(float f) {
            System.out.println("f4(float)");
        }

        public void f4(double d) {
            System.out.println("f4(double)");
        }

        public void f5(long l) {
            System.out.println("f5(long)");
        }

        public void f5(float f) {
            System.out.println("f5(float)");
        }

        public void f5(double d) {
            System.out.println("f5(double)");
        }

        public void f6(float f) {
            System.out.println("f6(float)");
        }

        public void f6(double d) {
            System.out.println("f6(double)");
        }

        public void f7(double d) {
            System.out.println("f7(double)");
        }

        public void testConstVal() {
            System.out.println(5);
            f1(5);
            f2(5);
            f3(5);
            f4(5);
            f5(5);
            f6(5);
            f7(5);
        }

        public void testChar() {
            char c = 'x';
            System.out.println("char:");
            f1(c);
            f2(c);
            f3(c);
            f4(c);
            f5(c);
            f6(c);
            f7(c);
        }

        public void testByte() {
            byte b = 0;
            System.out.println("byte:");
            f1(b);
            f2(b);
            f3(b);
            f4(b);
            f5(b);
            f6(b);
            f7(b);
        }

        public void testShort() {
            short s = 0;
            System.out.println("short:");
            f1(s);
            f2(s);
            f3(s);
            f4(s);
            f5(s);
            f6(s);
            f7(s);
        }

        public void testInt() {
            int s = 0;
            System.out.println("int:");
            f1(s);
            f2(s);
            f3(s);
            f4(s);
            f5(s);
            f6(s);
            f7(s);
        }

        public void testLong() {
            long s = 0;
            System.out.println("long:");
            f1(s);
            f2(s);
            f3(s);
            f4(s);
            f5(s);
            f6(s);
            f7(s);
        }

        public void testFloat() {
            float s = 0;
            System.out.println("float:");
            f1(s);
            f2(s);
            f3(s);
            f4(s);
            f5(s);
            f6(s);
            f7(s);
        }

        public void testDouble() {
            double s = 0;
            System.out.println("double:");
            f1(s);
            f2(s);
            f3(s);
            f4(s);
            f5(s);
            f6(s);
            f7(s);
        }
    }
	
	public class TestOverloadingOrder {
        @Test
        public void test() {
            OverloadingOrder overloadingOrder = new OverloadingOrder();
            overloadingOrder.testConstVal();
            overloadingOrder.testChar();
            overloadingOrder.testByte();
            overloadingOrder.testShort();
            overloadingOrder.testInt();
            overloadingOrder.testLong();
            overloadingOrder.testFloat();
            overloadingOrder.testDouble();
        }
	}
```

​	

​	你会发现常数值5被当作int值处理，所以如果有某个重载方法接受int类型参数，它就会被调用。至于其它情况，**如果传入的数据类型（实际参数类型）小于方法中声明的形式参数类型，实际参数类型就会被提升**。char类型略有不同，如果无法找到恰好接受char类型参数的方法，就会把char类型直接提升至int类型（**Unicode字符可以用数字来表示**）。

​	

```java
	@Test
    public void test() {
        char c = '徐';
        System.out.println((int) c);
        System.out.println(Character.toChars(24464)[0]);
       
    }
```

​	

​	如果传入的实际参数大于重载方法声明的形式参数，会出现什么情况呢？

​			

```java
package com.github.initandclean;

public class OverloadingOrder {

    public void f1(char c) {
        System.out.println("f1(char)");
    }

    public void f1(byte b) {
        System.out.println("f1(byte)");
    }

    public void f1(short s) {
        System.out.println("f1(short)");
    }

    public void f1(int i) {
        System.out.println("f1(int)");
    }

    public void f1(long l) {
        System.out.println("f1(long)");
    }

    public void f1(float f) {
        System.out.println("f1(float)");
    }

    public void f1(double d) {
        System.out.println("f1(double)");
    }


    public void f2(char c) {
        System.out.println("f2(char)");
    }

    public void f2(byte b) {
        System.out.println("f2(byte)");
    }

    public void f2(short s) {
        System.out.println("f2(short)");
    }

    public void f2(int i) {
        System.out.println("f2(int)");
    }

    public void f2(long l) {
        System.out.println("f2(long)");
    }

    public void f2(float f) {
        System.out.println("f2(float)");
    }


    public void f3(char c) {
        System.out.println("f3(char)");
    }

    public void f3(byte b) {
        System.out.println("f3(byte)");
    }

    public void f3(short s) {
        System.out.println("f3(short)");
    }

    public void f3(int i) {
        System.out.println("f3(int)");
    }

    public void f3(long l) {
        System.out.println("f3(long)");
    }


    public void f4(char c) {
        System.out.println("f4(char)");
    }

    public void f4(byte b) {
        System.out.println("f4(byte)");
    }

    public void f4(short s) {
        System.out.println("f4(short)");
    }

    public void f4(int i) {
        System.out.println("f4(int)");
    }


    public void f5(char c) {
        System.out.println("f5(char)");
    }

    public void f5(byte b) {
        System.out.println("f5(byte)");
    }

    public void f5(short s) {
        System.out.println("f5(short)");
    }

    public void f6(char c) {
        System.out.println("f6(char)");
    }

    public void f6(byte b) {
        System.out.println("f6(byte)");
    }

    public void f7(char c) {
        System.out.println("f7(char)");
    }


    public void testDouble() {
        double s = 0;
        System.out.println("double:");
        f1(s);
        f2((float) s);
        f3((long) s);
        f4((int) s);
        f5((short) s);
        f6((byte) s);
        f7((char) s);
    }
}

public class TestOverloadingOrder {
    @Test
    public void test() {
        OverloadingOrder overloadingOrder = new OverloadingOrder();
        overloadingOrder.testDouble();
    }
}
```

​	

​	在这里，方法接受较小的基本类型作为参数。**如果传入的实际参数较大，就得通过类型转换来执行窄化转换**。如果不这样做，编译器就会报错。



##### 5.2.3 以返回值区分重载方法

​	读者可能会想：“在区分重载方法的时候，为什么只能以类名和方法的形式参数列表作为标准呢？能否考虑用方法的返回值来区分呢？”比如下面的两个方法，虽然它们有同样的名字和形式参数，但却很容易区分它们：



```java
	void f();
	int f() {return 1; }
```

​	

​	只要编译器可以根据语境明确判断出语义，比如在int x = f()中，那么的确可以据此区分重载方法。不过，有时你并不关心方法的返回值，你想要的是方法调用的其它效果（执行业务逻辑、校验信息是否合法），这是你可能会调用方法而忽略其返回值。所以，如果像下面这样调用方法：

​	

```java
	f();
```



​	此时Java如何才能判断该调用哪一个f()呢？别人该如何理解这种代码呢？因此，根据方法的返回值来区分重载方法是行不通的。

​	**重载的定义：在同一类中，方法名称相同，参数列表不同，与方法的返回值和访问修饰符无关**。



#### 5.3 默认构造器

​	如前所述，默认构造器（又名“无参”构造器）是没有形式参数的——它的作用是创建一个“默认对象”。如果你写的类中没有构造器，则编译器会自动帮你创建一个默认构造器。

​	但是，如果类中已经定义了一个构造器（无论是否有参数），编译器就不会帮你自动创建默认构造器。	

#### 5.4 this关键字

​	如果有同一类型的两个对象，分别是a和b。你可能想知道，如何才能让这两个对象都能调用peel()方法呢？

​		

```java
	public class Banana {
		
        public void peel(int i) {
            
        }
        
        public static void main(String[] args) {
        	
    	}
	}
```

​		

#### 5.5 清理：终结处理和垃圾回收

​	程序员都了解初始化的重要性，但常常会忘记同样也重要的清理工作。毕竟，谁需要清理一个int呢？但在使用程序库时，把一个对象用完后就“弃之不顾”的做法并非总是安全的。当然，Java有垃圾回收器负责回收无用对象占据的内存资源。但也有特殊的情况：假定你的对象（并非使用new）获得了一块“特殊”的内存区域，由于垃圾回收器只知道释放那些经由new分配的内存（堆内存），所以它不知道该如何释放该对象的这块“特殊“内存。为了应对这种情况，Java允许在类中定义一个名为finalize()的方法。它的工作原理”假定”是这样的：一旦垃圾回收器准备好释放对象占用的存储空间，将首先调用finalize()方法，并且在下一次垃圾回收动作发生时，才会真正回收对象占用的内存。所以要是你打算用finalize()，就能在垃圾回收时刻做一些重要的清理工作。

​	这里有一个潜在的编程陷阱，因为有些程序员（特别是C++程序员）刚开始可能会误把finalize()当作C++中的**析构函数（C++中销毁对象必须用到这个函数）**。所以有必要明确区分一下：在C++中，对象一定会被销毁（如果程序中没有缺陷的话）；而Java里的对象却并非总是被垃圾回收。或者换句话说：

​	1.对象可能不被垃圾回收。

​	2.**垃圾回收并不等于“析构”**。

​	这意味着在你不再需要某个对象之前，如果必须执行某些动作，那么你得自己去做。Java并未提供“析构函数”或相似的概念，要做类似的清理工作，必须自己动手创建一个执行清理工作的普通方法。

​	只要程序没有濒临存储空间用完的那一刻，对象占用的空间就总也得不到释放。如果程序执行结束，并且垃圾回收器一直没有释放你创建的人户对象的存储空间，则随着程序的退出，那些资源也会全部交还给操作系统。这个策略是恰当的，因为垃圾回收本身也有开销（Java的垃圾回收机制有额外的线程、本地**native**资源开销），要是不使用它，那就不用支付这一部分的开销了。

​	





































