---
title: rsServerConfigurationError - Reporting Services 錯誤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsServerConfigurationError
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02f8a18c42715d1f118920614eb425820130dacb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706149"
---
# <a name="rsserverconfigurationerror---reporting-services-error"></a><span data-ttu-id="55858-102">rsServerConfigurationError - Reporting Services 錯誤</span><span class="sxs-lookup"><span data-stu-id="55858-102">rsServerConfigurationError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="55858-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="55858-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="55858-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="55858-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="55858-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="55858-105">Event ID</span></span>|<span data-ttu-id="55858-106">rsServerConfiguration</span><span class="sxs-lookup"><span data-stu-id="55858-106">rsServerConfiguration</span></span>|  
|<span data-ttu-id="55858-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="55858-107">Event Source</span></span>|<span data-ttu-id="55858-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="55858-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="55858-109">元件</span><span class="sxs-lookup"><span data-stu-id="55858-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="55858-110">訊息文字</span><span class="sxs-lookup"><span data-stu-id="55858-110">Message Text</span></span>|<span data-ttu-id="55858-111">報表伺服器發生組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="55858-111">The report server has encountered a configuration error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="55858-112">說明</span><span class="sxs-lookup"><span data-stu-id="55858-112">Explanation</span></span>  
 <span data-ttu-id="55858-113">這是一般用途錯誤，當報表伺服器或報表撰寫工具具有無效的組態設定時，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="55858-113">This is a general purpose error that occurs when either the report server or a report authoring tool has invalid configuration settings.</span></span> <span data-ttu-id="55858-114">此錯誤通常伴隨著陳述錯誤之實際原因的第二則訊息。</span><span class="sxs-lookup"><span data-stu-id="55858-114">The error is usually accompanied by a second message that states the actual cause of the error.</span></span>  
  
 <span data-ttu-id="55858-115">下列清單摘要列出可能的原因：</span><span class="sxs-lookup"><span data-stu-id="55858-115">The following list summarizes possible causes:</span></span>  
  
-   <span data-ttu-id="55858-116">找不到或無法讀取 RSReportServer.config 或 RSReportDesigner.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="55858-116">The RSReportServer.config or RSReportDesigner.config file cannot be found or read.</span></span>  
  
-   <span data-ttu-id="55858-117">組態檔中的 XML 元素遺失或無效。</span><span class="sxs-lookup"><span data-stu-id="55858-117">XML elements in either configuration file are missing or invalid.</span></span>  
  
-   <span data-ttu-id="55858-118">一或多個 XML 元素的值遺失或無效。</span><span class="sxs-lookup"><span data-stu-id="55858-118">Values for one or more XML elements are missing or invalid.</span></span>  
  
-   <span data-ttu-id="55858-119">登錄設定無效。</span><span class="sxs-lookup"><span data-stu-id="55858-119">Registry settings are invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="55858-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="55858-120">User Action</span></span>  
 <span data-ttu-id="55858-121">如果當您在手動編輯組態檔之後開始發生這個錯誤，請移除您的變更並輸入之前的值，或者如果您有備份則還原舊版。</span><span class="sxs-lookup"><span data-stu-id="55858-121">If this error began to occur after you manually edited a configuration file, remove your changes and enter the previous value, or restore a previous version if you have a backup.</span></span>  
  
 <span data-ttu-id="55858-122">若要查看錯誤伴隨的其他錯誤訊息資訊 `rsServerConfiguration` ，請參閱報表伺服器追蹤記錄檔，這些檔案位於 \MICROSOFT SQL Server\MSRS12. \<instancename >\Reporting Services\logfiles</span><span class="sxs-lookup"><span data-stu-id="55858-122">To review additional error message information that accompanies the `rsServerConfiguration` error, review the report server trace log files, which are located at \Microsoft SQL Server\MSRS12.\<instancename >\Reporting Services\LogFiles.</span></span> <span data-ttu-id="55858-123">如需詳細資訊，請參閱 [Reporting Services 記錄檔和來源](../report-server/reporting-services-log-files-and-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="55858-123">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="55858-124">僅供內部使用</span><span class="sxs-lookup"><span data-stu-id="55858-124">Internal-Only</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55858-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55858-125">See Also</span></span>  
 <span data-ttu-id="55858-126">[Reporting Services 組態檔](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="55858-126">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="55858-127">修改 Reporting Services 設定檔 &#40;RSreportserver.config&#41;</span><span class="sxs-lookup"><span data-stu-id="55858-127">Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;</span></span>](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
  
