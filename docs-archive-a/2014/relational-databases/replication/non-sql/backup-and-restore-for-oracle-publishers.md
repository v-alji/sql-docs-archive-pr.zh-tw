---
title: Oracle 發行者的備份與還原 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server replication], Oracle publishing
- backups [SQL Server replication], Oracle publishing
- Oracle publishing [SQL Server replication], backup and restore
- restoring [SQL Server replication], Oracle publishing
ms.assetid: e5f181d0-cacf-442b-8b7a-202b3cfc358b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e6b994c34e4f4bebc010fe6d71bbd43f6e557cbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585300"
---
# <a name="backup-and-restore-for-oracle-publishers"></a><span data-ttu-id="080ad-102">Oracle 發行者的備份與還原</span><span class="sxs-lookup"><span data-stu-id="080ad-102">Backup and Restore for Oracle Publishers</span></span>
  <span data-ttu-id="080ad-103">在備份與還原時，請遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="080ad-103">Follow these guidelines when backing up and restoring:</span></span>  
  
-   <span data-ttu-id="080ad-104">確定「記錄讀取器代理程式」未執行，並且已發行資料表中的其他資料庫活動不會在備份「發行者」時出現。</span><span class="sxs-lookup"><span data-stu-id="080ad-104">Ensure the Log Reader Agent does not run and that other database activity on the published tables does not occur while the Publisher is being backed up.</span></span>  
  
-   <span data-ttu-id="080ad-105">同時備份「發行者」和「散發者」。</span><span class="sxs-lookup"><span data-stu-id="080ad-105">Backup up the Publisher and Distributor at the same time.</span></span>  
  
-   <span data-ttu-id="080ad-106">如果必須還原「發行者」或「散發者」，請重新初始化所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="080ad-106">If the Publisher or Distributor must be restored, reinitialize all subscriptions.</span></span>  
  
-   <span data-ttu-id="080ad-107">若要從備份還原「訂閱者」(無需重新初始化訂閱)，則在上次訂閱資料庫備份完成後，傳遞到散發資料庫的交易必須仍然可用。</span><span class="sxs-lookup"><span data-stu-id="080ad-107">To restore a Subscriber from a backup (without having to reinitialize subscriptions), the transactions delivered to the distribution database after the last subscription database backup was completed must still be available.</span></span> <span data-ttu-id="080ad-108">交易的時間長短可視散發保留設定而定。</span><span class="sxs-lookup"><span data-stu-id="080ad-108">The length of time transactions are available depends on distribution retention settings.</span></span> <span data-ttu-id="080ad-109">如需這些設定的詳細資訊，請參閱[訂閱逾期與停用](../subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="080ad-109">For information on these settings, see [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md).</span></span>  
  
-   <span data-ttu-id="080ad-110">如果「發行者」或「散發者」在還原資料庫後無法變得不一致，則複寫代理程式將記錄錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="080ad-110">If the Publisher or Distributor becomes out of sync as the result of a database restore, the replication agents log error messages.</span></span> <span data-ttu-id="080ad-111">此時，您必須卸除並重新建立所有相關的發行集和訂閱：</span><span class="sxs-lookup"><span data-stu-id="080ad-111">At this point, you must drop and recreate all relevant publications and subscriptions:</span></span>  
  
    1.  <span data-ttu-id="080ad-112">為發行集和訂閱的定義編寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="080ad-112">Script the definition of the publications and subscriptions.</span></span> <span data-ttu-id="080ad-113">如需詳細資訊，請參閱 [Scripting Replication](../scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="080ad-113">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
         <span data-ttu-id="080ad-114">如果發行集定義在「發行者」與「散發者」各版本之間作變更，則您需要修改指令碼。</span><span class="sxs-lookup"><span data-stu-id="080ad-114">If the definition of the publications has changed between the versions of the Publisher and Distributor states, you will need to modify the scripts.</span></span>  
  
    2.  <span data-ttu-id="080ad-115">卸除發行集和訂閱。</span><span class="sxs-lookup"><span data-stu-id="080ad-115">Drop the publications and subscriptions.</span></span>  
  
    3.  <span data-ttu-id="080ad-116">執行在步驟 1 中建立的指令碼。</span><span class="sxs-lookup"><span data-stu-id="080ad-116">Run the scripts created in step 1.</span></span>  
  
     <span data-ttu-id="080ad-117">如果必須卸除並重新設定「發行者」，請使用 **CASCADE** 選項卸除 **MSSQLSERVERDISTRIBUTOR** 公用同義字和設定的 Oracle 複寫使用者，以便從「Oracle 發行者」上移除所有複寫物件。</span><span class="sxs-lookup"><span data-stu-id="080ad-117">If the Publisher must be dropped and reconfigured, drop the **MSSQLSERVERDISTRIBUTOR** public synonym and the configured Oracle replication user with the **CASCADE** option to remove all replication objects from the Oracle Publisher.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="080ad-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="080ad-118">See Also</span></span>  
 <span data-ttu-id="080ad-119">[備份及還原複寫的資料庫](../administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="080ad-119">[Back Up and Restore Replicated Databases](../administration/back-up-and-restore-replicated-databases.md) </span></span>  
 <span data-ttu-id="080ad-120">[設定 Oracle 發行者](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="080ad-120">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 [<span data-ttu-id="080ad-121">Oracle 發行概觀</span><span class="sxs-lookup"><span data-stu-id="080ad-121">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
