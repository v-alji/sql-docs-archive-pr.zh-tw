---
title: 活頁簿中的資料連接路徑指向本機磁碟機上的檔案或者是無效的 URI。 下列連接無法重新整理： PowerPivot 資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: bd22e41a-0931-4d32-888a-633a3046fc5e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3349af08290e2ff659db1441d849b2afef51e95b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595311"
---
# <a name="the-data-connection-path-in-the-workbook-points-to-a-file-on-the-local-drive-or-is-an-invalid-uri-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="bd4c7-103">活頁簿中的資料連接路徑指向本機磁碟機上的檔案或者是無效的 URI。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-103">The data connection path in the workbook points to a file on the local drive or is an invalid URI.</span></span> <span data-ttu-id="bd4c7-104">下列連接無法重新整理：PowerPivot 資料</span><span class="sxs-lookup"><span data-stu-id="bd4c7-104">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="bd4c7-105">如果是包含 PowerPivot 資料的 Excel 活頁簿，Excel Services 會在無法連接到內嵌資料來源時傳回這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-105">For Excel workbooks that contain PowerPivot data, Excel Services returns this error if it cannot connect to embedded data sources.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bd4c7-106">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bd4c7-106">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bd4c7-107">適用於</span><span class="sxs-lookup"><span data-stu-id="bd4c7-107">Applies to</span></span>|<span data-ttu-id="bd4c7-108">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="bd4c7-108">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="bd4c7-109">產品版本</span><span class="sxs-lookup"><span data-stu-id="bd4c7-109">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="bd4c7-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd4c7-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="bd4c7-111">原因</span><span class="sxs-lookup"><span data-stu-id="bd4c7-111">Cause</span></span>|<span data-ttu-id="bd4c7-112">Excel Services 設定為只允許來自信任資料連線庫中 .odc 檔案的資料連接。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-112">Excel Services is configured to only allow data connections from .odc files that are in a trusted data connection library.</span></span>|  
|<span data-ttu-id="bd4c7-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bd4c7-113">Message Text</span></span>|<span data-ttu-id="bd4c7-114">活頁簿中的資料連接路徑指向本機磁碟機上的檔案或者是無效的 URI。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-114">The data connection path in the workbook points to a file on the local drive or is an invalid URI.</span></span> <span data-ttu-id="bd4c7-115">下列連接無法重新整理：PowerPivot 資料</span><span class="sxs-lookup"><span data-stu-id="bd4c7-115">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bd4c7-116">說明</span><span class="sxs-lookup"><span data-stu-id="bd4c7-116">Explanation</span></span>  
 <span data-ttu-id="bd4c7-117">PowerPivot 活頁簿包含內嵌資料連接。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-117">PowerPivot workbooks contain embedded data connections.</span></span> <span data-ttu-id="bd4c7-118">若要透過交叉分析篩選器和篩選器來支援活頁簿互動，Excel Services 必須設定為可允許透過內嵌連接資訊來進行外部資料存取。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-118">To support workbook interaction through slicers and filters, Excel Services must be configured to allow external data access through embedded connection information.</span></span> <span data-ttu-id="bd4c7-119">擷取伺服陣列中 PowerPivot 伺服器上所載入的 PowerPivot 資料時，需要外部資料存取。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-119">External data access is required for retrieving PowerPivot data that is loaded on PowerPivot servers in the farm.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bd4c7-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bd4c7-120">User Action</span></span>  
 <span data-ttu-id="bd4c7-121">變更組態設定來允許內嵌資料來源連線。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-121">Change the configuration settings to allow embedded data source connections.</span></span>  
  
1.  <span data-ttu-id="bd4c7-122">在 [管理中心] 的 [應用程式管理] 中，按一下 **[管理服務應用程式]** 。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-122">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="bd4c7-123">按一下 [Excel Services 應用程式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-123">Click **Excel Services Application**.</span></span>  
  
3.  <span data-ttu-id="bd4c7-124">按一下 [信任的檔案位置]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-124">Click **Trusted File Location**.</span></span>  
  
4.  <span data-ttu-id="bd4c7-125">按一下 [http://]\*\*\*\* 或是您想要設定的位置。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-125">Click **http://** or the location you want to configure.</span></span>  
  
5.  <span data-ttu-id="bd4c7-126">在 [外部資料] 中，於 [允許外部資料] 內按一下 [信任的資料連線庫與內嵌連線]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-126">In External Data, in Allow External Data, click **Trusted data connection libraries and embedded**.</span></span>  
  
6.  <span data-ttu-id="bd4c7-127">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-127">Click **OK**.</span></span>  
  
 <span data-ttu-id="bd4c7-128">或者，您可以針對包含 PowerPivot 活頁簿的網站建立新的信任位置，然後只針對該網站修改組態設定。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-128">Alternatively, you can create a new trusted location for sites that contain PowerPivot workbooks, and then modify the configuration settings for just that site.</span></span> <span data-ttu-id="bd4c7-129">如需相關資訊，請參閱 [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="bd4c7-129">For more information, see [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).</span></span>  
  
  
