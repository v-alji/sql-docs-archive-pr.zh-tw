---
title: 在指令碼元件中記錄 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c29dfffee6cacb39272aef07caa5539555cdd4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597209"
---
# <a name="logging-in-the-script-component"></a><span data-ttu-id="a9f14-102">在指令碼元件中記錄</span><span class="sxs-lookup"><span data-stu-id="a9f14-102">Logging in the Script Component</span></span>
  <span data-ttu-id="a9f14-103">在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 封裝中記錄可以讓您藉由記錄預先定義之事件或使用者定義訊息，記錄關於執行進度、結果和問題的詳細資訊以供稍後分析。</span><span class="sxs-lookup"><span data-stu-id="a9f14-103">Logging in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages lets you save detailed information about execution progress, results, and problems by recording predefined events or user-defined messages for later analysis.</span></span> <span data-ttu-id="a9f14-104">指令碼元件可以使用 `ScriptMain` 類別的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 方法記錄使用者定義的資料。</span><span class="sxs-lookup"><span data-stu-id="a9f14-104">The Script component can use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method of the `ScriptMain` class to log user-defined data.</span></span> <span data-ttu-id="a9f14-105">如果已啟用記錄，而且已在 [設定 SSIS 記錄] 對話方塊的 [詳細資料] 索引標籤上選取 **ScriptComponentLogEntry** 事件以進行記錄，<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 方法的單一呼叫會儲存為資料流程工作設定之所有記錄提供者中的事件資訊。</span><span class="sxs-lookup"><span data-stu-id="a9f14-105">If logging is enabled, and the **ScriptComponentLogEntry** event is selected for logging on the **Details** tab of the **Configure SSIS Logs** dialog box, a single call to the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method stores the event information in all the log providers that have been configured for the data flow task.</span></span>  
  
 <span data-ttu-id="a9f14-106">以下是記錄的一個簡單範例：</span><span class="sxs-lookup"><span data-stu-id="a9f14-106">Here is a simple example of logging:</span></span>  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  <span data-ttu-id="a9f14-107">雖然您可以直接從指令碼元件執行記錄，不過您可能會想要考慮實作事件，而不是記錄。</span><span class="sxs-lookup"><span data-stu-id="a9f14-107">Although you can perform logging directly from your Script component, you may want to consider implementing events rather than logging.</span></span> <span data-ttu-id="a9f14-108">使用事件時，不僅可以啟用事件訊息的記錄，還可用預設或使用者定義的事件處理常式回應事件。</span><span class="sxs-lookup"><span data-stu-id="a9f14-108">When using events, not only can you enable the logging of event messages, but you can respond to the event with default or user-defined event handlers.</span></span>  
  
 <span data-ttu-id="a9f14-109">如需記錄的詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 記錄](../../performance/integration-services-ssis-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="a9f14-109">For more information about logging, see [Integration Services &#40;SSIS&#41; Logging](../../performance/integration-services-ssis-logging.md).</span></span>  
  
<span data-ttu-id="a9f14-110">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="a9f14-110">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a9f14-111">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="a9f14-111">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a9f14-112">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="a9f14-112">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a9f14-113">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="a9f14-113">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f14-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9f14-114">See Also</span></span>  
 [<span data-ttu-id="a9f14-115">Integration Services &#40;SSIS&#41; 記錄</span><span class="sxs-lookup"><span data-stu-id="a9f14-115">Integration Services &#40;SSIS&#41; Logging</span></span>](../../performance/integration-services-ssis-logging.md)  
  
  
