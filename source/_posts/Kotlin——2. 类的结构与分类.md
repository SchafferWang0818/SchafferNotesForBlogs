---

title: Kotlin——2. 类的结构与分类
categories: "Kotlin"
tags: 
	- Kotlin
	- android
---
## 类的结构 ##
类可以包括:

	- 初始化块
		- 初始化代码块(init)中可以使用主构造的参数;
	- 构造函数
	- 属性
	- 函数
	- 嵌套类和内部类
	- 对象表达式
	- 对象声明

类的模拟结构如下:

```

	[open/abstract] class <类名> [<访问修饰符>] [<注解>] [constructor] 
		[([override] [val/var] <参数1>:<类型1> [= <默认值>],.....  )]
		[: < 基类/接口类名>([val/var] <参数N>:<类型N>,.....  ),...] {
		//类体
	
		//初始化代码块必须使用init字段
		init {
			...
        }		

		//次构造,委托或间接委托给主构造
		constructor (<参数1>:<类型1>,.....)[: this/super(<参数名>,...)]{
			...
		}

		//属性
		[open/override]	[<访问修饰符>] var/val <属性名称> [: <属性类型>] [ = <默认属性值>]
		[<属性的getter访问器>]// var / val 时均存在
		[<属性的setter访问器>]// val 时不存在,只能在构造函数中初始化


		//函数/方法
		[open/override] [<访问修饰符>] fun [<扩展函数指定调用类型 .>] [函数名称]
			([val/var] [形参名称]:[形参类型] [ = < 默认值 >],...) : [<返回值类型>/Unit]{
				
			//函数体
			...

			//return Unit
			return 
		}

		//对象表达式,接收者可以是属性或函数
		属性/函数 = object [:<继承/实现基类>(参数:类型,....),...]{

			//属性和函数定义
			...

		}
		
		//高阶函数
		[open/override][<访问修饰符>] fun [<扩展函数指定调用类型 .>] [函数名称]
					([形参名称]:[形参类型] [ = < 默认值 >]
					,...
					,[定义函数名]:([传参类型1],...) -> [返回类型]) : [<返回值类型>/Unit]{
				
			......
			//函数体
			......
			//return Unit
			return 
		}


		//嵌套类/内部类(inner)
		[open/abstract] [inner]  class <类名> [<可见性修饰符>] [<注解>] [constructor] 
			[([override] [val/var] <参数1>:<类型1> [= <默认值>],.....  )]
			[: < 基类/接口类名>([val/var] <参数N>:<类型N>,.....  ),...]{

			...

		}

		
		//对象声明 = 静态单例,直接调用函数/属性
		object <名称> [:<继承/实现基类>(参数:类型,....),...]{

			//属性/函数定义
			...

		}

	}
```
----
## 类的分类 ##

### 数据类(data)- 特色:解构声明 & copy()

包含**保存的数据和数据机械推导而来的函数**的类,使用`data`修饰.

#### 构造 ####

	data class ClazzName(var param1:Int,val param2:String,...)
	
1. 参数要求
	1. **`val/var`** 修饰
	2. 构造必须有参数,除非参数均设置默认值
2. 修饰符要求：不能用抽象(**`abstract`**),开放(**`open`**),密封,内部的;
3. 继承要求 - 只能实现接口

构造自动导出以下函数(除非 **`自行定义以下函数造成覆盖`**):

- `equals()`
- `hashCode()`
- `toString()`格式为 `ClazzName(var param1=1,val param2="String",...)`
- 根据参数(属性)声明顺序生成解构声明`component1(),component2()....componentN()`
- `copy()`用于改变某个对象的某个属性,其他不变的情况
	
	```
	val jack = User(name = "Jack", age = 1)
	val olderJack = jack.copy(age = 2)
	```	
		
