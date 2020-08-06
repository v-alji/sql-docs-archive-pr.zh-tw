---
title: 發行資料 (適用于 Excel 的 MDS 增益集) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ea84a9aa-aeec-411b-ab8d-bc1b14f864a3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ab37a353469d1902394a3e2cd8060d9be82abb40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704285"
---
# <a name="publishing-data-mds-add-in-for-excel"></a><span data-ttu-id="a25a7-102">發行資料 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="a25a7-102">Publishing Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="a25a7-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，如果您想要與其他使用者共用資料，請將資料發行至 MDS 存放庫。</span><span class="sxs-lookup"><span data-stu-id="a25a7-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], publish data to the MDS repository when you want to share it with other users.</span></span> <span data-ttu-id="a25a7-104">一旦發行資料之後，這項資料就可供此增益集的其他使用者下載。</span><span class="sxs-lookup"><span data-stu-id="a25a7-104">As soon as data is published, it is available for other users of the Add-in to download.</span></span>  
  
 <span data-ttu-id="a25a7-105">發行資料時，您已新增或更新的任何資料都會發行至 MDS 存放庫。</span><span class="sxs-lookup"><span data-stu-id="a25a7-105">When you publish data, any data you've added or updated is published to the MDS repository.</span></span> <span data-ttu-id="a25a7-106">不過，您已刪除的資料則不會發行；您必須個別刪除資料。</span><span class="sxs-lookup"><span data-stu-id="a25a7-106">Data you've deleted is not published-you must delete data separately.</span></span> <span data-ttu-id="a25a7-107">如需詳細資訊，請參閱 [刪除資料列 &#40;適用於 Excel 的 MDS 增益集&#41;](delete-a-row-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="a25a7-107">For more information, see [Delete a Row &#40;MDS Add-in for Excel&#41;](delete-a-row-mds-add-in-for-excel.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a25a7-108">發行無法用來建立新的實體。</span><span class="sxs-lookup"><span data-stu-id="a25a7-108">Publishing cannot be used to create a new entity.</span></span> <span data-ttu-id="a25a7-109">如需建立實體的詳細資訊，請參閱[建立實體 &#40;MDS 適用於 Excel 的增益集&#41;](create-an-entity-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="a25a7-109">For more information about creating entities, see [Create an Entity &#40;MDS Add-in for Excel&#41;](create-an-entity-mds-add-in-for-excel.md).</span></span>  
  
## <a name="when-multiple-users-publish-at-the-same-time"></a><span data-ttu-id="a25a7-110">多位使用者同時發行時</span><span class="sxs-lookup"><span data-stu-id="a25a7-110">When Multiple Users Publish at the Same Time</span></span>  
 <span data-ttu-id="a25a7-111">多位使用者可以發行相同資料的更新。</span><span class="sxs-lookup"><span data-stu-id="a25a7-111">Multiple users can publish updates to the same data.</span></span> <span data-ttu-id="a25a7-112">當每位使用者發行時，更新會儲存至資料庫。</span><span class="sxs-lookup"><span data-stu-id="a25a7-112">As each user publishes, the update is saved to the database.</span></span> <span data-ttu-id="a25a7-113">這表示，沒有使用最近更新之資料的使用者仍然可以在發行時變更值。</span><span class="sxs-lookup"><span data-stu-id="a25a7-113">This means that a user who was not working with the most recently-updated data can still change the value when he or she publishes.</span></span>  
  
 <span data-ttu-id="a25a7-114">只有您所進行的更新會發行至資料庫。</span><span class="sxs-lookup"><span data-stu-id="a25a7-114">Only the updates you make are published to the database.</span></span> <span data-ttu-id="a25a7-115">系統不會發行工作表中的任何過期資料。</span><span class="sxs-lookup"><span data-stu-id="a25a7-115">Any out-of-date data in the worksheet is not published.</span></span>  
  
## <a name="transactions-and-annotations"></a><span data-ttu-id="a25a7-116">交易和註解</span><span class="sxs-lookup"><span data-stu-id="a25a7-116">Transactions and Annotations</span></span>  
 <span data-ttu-id="a25a7-117">每個發行的變更都會儲存成交易。</span><span class="sxs-lookup"><span data-stu-id="a25a7-117">Each published change is saved as a transaction.</span></span> <span data-ttu-id="a25a7-118">如果您選擇，可以將註解加入至交易，以便說明進行變更的原因。</span><span class="sxs-lookup"><span data-stu-id="a25a7-118">If you choose, you can add annotations (comments) to a transaction, to explain why you made the change.</span></span>  
  
-   <span data-ttu-id="a25a7-119">雖然刪除項目會儲存成可由管理員反轉的交易，不過您無法註解刪除項目。</span><span class="sxs-lookup"><span data-stu-id="a25a7-119">You cannot annotate deletions, although deletions are saved as transactions that can be reversed by an administrator.</span></span>  
  
-   <span data-ttu-id="a25a7-120">如果您變更了某個成員的**Code**值，它就不會記錄為交易，而且該成員的所有先前交易都無法使用。</span><span class="sxs-lookup"><span data-stu-id="a25a7-120">If you change the **Code** value for a member, it is not recorded as a transaction, and all previous transactions for the member are unavailable.</span></span>  
  
-   <span data-ttu-id="a25a7-121">您可以檢視其他使用者對成員所做的交易。</span><span class="sxs-lookup"><span data-stu-id="a25a7-121">You can view transactions made to a member by other users.</span></span> <span data-ttu-id="a25a7-122">您也可以檢視自己對成員所做的所有交易，即使您不再擁有特定屬性的權限也一樣。</span><span class="sxs-lookup"><span data-stu-id="a25a7-122">You can also view all transactions you've made to a member, even if you no longer have permission to specific attributes.</span></span>  
  
 <span data-ttu-id="a25a7-123">您可以檢視對成員所做的所有交易。</span><span class="sxs-lookup"><span data-stu-id="a25a7-123">You can view all transactions made to a member.</span></span> <span data-ttu-id="a25a7-124">如需詳細資訊，請參閱 [檢視成員的所有註解或交易 &#40;適用於 Excel 的 MDS 增益集&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="a25a7-124">For more information, see [View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a25a7-125">如果您輸入了超過 500 個字元的註解，系統將自動截斷註解。</span><span class="sxs-lookup"><span data-stu-id="a25a7-125">If you enter an annotation of more than 500 characters, the annotation is automatically truncated.</span></span>  
  
## <a name="business-rule-and-other-validation"></a><span data-ttu-id="a25a7-126">商務規則和其他驗證</span><span class="sxs-lookup"><span data-stu-id="a25a7-126">Business Rule and Other Validation</span></span>  
 <span data-ttu-id="a25a7-127">發行資料時，系統會在資料新增至 MDS 存放庫之前執行驗證，確保資料正確無誤。</span><span class="sxs-lookup"><span data-stu-id="a25a7-127">When you publish data, validation is performed to ensure data is accurate before it's added to the MDS repository.</span></span> <span data-ttu-id="a25a7-128">如果資料不符合指定的準則，就不會發行至儲存機制。</span><span class="sxs-lookup"><span data-stu-id="a25a7-128">If the data does not meet specified criteria, it will not be published to the repository.</span></span> <span data-ttu-id="a25a7-129">如需詳細資訊，請參閱[驗證資料 &#40;MDS 適用於 Excel 的增益集&#41;](validating-data-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="a25a7-129">For more information, see [Validating Data &#40;MDS Add-in for Excel&#41;](validating-data-mds-add-in-for-excel.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="a25a7-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="a25a7-130">Related Tasks</span></span>  
  
|<span data-ttu-id="a25a7-131">工作描述</span><span class="sxs-lookup"><span data-stu-id="a25a7-131">Task Description</span></span>|<span data-ttu-id="a25a7-132">主題</span><span class="sxs-lookup"><span data-stu-id="a25a7-132">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="a25a7-133">將資料從使用中工作表發行回 MDS 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="a25a7-133">Publish data from the active worksheet back to the MDS repository.</span></span>|[<span data-ttu-id="a25a7-134">將 Excel 的資料發行至適用于 Excel 的 mds 增益集 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="a25a7-134">Publish Data from Excel to MDS &#40;MDS Add-in for Excel&#41;</span></span>](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|<span data-ttu-id="a25a7-135">同時從 MDS 儲存機制和工作表中刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="a25a7-135">Delete a row from the MDS repository and from the worksheet at the same time.</span></span>|[<span data-ttu-id="a25a7-136">刪除資料列 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="a25a7-136">Delete a Row &#40;MDS Add-in for Excel&#41;</span></span>](delete-a-row-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="a25a7-137">相關內容</span><span class="sxs-lookup"><span data-stu-id="a25a7-137">Related Content</span></span>  
  
-   [<span data-ttu-id="a25a7-138">重新整理資料 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="a25a7-138">Refreshing Data &#40;MDS Add-in for Excel&#41;</span></span>](refreshing-data-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="a25a7-139">適用於 Microsoft Excel 的 Master Data Services 增益集</span><span class="sxs-lookup"><span data-stu-id="a25a7-139">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
  
