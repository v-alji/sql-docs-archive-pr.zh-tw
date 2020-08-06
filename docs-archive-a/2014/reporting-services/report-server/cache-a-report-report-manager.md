---
title: 快取報表 (報表管理員) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- cache [Reporting Services]
- cached reports [Reporting Services]
- schedules [Reporting Services], report expiration
- expiration [Reporting Services]
ms.assetid: 723d1cb0-c2e7-4763-8690-a6a7a8bbbb90
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e359e6c7a40b267979137ef2b3a285667a6fdb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597611"
---
# <a name="cache-a-report-report-manager"></a><span data-ttu-id="42e8d-102">快取報表 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="42e8d-102">Cache a Report (Report Manager)</span></span>
  <span data-ttu-id="42e8d-103">改善效能的其中一種方式就是設定報表的快取屬性。</span><span class="sxs-lookup"><span data-stu-id="42e8d-103">One way to improve performance is to configure caching properties for a report.</span></span> <span data-ttu-id="42e8d-104">快取報表時，系統就會在一段短時間內儲存已轉譯報表的副本。</span><span class="sxs-lookup"><span data-stu-id="42e8d-104">When a report is cached, a copy of the rendered report is saved for a short period of time.</span></span> <span data-ttu-id="42e8d-105">要求報表的第一位使用者必須等候所有處理都完成，然後才能檢視該報表。</span><span class="sxs-lookup"><span data-stu-id="42e8d-105">The first user who requests the report must wait for all processing to complete before viewing the report.</span></span> <span data-ttu-id="42e8d-106">在快取期間內要求該報表的後續使用者可以立即檢視報表，因為處理已經進行了。</span><span class="sxs-lookup"><span data-stu-id="42e8d-106">Subsequent users who request the report within the caching period can view it right away because processing has already occurred.</span></span>  
  
 <span data-ttu-id="42e8d-107">您可以快取的報表類型有所限制。</span><span class="sxs-lookup"><span data-stu-id="42e8d-107">There are restrictions on the types of reports that you can cache.</span></span> <span data-ttu-id="42e8d-108">例如，如果報表輸出會因使用者識別而不同，或者資料是使用要求報表之使用者的安全性 Token 擷取的，系統就無法快取該報表。</span><span class="sxs-lookup"><span data-stu-id="42e8d-108">For example, a report cannot be cached if report output varies based on the user identity or if data is retrieved using the security token of the user who requests the report.</span></span> <span data-ttu-id="42e8d-109">如需詳細資訊，請參閱 [快取報表 &#40;SSRS&#41;](caching-reports-ssrs.md)的版本中預先載入快取的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="42e8d-109">For more information, see [Caching Reports &#40;SSRS&#41;](caching-reports-ssrs.md).</span></span>  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a><span data-ttu-id="42e8d-110">若要排程快取報表的逾期</span><span class="sxs-lookup"><span data-stu-id="42e8d-110">To schedule the expiration of a cached report</span></span>  
  
1.  <span data-ttu-id="42e8d-111">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="42e8d-111">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="42e8d-112">在報表管理員中，導覽至 **[內容]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="42e8d-112">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="42e8d-113">導覽至您想要設定快取屬性的報表、將滑鼠停留在該項目上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="42e8d-113">Navigate to the report for which you want to set caching properties, hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="42e8d-114">在下拉式功能表中，按一下 **[管理]** 。</span><span class="sxs-lookup"><span data-stu-id="42e8d-114">In the drop-down menu, click **Manage**.</span></span>  
  
4.  <span data-ttu-id="42e8d-115">在左框架內，按一下 [處理選項]  。</span><span class="sxs-lookup"><span data-stu-id="42e8d-115">In the left frame, click the **Processing Options**.</span></span>  
  
5.  <span data-ttu-id="42e8d-116">在頁面上，選取 [永遠以最新的資料執行此報表]  。</span><span class="sxs-lookup"><span data-stu-id="42e8d-116">On the page, select **Always run this report with the most recent data**.</span></span>  
  
6.  <span data-ttu-id="42e8d-117">選取下列兩個快取選項的其中之一，並設定逾期如下：</span><span class="sxs-lookup"><span data-stu-id="42e8d-117">Select one of the following two cache options and configure expiration as follows:</span></span>  
  
    -   <span data-ttu-id="42e8d-118">若要設定快取副本在特定時間週期之後過期，請按一下 **[快取報表的暫存副本。報表副本會在下列分鐘數後過期]** 。</span><span class="sxs-lookup"><span data-stu-id="42e8d-118">To configure a cached copy to expire after a particular time period, click **Cache a temporary copy of the report. Expire copy of report after a number of minutes**.</span></span> <span data-ttu-id="42e8d-119">輸入報表過期的分鐘數。</span><span class="sxs-lookup"><span data-stu-id="42e8d-119">Type the number of minutes for report expiration.</span></span>  
  
    -   <span data-ttu-id="42e8d-120">若要設定快取副本依據排程過期，請按一下 **[快取報表的暫存副本。報表副本會在下列排程過期]** 。</span><span class="sxs-lookup"><span data-stu-id="42e8d-120">To configure a cached copy to expire on a schedule, click **Cache a temporary copy of the report. Expire copy of report on the following schedule.**</span></span> <span data-ttu-id="42e8d-121">按一下 [設定]  ，或選取共用排程來控制報表逾期</span><span class="sxs-lookup"><span data-stu-id="42e8d-121">Click **Configure**, or select a shared schedule to control report expiration</span></span>  
  
7.  <span data-ttu-id="42e8d-122">按一下 [套用]  。</span><span class="sxs-lookup"><span data-stu-id="42e8d-122">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e8d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42e8d-123">See Also</span></span>  
 <span data-ttu-id="42e8d-124">[設定報表處理屬性](set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="42e8d-124">[Set Report Processing Properties](set-report-processing-properties.md) </span></span>  
 [<span data-ttu-id="42e8d-125">快取報表 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="42e8d-125">Caching Reports &#40;SSRS&#41;</span></span>](caching-reports-ssrs.md)  
  
  
