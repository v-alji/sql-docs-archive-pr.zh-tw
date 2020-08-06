---
title: 從指令碼工作傳回結果 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], status information
- ExecutionValue property
- status information [Integration Services]
- TaskResult property
- SSIS Script task, status information
ms.assetid: ac06805b-c2db-44bd-af5c-5a0debe36dd7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bef3e93644377f715b5ad24e0a53df053197a03a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700018"
---
# <a name="returning-results-from-the-script-task"></a><span data-ttu-id="2673b-102">從指令碼工作中傳回結果</span><span class="sxs-lookup"><span data-stu-id="2673b-102">Returning Results from the Script Task</span></span>
  <span data-ttu-id="2673b-103">指令碼工作使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> 與選擇性的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 屬性，將狀態資訊傳回 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 執行階段，可用以判斷在完成指令碼工作之後的工作流程路徑。</span><span class="sxs-lookup"><span data-stu-id="2673b-103">The Script task uses the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> and the optional <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> properties to return status information to the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime that can be used to determine the path of the workflow after the Script task has finished.</span></span>  
  
## <a name="taskresult"></a><span data-ttu-id="2673b-104">TaskResult</span><span class="sxs-lookup"><span data-stu-id="2673b-104">TaskResult</span></span>  
 <span data-ttu-id="2673b-105"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> 屬性會報告工作是否已成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="2673b-105">The <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> property reports whether the task succeeded or failed.</span></span> <span data-ttu-id="2673b-106">例如：</span><span class="sxs-lookup"><span data-stu-id="2673b-106">For example:</span></span>  
  
 `Dts.TaskResult = ScriptResults.Success`  
  
## <a name="executionvalue"></a><span data-ttu-id="2673b-107">ExecutionValue</span><span class="sxs-lookup"><span data-stu-id="2673b-107">ExecutionValue</span></span>  
 <span data-ttu-id="2673b-108"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 屬性會選擇性地傳回使用者定義的物件，以量化或提供有關指令碼工作的成功或失敗的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2673b-108">The <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> property optionally returns a user-defined object that quantifies or provides more information about the success or failure of the Script task.</span></span> <span data-ttu-id="2673b-109">例如，FTP 工作使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 屬性傳回傳送的檔案數目。</span><span class="sxs-lookup"><span data-stu-id="2673b-109">For example, the FTP task uses the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> property to return the number of files transferred.</span></span> <span data-ttu-id="2673b-110">執行 SQL 工作會傳回工作影響的資料列數。</span><span class="sxs-lookup"><span data-stu-id="2673b-110">The Execute SQL task returns the number of rows affected by the task.</span></span> <span data-ttu-id="2673b-111"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 也可用以判斷工作流程的路徑。</span><span class="sxs-lookup"><span data-stu-id="2673b-111">The <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> can also be used to determine the path of the workflow.</span></span> <span data-ttu-id="2673b-112">例如：</span><span class="sxs-lookup"><span data-stu-id="2673b-112">For example:</span></span>  
  
 `Dim rowsAffected as Integer`  
  
 `...`  
  
 `rowsAffected = 1000`  
  
 `Dts.ExecutionValue = rowsAffected`  
  
<span data-ttu-id="2673b-113">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="2673b-113">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="2673b-114">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="2673b-114">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="2673b-115">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="2673b-115">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="2673b-116">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="2673b-116">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
