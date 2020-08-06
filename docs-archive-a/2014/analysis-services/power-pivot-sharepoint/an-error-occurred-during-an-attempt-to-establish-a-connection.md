---
title: 嘗試建立與外部資料來源之間的連接時，發生錯誤。 下列連接無法重新整理： PowerPivot 資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1b951da1-f62d-43d2-b40b-270a4a9ab92c
author: minewiskan
ms.author: owend
ms.openlocfilehash: eb4329440b69d1bdfdbb96fbcc3926fa000d8877
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700321"
---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection-to-the-external-data-source-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="8cc73-103">嘗試建立與外部資料來源之間的連接時，發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8cc73-103">An error occurred during an attempt to establish a connection to the external data source.</span></span> <span data-ttu-id="8cc73-104">下列連接無法重新整理：PowerPivot 資料</span><span class="sxs-lookup"><span data-stu-id="8cc73-104">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="8cc73-105">如果您在沒有安裝 PowerPivot for SharePoint 的伺服器上查詢 PowerPivot 資料，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="8cc73-105">This error occurs if you query PowerPivot data on a server that does not have PowerPivot for SharePoint installed.</span></span> <span data-ttu-id="8cc73-106">如果 SQL Server Analysis Services (PowerPivot) 服務停止，或者您嘗試從舊版檢視 PowerPivot 資料，也會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="8cc73-106">It also occurs if the SQL Server Analysis Services (PowerPivot) service is stopped, or if you are attempting to view PowerPivot data from an earlier version.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8cc73-107">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8cc73-107">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8cc73-108">適用於</span><span class="sxs-lookup"><span data-stu-id="8cc73-108">Applies to</span></span>|<span data-ttu-id="8cc73-109">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="8cc73-109">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="8cc73-110">產品版本</span><span class="sxs-lookup"><span data-stu-id="8cc73-110">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="8cc73-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cc73-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="8cc73-112">原因</span><span class="sxs-lookup"><span data-stu-id="8cc73-112">Cause</span></span>|<span data-ttu-id="8cc73-113">資料連接失敗。</span><span class="sxs-lookup"><span data-stu-id="8cc73-113">The data connection failed.</span></span>|  
|<span data-ttu-id="8cc73-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8cc73-114">Message Text</span></span>|<span data-ttu-id="8cc73-115">嘗試建立與外部資料來源之間的連接時，發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8cc73-115">An error occurred during an attempt to establish a connection to the external data source.</span></span> <span data-ttu-id="8cc73-116">下列連接無法重新整理：PowerPivot 資料</span><span class="sxs-lookup"><span data-stu-id="8cc73-116">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8cc73-117">說明</span><span class="sxs-lookup"><span data-stu-id="8cc73-117">Explanation</span></span>  
 <span data-ttu-id="8cc73-118">當您查詢發行到 SharePoint 之 Excel 活頁簿中的 PowerPivot 資料，而 SharePoint 環境中沒有 PowerPivot for SharePoint 伺服器或者 SQL Server Analysis Services (PowerPivot) 服務已停止時，Excel Services 即會傳回此錯誤。</span><span class="sxs-lookup"><span data-stu-id="8cc73-118">Excel Services returns this error when you query PowerPivot data in an Excel workbook that is published to SharePoint, and the SharePoint environment does not have a PowerPivot for SharePoint server, or the SQL Server Analysis Services (PowerPivot) service is stopped.</span></span>  
  
 <span data-ttu-id="8cc73-119">如果查詢引擎無法使用，您在配量或篩選 PowerPivot 資料時將會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="8cc73-119">The error occurs when you slice or filter PowerPivot data when the query engine is not available.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8cc73-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8cc73-120">User Action</span></span>  
 <span data-ttu-id="8cc73-121">安裝 PowerPivot for SharePoint 或是將 PowerPivot 活頁簿移到已安裝 PowerPivot for SharePoint 的 SharePoint 環境。</span><span class="sxs-lookup"><span data-stu-id="8cc73-121">Install PowerPivot for SharePoint or move the PowerPivot workbook to a SharePoint environment that has PowerPivot for SharePoint installed.</span></span> <span data-ttu-id="8cc73-122">如需詳細資訊，請參閱＜ [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8cc73-122">For more information, see [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md).</span></span>  
  
 <span data-ttu-id="8cc73-123">如果安裝了該軟體，請確認 SQL Server Analysis Services (PowerPivot) 執行個體正在執行。</span><span class="sxs-lookup"><span data-stu-id="8cc73-123">If the software is installed, verify that the SQL Server Analysis Services (PowerPivot) instance is running.</span></span> <span data-ttu-id="8cc73-124">核取 [管理中心] 內的 [管理伺服器上的服務]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cc73-124">Check **Manage services on server** in Central Administration.</span></span> <span data-ttu-id="8cc73-125">此外，請檢查 [系統管理工具] 中的 [服務] 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="8cc73-125">Also check the Services console application in Administrative Tools.</span></span>  
  
 <span data-ttu-id="8cc73-126">若是在 SQL Server 2008 R2 版 PowerPivot for Excel 中建立的 PowerPivot 活頁簿，您必須安裝 SQL Server 2008 R2 版的 Analysis Services OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="8cc73-126">For PowerPivot workbooks that were created in a SQL Server 2008 R2 version of PowerPivot for Excel, you must install the SQL Server 2008 R2 version of the Analysis Services OLE DB provider.</span></span> <span data-ttu-id="8cc73-127">如果安裝了此提供者，但沒有註冊 Microsoft.AnalysisServices.ChannelTransport.dll 檔案，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="8cc73-127">This error will occur if you installed the provider, but did not register the Microsoft.AnalysisServices.ChannelTransport.dll file.</span></span> <span data-ttu-id="8cc73-128">如需檔案註冊的詳細資訊，請參閱 [在 SharePoint 伺服器上安裝 Analysis Services OLE DB 提供者](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="8cc73-128">For more information about file registration, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc73-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cc73-129">See Also</span></span>  
 [<span data-ttu-id="8cc73-130">資料連接是使用 Windows 驗證，而且無法委派使用者認證。下列連接無法重新整理：PowerPivot 資料</span><span class="sxs-lookup"><span data-stu-id="8cc73-130">The data connection uses Windows Authentication and user credentials could not be delegated. The following connections failed to refresh: PowerPivot Data</span></span>](the-data-connection-user-could-not-be-delegated.md)  
  
  
