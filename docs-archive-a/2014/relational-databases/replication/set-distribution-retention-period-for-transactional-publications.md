---
title: 設定交易式發行集的散發保留週期 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a68f092c63e75196ab82a81d2a8ca36d13142813
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606751"
---
# <a name="set-the-distribution-retention-period-for-transactional-publications-sql-server-management-studio"></a><span data-ttu-id="495e7-102">設定交易式發行集的散發保留週期 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="495e7-102">Set the Distribution Retention Period for Transactional Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="495e7-103">在 [散發資料庫屬性 - \<DistributionDatabase>] 對話方塊中，指定最短散發保留週期和最長散發保留週期。</span><span class="sxs-lookup"><span data-stu-id="495e7-103">Specify the minimum distribution retention period and maximum distribution retention period on the **Distribution Database Properties - \<DistributionDatabase>** dialog box.</span></span> <span data-ttu-id="495e7-104">這會在 [散發者屬性 - \<Distributor>] 對話方塊的 [一般] 頁面上提供。</span><span class="sxs-lookup"><span data-stu-id="495e7-104">This is available from the **General** page of the **Distributor Properties - \<Distributor>** dialog box.</span></span> <span data-ttu-id="495e7-105">如需存取此對話方塊的詳細資訊，請參閱[檢視及修改散發者和發行者屬性](view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="495e7-105">For more information about accessing this dialog box, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
### <a name="to-specify-the-distribution-retention-period"></a><span data-ttu-id="495e7-106">若要指定散發保留期限</span><span class="sxs-lookup"><span data-stu-id="495e7-106">To specify the distribution retention period</span></span>  
  
1.  <span data-ttu-id="495e7-107">在 [散發者屬性 - \<Distributor>] 對話方塊的 [一般] 頁面上，按一下散發資料庫的屬性按鈕 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="495e7-107">On the **General** page of the **Distributor Properties - \<Distributor>** dialog box, click the properties button (**...**) for the distribution database.</span></span>  
  
2.  <span data-ttu-id="495e7-108">若要指定最短散發保留期限，請在 **[至少]** 方塊中輸入值；若要指定最長散發期限，請在 **[但是不能超過]** 方塊中輸入值。</span><span class="sxs-lookup"><span data-stu-id="495e7-108">To specify the minimum distribution retention period, enter a value in the **At least** box; to specify the maximum distribution retention period, enter a value in the **But not more than** box.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="495e7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="495e7-109">See Also</span></span>  
 <span data-ttu-id="495e7-110">[[設定散發]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="495e7-110">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="495e7-111">訂閱逾期與停用</span><span class="sxs-lookup"><span data-stu-id="495e7-111">Subscription Expiration and Deactivation</span></span>](subscription-expiration-and-deactivation.md)  
  
  
