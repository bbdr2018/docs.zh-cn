---
title: "&lt;netPeerTcpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "netPeerBinding 元素"
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
caps.latest.revision: 20
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 20
---
# &lt;netPeerTcpBinding&gt;
为特定于对等通道的 TCP 消息定义绑定。  
  
## 语法  
  
```  
  
<netPeerBinding>  
    <binding name="string"  
         closeTimeout="TimeSpan"  
         openTimeout="TimeSpan"   
         receiveTimeout="TimeSpan"  
         sendTimeout="TimeSpan"  
         listenIPAddress="String"  
          maxBufferPoolSize="integer"  
         maxReceiveMessageSize="Integer"   
         port="Integer"  
         <security mode="None/Transport/Message/TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|closeTimeout|一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。  此值应大于或等于 <xref:System.TimeSpan.Zero>。  默认值为 00:01:00。|  
|listenIPAddress|一个字符串，指定对等节点将在其上侦听 TCP 消息的 IP 地址。  默认值为 `null`。|  
|maxBufferPoolSize|一个整数，指定此绑定的最大缓冲池大小。  默认值为 524,288 字节 \(512 \* 1024\)。  Windows Communication Foundation \(WCF\) 的许多部件使用缓冲区。  每次使用缓冲区时，创建和销毁它们都将占用大量资源，而缓冲区的垃圾回收过程也是如此。  利用缓冲池，可以从缓冲池中获得缓冲区，使用缓冲区，然后在完成工作后将其返回给缓冲池。  这样就避免了创建和销毁缓冲区的系统开销。|  
|maxReceivedMessageSize|一个正整数，指定采用此绑定配置的通道上可以接收的最大消息大小（字节），包括消息头。  如果消息超出此限制，则发送方将收到 SOAP 错误。  接收方将删除该消息，并在跟踪日志中创建事件项。  默认值为 65536。|  
|name|一个包含绑定的配置名称的字符串。  因为此值用作绑定的标识，所以它应该是唯一的。  从 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 开始，不要求绑定和行为具有名称。  有关默认配置以及无名称绑定和行为的更多信息，请参见[简化配置](../../../../../docs/framework/wcf/simplified-configuration.md)和 [WCF 服务的简化配置](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。|  
|openTimeout|一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。  此值应大于或等于 <xref:System.TimeSpan.Zero>。  默认值为 00:01:00。|  
|端口|一个整数，指定此绑定将用于处理对等通道 TCP 消息的网络接口端口。  该值必须介于 <xref:System.Net.IPEndPoint.MinPort> 和 <xref:System.Net.IPEndPoint.MaxPort> 之间。  默认值为 0。|  
|receiveTimeout|一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。  此值应大于或等于 <xref:System.TimeSpan.Zero>。  默认值为 00:10:00。|  
|sendTimeout|一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。  此值应大于或等于 <xref:System.TimeSpan.Zero>。  默认值为 00:01:00。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。  此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。|  
|[\<resolver\>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|指定一个对等解析程序，此绑定将使用该解析程序将对等网格 ID 解析为对等网格中节点的终结点 IP 地址。|  
|[\<安全性\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|定义消息的安全设置。  此元素的类型为 <xref:System.ServiceModel.Configuration.PeerSecurityElement>。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[\<绑定\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|此元素包含标准绑定和自定义绑定的集合。|  
  
## 备注  
 此绑定为使用 TCP 上的对等传输创建对等应用程序或多方应用程序提供支持。  每个对等节点均可承载使用此绑定类型定义的多个对等通道。  
  
## 示例  
 下面的示例演示如何使用 NetPeerTcpBinding 绑定，该绑定使用对等通道提供多方通信。  有关使用此绑定的详细方案，请参见[Net Peer TCP](http://msdn.microsoft.com/zh-cn/31f4db66-edb2-40a6-b92a-14098e92acae)。  
  
```  
<configuration>  
<system.ServiceModel>  
<bindings>  
<netPeerBinding>  
    <binding   
         closeTimeout="00:00:10"  
         openTimeout="00:00:20"   
         receiveTimeout="00:00:30"  
         sendTimeout="00:00:40"  
         maxBufferSize="1001"  
         maxConnections="123"   
         maxReceiveMessageSize="1000">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00"  
            enabled="true" />  
        <security mode="TransportWithMessageCredential">  
            <message clientCredentialType="CardSpace" />  
        </security>  
    </binding>  
</netPeerBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## 请参阅  
 <xref:System.ServiceModel.NetPeerTcpBinding>   
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>   
 [绑定](../../../../../docs/framework/wcf/bindings.md)   
 [配置系统提供的绑定](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-cn/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<绑定\>](../../../../../docs/framework/misc/binding.md)   
 [Net Peer TCP](http://msdn.microsoft.com/zh-cn/31f4db66-edb2-40a6-b92a-14098e92acae)   
 [对等网络](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)