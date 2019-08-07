# https-github.com-keepingtheway-tab-repositories
面向对象那些事儿
面向对象编程
1、理解类和对象：
类：一类事务的抽象：例如水果类 汽车类
对象：事务中具体的个体   苹果、香蕉
2、类有属性和方法
属性：一类事物所类似的共有的特性  某个类的特征
方法： 一类事物的行为                       某个类的动作
3、新建一个类 类中有属性和方法  实例化对象 通过对象调用属性和方法
三、封装以及this的应用
1、创建一个汽车类
     属性性： 品牌、价格
     方法： 载客
     问题：价格为int类型，例如，价格为250元；
         程序没问题，但数据不合理

处理方案： （封装性）
给定一个默认值--如果有问题，默认10万
编写set/get方法，set给属性赋值，get获取属性值
概念：不要用new的对象直接调用属性赋值 而是用set/get进行封装
先进行类中的属性私有化 通过对象调用set/get方法进行处理
好处：规避数据的不合理性（安全性）set、get对数据进行封装（封装性）
2、this： 谁调用this所在方法 this就代表谁  this调属性 this.属性
引入封装性：  3大特性-封装、继承、多态
 * 封装两层含义： 1.功能性封装：前面的方法及  吃、洗衣服等
 *            2.数据的封装（属性的封装）：set/get方法
 *            set： 给属性赋值         规范： setAge()
 *            get： 获取属性的值      规范： getAge()
 *            
 * 封装性： 外部不要直接调属性，而是通过set/get方法进行封装           
 * 
 * 封装性操作步骤：
 * 1.属性私有化
 * 2.设计set/get方法
 *    
 * 好处： 安全、结构清晰，易于复用
 */
四、构造方法
1、什么是构造方法
实例化对象   类名  对象= new 类名（）：调用无参构造方法
1．构造方法的语法格式
访问修饰符 类名(参数列表){
    方法体;
}
2．默认构造方法
3．带参的构造方法
4．默认特性，系统默认会给我们提供一个无参的构造方法
A. 无参构造方法
 * 
 * 调用： new 类名();
 * 实现：public 类名(){}
 * 1. 当我们不写构造方法实现，系统会默认生成无参构造方法----查看反编译工具：xjad
 * 2. 当我们写了构造方法实现，系统不会默认生成无参构造方法
 * B. 有参构造方法
 * 调用： new 类名(参数);
 * 实现：public 类名(参数){
 *        赋值
 *     }
 * 注意： 往往使用有参构造的目的是给属性赋初始值    
 * 注意： 如果自定义了有参构造，一定要带上无参构造；---规范
 *
 */
代码解释
public class Student {
	private String name;  //属性
	private int    age;
	
	//注意： 如果自定义了有参构造，一定要带上无参构造；---规范
	public Student(){
		System.out.println("调无参构造...");
	}
	
	//this用法：
	//this.属性  （常用）
	//this.方法()
	//this(参数)： this调构造方法
	public Student(String name,int age){
		//this.name = name;   //this.属性
		//this.age  = age;
		
		this(name);  //this调带一个参数的构造方法
		//this(age);//构造方法必须出现在第一句，且两个构造方法调用只能用一个
	
		//this.setName(name);   //this.方法
		setAge(age);  //不写this，默认会有
	}
	
    //构造方法也可以重载
	public Student(String name) {
		this.name = name;
	}
	
	public Student(int age) {
		this.age = age;
	}

	//--------set/get方法---------
	public void setName(String name){
		//this(name);  this调构造方法只能放在构造方法中
		this.name = name;
	}
	
	public String getName(){
		return name;  //不写默认也是this.name  
	}
	
	public void setAge(int age){
		this.age = age;
	}
	
	public int getAge(){
		return age;
	}
	
	//功能性方法
	public void play(){
		System.out.println(name+"正在玩代码...");
	}
}
五、成员变量和局部变量
成员变量 VS  局部变量
1. 出现位置
   成员变量出现在类中
   局部变量出现在方法体，方法参数，main方法
2. 作用域不同
   成员变量至少在当前类中
   局部变量只能在方法体中
3. 内存位置不同
   成员变量在堆区
   局部变量在栈区--内存分析时讲解
4. 初始值不同
   成员变量有初始值，String默认null，int默认0
   局部变量无初始值，需要自己初始化
5. 出现重名时，优先级问题；局部变量优先--(重名时，作用域小的会覆盖作用域大的)