#### 解构声明 - 将一个对象属性同时赋值给一组的多个变量

		val jane = User("Jane", 35)
		val (name, age) = jane
		//name与age为从对象jane获取值并同时声明的成员变量
		
		val (name, age) = jane 
		相当于:
		val name = jane.component1()
		val age = jane.component2()
	
	`componentN()` 函数需要用 **`operator`** 关键字标记，以允许在解构声明中使用它们。		

**注意**:

1. 可以用在`for-`循环中,经常用于a,b属性对于集合(**可提供将映射表示为一个值的序列的iterator() 函数**)中对象的属性的判断`for ((a, b) in collection) { …… }`

2. 解构声明作为函数返回值存在的情况 (`val (param1,param2) = function(....)`),`function()`**函数返回对应数据类对象或标准类 `Pair<type1,type2>`**

3. **解构声明对应数据类对象的参数的个数**,不需要某个参数,可以使用`下划线"_"`代替

---

###  密封类 - 文件限制和When分支覆盖 ###
是一个**值为有限集中的类型、而不能有任何其他类型**,可以有**包含状态的多个实例的子类**,并且 **子类必须和基类位于同一个文件,孙类不做限制（在 Kotlin 1.1 之前， 子类必须嵌套在密封类声明的内部）**,使用**`sealed`**关键字的类.

	sealed class Expr
	data class Const(val number: Double) : Expr()
	data class Sum(val e1: Expr, val e2: Expr) : Expr()
	object NotANumber : Expr()
	

	//when分支情况
	fun eval(expr: Expr): Double = when(expr) {
	    is Const -> expr.number
	    is Sum -> eval(expr.e1) + eval(expr.e2)
	    NotANumber -> Double.NaN
	    // 不再需要 `else` 子句，因为我们已经覆盖了所有的情况
	}

使用密封类的关键好处在于使用 when 表达式 的时候，如果能够 验证语句覆盖了所有情况，就不需要为该语句再添加一个 else 子句了。

---

###  嵌套类,内部类,匿名内部类

1. 嵌套类是指嵌套于其他类中的类;
2. 内部类有 inner 关键字,内部类可以访问外部类成员属性,持有外部类引用;
3. 匿名内部类用于函数参数传入,与java相同,可以使用带接口类型前缀的lambda表达式创建它;

		val listener = ActionListener { println("clicked") }

---

###  枚举类
#### 枚举类的声明

1. 使用enum关键字;
2. 每一个枚举分别是一个当前类的对象,可以有初始化的值使用"()"包围;
3. 当类需要定义其他成员属性或函数,要使用";"将成员与其他分开;

		enum class Direction {
		    NORTH, SOUTH, WEST, EAST
		}
	
		//构造有参数,枚举有初始值
		enum class Color(val rgb: Int) {
	        RED(0xFF0000),GREEN(0x00FF00),BLUE(0x0000FF)
		}
	
		//自定义成员抽象函数,枚举对象实现函数
		enum class ProtocolState {
		    WAITING {
		        override fun signal() = TALKING
		    },
		
		    TALKING {
		        override fun signal() = WAITING
		    };
		
		    abstract fun signal(): ProtocolState
		}	

#### 枚举常量使用
1. 枚举常量可以获得在类声明中名称和属性.

		val name: String
		val ordinal: Int

2. 枚举常量实现`Comparable` 接口,自然排序顺序是定义顺序.

3. 枚举类有成方法允许列出定义的枚举常量以及通过名称获取枚举常量。

		EnumClass.valueOf(value: String): EnumClass
		EnumClass.values(): Array<EnumClass>

4. 使用 `enumValues<T>()` 和 `enumValueOf<T>()` 函数以泛型的方式访问枚举类中的常量 

		enum class RGB { RED, GREEN, BLUE }
		
		inline fun <reified T : Enum<T>> printAllValues() {
		    print(enumValues<T>().joinToString { it.name })
		}
		
		printAllValues<RGB>() // 输出 RED, GREEN, BLUE

----

本文参考自[ Kotlin语言中心站 ](https://www.kotlincn.net/docs/reference/)
