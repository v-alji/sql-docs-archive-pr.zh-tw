---
title: 登入指令碼工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- logs [Integration Services], scripts
- Integration Services packages, logs
- Log method
- SSIS Script task, logs
- Script task [Integration Services], logs
- packages [Integration Services], logs
ms.assetid: 2e11fc15-df18-4309-bd2d-fc58aa4b9b7a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 61f7a46088de5df2765d860bd4a43e4872a1be6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700036"
---
# <a name="logging-in-the-script-task"></a><span data-ttu-id="e153a-102">在指令碼工作中記錄</span><span class="sxs-lookup"><span data-stu-id="e153a-102">Logging in the Script Task</span></span>
  <span data-ttu-id="e153a-103">在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 封裝中使用記錄可以讓您藉由記錄預先定義事件或使用者定義訊息，記錄關於執行進度、結果和問題的詳細資訊以供稍後分析。</span><span class="sxs-lookup"><span data-stu-id="e153a-103">The use of logging in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages lets you record detailed information about execution progress, results, and problems by recording predefined events or user-defined messages for later analysis.</span></span> <span data-ttu-id="e153a-104">指令碼工作可以使用 `Dts` 物件的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 方法記錄使用者定義的資料。</span><span class="sxs-lookup"><span data-stu-id="e153a-104">The Script task can use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method of the `Dts` object to log user-defined data.</span></span> <span data-ttu-id="e153a-105">如果記錄已啟用，而且已在 [設定 SSIS 記錄]  對話方塊的 [詳細資料]  索引標籤上選取 **ScriptTaskLogEntry** 事件以進行記錄，<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 方法的呼叫會儲存為工作設定之所有記錄提供者中的事件資訊。</span><span class="sxs-lookup"><span data-stu-id="e153a-105">If logging is enabled, and the **ScriptTaskLogEntry** event is selected for logging on the **Details** tab of the **Configure SSIS Logs** dialog box, a single call to the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method stores the event information in all the log providers configured for the task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e153a-106">雖然您可以直接從指令碼工作執行記錄，不過可能會想考慮實作事件，而不是記錄。</span><span class="sxs-lookup"><span data-stu-id="e153a-106">Although you can perform logging directly from your Script task, you may want to consider implementing events rather than logging.</span></span> <span data-ttu-id="e153a-107">使用事件時，不僅可以啟用事件訊息的記錄，還可用預設或使用者定義的事件處理常式回應事件。</span><span class="sxs-lookup"><span data-stu-id="e153a-107">When using events, not only can you enable the logging of event messages, but you can also respond to the event with default or user-defined event handlers.</span></span>  
  
 <span data-ttu-id="e153a-108">如需記錄的詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 記錄](../../performance/integration-services-ssis-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="e153a-108">For more information about logging, see [Integration Services &#40;SSIS&#41; Logging](../../performance/integration-services-ssis-logging.md).</span></span>  
  
## <a name="logging-example"></a><span data-ttu-id="e153a-109">記錄範例</span><span class="sxs-lookup"><span data-stu-id="e153a-109">Logging Example</span></span>  
 <span data-ttu-id="e153a-110">下列範例示範如何透過記錄代表已處理的資料列數目值，從指令碼工作進行記錄。</span><span class="sxs-lookup"><span data-stu-id="e153a-110">The following example demonstrates logging from the Script task by logging a value that represents the number of rows processed.</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim rowsProcessed As Integer = 100  
    Dim emptyBytes(0) As Byte  
  
    Try  
        Dts.Log("Rows processed: " & rowsProcessed.ToString, _  
            0, _  
            emptyBytes)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
            //  
            int rowsProcessed = 100;  
            byte[] emptyBytes = new byte[0];  
  
            try  
            {  
                Dts.Log("Rows processed: " + rowsProcessed.ToString(), 0, emptyBytes);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                //An error occurred.  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
```  
  
 <span data-ttu-id="e153a-111">}</span><span class="sxs-lookup"><span data-stu-id="e153a-111">}</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="e153a-112">外部資源</span><span class="sxs-lookup"><span data-stu-id="e153a-112">External Resources</span></span>  
  
<span data-ttu-id="e153a-113">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="e153a-113">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e153a-114">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="e153a-114">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e153a-115">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="e153a-115">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e153a-116">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="e153a-116">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e153a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e153a-117">See Also</span></span>  
 [<span data-ttu-id="e153a-118">Integration Services &#40;SSIS&#41; 記錄</span><span class="sxs-lookup"><span data-stu-id="e153a-118">Integration Services &#40;SSIS&#41; Logging</span></span>](../../performance/integration-services-ssis-logging.md)  
  
  
