---

title: Kotlin——1. 包,数据类型,普通类,接口
categories: "Kotlin"
tags: 
	- Kotlin
	- android
---
## 包 - 当前包和导包 ##

### 当前包 ###
例如:

	package demo

### 导包 ###
当导入的类名相同时可以使用 **`as`** 指定某个类的新名称并不创建新的类.

例如:

	import foo.Bar // Bar 可访问
	import bar.Bar as bBar // bBar 代表“bar.Bar”

----

## 数据类型 ##

### **基本数据类型 `Byte,Short,Int,Long,Float,Double`** ###

- 字节比(单位bit位-> 字节): **`Byte:Short:Int:Long:Float:Double = 8:16:32:64:32:64 = 1:2:4:8:4:8`**;
- Long类型后跟"L",Float类型后跟"f" or "F";
- 16进制表示:**0x**3FA;2进制表示:**0b**00000011;
- 可以使用下划线使易读;
- **较小的类型不能隐式转换为较大的类型,只能显式转换**;

			    - toByte(): Byte
			    - toShort(): Short
			    - toInt(): Int
			    - toLong(): Long
			    - toFloat(): Float
			    - toDouble(): Double
			    - toChar(): Char

- **数据比较判断,涉及装箱.**

	需要可空引用时，数字、字符会被装箱。如下:

				val a: Int = 10000
				val boxedA: Int? = a
				val anotherBoxedA: Int? = a
				print(boxedA === anotherBoxedA)		//false,装箱不同一性
				print(boxedA == anotherBoxedA)		//true,相等性

- 位运算符
				
			- shl(bits) – 有符号左移 (Java 的 <<)
			- shr(bits) – 有符号右移 (Java 的 >>)
			- ushr(bits) – 无符号右移 (Java 的 >>>)
			- and(bits) – 位与
			- or(bits) – 位或
			- xor(bits) – 位异或
			- inv() – 位非
		
			例如: val x = (1 shl 2) and 0x000FF000
				 类似于x = (1 << 2) &	0x000FF000		
	
### **`Char`**字符,可以使用**`.toInt()`**显式转为Int ###

		- 字符字面值用单引号括起来: '1'。 特殊字符可以用反斜杠转义。 
		- 支持这几个转义序列：\t、 \b、\n、\r、\'、\"、\\ 和 \$。 
		- 编码其他字符要用 Unicode 转义序列语法：'\uFF00'。

### Array数组 - 创建和赋值(不形变) ###

- 库函数 `arrayOf()` 来创建一个数组并传递元素值给它

			val asc = arrayOf(1,2,3,4,5);//[1,2,3,4,5]

- 库函数 `arrayOfNulls()` 可以用于创建一个指定大小、元素都为空的数组。
		
- Array构造

			// 创建一个 Array<String> 初始化为 ["0", "1", "4", "9", "16"]
			val asc = Array(5, { i -> (i * i).toString() })
			// - 接受数组大小 
			// - 工厂函数，用作参数的函数能够返回,给定索引的每个元素初始值

	- 其他未装箱的数组:ByteArray、 ShortArray、IntArray 等等。
	
	
### 字符串 ###

- 原生字符串: 使用**三引号包裹**,没有转义字符序列的字符串

				val text = """
				    | 这是什么
				    | 这是原生字符串
				    | 好像挺有意思的,前面这个是什么?
					| 边界前缀
				    """.trimMargin()
				// | 用作默认边界前缀，但你可以选择其他字符并作为参数传入
				//比如 trimMargin(">")。		

- 转义字符串: 可以有转义序列的字符串.\t、 \b、\n、\r、\'、\"、\\ 和 \$。

- **字符串中使用 ' $ ' 引用要添加入字符串的值或 调用值和表达式(使用 "{" 和 "}" )**.原生字符串中需要${'$'}.

			val s = "abc"
			val str = "$s.length is ${s.length}" // str = "abc.length is 3"

---

## 普通类和接口 ##

### 简单类和接口的定义

		class ClazzName{}
		class ClazzName		//没有类体
		interface Foo{
			
			fun a()
			fun b(){...}

		}
		class A:Foo{...}

1. 	类可以相互嵌套,可以继承或实现接口,使用`:`操作符;
2. 	接口默认使用`open`关键字;
3. 	接口函数可以有函数体.


本文参考自[ Kotlin语言中心站 ](https://www.kotlincn.net/docs/reference/)
