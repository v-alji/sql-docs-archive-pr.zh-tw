---
title: 以指令碼工作傳送至遠端私用訊息佇列 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], remote private message queues
- Message Queue task [Integration Services]
- Script task [Integration Services], examples
ms.assetid: 636314fd-d099-45cd-8bb4-f730d0a06739
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 308815293dfc41f0a0ac60c21ce7f561a5e7f660
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701293"
---
# <a name="sending-to-a-remote-private-message-queue-with-the-script-task"></a><span data-ttu-id="88016-102">以指令碼工作傳送至遠端私用訊息佇列</span><span class="sxs-lookup"><span data-stu-id="88016-102">Sending to a Remote Private Message Queue with the Script Task</span></span>
  <span data-ttu-id="88016-103">訊息佇列 (又稱為 MSMQ) 能夠讓開發人員容易藉由傳送和接收訊息來與應用程式快速且確實地通訊。</span><span class="sxs-lookup"><span data-stu-id="88016-103">Message Queuing (also known as MSMQ) makes it easy for developers to communicate with application programs quickly and reliably by sending and receiving messages.</span></span> <span data-ttu-id="88016-104">訊息佇列有可能位於本機電腦或是遠端電腦上，而且可能是公用或私用的。</span><span class="sxs-lookup"><span data-stu-id="88016-104">A message queue may be located on the local computer or a remote computer, and may be public or private.</span></span> <span data-ttu-id="88016-105">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中，MSMQ 連接管理員與訊息佇列工作不支援傳送到遠端電腦上的私用佇列。</span><span class="sxs-lookup"><span data-stu-id="88016-105">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the MSMQ connection manager and Message Queue task do not support sending to a private queue on a remote computer.</span></span> <span data-ttu-id="88016-106">不過，透過使用指令碼工作，就可以很輕鬆地將訊息傳送到遠端私用佇列。</span><span class="sxs-lookup"><span data-stu-id="88016-106">However, by using the Script task, it is easy to send a message to a remote private queue.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88016-107">如果您想要建立可更輕鬆地在多個封裝之間重複使用的工作，請考慮使用此指令碼工作範例中的程式碼做為自訂工作的起點。</span><span class="sxs-lookup"><span data-stu-id="88016-107">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="88016-108">如需詳細資訊，請參閱 [開發自訂工作](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="88016-108">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="88016-109">描述</span><span class="sxs-lookup"><span data-stu-id="88016-109">Description</span></span>  
 <span data-ttu-id="88016-110">下列範例使用現有的 MSMQ 連線管理員，加上來自 System.Messaging 命名空間的物件與方法，將包含在封裝變數中的文字傳送到遠端私用訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="88016-110">The following example uses an existing MSMQ connection manager, together with objects and methods from the System.Messaging namespace, to send the text contained in a package variable to a remote private message queue.</span></span> <span data-ttu-id="88016-111">呼叫 MSMQ 連線管理員的 M:Microsoft.SqlServer.Dts.ManagedConnections.MSMQConn.AcquireConnection (System.object) 方法，會傳回其方法完成這項工作的**MessageQueue**物件 `Send` 。</span><span class="sxs-lookup"><span data-stu-id="88016-111">The call to the M:Microsoft.SqlServer.Dts.ManagedConnections.MSMQConn.AcquireConnection(System.Object) method of the MSMQ connection manager returns a **MessageQueue** object whose `Send` method accomplishes this task.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="88016-112">設定此指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="88016-112">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="88016-113">使用預設名稱建立 MSMQ 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="88016-113">Create an MSMQ connection manager with the default name.</span></span> <span data-ttu-id="88016-114">以下列格式設定有效的遠端私用佇列路徑：</span><span class="sxs-lookup"><span data-stu-id="88016-114">Set the path of a valid remote private queue, in the following format:</span></span>  
  
    ```  
    FORMATNAME:DIRECT=OS:<computername>\private$\<queuename>  
    ```  
  
2.  <span data-ttu-id="88016-115">建立 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 類型為**MessageText**的變數 `String` ，以將郵件內文傳遞至腳本。</span><span class="sxs-lookup"><span data-stu-id="88016-115">Create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable named **MessageText** of type `String` to pass the message text into the script.</span></span> <span data-ttu-id="88016-116">輸入預設訊息做為變數值。</span><span class="sxs-lookup"><span data-stu-id="88016-116">Enter a default message as the value of the variable.</span></span>  
  
3.  <span data-ttu-id="88016-117">將指令碼工作加入設計介面並編輯它。</span><span class="sxs-lookup"><span data-stu-id="88016-117">Add a Script Task to the design surface and edit it.</span></span> <span data-ttu-id="88016-118">在 [指令碼工作編輯器] 的 [指令碼] 索引標籤上，將 `MessageText` 變數加入 **ReadOnlyVariables** 屬性，以便在指令碼中使用此變數。</span><span class="sxs-lookup"><span data-stu-id="88016-118">On the **Script** tab of the **Script Task Editor**, add the `MessageText` variable to the **ReadOnlyVariables** property to make the variable available inside the script.</span></span>  
  
4.  <span data-ttu-id="88016-119">按一下 [編輯指令碼]  以開啟 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 指令碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="88016-119">Click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) script editor.</span></span>  
  
5.  <span data-ttu-id="88016-120">在指令碼專案中，加入 `System.Messaging` 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="88016-120">Add a reference in the script project to the `System.Messaging` namespace.</span></span>  
  
6.  <span data-ttu-id="88016-121">以下列小節中的程式碼取代指令碼視窗中的內容。</span><span class="sxs-lookup"><span data-stu-id="88016-121">Replace the contents of the script window with the code in the following section.</span></span>  
  
## <a name="code"></a><span data-ttu-id="88016-122">程式碼</span><span class="sxs-lookup"><span data-stu-id="88016-122">Code</span></span>  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Messaging  
  
Public Class ScriptMain  
  
    Public Sub Main()  
  
        Dim remotePrivateQueue As MessageQueue  
        Dim messageText As String  
  
        remotePrivateQueue = _  
            DirectCast(Dts.Connections("Message Queue Connection Manager").AcquireConnection(Dts.Transaction), _  
            MessageQueue)  
        messageText = DirectCast(Dts.Variables("MessageText").Value, String)  
        remotePrivateQueue.Send(messageText)  
  
        Dts.TaskResult = ScriptResults.Success  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Messaging;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
  
            MessageQueue remotePrivateQueue = new MessageQueue();  
            string messageText;  
  
            remotePrivateQueue = (MessageQueue)(Dts.Connections["Message Queue Connection Manager"].AcquireConnection(Dts.Transaction) as MessageQueue);  
            messageText = (string)(Dts.Variables["MessageText"].Value);  
            remotePrivateQueue.Send(messageText);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
```  
  
<span data-ttu-id="88016-123">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="88016-123">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="88016-124">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="88016-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="88016-125">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="88016-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="88016-126">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="88016-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88016-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88016-127">See Also</span></span>  
 [<span data-ttu-id="88016-128">訊息佇列工作</span><span class="sxs-lookup"><span data-stu-id="88016-128">Message Queue Task</span></span>](../control-flow/message-queue-task.md)  
  
  
