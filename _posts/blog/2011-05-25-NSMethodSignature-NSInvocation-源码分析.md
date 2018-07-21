# NSMethodSignature, NSInvocation源码分析
##### Tips

```
void 的字面意思是 "无类型"，void * 则为 "无类型 指针"
void *可以指定任何类型的数据。
```

#### NSMethodSignature

通过类型编码，构造一个方法签名，比如: @:* ,返回参数是id，传入参数是 char *，一般在 Objective-C 中类型编码返回值 第一个参数是返回值，第二个参数是 SEL。
 
```
+ (nullable NSMethodSignature *)signatureWithObjCTypes:(const char *)types;
```

这个方法签名有多少个参数，第一第二个参数一个是 返回值，一个是 SEL

```
@property (readonly) NSUInteger numberOfArguments;
```

通过idx索引得到第几个编码值

```
- (const char *)getArgumentTypeAtIndex:(NSUInteger)idx
```

参数在栈上占用的字节数，这个数字随着应用程序运行的硬件体系结构而变化。

```
@property (readonly) NSUInteger frameLength;
```
方法返回类型，字符串编码

```
@property (readonly) const char *methodReturnType;
```
方法返回类型字节

```
@property (readonly) NSUInteger methodReturnLength;
```

#### NSInvocation
一个 NSInvocation 对象包含： 一个 target, 一个 selector，参数和返回值（return value），每一个元素都能够被直接赋值，当 NSInvocation 对象被调用的时候，这个返回值被自动设置。


通过方法签名返回一个 NSInvocation 对象

```
+ (NSInvocation *)invocationWithMethodSignature:(NSMethodSignature *)sig;
```

保留参数，它会将传入的所有参数以及 target 都 retain 一遍

```
- (void)retainArguments;
```

判断接收者是否保留了参数，在调用 retainArguments 之前为 NO,调用之后为 YES

```
@property (readonly) BOOL argumentsRetained;
```

设置消息调用者，target 也是发送消息的接收者

```
@property (nullable, assign) id target;
```

设置要调用的消息

```
@property SEL selector;
```

得到返回值和设置返回值，注意是无类型的指针

```
- (void)getReturnValue:(void *)retLoc;
- (void)setReturnValue:(void *)retLoc;
```

通过索引设置或得到返回值

```
- (void)getArgument:(void *)argumentLocation atIndex:(NSInteger)idx;
- (void)setArgument:(void *)argumentLocation atIndex:(NSInteger)idx;
```

调用方法

```
- (void)invoke;
- (void)invokeWithTarget:(id)target;
```




