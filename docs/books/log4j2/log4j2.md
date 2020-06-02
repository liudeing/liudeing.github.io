## slf4j+log4j2的主要流程
slf4j-api --> slf4j-log4j-impl --> log4j-api

```flow
st=>start: slf4j-api
a=>operation: slf4j-log4j-impl 
b=>end: log4j-api

st->a
a->b
```

流程：比如 log.info

AbstractLogger-->messageFactory.newMessage()

-->ParameterizedMessage/SimpleMessage/ObjectMessage

--> push (LogEvent)    这里具体使用的是 disruptor 发布事件

--> 异步接收到监听事件listen event 

--> LogEvent --> PatternLayout 
--> toSerializable() { 
	format (根据%m%n等配置的各种layout，对应有各种Convert，经过各种Convert之后，得到最终打印内容) 
	其中%m 是日志主体内容，对应的Convert为 MessagePatternConverter --> format() 获取message --> formateTo() 
}