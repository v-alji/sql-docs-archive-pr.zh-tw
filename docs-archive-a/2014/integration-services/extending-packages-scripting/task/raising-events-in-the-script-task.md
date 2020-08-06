---
title: 在指令碼工作中引發事件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- events [Integration Services], scripts
- warnings [Integration Services]
- SSIS events, scripts
- errors [Integration Services], events
- SSIS Script task, events
- Events property
- Script task [Integration Services], events
ms.assetid: 21ea07d1-e267-4fb1-a6cc-82c95a39beae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e20a276b91e434b6915cfb218eba17c07acd6544
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700030"
---
# <a name="raising-events-in-the-script-task"></a><span data-ttu-id="1d0eb-102">在指令碼工作中引發事件</span><span class="sxs-lookup"><span data-stu-id="1d0eb-102">Raising Events in the Script Task</span></span>
  <span data-ttu-id="1d0eb-103">事件會提供向包含封裝報告錯誤、警告和其他資訊 (例如工作進度或狀態) 的方法。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-103">Events provide a way to report errors, warnings, and other information, such as task progress or status, to the containing package.</span></span> <span data-ttu-id="1d0eb-104">封裝提供管理事件通知的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-104">The package provides event handlers for managing event notifications.</span></span> <span data-ttu-id="1d0eb-105">指令碼工作可以呼叫 `Dts` 物件之 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 屬性上的方法來引發事件。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-105">The Script task can raise events by calling methods on the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property of the `Dts` object.</span></span> <span data-ttu-id="1d0eb-106">如需 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 套件如何處理事件的詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 事件處理常式](../../integration-services-ssis-event-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-106">For more information about how [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages handle events, see [Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md).</span></span>  
  
 <span data-ttu-id="1d0eb-107">事件可以記錄到封裝中啟用的任何記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-107">Events can be logged to any log provider that is enabled in the package.</span></span> <span data-ttu-id="1d0eb-108">記錄提供者會在資料存放區中儲存事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-108">Log providers store information about events in a data store.</span></span> <span data-ttu-id="1d0eb-109">指令碼工作也可以使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 方法將資訊記錄到記錄提供者，而不會引發事件。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-109">The Script task can also use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method to log information to a log provider without raising an event.</span></span> <span data-ttu-id="1d0eb-110">如需如何使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 方法的詳細資訊，請參閱[在指令碼工作中記錄](logging-in-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-110">For more information about how to use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method, see [Logging in the Script Task](logging-in-the-script-task.md).</span></span>  
  
 <span data-ttu-id="1d0eb-111">為了引發事件，指令碼工作會呼叫 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 屬性所公開的其中一個方法。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-111">To raise an event, the Script task calls one of the methods exposed by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property.</span></span> <span data-ttu-id="1d0eb-112">下表列出 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 屬性所公開的方法。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-112">The following table lists the methods exposed by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property.</span></span>  
  
|<span data-ttu-id="1d0eb-113">事件</span><span class="sxs-lookup"><span data-stu-id="1d0eb-113">Event</span></span>|<span data-ttu-id="1d0eb-114">描述</span><span class="sxs-lookup"><span data-stu-id="1d0eb-114">Description</span></span>|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A>|<span data-ttu-id="1d0eb-115">引發封裝中使用者定義的自訂事件。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-115">Raises a user-defined custom event in the package.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A>|<span data-ttu-id="1d0eb-116">通知封裝有關錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-116">Informs the package of an error condition.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireInformation%2A>|<span data-ttu-id="1d0eb-117">提供資訊給使用者。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-117">Provides information to the user.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A>|<span data-ttu-id="1d0eb-118">通知封裝有關工作的進度。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-118">Informs the package of the progress of the task.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireQueryCancel%2A>|<span data-ttu-id="1d0eb-119">傳回一個值，指出此封裝是否需要提前關閉工作。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-119">Returns a value that indicates whether the package needs the task to shut down prematurely.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A>|<span data-ttu-id="1d0eb-120">通知封裝此工作是在需要使用者通知的狀態，但不是錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-120">Informs the package that the task is in a state that warrants user notification, but is not an error condition.</span></span>|  
  
## <a name="events-example"></a><span data-ttu-id="1d0eb-121">事件範例</span><span class="sxs-lookup"><span data-stu-id="1d0eb-121">Events Example</span></span>  
 <span data-ttu-id="1d0eb-122">下列範例會示範如何在指令碼工作內引發事件。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-122">The following example demonstrates how to raise events from within the Script task.</span></span> <span data-ttu-id="1d0eb-123">此範例會使用原生 Windows API 函數來判斷是否可使用網際網路連接。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-123">The example uses a native Windows API function to determine whether an Internet connection is available.</span></span> <span data-ttu-id="1d0eb-124">如果無任何可用的連接，則會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-124">If no connection is available, it raises an error.</span></span> <span data-ttu-id="1d0eb-125">如果正在使用可能不穩定的數據機連接，此範例會引發警告。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-125">If a potentially volatile modem connection is in use, the example raises a warning.</span></span> <span data-ttu-id="1d0eb-126">否則，它會傳回參考用訊息，表示已偵測到網際網路連接。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-126">Otherwise, it returns an informational message that an Internet connection has been detected.</span></span>  
  
```vb  
Private Declare Function InternetGetConnectedState Lib "wininet" _  
    (ByRef dwFlags As Long, ByVal dwReserved As Long) As Long  
  
Private Enum ConnectedStates  
    LAN = &H2  
    Modem = &H1  
    Proxy = &H4  
    Offline = &H20  
    Configured = &H40  
    RasInstalled = &H10  
End Enum  
  
Public Sub Main()  
  
    Dim dwFlags As Long  
    Dim connectedState As Long  
    Dim fireAgain as Boolean  
  
    connectedState = InternetGetConnectedState(dwFlags, 0)  
  
    If connectedState <> 0 Then  
        If (dwFlags And ConnectedStates.Modem) = ConnectedStates.Modem Then  
            Dts.Events.FireWarning(0, "Script Task Example", _  
                "Volatile Internet connection detected.", String.Empty, 0)  
        Else  
            Dts.Events.FireInformation(0, "Script Task Example", _  
                "Internet connection detected.", String.Empty, 0, fireAgain)  
        End If  
    Else  
        ' If not connected to the Internet, raise an error.  
        Dts.Events.FireError(0, "Script Task Example", _  
            "Internet connection not available.", String.Empty, 0)  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
using System.Runtime.InteropServices;  
  
public class ScriptMain  
{  
  
[DllImport("wininet")]  
        private extern static long InternetGetConnectedState(ref long dwFlags, long dwReserved);  
  
        private enum ConnectedStates  
        {  
            LAN = 0x2,  
            Modem = 0x1,  
            Proxy = 0x4,  
            Offline = 0x20,  
            Configured = 0x40,  
            RasInstalled = 0x10  
        };  
  
        public void Main()  
        {  
            //  
            long dwFlags = 0;  
            long connectedState;  
            bool fireAgain = true;  
            int state;  
  
            connectedState = InternetGetConnectedState(ref dwFlags, 0);  
            state = (int)ConnectedStates.Modem;  
            if (connectedState != 0)  
            {  
                if ((dwFlags & state) == state)  
                {  
                    Dts.Events.FireWarning(0, "Script Task Example", "Volatile Internet connection detected.", String.Empty, 0);  
                }  
                else  
                {  
                    Dts.Events.FireInformation(0, "Script Task Example", "Internet connection detected.", String.Empty, 0, ref fireAgain);  
                }  
            }  
            else  
            {  
                // If not connected to the Internet, raise an error.  
                Dts.Events.FireError(0, "Script Task Example", "Internet connection not available.", String.Empty, 0);  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
```  
  
<span data-ttu-id="1d0eb-127">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="1d0eb-127">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1d0eb-128">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="1d0eb-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1d0eb-129">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="1d0eb-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1d0eb-130">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d0eb-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d0eb-131">See Also</span></span>  
 <span data-ttu-id="1d0eb-132">[Integration Services &#40;SSIS&#41; 事件處理常式](../../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="1d0eb-132">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) </span></span>  
 [<span data-ttu-id="1d0eb-133">將事件處理常式新增至套件</span><span class="sxs-lookup"><span data-stu-id="1d0eb-133">Add an Event Handler to a Package</span></span>](../../add-an-event-handler-to-a-package.md)  
  
  
