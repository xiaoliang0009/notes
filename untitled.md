# RabbitMQ

## AMQP

高级消息队列协议，是应用层协议的一个开放标准，为面向消息的中间件设计。

## 核心概念

![&#x6A21;&#x578B;&#x67B6;&#x6784;](http://flighter-img.oss-cn-hangzhou.aliyuncs.com/1722cd79f0e53e1f.webp)

```text
Message : 消息
Queue : 队列
Producer : 生产者，消息发送方
Consumer : 消费者，消息接收方
Exchnage : 消息交换机, 生产者将消息发送给Exchange，Exchange再将消息路由给队列。
  - 消息的路径是：生产者 -> 交换机 -> 队列
RoutingKey : 路由键
Binding :
  - 可以理解为三元组, 类似于 <x,y,value> (<行, 列, 值>) (<queueName, exchangeName, bindingKey>)
  - 表示将queue用bindingKey绑定到exchange，该exchange收到的消息时，会根据exchange类型和消息的routingKey将消息路由到符合的队列。


Broker : RabbitMQ服务器实例, 节点
Connection : 客户端与服务器之间建立的一个TCP网络连接
Channel : 
  - RabbitMQ几乎所有操作均是通过Channel完成，包括发送消息、创建队列、交换机等、消费消息。先创建Connection、然后创建Channel，再使用Channel执行操作。
```

## 工作模式

* 简单模式 \(simple\)

  只有一个生产者、一个消费者和一个队列

![simple](http://flighter-img.oss-cn-hangzhou.aliyuncs.com/1722d5a23685a99a.webp)

* 工作模式 \(work\)

  在simple模式下只有一个生产者和消费者，当生产者生产消息的速度大于消费者的消费速度时，我们可以添加一个或多个消费者来加快消费速度

可以有多个消费者，但一条消息只能被一个消费者获取 发送到队列中的消息，由服务器平均分配给不同消费者进行消费

发布/订阅模式 \(pub/sub\) 消息被Exchange转到多个队列，一条消息可以被多个消费者获取

路由模式 \(routing\)

```text
* 队列阻塞
```

