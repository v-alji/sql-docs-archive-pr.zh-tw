---
title: 快取頁面、共用資料集 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eac372e9-d2a1-48a8-bbe5-09d101df16ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62d899964911a6f2d35e59d49d925ff80013af42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595812"
---
# <a name="caching-page-shared-datasets-report-manager"></a><span data-ttu-id="efab9-102">快取頁面、共用資料集 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="efab9-102">Caching Page, Shared Datasets (Report Manager)</span></span>
  <span data-ttu-id="efab9-103">使用 [快取屬性] 頁面，即可設定共用資料集的快取選項。</span><span class="sxs-lookup"><span data-stu-id="efab9-103">Use the Caching properties page to set the cache options for a shared dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="efab9-104">並非所有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]版本都提供此功能。</span><span class="sxs-lookup"><span data-stu-id="efab9-104">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="efab9-105">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="efab9-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="efab9-106">導覽</span><span class="sxs-lookup"><span data-stu-id="efab9-106">Navigation</span></span>  
 <span data-ttu-id="efab9-107">您可以使用下列程序，在使用者介面中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="efab9-107">Use the following procedure to navigate to this location in the user interface.</span></span>  
  
### <a name="to-open-the-caching-properties-page-for-a-shared-dataset"></a><span data-ttu-id="efab9-108">開啟共用資料集的快取屬性頁面</span><span class="sxs-lookup"><span data-stu-id="efab9-108">To open the Caching properties page for a shared dataset</span></span>  
  
1.  <span data-ttu-id="efab9-109">開啟報表管理員，然後找出您想要設定共用資料集屬性的報表。</span><span class="sxs-lookup"><span data-stu-id="efab9-109">Open Report Manager, and locate the report for which you want to configure shared dataset properties.</span></span>  
  
2.  <span data-ttu-id="efab9-110">指向共用資料集，然後按下拉式箭號。</span><span class="sxs-lookup"><span data-stu-id="efab9-110">Point to the shared dataset, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="efab9-111">在下拉式清單中，按一下 **[管理]**，</span><span class="sxs-lookup"><span data-stu-id="efab9-111">In the drop-down list, click **Manage**.</span></span> <span data-ttu-id="efab9-112">報表的 [一般屬性] 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="efab9-112">The General properties page for the report opens.</span></span>  
  
4.  <span data-ttu-id="efab9-113">按一下 **[快取]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="efab9-113">Click the **Caching** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="efab9-114">選項</span><span class="sxs-lookup"><span data-stu-id="efab9-114">Options</span></span>  
 <span data-ttu-id="efab9-115">**快取共用資料集**</span><span class="sxs-lookup"><span data-stu-id="efab9-115">**Cache shared dataset**</span></span>  
 <span data-ttu-id="efab9-116">當使用者第一次開啟使用此共用資料集的報表時，會在快取中放置資料的暫存副本。</span><span class="sxs-lookup"><span data-stu-id="efab9-116">Places a temporary copy of the data in a cache when a user first opens a report that uses this shared dataset.</span></span> <span data-ttu-id="efab9-117">在快取期間內執行此報表的後續使用者都會收到快取的資料副本。</span><span class="sxs-lookup"><span data-stu-id="efab9-117">Subsequent users who run the report within the caching period receive the cached copy of the data.</span></span> <span data-ttu-id="efab9-118">快取通常會改善效能，因為資料是從快取傳回，而非再次執行資料集查詢。</span><span class="sxs-lookup"><span data-stu-id="efab9-118">Caching usually improves performance because the data is returned from the cache instead of running the dataset query again.</span></span>  
  
 <span data-ttu-id="efab9-119">**快取於這個分鐘數後過期**</span><span class="sxs-lookup"><span data-stu-id="efab9-119">**Expire the cache after a number of minutes**</span></span>  
 <span data-ttu-id="efab9-120">指定要儲存快取之資料副本的分鐘數。</span><span class="sxs-lookup"><span data-stu-id="efab9-120">Specify the number of minutes to save the cached copy of the data.</span></span> <span data-ttu-id="efab9-121">一旦暫存副本過期，就不會再從快取中傳回資料。</span><span class="sxs-lookup"><span data-stu-id="efab9-121">As soon as a temporary copy expires, the data is no longer returned from the cache.</span></span> <span data-ttu-id="efab9-122">使用者下次開啟使用此共用資料集的報表時，會執行資料集查詢，然後報表伺服器會將重新整理過的資料副本放回快取中。</span><span class="sxs-lookup"><span data-stu-id="efab9-122">The next time a user opens a report that uses this shared dataset, the dataset query runs and the report server places a copy of the refreshed data back in the cache.</span></span>  
  
 <span data-ttu-id="efab9-123">**快取於下列排程時到期**</span><span class="sxs-lookup"><span data-stu-id="efab9-123">**Expire the cache on the following schedule**</span></span>  
 <span data-ttu-id="efab9-124">排程快取的資料不再有效並從快取移除的時間。</span><span class="sxs-lookup"><span data-stu-id="efab9-124">Schedule the time when the cached data is no longer valid and is removed from the cache.</span></span> <span data-ttu-id="efab9-125">排程可以是共用的排程或是特屬目前共用資料集的排程。</span><span class="sxs-lookup"><span data-stu-id="efab9-125">The schedule can be a shared schedule or one that is specific for only the current shared dataset.</span></span>  
  
 <span data-ttu-id="efab9-126">**資料集特定排程**</span><span class="sxs-lookup"><span data-stu-id="efab9-126">**Dataset-specific schedule**</span></span>  
 <span data-ttu-id="efab9-127">指定僅供此資料集使用的排程。</span><span class="sxs-lookup"><span data-stu-id="efab9-127">Specify a schedule that is used only by this dataset.</span></span>  
  
 <span data-ttu-id="efab9-128">**共用排程**</span><span class="sxs-lookup"><span data-stu-id="efab9-128">**Shared schedule**</span></span>  
 <span data-ttu-id="efab9-129">指定報表、訂閱及其他共用資料集所共用的排程。</span><span class="sxs-lookup"><span data-stu-id="efab9-129">Specify a schedule that is shared among reports, subscriptions, and other shared datasets.</span></span>  
  
 <span data-ttu-id="efab9-130">**套用**</span><span class="sxs-lookup"><span data-stu-id="efab9-130">**Apply**</span></span>  
 <span data-ttu-id="efab9-131">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="efab9-131">Save your changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efab9-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efab9-132">See Also</span></span>  
 <span data-ttu-id="efab9-133">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="efab9-133">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="efab9-134">[報表管理員 F1 說明](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="efab9-134">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="efab9-135">[&#40;SSRS&#41;快取共用資料集](report-server/cache-shared-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="efab9-135">[Cache Shared Datasets &#40;SSRS&#41;](report-server/cache-shared-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="efab9-136">排程</span><span class="sxs-lookup"><span data-stu-id="efab9-136">Schedules</span></span>](subscriptions/schedules.md)  
  
  
