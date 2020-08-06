---
title: rsInternalError - Reporting Services 錯誤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsInternalError
ms.assetid: 52613d52-fc78-4870-93f0-7d393ab9c335
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 85b88519df810f60c580ad2d6eb355dde236d081
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596461"
---
# <a name="rsinternalerror---reporting-services-error"></a><span data-ttu-id="f7ecf-102">rsInternalError - Reporting Services 錯誤</span><span class="sxs-lookup"><span data-stu-id="f7ecf-102">rsInternalError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="f7ecf-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f7ecf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f7ecf-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f7ecf-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="f7ecf-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f7ecf-105">Event ID</span></span>|<span data-ttu-id="f7ecf-106">rsInternalError</span><span class="sxs-lookup"><span data-stu-id="f7ecf-106">rsInternalError</span></span>|  
|<span data-ttu-id="f7ecf-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f7ecf-107">Event Source</span></span>|<span data-ttu-id="f7ecf-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="f7ecf-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="f7ecf-109">元件</span><span class="sxs-lookup"><span data-stu-id="f7ecf-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="f7ecf-110">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f7ecf-110">Message Text</span></span>|<span data-ttu-id="f7ecf-111">報表伺服器發生內部錯誤。</span><span class="sxs-lookup"><span data-stu-id="f7ecf-111">An internal error occurred on the report server.</span></span> <span data-ttu-id="f7ecf-112">請參閱錯誤記錄以取得更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f7ecf-112">See the error log for more details.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f7ecf-113">說明</span><span class="sxs-lookup"><span data-stu-id="f7ecf-113">Explanation</span></span>  
 <span data-ttu-id="f7ecf-114">這是一般錯誤訊息，後面通常會跟隨更具描述性的錯誤訊息，提供更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f7ecf-114">This is a generic error message that is often followed by a more descriptive error that provides more detail.</span></span>  
  
 <span data-ttu-id="f7ecf-115">內部錯誤並不常見。</span><span class="sxs-lookup"><span data-stu-id="f7ecf-115">Internal errors are uncommon.</span></span> <span data-ttu-id="f7ecf-116">如果您收到這個錯誤，可以在報表伺服器追蹤記錄內取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f7ecf-116">If you get this error, more information is available in report server trace logs.</span></span> <span data-ttu-id="f7ecf-117">除此之外，如果您是以本機管理員的身分在發生錯誤的電腦上執行，則可以檢視呼叫堆疊，以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f7ecf-117">In addition, if you are running as local administrator on the same computer on which the error occurs, you can view the call stack for more information.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f7ecf-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f7ecf-118">User Action</span></span>  
 <span data-ttu-id="f7ecf-119">若要判斷此訊息的特定原因，請參閱位於 \Microsoft SQL Server\MSRS12. \<instancename > 的報表伺服器記錄檔。\Reporting Services\logfiles</span><span class="sxs-lookup"><span data-stu-id="f7ecf-119">To determine the specific cause for this message, review the report server log files, which are located at \Microsoft SQL Server\MSRS12.\<instancename >\Reporting Services\LogFiles.</span></span> <span data-ttu-id="f7ecf-120">如需詳細資訊，請參閱 [Reporting Services 記錄檔和來源](../report-server/reporting-services-log-files-and-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="f7ecf-120">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
 <span data-ttu-id="f7ecf-121">若要檢視呼叫堆疊，請以滑鼠右鍵按一下發生錯誤的頁面，然後指向 [檢視來源]  。</span><span class="sxs-lookup"><span data-stu-id="f7ecf-121">To view the call stack, right-click the page on which the error occurs and point to **View Source**.</span></span> <span data-ttu-id="f7ecf-122">檢視呼叫堆疊時，將需要錯誤發生所在之相同電腦上的系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="f7ecf-122">Viewing the call stack requires administrator permissions on the same computer on which the error occurs.</span></span>  
  
 <span data-ttu-id="f7ecf-123">如果沒有其他資訊可用，您可以再次嘗試您的要求。</span><span class="sxs-lookup"><span data-stu-id="f7ecf-123">If there is no additional information available, you can try your request again.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="f7ecf-124">僅供內部使用</span><span class="sxs-lookup"><span data-stu-id="f7ecf-124">Internal-Only</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7ecf-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7ecf-125">See Also</span></span>  
 [<span data-ttu-id="f7ecf-126">啟動與停止報表伺服器服務</span><span class="sxs-lookup"><span data-stu-id="f7ecf-126">Start and Stop the Report Server Service</span></span>](../report-server/start-and-stop-the-report-server-service.md)  
  
  
