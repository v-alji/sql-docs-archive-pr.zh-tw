---
title: 驗證合併訂閱者的資料分割資訊 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication data validation [SQL Server replication], partitions
- parameterized filters [SQL Server replication], validating partition information
- validating partition information
ms.assetid: c059553e-df2c-4333-ba79-e8d6e2890c34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3032ff13af69a0690e1f81f08f7b3fb17aae0ee1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585251"
---
# <a name="validate-partition-information-for-a-merge-subscriber"></a><span data-ttu-id="af88a-102">驗證合併訂閱者的資料分割資訊</span><span class="sxs-lookup"><span data-stu-id="af88a-102">Validate Partition Information for a Merge Subscriber</span></span>
  <span data-ttu-id="af88a-103">在為合併式發行集定義參數化資料列篩選器時，可以使用參考「訂閱者」資訊的功能，例如「訂閱者」的登入名稱。</span><span class="sxs-lookup"><span data-stu-id="af88a-103">When you define a parameterized row filter for a merge publication, you use a function that references Subscriber information, such as the Subscriber's login name.</span></span> <span data-ttu-id="af88a-104">依預設，複寫將在每次同步處理和在「訂閱者」端套用快照集之前，根據該功能驗證「訂閱者」資訊。</span><span class="sxs-lookup"><span data-stu-id="af88a-104">By default, replication validates Subscriber information based on that function before each synchronization and whenever a snapshot is applied at the Subscriber.</span></span> <span data-ttu-id="af88a-105">驗證處理可確保為每個「訂閱者」正確分割資料。</span><span class="sxs-lookup"><span data-stu-id="af88a-105">The validation process ensures that data is partitioned correctly for each Subscriber.</span></span> <span data-ttu-id="af88a-106">驗證行為由 **validate_subscriber_info** 發行集屬性控制，該發行集屬性可使用 [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) 或在 [發行集屬性]  對話方塊的 [訂閱選項]  頁面中變更。</span><span class="sxs-lookup"><span data-stu-id="af88a-106">Validation behavior is controlled by the **validate_subscriber_info** publication property, which can be changed using [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) or on the **Subscription Options** page of the **Publication Properties** dialog box.</span></span> <span data-ttu-id="af88a-107">如需有關變更發行集屬性的詳細資訊，請參閱＜ [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="af88a-107">For more information about changing publication properties, see [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).</span></span>  
  
## <a name="how-partition-validation-works"></a><span data-ttu-id="af88a-108">資料分割驗證的運作方式</span><span class="sxs-lookup"><span data-stu-id="af88a-108">How Partition Validation Works</span></span>  
 <span data-ttu-id="af88a-109">例如，使用函數 **SUSER_SNAME()** 對某發行集進行篩選後，「合併代理程式」便會根據有效的 **SUSER_SNAME()** 運算式資料，將初始快照套用到每個「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="af88a-109">When a publication is filtered, for example, using the function **SUSER_SNAME()**, the Merge Agent applies the initial snapshot to each Subscriber based on data that is valid for the **SUSER_SNAME()** expression.</span></span>  
  
 <span data-ttu-id="af88a-110">如果在「訂閱者」重新連接到「發行者」以進行下一次同步處理時已啟用驗證，「合併代理程式」便會在「訂閱者」端驗證資訊，並確定每個「訂閱者」的資料分割與初始快照集中接收的資料分割相同。</span><span class="sxs-lookup"><span data-stu-id="af88a-110">If validation is enabled, when the Subscriber reconnects to the Publisher for the next synchronization, the Merge Agent validates the information at the Subscriber and ensures that each Subscriber's partition is the same as the one received in the initial snapshot.</span></span> <span data-ttu-id="af88a-111">對於每個後續合併或快照集應用程式，「合併代理程式」會驗證每個「訂閱者」的資料分割。</span><span class="sxs-lookup"><span data-stu-id="af88a-111">For each subsequent merge or snapshot application, the Merge Agent validates each Subscriber's partition.</span></span>  
  
 <span data-ttu-id="af88a-112">如果「合併代理程式」偵測到，篩選運算式中使用的函數傳回不同於初始快照集中獲得的值，合併或快照集應用程式便會失敗，且「訂閱者」的訂閱可能需要重新初始化。</span><span class="sxs-lookup"><span data-stu-id="af88a-112">If the Merge Agent detects that the function used in the filtering expression returns a different value than it did at the initial snapshot, the merge or snapshot application fails, and that Subscriber's subscription might require reinitialization.</span></span> <span data-ttu-id="af88a-113">如果「訂閱者」的合併設定發生變更，則可能需要重新初始化以防止出現問題，但在「訂閱者」端將資訊 (例如登入名稱) 變更回原始快照集所使用的值或許已足夠。</span><span class="sxs-lookup"><span data-stu-id="af88a-113">Reinitialization might be necessary to prevent problems that can arise if the merge settings of a Subscriber are changed, but it might be sufficient to change information at the Subscriber, such as the login name, back to the value used at the time of the original snapshot.</span></span>  
  
 <span data-ttu-id="af88a-114">在「合併代理程式」驗證分割時，除了根據篩選運算式中所使用之函數傳回的值來驗證分割外，代理程式還會檢查快照集在使其無效的變更 (例如中繼資料清除作業或結構描述變更) 發生前是否已產生。</span><span class="sxs-lookup"><span data-stu-id="af88a-114">When the Merge Agent validates a partition, in addition to validating the partition against the values returned by any functions used in filtering expressions, the agent also checks whether the snapshot was generated prior to changes that invalidate it, such as metadata cleanup operations or schema changes.</span></span> <span data-ttu-id="af88a-115">如果分割的快照集太舊，「合併代理程式」將傳回錯誤，且您必須根據目前的一般快照集為該「訂閱者」重新產生分割的快照集。</span><span class="sxs-lookup"><span data-stu-id="af88a-115">If a partitioned snapshot is too old, the Merge Agent will return an error and you must regenerate a partitioned snapshot for that Subscriber based on a current regular snapshot.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af88a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af88a-116">See Also</span></span>  
 <span data-ttu-id="af88a-117">[複寫管理常見問題集](administration/frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="af88a-117">[Replication Administration FAQ](administration/frequently-asked-questions-for-replication-administrators.md) </span></span>  
 <span data-ttu-id="af88a-118">[Best Practices for Replication Administration](administration/best-practices-for-replication-administration.md) </span><span class="sxs-lookup"><span data-stu-id="af88a-118">[Best Practices for Replication Administration](administration/best-practices-for-replication-administration.md) </span></span>  
 <span data-ttu-id="af88a-119">[重新初始化訂閱](reinitialize-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="af88a-119">[Reinitialize Subscriptions](reinitialize-subscriptions.md) </span></span>  
 [<span data-ttu-id="af88a-120">驗證複寫的資料</span><span class="sxs-lookup"><span data-stu-id="af88a-120">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
