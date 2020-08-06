---
title: 快取共用資料集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c2d8c81a-da1e-4a8a-9845-fff9a0903d24
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d4757d82425368efcb6a0a555c6cfe1deacf48c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597610"
---
# <a name="cache-a-shared-dataset"></a><span data-ttu-id="1c20c-102">快取共用資料集</span><span class="sxs-lookup"><span data-stu-id="1c20c-102">Cache a Shared Dataset</span></span>
  <span data-ttu-id="1c20c-103">改善效能的其中一種方式就是設定共用資料集的快取屬性。</span><span class="sxs-lookup"><span data-stu-id="1c20c-103">One way to improve performance is to configure caching properties for a shared dataset.</span></span> <span data-ttu-id="1c20c-104">快取共用資料集時，系統會在一段指定的時間內儲存查詢結果的副本。</span><span class="sxs-lookup"><span data-stu-id="1c20c-104">When a shared dataset is cached, a copy of the query results is saved for a specified period of time.</span></span> <span data-ttu-id="1c20c-105">要求使用共用資料集之報表的第一位使用者必須等候查詢結果以及所有處理都完成，然後才能檢視該報表。</span><span class="sxs-lookup"><span data-stu-id="1c20c-105">The first user who requests a report that uses the shared dataset must wait for the query results and all processing to complete before viewing the report.</span></span> <span data-ttu-id="1c20c-106">在快取期間內要求該報表的後續使用者將會立即體驗到增進的效能，因為查詢和處理都已經進行了。</span><span class="sxs-lookup"><span data-stu-id="1c20c-106">Subsequent users who request the report within the caching period will experience improved performance because the query and processing has already occurred.</span></span> <span data-ttu-id="1c20c-107">您也可以指定執行查詢的快取重新整理計劃，並在指定的快取逾期前快取結果。</span><span class="sxs-lookup"><span data-stu-id="1c20c-107">You can also specify a cache refresh plan to run the query and cache the results until the specified cache expiration.</span></span>  
  
 <span data-ttu-id="1c20c-108">根據共用資料集或快取重新整理計劃執行報表的使用者會建立查詢快取，而且在這兩種情況下，都可以根據快取逾期選項使用快取。</span><span class="sxs-lookup"><span data-stu-id="1c20c-108">Users running reports based on a shared dataset or cache refresh plans create the query cache and in both cases, the cache is available based on the cache expiration options.</span></span>  
  
 <span data-ttu-id="1c20c-109">您可以快取的共用資料集類型有所限制。</span><span class="sxs-lookup"><span data-stu-id="1c20c-109">There are restrictions on the types of shared datasets that you can cache.</span></span> <span data-ttu-id="1c20c-110">例如，如果資料會因使用者識別而不同，或者資料是使用要求報表之使用者的安全性 Token 擷取的，系統就無法快取該查詢結果。</span><span class="sxs-lookup"><span data-stu-id="1c20c-110">For example, the query results cannot be cached if the data varies based on the user identity or if data is retrieved using the security token of the user who requests the report.</span></span> <span data-ttu-id="1c20c-111">如需詳細資訊，請參閱[快取共用資料集 &#40;SSRS&#41;](cache-shared-datasets-ssrs.md) 和[快取多個報表 &#40;SSRS&#41;](caching-reports-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1c20c-111">For more information, see [Cache Shared Datasets &#40;SSRS&#41;](cache-shared-datasets-ssrs.md) and [Caching Reports &#40;SSRS&#41;](caching-reports-ssrs.md).</span></span>  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a><span data-ttu-id="1c20c-112">若要排程快取報表的逾期</span><span class="sxs-lookup"><span data-stu-id="1c20c-112">To schedule the expiration of a cached report</span></span>  
  
1.  <span data-ttu-id="1c20c-113">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="1c20c-113">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="1c20c-114">在報表管理員中，導覽至您想要設定快取屬性的共用資料集、將滑鼠停留在該項目上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="1c20c-114">In Report Manager, navigate to the shared dataset for which you want to set caching properties, hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="1c20c-115">在下拉式功能表中，按一下 **[管理]** 。</span><span class="sxs-lookup"><span data-stu-id="1c20c-115">In the drop-down menu, click **Manage**.</span></span>  
  
4.  <span data-ttu-id="1c20c-116">在左框架內，按一下 **[快取]** 。</span><span class="sxs-lookup"><span data-stu-id="1c20c-116">In the left frame, click **Caching**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c20c-117">如果您看到「 **尚未儲存用來執行共用資料集的認證**」這個錯誤，將會停用快取共用資料集選項。</span><span class="sxs-lookup"><span data-stu-id="1c20c-117">If you see the error **Credentials used to run the shared dataset are not stored**, the cache shared dataset option will be disabled.</span></span> <span data-ttu-id="1c20c-118">您需要修改資料來源來儲存認證，或修改共用資料集來使用與儲存認證不同的資料來源。</span><span class="sxs-lookup"><span data-stu-id="1c20c-118">You need modify the data source to store credentials or modify the shared dataset to use a different data source that does store credentials.</span></span>  
  
5.  <span data-ttu-id="1c20c-119">選取 **[快取共用資料集]** 。</span><span class="sxs-lookup"><span data-stu-id="1c20c-119">Select **Cache share dataset**.</span></span>  
  
6.  <span data-ttu-id="1c20c-120">選取快取於 30 分鐘後過期的選項。</span><span class="sxs-lookup"><span data-stu-id="1c20c-120">Select the option to expire the cache after 30 minutes.</span></span> <span data-ttu-id="1c20c-121">您也可以選擇讓快取在指定的排程時間過期。</span><span class="sxs-lookup"><span data-stu-id="1c20c-121">You can also choose for the cache to expire on a specified schedule.</span></span>  
  
7.  <span data-ttu-id="1c20c-122">按一下 [套用]  。</span><span class="sxs-lookup"><span data-stu-id="1c20c-122">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c20c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c20c-123">See Also</span></span>  
 [<span data-ttu-id="1c20c-124">管理共用資料集</span><span class="sxs-lookup"><span data-stu-id="1c20c-124">Manage Shared Datasets</span></span>](../report-data/manage-shared-datasets.md)  
  
  
