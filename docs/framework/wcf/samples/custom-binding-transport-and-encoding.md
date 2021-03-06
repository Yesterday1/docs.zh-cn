---
title: 自定义绑定传输和编码
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: ee15fd37390f8bf4ca3bc287f9a3dbd5f8ebd935
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "45994567"
---
# <a name="custom-binding-transport-and-encoding"></a>自定义绑定传输和编码
自定义绑定由离散绑定元素的有序列表定义。 本示例演示如何使用各种传输和消息编码元素配置自定义绑定。  
  
> [!NOTE]
>  本主题的最后介绍了此示例的设置过程和生成说明。  
  
 此示例基于[自托管](../../../../docs/framework/wcf/samples/self-host.md)，并已修改为三个终结点配置为使用自定义绑定支持 HTTP、 TCP 和 NamedPipe 传输。 并对客户端配置进行了类似修改，将客户端代码更改为能与这三个终结点中的每一个进行通信。  
  
 本示例演示如何配置支持特定传输和消息编码的自定义绑定。 这是通过为 `binding` 元素配置传输和消息编码而实现的。 绑定元素的顺序十分重要中定义自定义绑定，因为每个表示通道堆栈中的层 (请参阅[自定义绑定](../../../../docs/framework/wcf/extending/custom-bindings.md))。 本示例配置三个自定义绑定：使用文本编码的 HTTP 传输、使用文本编码的 TCP 传输和使用二进制编码的 NamedPipe 传输。  
  
 服务配置按如下所示定义自定义绑定：  
  
```xml  
<bindings>  
    <customBinding>  
        <binding name="HttpBinding" >  
            <textMessageEncoding   
                messageVersion="Soap12Addressing10"/>  
            <httpTransport />  
        </binding>  
        <binding name="TcpBinding" >  
            <textMessageEncoding />  
            <tcpTransport />  
        </binding>  
        <binding name="NamedPipeBinding" >  
            <binaryMessageEncoding />  
            <namedPipeTransport />  
        </binding>  
    </customBinding>  
</bindings>  
```  
  
 运行示例时，操作请求和响应将显示在服务和客户端控制台窗口中。 客户端将逐一与三个终结点进行通信，首先访问 HTTP，接着是 TCP，最后为 NamedPipe。 在每个控制台窗口中按 Enter 可以关闭服务和客户端。  
  
 `namedPipeTransport` 绑定不支持计算机到计算机的操作。 它仅用于同一计算机上的通信。 因此，当在跨计算机的方案中运行示例时，应注释掉客户端代码文件中的以下行：  
  
```csharp  
CalculatorClient client = new CalculatorClient("default");  
Console.WriteLine("Communicate with named pipe endpoint.");  
// Call operations.  
DoCalculations(client);  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
```vb  
Dim client As New CalculatorClient("default")  
Console.WriteLine("Communicate with named pipe endpoint.")  
' call operations  
DoCalculations(client)  
'Closing the client gracefully closes the connection and cleans up resources  
client.Close()  
```  
  
> [!NOTE]
>  如果使用 Svcutil.exe 为此示例重新生成配置，请确保在客户端配置中修改终结点名称以与客户端代码匹配。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1.  请确保您具有执行[的 Windows Communication Foundation 示例的一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要生成解决方案的 C#、 c + + 或 Visual Basic.NET 版本，请按照中的说明[生成 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3.  若要在单或跨计算机配置中运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a>请参阅
