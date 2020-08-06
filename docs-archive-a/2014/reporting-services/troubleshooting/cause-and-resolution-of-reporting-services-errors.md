---
title: Reporting Services 錯誤的原因和解決方案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- messages [Reporting Services]
- errors [Reporting Services]
- troubleshooting [Reporting Services], errors
ms.assetid: 3db0fef3-37f8-40d0-acc7-1928760dc0e9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fa98b9f760485b80f4fa4ac74f3b8008dc3bbec3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700651"
---
# <a name="cause-and-resolution-of-reporting-services-errors"></a><span data-ttu-id="4df04-102">Reporting Services 錯誤的原因和解決方案</span><span class="sxs-lookup"><span data-stu-id="4df04-102">Cause and Resolution of Reporting Services Errors</span></span>
  <span data-ttu-id="4df04-103">本主題包含數個與 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]相關之錯誤的原因和解決方案資訊。</span><span class="sxs-lookup"><span data-stu-id="4df04-103">This topic contains cause and resolution information for a number of errors related to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="4df04-104">本節中的錯誤訊息主題提供錯誤訊息的說明、可能的原因，以及您可以採取哪些動作以更正問題。</span><span class="sxs-lookup"><span data-stu-id="4df04-104">The error message topics in this section provide an explanation of the error message, possible causes, and any actions you can take to correct the problem.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4df04-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="4df04-105">In This Section</span></span>  
  
|<span data-ttu-id="4df04-106">錯誤</span><span class="sxs-lookup"><span data-stu-id="4df04-106">Error</span></span>|<span data-ttu-id="4df04-107">訊息</span><span class="sxs-lookup"><span data-stu-id="4df04-107">Message</span></span>|  
|-----------|-------------|  
|[<span data-ttu-id="4df04-108">rsAccessedDenied - Reporting Services 錯誤</span><span class="sxs-lookup"><span data-stu-id="4df04-108">rsAccessedDenied - Reporting Services Error</span></span>](rsaccesseddenied-reporting-services-error.md)|<span data-ttu-id="4df04-109">授與使用者 'mydomain\myAccount' 的權限不足，無法執行此作業。</span><span class="sxs-lookup"><span data-stu-id="4df04-109">The permissions granted to user 'mydomain\myAccount' are insufficient for performing this operation.</span></span> <span data-ttu-id="4df04-110">(rsAccessDenied) (ReportingServicesLibrary)。</span><span class="sxs-lookup"><span data-stu-id="4df04-110">(rsAccessDenied) (ReportingServicesLibrary).</span></span>|  
|[<span data-ttu-id="4df04-111">rsInternalError - Reporting Services 錯誤</span><span class="sxs-lookup"><span data-stu-id="4df04-111">rsInternalError - Reporting Services Error</span></span>](rsinternalerror-reporting-services-error.md)|<span data-ttu-id="4df04-112">報表伺服器發生內部錯誤。</span><span class="sxs-lookup"><span data-stu-id="4df04-112">An internal error occurred on the report server.</span></span> <span data-ttu-id="4df04-113">請參閱錯誤記錄以取得更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4df04-113">See the error log for more details.</span></span>|  
|[<span data-ttu-id="4df04-114">rsModelGenerationError - Reporting Services 錯誤</span><span class="sxs-lookup"><span data-stu-id="4df04-114">rsModelGenerationError - Reporting Services Error</span></span>](rsmodelgenerationerror-reporting-services-error.md)|<span data-ttu-id="4df04-115">產生模型時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4df04-115">An error occurred while generating model.</span></span> <span data-ttu-id="4df04-116">(rsModelGenerationError) (ReportingServicesLibrary) %1。</span><span class="sxs-lookup"><span data-stu-id="4df04-116">(rsModelGenerationError) (ReportingServicesLibrary) %1.</span></span>|  
|[<span data-ttu-id="4df04-117">rsProcessingError - Reporting Services 錯誤</span><span class="sxs-lookup"><span data-stu-id="4df04-117">rsProcessingError - Reporting Services Error</span></span>](rsprocessingerror-reporting-services-error.md)|<span data-ttu-id="4df04-118">報表處理時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4df04-118">Errors have occurred in report processing.</span></span>|  
|[<span data-ttu-id="4df04-119">rsServerConfigurationError - Reporting Services 錯誤</span><span class="sxs-lookup"><span data-stu-id="4df04-119">rsServerConfigurationError - Reporting Services Error</span></span>](rsserverconfigurationerror-reporting-services-error.md)|<span data-ttu-id="4df04-120">報表伺服器發生組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="4df04-120">The report server has encountered a configuration error.</span></span>|  
|[<span data-ttu-id="4df04-121">rrRenderingError - Reporting Services 錯誤</span><span class="sxs-lookup"><span data-stu-id="4df04-121">rrRenderingError - Reporting Services Error</span></span>](rrrenderingerror-reporting-services-error.md)|<span data-ttu-id="4df04-122">轉譯報表期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4df04-122">An error occurred during rendering of the report.</span></span> <span data-ttu-id="4df04-123">(rrRenderingError) %1。</span><span class="sxs-lookup"><span data-stu-id="4df04-123">(rrRenderingError) %1.</span></span>|  
|[<span data-ttu-id="4df04-124">報表伺服器 Windows 服務 &#40;MSSQLServer&#41; 107</span><span class="sxs-lookup"><span data-stu-id="4df04-124">Report Server Windows Service &#40;MSSQLServer&#41; 107</span></span>](../../relational-databases/errors-events/mssqlserver-107-database-engine-error.md)|<span data-ttu-id="4df04-125">報表伺服器 Windows 服務 (MSSQLSERVER) 無法連接到報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="4df04-125">Report Server Windows service (MSSQLSERVER) cannot connect to the report server database.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4df04-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4df04-126">See Also</span></span>  
 <span data-ttu-id="4df04-127">[Reporting Services 記錄檔和來源](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="4df04-127">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 [<span data-ttu-id="4df04-128">錯誤和事件參考 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4df04-128">Errors and Events Reference &#40;Reporting Services&#41;</span></span>](errors-and-events-reference-reporting-services.md)  
  
  
