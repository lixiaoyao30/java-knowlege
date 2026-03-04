3. SSM  
#   
# Spring AOP 完整学习笔记  
基于项目：spring_17 ~ spring_23（黑马程序员 SSM 课程） 目标：0基础小白看完能掌握全部AOP知识，理解原理，直接上手实战  
  
## 目录  
1. [AOP是什么，为什么要用](https://file+.vscode-resource.vscode-cdn.net/Users/C5402760/java/SSM_Demo01/%F0%9F%94%B7%20AOP%E5%AE%8C%E6%95%B4%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.md#%E4%B8%80aop%E6%98%AF%E4%BB%80%E4%B9%88%E4%B8%BA%E4%BB%80%E4%B9%88%E8%A6%81%E7%94%A8)  
2. [6大核心概念](https://file+.vscode-resource.vscode-cdn.net/Users/C5402760/java/SSM_Demo01/%F0%9F%94%B7%20AOP%E5%AE%8C%E6%95%B4%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.md#%E4%BA%8C6%E5%A4%A7%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5)  
3. [AOP工作流程](https://file+.vscode-resource.vscode-cdn.net/Users/C5402760/java/SSM_Demo01/%F0%9F%94%B7%20AOP%E5%AE%8C%E6%95%B4%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.md#%E4%B8%89aop%E5%B7%A5%E4%BD%9C%E6%B5%81%E7%A8%8B)  
4. [快速入门三步走](https://file+.vscode-resource.vscode-cdn.net/Users/C5402760/java/SSM_Demo01/%F0%9F%94%B7%20AOP%E5%AE%8C%E6%95%B4%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.md#%E5%9B%9B%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8%E4%B8%89%E6%AD%A5%E8%B5%B0)  
5. [切入点表达式](https://file+.vscode-resource.vscode-cdn.net/Users/C5402760/java/SSM_Demo01/%F0%9F%94%B7%20AOP%E5%AE%8C%E6%95%B4%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.md#%E4%BA%94%E5%88%87%E5%85%A5%E7%82%B9%E8%A1%A8%E8%BE%BE%E5%BC%8F)  
6. [5种通知类型](https://file+.vscode-resource.vscode-cdn.net/Users/C5402760/java/SSM_Demo01/%F0%9F%94%B7%20AOP%E5%AE%8C%E6%95%B4%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.md#%E5%85%AD5%E7%A7%8D%E9%80%9A%E7%9F%A5%E7%B1%BB%E5%9E%8B)  
7. [@Around环绕通知深度详解](https://file+.vscode-resource.vscode-cdn.net/Users/C5402760/java/SSM_Demo01/%F0%9F%94%B7%20AOP%E5%AE%8C%E6%95%B4%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.md#%E4%B8%83around%E7%8E%AF%E7%BB%95%E9%80%9A%E7%9F%A5%E6%B7%B1%E5%BA%A6%E8%AF%A6%E8%A7%A3)  
8. [通知获取数据](https://file+.vscode-resource.vscode-cdn.net/Users/C5402760/java/SSM_Demo01/%F0%9F%94%B7%20AOP%E5%AE%8C%E6%95%B4%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.md#%E5%85%AB%E9%80%9A%E7%9F%A5%E8%8E%B7%E5%8F%96%E6%95%B0%E6%8D%AE)  
9. [真实项目案例3个](https://file+.vscode-resource.vscode-cdn.net/Users/C5402760/java/SSM_Demo01/%F0%9F%94%B7%20AOP%E5%AE%8C%E6%95%B4%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.md#%E4%B9%9D%E7%9C%9F%E5%AE%9E%E9%A1%B9%E7%9B%AE%E6%A1%88%E4%BE%8B3%E4%B8%AA)  
10. [所有注解速查](https://file+.vscode-resource.vscode-cdn.net/Users/C5402760/java/SSM_Demo01/%F0%9F%94%B7%20AOP%E5%AE%8C%E6%95%B4%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.md#%E5%8D%81%E6%89%80%E6%9C%89%E6%B3%A8%E8%A7%A3%E9%80%9F%E6%9F%A5)  
11. [常见错误避坑指南](https://file+.vscode-resource.vscode-cdn.net/Users/C5402760/java/SSM_Demo01/%F0%9F%94%B7%20AOP%E5%AE%8C%E6%95%B4%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.md#%E5%8D%81%E4%B8%80%E5%B8%B8%E8%A7%81%E9%94%99%E8%AF%AF%E9%81%BF%E5%9D%91%E6%8C%87%E5%8D%97)  
12. [记忆总结口诀](https://file+.vscode-resource.vscode-cdn.net/Users/C5402760/java/SSM_Demo01/%F0%9F%94%B7%20AOP%E5%AE%8C%E6%95%B4%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.md#%E5%8D%81%E4%BA%8C%E8%AE%B0%E5%BF%86%E6%80%BB%E7%BB%93%E5%8F%A3%E8%AF%80)  
  
## 一、AOP是什么，为什么要用  
## 问题场景  
```
// ❌ 没有AOP：业务代码和额外功能混在一起
public void save() {
    Long start = System.currentTimeMillis();  // 计时（额外功能）
    System.out.println("book dao save ...");  // 业务代码（只有这1行）
    Long end = System.currentTimeMillis();    // 计时（额外功能）
    System.out.println("耗时：" + (end - start) + "ms");
}
// 问题：100个方法都要加计时 → 改100处
// 需求变了（改成日志）→ 再改100处 → 噩梦
// ✅ 有了AOP：业务代码干净，额外功能统一管理
public void save() {
    System.out.println("book dao save ...");  // 只有业务，清爽
}
// 计时代码写在切面类 MyAdvice，AOP自动插入到100个方法
// 需求变了 → 只改 MyAdvice 一个地方

```
## AOP 核心定义  
**AOP = Aspect Oriented Programming = 面向切面编程**  
**作用：在不修改原始代码的基础上，给方法增加额外功能。**  
**本质：动态代理**（Spring在运行时自动生成代理对象）  
## 典型使用场景  

| 场景   | 说明                             |
| ---- | ------------------------------ |
| 性能监控 | 记录每个方法的执行耗时                    |
| 日志记录 | 自动打印方法的入参、出参、执行时间              |
| 权限控制 | 验证用户是否有权限执行该方法                 |
| 参数处理 | 自动去除字符串参数的首尾空格                 |
| 事务管理 | Spring的@Transactional底层就是AOP实现 |
| 异常处理 | 统一捕获并记录异常信息                    |
  
## 二、6大核心概念  
## 用一张图理解所有概念  
```
你写的原始类：
BookDaoImpl  ←─────────────────────── 目标对象 Target（被代理的原始对象）
  ├── save()    ←─────────────────── 连接点 JoinPoint（所有方法，"有资格"被拦截）
  ├── update()  ←─────────────────── 连接点 JoinPoint
  ├── delete()  ←─────────────────── 连接点 JoinPoint
  └── select()  ←─────────────────── 连接点 JoinPoint
          │
          │ 切入点表达式筛选（选哪些方法被拦截）
          ▼
       update()  ←──────────────────  切入点 Pointcut（被选中要拦截的方法）
          │
          │ 绑定
          ▼
     计时/日志代码  ←───────────────── 通知 Advice（要插入的额外功能代码）
     写在 MyAdvice 类 ←─────────────── 通知类（存放通知的类）
     @Around("pt()")  ←─────────────── 切面 Aspect（通知+切入点的绑定关系）
          │
          │ Spring自动生成
          ▼
     $Proxy20  ←─────────────────────  代理对象 Proxy（你实际从容器拿到的）

```
## 6大概念速查表  

| 概念            | 简单理解                    | 代码位置                        |
| ------------- | ----------------------- | --------------------------- |
| 连接点 JoinPoint | 所有可以被拦截的方法（有资格，不一定真被拦截） | BookDaoImpl 的每个方法           |
| 切入点 Pointcut  | 用表达式实际选中要拦截的方法          | @Pointcut("execution(...)") |
| 通知 Advice     | 额外插入的功能代码（写成一个方法）       | MyAdvice 里的方法体              |
| 通知类           | 存放通知方法的类                | MyAdvice.java               |
| 切面 Aspect     | 通知 + 切入点的绑定关系描述         | @Around("pt()")             |
| 目标对象 Target   | 你写的原始类的实例               | BookDaoImpl 实例              |
| 代理对象 Proxy    | Spring生成的增强对象（包裹Target） | $Proxy20 实例                 |
  
## 三、AOP工作流程  
## 完整时间线  
```
T=0: new AnnotationConfigApplicationContext(SpringConfig.class)
      │
      ├─① 发现 @EnableAspectJAutoProxy → AOP功能开启
      │
      ├─② 扫描到 MyAdvice（@Component + @Aspect）
      │    └─ 提取切入点规则：拦截 BookDao.update()
      │        对应通知：@Before 执行 method()
      │
      └─③ 扫描到 BookDaoImpl（@Repository）
           ├─ 判断：BookDaoImpl 的方法是否匹配切入点？
           │   ├─ update() → 匹配 ✅
           │   ├─ save()   → 不匹配 ❌
           │   └─ ...
           │
           ├─ 匹配失败 → 直接 new BookDaoImpl() 放进容器（普通对象）
           └─ 匹配成功 → 生成代理对象 $Proxy20 放进容器
                         （代理对象内部包裹着 BookDaoImpl）

T=1: BookDao bookDao = ctx.getBean(BookDao.class)
      └─ 拿到 $Proxy20（不是BookDaoImpl本身！）
         证据：bookDao.getClass() 输出 class com.sun.proxy.$Proxy20

T=2: bookDao.update()
      └─ $Proxy20 拦截到调用
          ├─ 检查：update() 有通知要执行吗？→ 有！@Before method()
          ├─ 执行 @Before method()：打印时间戳
          └─ 执行真实方法 BookDaoImpl.update()：打印 "book dao update ..."

```
## 关键结论  
* Spring容器里存的是**代理对象**（如果方法匹配切入点），不是原始对象  
* 调用方完全感知不到代理的存在，用起来和原始对象一模一样  
* **SpringAOP的本质 = 动态代理**  
  
## 四、快速入门三步走  
## 步骤1：pom.xml 加依赖  
```
<!-- AOP必须加这个依赖，提供 @Aspect @Pointcut @Around 等注解 -->
<dependency>
    <groupId>org.aspectj</groupId>
    <artifactId>aspectjweaver</artifactId>
    <version>1.9.4</version>
</dependency>

```
⚠️ 没有这个依赖，@Aspect 等注解根本不存在，直接编译报错！  
## 步骤2：SpringConfig 开启AOP总开关  
```
@Configuration
@ComponentScan("com.itheima")
@EnableAspectJAutoProxy   // ← AOP总开关，必须加！不加则 @Aspect 完全被忽略
public class SpringConfig {
}

```
## 步骤3：写切面类  
```
@Component   // ← 让Spring管理（必须）
@Aspect      // ← 声明这是切面类（必须）
// 注意：@Component 和 @Aspect 缺一不可！
public class MyAdvice {

    // 切入点：选中哪些方法（空方法体，只是命名标签）
    @Pointcut("execution(void com.itheima.dao.BookDao.update())")
    private void pt() {}

    // 前置通知：在 update() 执行前自动触发
    @Before("pt()")
    public void method() {
        System.out.println(System.currentTimeMillis());
    }
}

```
## 调用入口  
```
public class App {
    public static void main(String[] args) {
        ApplicationContext ctx = new AnnotationConfigApplicationContext(SpringConfig.class);
        BookDao bookDao = ctx.getBean(BookDao.class);
        bookDao.update();   // ← 触发AOP
    }
}

```
## 执行效果  
```
1709123456789           ← @Before 先执行（时间戳）
book dao update ...     ← 原始方法后执行

```
  
## 五、切入点表达式  
## 完整语法  
```
execution( 访问修饰符  返回值  包名.类名.方法名(参数)  异常 )

示例：
execution( public  User  com.itheima.service.UserService.findById(int) )
            ↑可省   ↑      ↑包名                ↑类名      ↑方法名   ↑参数

实际最常用：
execution( *  com.itheima.service.*Service.*(..))
           ↑           ↑              ↑    ↑↑
        返回值任意     包名           类名  参数任意
                              以Service结尾

```
## 3个通配符详解  
********* —— 任意一个（单个位置）  
```
// 任意返回值
execution(* com.itheima.dao.BookDao.update())

// 任意包名（单层）
execution(void com.itheima.*.BookDao.update())

// 任意类名
execution(void com.itheima.dao.*.update())

// 任意方法名
execution(void com.itheima.dao.BookDao.*())

// 任意一个参数
execution(void com.itheima.dao.BookDao.update(*))

```
****..**** —— 任意多个（参数 或 包名多层级）  
```
// 任意参数（无参/一个参数/多个参数 都能匹配）
execution(void com.itheima.dao.BookDao.update(..))

// 任意多层包名
execution(void com..BookDao.update())
// com 后面跟任意多层包，只要最后是 BookDao.update()

```
****+**** —— 匹配子类类型（了解即可）  
```
execution(* *..BookDao+.*(..))
// 匹配 BookDao 及其所有实现类的所有方法

```
## 书写技巧6条（实战规则）  
技巧1：描述接口，不描述实现类  
```
// ✅ 推荐：描述接口（解耦）
execution(* com.itheima.dao.BookDao.*(..))

// ❌ 不推荐：描述实现类（换实现类时这里还要改）
execution(* com.itheima.dao.impl.BookDaoImpl.*(..))

```
技巧2：访问修饰符可以省略  
```
execution(public void com.itheima.dao.BookDao.update())  // 等价
execution(void com.itheima.dao.BookDao.update())         // ✅ 推荐省略

```
技巧3：返回值——增删改精确，查询用 *********  
```
// 增删改：返回void，精确写
execution(void com.itheima.dao.BookDao.save(..))
execution(void com.itheima.dao.BookDao.update(..))
execution(void com.itheima.dao.BookDao.delete(..))

// 查询：返回值不固定（User/List/int...），用*通配
execution(* com.itheima.dao.BookDao.findById(..))
execution(* com.itheima.dao.BookDao.findAll(..))

```
技巧4：包名用 *********，少用 ****..****  
```
// ✅ 推荐：* 逐级精确匹配（性能好）
execution(* com.itheima.dao.BookDao.*(..))

// ❌ 少用：.. 效率低（Spring需要扫描大量路径）
execution(* com..BookDao.*(..))

```
技巧5：类名用 ********* 匹配同类型  
```
// 匹配所有 Service 层接口的所有方法
execution(* com.itheima.service.*Service.*(..))
// UserService、OrderService、BookService 全部命中

// 匹配所有 Dao 层接口
execution(* com.itheima.dao.*Dao.*(..))

```
技巧6：方法名——动词精确，名词用 *********  
```
// getById → 动词get精确，Id是名词用*代替
execution(* com.itheima.service.*Service.getBy*(..))
// 能匹配：getById、getByName、getByPhone ...

// 所有以find开头的查询方法
execution(* com.itheima.service.*Service.find*(..))
// 能匹配：findAll、findById、findByName ...

```
## 企业最常用的4个表达式  
```
// 1. Service层所有方法（最常见，拦截所有业务）
"execution(* com.itheima.service.*Service.*(..))"

// 2. Service层所有查询方法
"execution(* com.itheima.service.*Service.find*(..))"

// 3. Dao层所有增删改方法
"execution(void com.itheima.dao.*Dao.*(..))"

// 4. 精确匹配一个方法
"execution(void com.itheima.dao.BookDao.update())"

```
## 切入点表达式速查表  

| 部分  | 推荐写法          | 不推荐     |
| --- | ------------- | ------- |
| 目标  | 描述接口          | 描述实现类   |
| 修饰符 | 省略            | 写public |
| 返回值 | 增删改写void，查询写* | 全部写*    |
| 包名  | 用*逐级匹配        | 用..偷懒   |
| 类名  | *Service、*Dao | 写具体类名   |
| 方法名 | 动词精确 + 名词*    | 全部*     |
| 参数  | 灵活，常用(..)     | —       |
| 异常  | 省略            | 写具体异常   |
  
## 六、5种通知类型  
## 执行位置时间轴  
```
  @Before   →  [ 原始方法 开始 → 执行 → 结束 ]  →  @AfterReturning（正常返回）
  （前置）              ↓ 如果抛了异常                  （返回后通知）
                    @AfterThrowing
                    （异常通知）

              @After（最后执行，不管成功还是抛异常，类似finally）

  @Around ══════════════════ 包裹整个过程 ══════════════════（最强大！重点）

```
## 各通知代码详解  
① ****@Before**** 前置通知  
```
@Before("pt()")
public void before() {
    System.out.println("before advice ...");
}

```
**执行顺序：**  
```
before advice ...       ← @Before 先执行
book dao update ...     ← 原始方法后执行

```
**使用场景：** 权限检查、打印方法入参日志、参数校验  
  
② ****@After**** 后置通知（不管成功失败都执行）  
```
@After("pt()")
public void after() {
    System.out.println("after advice ...");
}

```
**执行顺序：**  
```
# 正常情况：
book dao update ...     ← 原始方法先执行
after advice ...        ← @After 后执行

# 抛异常情况：
（异常发生）
after advice ...        ← @After 仍然执行！（类似finally）

```
**使用场景：** 资源释放（不管成功失败都要执行的操作）  
  
③ ****@AfterReturning**** 返回后通知（正常返回才执行）  
```
@AfterReturning("pt()")
public void afterReturning() {
    System.out.println("afterReturning advice ...");
}

```
**执行顺序：**  
```
# 正常情况：
book dao update ...         ← 原始方法执行
afterReturning advice ...   ← 正常返回后执行 ✅

# 抛异常情况：
（异常发生）
（afterReturning 不执行）❌

```
****@After vs @AfterReturning 区别：****  

| 通知              | 正常执行 | 抛异常    |
| --------------- | ---- | ------ |
| @After          | ✅ 执行 | ✅ 仍然执行 |
| @AfterReturning | ✅ 执行 | ❌ 不执行  |
  
**使用场景：** 只有成功才执行的后续操作、处理返回值  
  
④ ****@AfterThrowing**** 异常通知（抛异常才执行）  
```
@AfterThrowing("pt()")
public void afterThrowing() {
    System.out.println("afterThrowing advice ...");
}

```
**执行顺序：**  
```
# 正常情况：
book dao update ...       ← 正常执行
（afterThrowing 不执行）❌

# 抛异常情况：
（异常发生）
afterThrowing advice ...  ← 有异常才执行 ✅

```
**使用场景：** 异常日志记录、发送告警通知  
  
⑤ ****@Around**** 环绕通知（重点！最常用！）  
```
@Around("pt()")
public Object around(ProceedingJoinPoint pjp) throws Throwable {
    System.out.println("around before advice ...");  // 前置逻辑

    Object ret = pjp.proceed();   // 执行原始方法（分界线）

    System.out.println("around after advice ...");   // 后置逻辑

    return ret;   // 必须返回！
}

```
**执行顺序：**  
```
around before advice ...   ← 前置区域
book dao update ...        ← 原始方法
around after advice ...    ← 后置区域

```
## 5种通知使用场景速查  

| 通知              | 执行时机          | 重要度 | 典型使用场景        |
| --------------- | ------------- | --- | ------------- |
| @Before         | 方法执行前         | 常用  | 权限检查、参数校验     |
| @After          | 方法执行后（不管成功失败） | 常用  | 资源释放          |
| @AfterReturning | 正常返回后         | 了解  | 处理返回值         |
| @AfterThrowing  | 抛异常后          | 了解  | 异常日志          |
| @Around         | 包裹整个方法        | 重点  | 计时/日志/权限/参数处理 |
  
## 七、@Around 环绕通知深度详解  
## 标准模板（直接套用）  
```
@Around("pt()")
public Object around(ProceedingJoinPoint pjp) throws Throwable {

    // ════ 前置区域：原始方法执行之前 ════
    System.out.println("前置逻辑");

    Object ret = pjp.proceed();  // ← 分界线，这一行触发原始方法执行

    // ════ 后置区域：原始方法执行之后 ════
    System.out.println("后置逻辑");

    return ret;  // ← 必须返回原始方法的结果
}

```
## 4个必须（违反任意一个必出问题）  
```
// 必须1：参数必须是 ProceedingJoinPoint（不能是JoinPoint）
public Object around(ProceedingJoinPoint pjp) throws Throwable { }
//                   ↑ 这个参数提供 proceed() 方法

// 必须2：必须调用 pjp.proceed()，否则原始方法永远不执行
Object ret = pjp.proceed();

// 必须3：返回值必须是 Object，且必须 return
return ret;  // 不return → 调用方拿到null

// 必须4：throws Throwable（proceed()可能抛任何异常）

```
## 6种能力（其他通知做不到的）  
```
@Around("pt()")
public Object around(ProceedingJoinPoint pjp) throws Throwable {

    // ─── 能力1：前置执行任意逻辑 ───
    System.out.println("前置");

    // ─── 能力2：读取方法参数 ───
    Object[] args = pjp.getArgs();
    System.out.println("参数：" + Arrays.toString(args));  // [100, "itheima"]

    // ─── 能力3：修改参数 ───
    args[0] = 666;
    // 注意：修改后必须用 pjp.proceed(args) 传入，否则修改无效！

    // ─── 能力4：控制是否执行原始方法（权限控制！）───
    if (无权限) {
        return null;           // 直接return，原始方法完全不执行
    }
    Object ret = pjp.proceed(args);  // 有权限才执行

    // ─── 能力5：后置执行任意逻辑 ───
    System.out.println("后置：" + ret);

    // ─── 能力6：修改返回值 ───
    // ret = "修改后的值";  // 可以改变返回给调用方的结果

    return ret;
}

```
## pjp 的所有常用方法  
```
pjp.getArgs()                  // 获取参数数组 Object[]
pjp.proceed()                  // 用原始参数执行原始方法
pjp.proceed(args)              // 用修改后的参数执行原始方法
pjp.getSignature()             // 获取方法签名对象
pjp.getSignature().getName()               // 方法名：findById
pjp.getSignature().getDeclaringTypeName()  // 完整类名：com.itheima.service.AccountService
pjp.getTarget()                // 获取目标对象（BookDaoImpl实例）

```
## pjp.proceed() 和 pjp.proceed(args) 的区别  
```
Object[] args = pjp.getArgs();  // 获取到原始参数 [100, "itheima"]
args[0] = 666;                   // 修改参数

pjp.proceed()        // ← 用原始参数执行：findName(100, "itheima")  ❌ 修改没生效
pjp.proceed(args)    // ← 用修改后参数：findName(666, "itheima")    ✅ 修改生效

```
## 异常处理两种方式  
```
// 方式1：throws Throwable（异常继续往上传，调用方感知到异常）
@Around("pt()")
public Object around(ProceedingJoinPoint pjp) throws Throwable {
    Object ret = pjp.proceed();
    return ret;
}

// 方式2：try-catch（自己处理异常，可选择吞掉或重新抛）
@Around("pt()")
public Object around(ProceedingJoinPoint pjp) {  // 不throws
    Object ret = null;
    try {
        ret = pjp.proceed();
    } catch (Throwable t) {
        System.out.println("异常：" + t.getMessage());
        // 选择1：不throw → 异常被吞掉，调用方拿到null，不知道出错了
        // 选择2：重新抛 → 调用方能感知异常
        throw new RuntimeException(t);
    }
    return ret;
}

```
  
## 八、通知获取数据  
## 8.1 获取方法参数  
****JoinPoint**** —— 用于前置/后置/返回后/异常通知  
规则：JoinPoint jp 必须是方法的**第一个参数**！  
```
@Before("pt()")
public void before(JoinPoint jp) {
    Object[] args = jp.getArgs();   // 获取参数数组
    System.out.println("参数：" + Arrays.toString(args));
}
// 调用 findName(100, "itheima") → 打印：参数：[100, itheima]

@After("pt()")
public void after(JoinPoint jp) {
    Object[] args = jp.getArgs();   // 写法完全相同
    System.out.println("参数：" + Arrays.toString(args));
}

// ❌ 错误：JoinPoint不在第一位
public void afterReturning(String ret, JoinPoint jp) { }  // 运行报错！

// ✅ 正确：JoinPoint必须是第一位
public void afterReturning(JoinPoint jp, String ret) { }

```
****ProceedingJoinPoint**** —— 只用于环绕通知（****JoinPoint**** 的子类）  
```
@Around("pt()")
public Object around(ProceedingJoinPoint pjp) throws Throwable {
    Object[] args = pjp.getArgs();         // 获取参数：[100, "itheima"]
    System.out.println("原始参数：" + Arrays.toString(args));

    args[0] = 666;                          // 修改第一个参数
    // 必须用 proceed(args) 传入，修改才生效！
    Object ret = pjp.proceed(args);        // 执行：findName(666, "itheima")
    return ret;
}

```
**完整调用链（以 findName(100, "itheima") 为例）：**  
```
App.java: bookDao.findName(100, "itheima")
    ↓ 代理对象拦截
around() 执行：
  ① getArgs() → [100, "itheima"]
     打印：around advice ...[100, itheima]
  ② args[0] = 666 → [666, "itheima"]
  ③ pjp.proceed(args) → 执行 BookDaoImpl.findName(666, "itheima")
       打印：id:666         ← 参数被改成666了！
       return "itcast"
  ④ ret = "itcast"
     打印：around advice ...itcast
  ⑤ return "itcast"
    ↓
App.java: System.out.println(name) → 打印：itcast

```
**控制台最终输出：**  
```
around advice ...[100, itheima]    ← 获取到原始参数
id:666                             ← 实际执行时参数被改成666
around advice ...itcast            ← 获取到返回值
itcast                             ← App.java打印的最终结果

```
## 8.2 获取返回值  
只有 ****@AfterReturning**** 和 ****@Around**** 能获取返回值。  
```
// 方式1：@AfterReturning（returning属性值 必须 和参数名相同）
@AfterReturning(value = "pt()", returning = "ret")
//                               ↑ "ret" 这个名字要和参数名一致
public void afterReturning(JoinPoint jp, String ret) {
//                                        ↑ 参数名必须是 "ret"
    System.out.println("返回值：" + ret);
    // findName() 正常返回 "itcast" → 打印：返回值：itcast
    // findName() 抛异常 → 此方法不触发！
}

// 方式2：@Around（更简单，直接接收 proceed() 的结果）
@Around("pt()")
public Object around(ProceedingJoinPoint pjp) throws Throwable {
    Object ret = pjp.proceed();     // ret 就是原始方法的返回值
    System.out.println("返回值：" + ret);
    return ret;                     // 必须返回！
}

```
## 8.3 获取异常信息  
只有 ****@AfterThrowing**** 和 ****@Around**** 能获取异常。  
```
// 方式1：@AfterThrowing（throwing属性值 必须 和参数名相同）
@AfterThrowing(value = "pt()", throwing = "t")
//                               ↑ "t" 这个名字要和参数名一致
public void afterThrowing(Throwable t) {
//                          ↑ 参数名必须是 "t"
    System.out.println("异常：" + t.getMessage());
}

// 方式2：@Around（try-catch捕获）
@Around("pt()")
public Object around(ProceedingJoinPoint pjp) {
    Object ret = null;
    try {
        ret = pjp.proceed();
    } catch (Throwable t) {
        System.out.println("异常：" + t.getMessage());
        // throw new RuntimeException(t);  // 需要向上传则加这行
    }
    return ret;
}

```
## 8.4 速查表：哪种通知能获取什么  

| 通知类型            | 获取参数 | 获取返回值        | 获取异常        | 需要的参数类型               |
| --------------- | ---- | ------------ | ----------- | --------------------- |
| @Before         | ✅    | ❌            | ❌           | JoinPoint（第一位）        |
| @After          | ✅    | ❌            | ❌           | JoinPoint（第一位）        |
| @AfterReturning | ✅    | ✅ returning= | ❌           | JoinPoint + returning |
| @AfterThrowing  | ✅    | ❌            | ✅ throwing= | JoinPoint + throwing  |
| @Around         | ✅    | ✅ 直接接收       | ✅ try-catch | ProceedingJoinPoint   |
  
## 九、真实项目案例3个  
## 案例1：接口性能测速（spring_21_case_interface_run_speed）  
**需求：** 不修改 Service 代码，测量每个方法执行10000次的耗时。  
```
// ProjectAdvice.java
@Component
@Aspect
public class ProjectAdvice {

    // 切入点：拦截所有Service层方法
    @Pointcut("execution(* com.itheima.service.*Service.*(..))")
    private void servicePt() {}

    // 引用本类切入点的另一种写法（加类名前缀，便于跨类引用）
    @Around("ProjectAdvice.servicePt()")
    public Object runSpeed(ProceedingJoinPoint pjp) throws Throwable {
        // 获取方法签名信息
        Signature signature = pjp.getSignature();
        String className = signature.getDeclaringTypeName();  // 完整类名
        String methodName = signature.getName();               // 方法名

        long start = System.currentTimeMillis();
        Object ret = null;
        for (int i = 0; i < 10000; i++) {
            ret = pjp.proceed();   // 循环执行10000次
        }
        long end = System.currentTimeMillis();

        System.out.println("万次执行：" + className + "." + methodName
                         + "---->" + (end - start) + "ms");
        return ret;
    }
}

```
**调用链：**  
```
AccountServiceTestCase.testFindById()
    ↓ 调用
accountService.findById(4)
    ↓ 代理对象拦截
ProjectAdvice.runSpeed() 执行：
    ① 获取类名：com.itheima.service.AccountService
    ② 获取方法名：findById
    ③ 记录开始时间
    ④ 循环10000次执行 AccountServiceImpl.findById(4)
    ⑤ 记录结束时间
    ⑥ 打印：万次执行：...findById---->1271ms
    ⑦ 返回最后一次查询结果

```
**控制台输出：**  
```
万次执行：com.itheima.service.AccountService.findById---->1271ms
查询结果：Account{id=4, name='张三', ...}

```
  
## 案例2：密码权限控制 + 自动去除空格（spring_22_aop_advice_data）  
**需求：** 用户调用 findName(100, "admin ") 时，自动去除密码空格，再验证权限。  
```
// MyAdvice.java
@Component
@Aspect
public class MyAdvice {

    @Pointcut("execution(* com.itheima.dao.BookDao.findName(..))")
    private void pt1() {}

    @Around("pt1()")
    public Object around1(ProceedingJoinPoint pjp) {
        // 第1步：获取参数
        Object[] args = pjp.getArgs();
        // args[0] = id（int）
        // args[1] = password（String，可能带空格）

        // 第2步：去除密码首尾空格
        String password = args[1].toString().trim();
        System.out.println("原始密码:[" + args[1] + "]  去空格后:[" + password + "]");

        // 第3步：写回参数（原始方法也用干净的参数）
        args[1] = password;

        // 第4步：权限检查
        if (!"admin".equals(password)) {
            System.out.println("权限不足！密码错误，拒绝访问！");
            return null;   // 不调proceed()，原始方法不执行
        }

        // 第5步：权限通过，用干净参数执行原始方法
        Object ret = null;
        try {
            ret = pjp.proceed(args);   // 必须传 args！
        } catch (Throwable t) {
            t.printStackTrace();
        }
        System.out.println("权限验证通过，执行结果：" + ret);
        return ret;
    }
}

```
**三种场景对比：**  
```
// App.java
bookDao.findName(100, "wrongpwd");   // 场景1：密码错误
bookDao.findName(200, "admin ");     // 场景2：密码带空格
bookDao.findName(300, "admin");      // 场景3：密码正确

```
**控制台输出：**  
```
===== 场景1：密码错误 =====
原始密码:[wrongpwd]  去空格后:[wrongpwd]
权限不足！密码错误，拒绝访问！
App拿到结果：null

===== 场景2：密码带空格 =====
原始密码:[admin ]  去空格后:[admin]    ← 空格被去掉
权限验证通过，执行结果：admin
App拿到结果：admin

===== 场景3：密码正确 =====
原始密码:[admin]  去空格后:[admin]
权限验证通过，执行结果：admin
App拿到结果：admin

```
  
## 案例3：自动去除所有String参数空格（spring_23_case_handle_password）  
**需求：** 所有 Service 层方法，自动去除 String 类型参数的首尾空格。  
```
// DataAdvice.java
@Component
@Aspect
public class DataAdvice {

    // 切入点：返回boolean，有两个参数的Service层方法
    @Pointcut("execution(boolean com.itheima.service.*Service.*(*,*))")
    private void servicePt() {}

    @Around("servicePt()")
    public Object trimStr(ProceedingJoinPoint pjp) throws Throwable {
        Object[] args = pjp.getArgs();

        // 遍历所有参数，只处理String类型
        for (int i = 0; i < args.length; i++) {
            if (args[i].getClass().equals(String.class)) {
                args[i] = args[i].toString().trim();   // 去空格
            }
        }

        // 必须传 args！否则修改无效
        Object ret = pjp.proceed(args);
        return ret;
    }
}

```
**调用链：**  
```
App.java:
  resourcesService.openURL("http://pan.baidu.com/haha", "root ")
                                                              ↑ 有空格！
    ↓ 代理对象拦截
DataAdvice.trimStr() 执行：
  ① 获取参数：["http://pan.baidu.com/haha", "root "]
  ② 遍历参数：
     args[0] = "http://..." → String类型 → .trim() → "http://..."（无空格无变化）
     args[1] = "root " → String类型 → .trim() → "root"（空格去掉）
  ③ pjp.proceed(args) → 执行 ResourcesServiceImpl.openURL("http://...", "root")
                                                                          ↑ 干净的密码
    ↓
底层数据库验证 "root" 密码，正常通过

```
**处理数组参数的扩展：**  
```
for (int i = 0; i < args.length; i++) {
    // 单个String
    if (args[i] instanceof String) {
        args[i] = ((String) args[i]).trim();
    }
    // String数组
    else if (args[i] instanceof String[]) {
        String[] arr = (String[]) args[i];
        for (int j = 0; j < arr.length; j++) {
            arr[j] = arr[j].trim();
        }
        args[i] = arr;
    }
    // 数字类型（int/Integer等）：不需要处理，跳过
}

```
  
## 十、所有注解速查  
```
// ══════════════════════════════════════════════════
// 1. 配置类注解 - AOP总开关（必须加在配置类上）
// ══════════════════════════════════════════════════
@EnableAspectJAutoProxy
// 加了：Spring处理 @Aspect，AOP生效
// 不加：@Aspect 完全被忽略，AOP不工作

// ══════════════════════════════════════════════════
// 2. 切面类注解（两个必须同时加在切面类上）
// ══════════════════════════════════════════════════
@Component    // 让Spring管理（纳入IoC容器）
@Aspect       // 声明这是切面类（含切入点和通知）

// ══════════════════════════════════════════════════
// 3. 切入点注解（加在空方法上，方法名作为切入点标签）
// ══════════════════════════════════════════════════
@Pointcut("execution(* com.itheima.service.*Service.*(..))")
private void pt() {}   // 方法体必须是空的

// ══════════════════════════════════════════════════
// 4. 通知注解（5种，加在通知方法上）
// ══════════════════════════════════════════════════
@Before("pt()")                                       // 前置通知
@After("pt()")                                        // 后置通知
@AfterReturning(value = "pt()", returning = "ret")    // 返回后通知
@AfterThrowing(value = "pt()", throwing = "t")        // 异常通知
@Around("pt()")                                       // 环绕通知（重点）

// ══════════════════════════════════════════════════
// 5. 跨类引用切入点（切入点在A类，通知在B类时使用）
// ══════════════════════════════════════════════════
// A类（集中管理切入点）
public class MyPointcuts {
    @Pointcut("execution(* com.itheima.service.*Service.*(..))")
    public void servicePt() {}   // 注意：跨类引用必须是 public！
}

// B类（通知类）引用A类的切入点
@Around("MyPointcuts.servicePt()")      // 格式：类名.切入点方法名()
public Object advice(ProceedingJoinPoint pjp) throws Throwable { }

```
  
## 十一、常见错误避坑指南  
## 错误1：@Around不调 proceed() → 原始方法不执行  
```
// ❌ 错误：忘记调 proceed()
@Around("pt()")
public Object around(ProceedingJoinPoint pjp) throws Throwable {
    System.out.println("before");
    return null;   // 原始方法永远不执行！调用方拿到null
}

// ✅ 正确：必须调用 proceed()
@Around("pt()")
public Object around(ProceedingJoinPoint pjp) throws Throwable {
    System.out.println("before");
    Object ret = pjp.proceed();  // 必须调！
    return ret;
}

```
## 错误2：修改参数后用 proceed() 无参版 → 修改不生效  
```
// ❌ 错误：修改了参数，但没传进 proceed()
Object[] args = pjp.getArgs();
args[0] = 666;
Object ret = pjp.proceed();        // 仍然用原始参数！666没生效

// ✅ 正确：必须用 proceed(args) 把修改后的参数传入
Object[] args = pjp.getArgs();
args[0] = 666;
Object ret = pjp.proceed(args);    // 用修改后的参数执行

```
## 错误3：returning/throwing 属性值和参数名不一致  
```
// ❌ 错误：returning="result" 但参数名是 ret，不一致 → 运行时报错
@AfterReturning(value = "pt()", returning = "result")
public void afterReturning(String ret) { }

// ✅ 正确：returning 的值必须和参数名完全一致
@AfterReturning(value = "pt()", returning = "ret")
public void afterReturning(String ret) { }

// 同理：@AfterThrowing
@AfterThrowing(value = "pt()", throwing = "t")
public void afterThrowing(Throwable t) { }  // 参数名必须是 "t"

```
## 错误4：@Around 返回 void → 调用方拿不到返回值  
```
// ❌ 错误：返回void，原始方法的返回值被丢弃
@Around("pt()")
public void around(ProceedingJoinPoint pjp) throws Throwable {
    pjp.proceed();  // 返回值被丢弃！
}

// ✅ 正确：必须 Object 类型 + return
@Around("pt()")
public Object around(ProceedingJoinPoint pjp) throws Throwable {
    Object ret = pjp.proceed();
    return ret;
}

```
## 错误5：切面类只有 @Aspect 没有 @Component  
```
// ❌ 错误：没有 @Component，Spring不管理这个类，AOP不生效
@Aspect
public class MyAdvice { }

// ✅ 正确：两个注解必须同时存在
@Component
@Aspect
public class MyAdvice { }

```
## 错误6：JoinPoint 不在第一个参数位置  
```
// ❌ 错误：JoinPoint 不在第一位 → 运行时报错
@AfterReturning(value = "pt()", returning = "ret")
public void afterReturning(String ret, JoinPoint jp) { }

// ✅ 正确：JoinPoint 必须放在第一位
@AfterReturning(value = "pt()", returning = "ret")
public void afterReturning(JoinPoint jp, String ret) { }

```
## 错误7：跨类引用切入点时，切入点方法是 private  
```
// ❌ 错误：private 方法，外部类无法引用
public class MyPointcuts {
    @Pointcut("...")
    private void servicePt() {}   // private！跨类引用报错
}

// ✅ 正确：跨类引用必须是 public
public class MyPointcuts {
    @Pointcut("...")
    public void servicePt() {}    // public！可以跨类引用
}

```
  
## 十二、记忆总结口诀  
## AOP三件套（缺一不可）  
```
1. pom.xml    →  aspectjweaver 依赖
2. 配置类     →  @EnableAspectJAutoProxy 总开关
3. 切面类     →  @Component + @Aspect 两个注解同时加

```
## 切入点表达式速记  
```
execution(返回值  包.类.方法(参数))

增删改 → void    查询 → *    参数 → (..)
类名   → *Service / *Dao
方法名 → 动词精确 + 名词*（getBy*、find*）
包名   → 用* 少用..

```
## @Around 四必须  
```
参数  → ProceedingJoinPoint pjp
调用  → pjp.proceed() 或 pjp.proceed(args)
返回  → Object 类型，return ret
异常  → throws Throwable 或 try-catch

```
## 获取数据三要点  
```
获取参数  → pjp.getArgs() / jp.getArgs()
获取返回值 → returning="ret" 或 直接接收 proceed() 结果
获取异常  → throwing="t"   或 try-catch
JoinPoint  → 必须放在方法第一个参数！

```
## 一张图记住全部  
```
┌── 配置 ─────────────────────────────────────────────┐
│  @EnableAspectJAutoProxy（AOP总开关）                 │
└─────────────────────────────────────────────────────┘
           ↓
┌── 切面类 ───────────────────────────────────────────┐
│  @Component + @Aspect                               │
│                                                     │
│  @Pointcut("execution(* 包.类.方法(..))")            │
│  private void pt() {}  ← 切入点命名标签              │
│                                                     │
│  @Around("pt()")                                    │
│  public Object method(ProceedingJoinPoint pjp)      │
│      throws Throwable {                             │
│      // 前置逻辑                                     │
│      Object ret = pjp.proceed();  ← 原始方法        │
│      // 后置逻辑                                     │
│      return ret;   ← 必须返回                       │
│  }                                                  │
└─────────────────────────────────────────────────────┘
           ↓ Spring自动生成代理对象
┌── 调用方 ───────────────────────────────────────────┐
│  BookDao bookDao = ctx.getBean(BookDao.class);       │
│  // bookDao 实际是 $Proxy20，不是 BookDaoImpl！       │
│  bookDao.update();  ← 自动触发通知                   │
└─────────────────────────────────────────────────────┘

```
  
## 附录：完整切面类模板  
```
package com.itheima.aop;

import org.aspectj.lang.JoinPoint;
import org.aspectj.lang.ProceedingJoinPoint;
import org.aspectj.lang.Signature;
import org.aspectj.lang.annotation.*;
import org.springframework.stereotype.Component;
import java.util.Arrays;

@Component
@Aspect
public class TemplateAdvice {

    // ════ 1. 定义切入点 ════
    @Pointcut("execution(* com.itheima.service.*Service.*(..))")
    private void servicePt() {}

    // ════ 2. 前置通知 ════
    @Before("servicePt()")
    public void before(JoinPoint jp) {
        Object[] args = jp.getArgs();
        System.out.println("【前置】参数：" + Arrays.toString(args));
    }

    // ════ 3. 后置通知 ════
    @After("servicePt()")
    public void after(JoinPoint jp) {
        System.out.println("【后置】方法执行完毕（不管成功失败）");
    }

    // ════ 4. 返回后通知 ════
    @AfterReturning(value = "servicePt()", returning = "ret")
    public void afterReturning(JoinPoint jp, Object ret) {
        System.out.println("【返回后】返回值：" + ret);
    }

    // ════ 5. 异常通知 ════
    @AfterThrowing(value = "servicePt()", throwing = "t")
    public void afterThrowing(JoinPoint jp, Throwable t) {
        System.out.println("【异常】" + t.getMessage());
    }

    // ════ 6. 环绕通知（最常用，包含了前置+后置+返回值+异常）════
    @Around("servicePt()")
    public Object around(ProceedingJoinPoint pjp) throws Throwable {
        // 获取方法信息
        Signature sig = pjp.getSignature();
        String className = sig.getDeclaringTypeName();
        String methodName = sig.getName();

        // 获取参数
        Object[] args = pjp.getArgs();
        System.out.println("【前置】" + className + "." + methodName
                         + " 参数：" + Arrays.toString(args));

        // 计时
        long start = System.currentTimeMillis();

        Object ret = null;
        try {
            // 如需修改参数：
            // args[0] = 新值;
            // ret = pjp.proceed(args);

            ret = pjp.proceed();   // 执行原始方法

        } catch (Throwable t) {
            System.out.println("【异常】" + t.getMessage());
            throw t;   // 继续向上抛，不吞异常
        }

        long end = System.currentTimeMillis();
        System.out.println("【后置】耗时：" + (end - start) + "ms，返回值：" + ret);

        return ret;
    }
}

```
  
## 十三、企业级完整案例：统一操作日志系统  
**场景：** 电商/后台管理系统中，记录每个用户的操作行为（谁、什么时间、调用了什么接口、传了什么参数、是否成功、耗时多少）。这是企业中 AOP 最高频的真实用法。  
## 效果预览  
```
[操作日志] 操作人：张三 | 模块：用户管理 | 操作：查询用户
           方法：UserService.findById | 入参：[1001]
           返回值：User{id=1001, name='李四'} | 耗时：12ms | 状态：成功

[操作日志] 操作人：张三 | 模块：订单管理 | 操作：删除订单
           方法：OrderService.delete | 入参：[88]
           异常：订单不存在 | 耗时：3ms | 状态：失败

```
## 项目结构  
```
com.itheima
  ├── annotation
  │   └── Log.java              ← 自定义注解（标记哪些方法要记录日志）
  ├── aop
  │   └── LogAdvice.java        ← 日志切面（核心AOP）
  ├── context
  │   └── UserContext.java      ← 用户上下文（ThreadLocal存当前操作人）
  ├── domain
  │   └── OperationLog.java     ← 操作日志实体类
  ├── service
  │   ├── UserService.java      ← 被拦截的Service（加了@Log注解）
  │   └── impl
  │       └── UserServiceImpl.java
  └── App.java                  ← 程序入口（模拟用户登录+操作）

```
  
## Step 1：自定义注解 @Log  
```
package com.itheima.annotation;

import java.lang.annotation.*;

/**
 * 操作日志注解：加在需要记录日志的Service方法上
 * 不加这个注解的方法，AOP不会处理
 */
@Target(ElementType.METHOD)       // 只能加在方法上
@Retention(RetentionPolicy.RUNTIME) // 运行时保留（AOP要读取它）
@Documented
public @interface Log {
    String module() default "";    // 模块名，如"用户管理"
    String operation() default ""; // 操作描述，如"查询用户"
}

```
**为什么要自定义注解而不是直接用切入点表达式？**  
* 精确控制：只有加了 @Log 的方法才记录，不是所有方法  
* 携带元数据：注解里可以写 module、operation 等描述信息  
* 灵活：不用改切入点表达式，加减注解就能控制  
  
## Step 2：用户上下文 UserContext  
```
package com.itheima.context;

/**
 * 用户上下文：用 ThreadLocal 存储当前登录用户信息
 * 每个请求线程独立，互不干扰
 */
public class UserContext {

    private static final ThreadLocal<String> CURRENT_USER = new ThreadLocal<>();

    /** 用户登录时调用（实际项目由Filter/Interceptor解析JWT后调用） */
    public static void setUser(String username) {
        CURRENT_USER.set(username);
    }

    /** 获取当前操作人 */
    public static String getUser() {
        String user = CURRENT_USER.get();
        return user != null ? user : "未登录";
    }

    /** 请求结束时清除，防止内存泄漏 */
    public static void clear() {
        CURRENT_USER.remove();
    }
}

```
  
## Step 3：操作日志实体 OperationLog  
```
package com.itheima.domain;

import java.time.LocalDateTime;

/**
 * 操作日志实体（真实项目中对应数据库 operation_log 表）
 */
public class OperationLog {
    private String operator;        // 操作人
    private String module;          // 模块
    private String operation;       // 操作描述
    private String methodName;      // 完整方法名
    private String params;          // 入参（JSON格式）
    private String result;          // 返回值（JSON格式）
    private String errorMsg;        // 异常信息（正常为null）
    private Long executionTime;     // 执行耗时（毫秒）
    private boolean success;        // 是否成功
    private LocalDateTime operateTime; // 操作时间

    // getter/setter 省略（实际项目用Lombok @Data）

    @Override
    public String toString() {
        return "\n[操作日志]" +
               "\n  操作人：" + operator +
               " | 模块：" + module +
               " | 操作：" + operation +
               "\n  方法：" + methodName +
               " | 入参：" + params +
               "\n  " + (success ? "返回值：" + result : "异常：" + errorMsg) +
               " | 耗时：" + executionTime + "ms" +
               " | 状态：" + (success ? "✅ 成功" : "❌ 失败");
    }

    // ── 以下为 getter/setter ──
    public void setOperator(String operator) { this.operator = operator; }
    public void setModule(String module) { this.module = module; }
    public void setOperation(String operation) { this.operation = operation; }
    public void setMethodName(String methodName) { this.methodName = methodName; }
    public void setParams(String params) { this.params = params; }
    public void setResult(String result) { this.result = result; }
    public void setErrorMsg(String errorMsg) { this.errorMsg = errorMsg; }
    public void setExecutionTime(Long executionTime) { this.executionTime = executionTime; }
    public void setSuccess(boolean success) { this.success = success; }
    public void setOperateTime(LocalDateTime operateTime) { this.operateTime = operateTime; }
}

```
  
## Step 4：日志切面 LogAdvice（AOP核心）  
```
package com.itheima.aop;

import com.itheima.annotation.Log;
import com.itheima.context.UserContext;
import com.itheima.domain.OperationLog;
import org.aspectj.lang.ProceedingJoinPoint;
import org.aspectj.lang.annotation.Around;
import org.aspectj.lang.annotation.Aspect;
import org.aspectj.lang.annotation.Pointcut;
import org.aspectj.lang.reflect.MethodSignature;
import org.springframework.stereotype.Component;

import java.lang.reflect.Method;
import java.time.LocalDateTime;
import java.util.Arrays;

@Component
@Aspect
public class LogAdvice {

    /**
     * 切入点：拦截所有加了 @Log 注解的方法
     * 注意：这里用注解匹配，不是用包路径匹配
     */
    @Pointcut("@annotation(com.itheima.annotation.Log)")
    private void logPt() {}

    @Around("logPt()")
    public Object recordLog(ProceedingJoinPoint pjp) throws Throwable {
        // ── 1. 准备日志对象 ──
        OperationLog log = new OperationLog();

        // ── 2. 读取 @Log 注解上的信息 ──
        MethodSignature signature = (MethodSignature) pjp.getSignature();
        Method method = signature.getMethod();
        Log logAnnotation = method.getAnnotation(Log.class);

        log.setModule(logAnnotation.module());
        log.setOperation(logAnnotation.operation());

        // ── 3. 记录方法信息 ──
        String className = pjp.getTarget().getClass().getName();
        String methodName = signature.getName();
        log.setMethodName(className + "." + methodName);

        // ── 4. 记录操作人和时间 ──
        log.setOperator(UserContext.getUser());
        log.setOperateTime(LocalDateTime.now());

        // ── 5. 记录入参 ──
        Object[] args = pjp.getArgs();
        log.setParams(Arrays.toString(args));

        // ── 6. 执行原始方法，记录结果/异常和耗时 ──
        long start = System.currentTimeMillis();
        try {
            Object ret = pjp.proceed();

            // 成功
            log.setSuccess(true);
            log.setResult(String.valueOf(ret));
            log.setExecutionTime(System.currentTimeMillis() - start);

            // 真实项目：在这里把 log 存入数据库
            // logService.save(log);
            System.out.println(log);

            return ret;

        } catch (Throwable t) {
            // 失败
            log.setSuccess(false);
            log.setErrorMsg(t.getMessage());
            log.setExecutionTime(System.currentTimeMillis() - start);

            // 真实项目：在这里把 log 存入数据库
            // logService.save(log);
            System.out.println(log);

            throw t;  // 异常继续向上传，不影响业务
        } finally {
            UserContext.clear();  // 清除ThreadLocal，防内存泄漏
        }
    }
}

```
  
## Step 5：被拦截的 Service（只需加 @Log 注解）  
```
package com.itheima.service;

import com.itheima.annotation.Log;

public interface UserService {

    @Log(module = "用户管理", operation = "查询用户")
    String findById(Integer id);

    @Log(module = "用户管理", operation = "删除用户")
    void delete(Integer id);

    @Log(module = "用户管理", operation = "新增用户")
    void save(String name, String phone);
}
package com.itheima.service.impl;

import com.itheima.service.UserService;
import org.springframework.stereotype.Service;

@Service
public class UserServiceImpl implements UserService {

    public String findById(Integer id) {
        // 模拟业务：找不到抛异常
        if (id == 999) throw new RuntimeException("用户不存在：" + id);
        return "User{id=" + id + ", name='测试用户'}";
    }

    public void delete(Integer id) {
        System.out.println("  [业务] 删除用户 id=" + id);
    }

    public void save(String name, String phone) {
        System.out.println("  [业务] 新增用户：" + name + " / " + phone);
    }
}

```
  
## Step 6：SpringConfig  
```
package com.itheima.config;

import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.EnableAspectJAutoProxy;

@Configuration
@ComponentScan("com.itheima")
@EnableAspectJAutoProxy
public class SpringConfig {}

```
  
## Step 7：入口 App.java（模拟3种场景）  
```
import com.itheima.config.SpringConfig;
import com.itheima.context.UserContext;
import com.itheima.service.UserService;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class App {
    public static void main(String[] args) {
        ApplicationContext ctx = new AnnotationConfigApplicationContext(SpringConfig.class);
        UserService userService = ctx.getBean(UserService.class);

        // ═══ 场景1：正常查询 ═══
        System.out.println("════ 场景1：正常查询 ════");
        UserContext.setUser("张三");
        String user = userService.findById(1001);
        System.out.println("  业务结果：" + user);

        // ═══ 场景2：正常删除 ═══
        System.out.println("\n════ 场景2：正常删除 ════");
        UserContext.setUser("李四");
        userService.delete(2001);

        // ═══ 场景3：抛出异常 ═══
        System.out.println("\n════ 场景3：查询不存在的用户（抛异常）════");
        UserContext.setUser("王五");
        try {
            userService.findById(999);
        } catch (RuntimeException e) {
            System.out.println("  业务层捕获：" + e.getMessage());
        }

        // ═══ 场景4：新增用户 ═══
        System.out.println("\n════ 场景4：新增用户 ════");
        UserContext.setUser("赵六");
        userService.save("陈七", "13900000001");
    }
}

```
  
## 完整控制台输出  
```
════ 场景1：正常查询 ════
[操作日志]
  操作人：张三 | 模块：用户管理 | 操作：查询用户
  方法：com.itheima.service.impl.UserServiceImpl.findById | 入参：[1001]
  返回值：User{id=1001, name='测试用户'} | 耗时：2ms | 状态：✅ 成功
  业务结果：User{id=1001, name='测试用户'}

════ 场景2：正常删除 ════
  [业务] 删除用户 id=2001
[操作日志]
  操作人：李四 | 模块：用户管理 | 操作：删除用户
  方法：com.itheima.service.impl.UserServiceImpl.delete | 入参：[2001]
  返回值：null | 耗时：1ms | 状态：✅ 成功

════ 场景3：查询不存在的用户（抛异常）════
[操作日志]
  操作人：王五 | 模块：用户管理 | 操作：查询用户
  方法：com.itheima.service.impl.UserServiceImpl.findById | 入参：[999]
  异常：用户不存在：999 | 耗时：0ms | 状态：❌ 失败
  业务层捕获：用户不存在：999

════ 场景4：新增用户 ════
  [业务] 新增用户：陈七 / 13900000001
[操作日志]
  操作人：赵六 | 模块：用户管理 | 操作：新增用户
  方法：com.itheima.service.impl.UserServiceImpl.save | 入参：[陈七, 13900000001]
  返回值：null | 耗时：1ms | 状态：✅ 成功

```
  
## 关键技术点汇总  
1. ****@annotation**** 切入点（最灵活的企业写法）  
```
// 方式A：包路径匹配（拦截范围固定，不够灵活）
@Pointcut("execution(* com.itheima.service.*Service.*(..))")

// 方式B：注解匹配（加注解就拦截，不加就不拦截，更灵活）✅ 企业推荐
@Pointcut("@annotation(com.itheima.annotation.Log)")

```
2. 读取方法上的注解信息  
```
// 通过 MethodSignature 拿到方法对象，再读取注解
MethodSignature signature = (MethodSignature) pjp.getSignature();
Method method = signature.getMethod();
Log logAnnotation = method.getAnnotation(Log.class);

String module    = logAnnotation.module();     // "用户管理"
String operation = logAnnotation.operation();  // "查询用户"

```
3. ****@Around**** 中异常的正确处理  
```
try {
    Object ret = pjp.proceed();
    // 成功逻辑...
    return ret;
} catch (Throwable t) {
    // 失败逻辑（记录异常信息）...
    throw t;   // ← 必须重新抛！不抛则业务层感知不到异常
}

```
4. ThreadLocal 和 AOP 配合（企业标准模式）  
```
HTTP请求 → Filter解析Token → UserContext.setUser("张三")
              ↓
         Controller → Service → AOP拦截
              ↓                    ↓ UserContext.getUser() 拿到"张三"
         业务执行              记录操作日志
              ↓
         finally → UserContext.clear()  ← 请求结束必须清除！

```
  
## 与 Spring Boot 的对应关系  
这个案例在 Spring Boot 真实项目中的完整形态：  
```
// Spring Boot 中通常这样使用（原理完全相同）

// 1. 注解不变
@Log(module = "用户管理", operation = "查询用户")

// 2. 切面类加 @Slf4j（用日志框架替代 System.out.println）
@Slf4j
@Component
@Aspect
public class LogAdvice {
    @Autowired
    private OperationLogMapper logMapper;  // 注入Mapper，把日志存入数据库

    @Around("@annotation(com.itheima.annotation.Log)")
    public Object recordLog(ProceedingJoinPoint pjp) throws Throwable {
        // 同上逻辑，最后：
        logMapper.insert(log);  // 存数据库，替代 System.out.println
    }
}

// 3. ThreadLocal 由 Spring Security / JWT Filter 维护
// 请求进来 → Filter解析JWT → 放入ThreadLocal → AOP读取

```
  
*最后更新：2026-03-04 | 基于 spring_17 ~ spring_23 项目*  
