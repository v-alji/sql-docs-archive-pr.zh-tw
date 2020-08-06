---
title: 指定合併訂閱類型和衝突解決優先權 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a19ae6246fe59308283fbaf2f35e2c49f96b140c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710569"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority-sql-server-management-studio"></a><span data-ttu-id="3d209-102">指定合併訂閱類型和衝突解決優先權 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3d209-102">Specify a Merge Subscription Type and Conflict Resolution Priority (SQL Server Management Studio)</span></span>
  <span data-ttu-id="3d209-103">在「新增訂閱精靈」的 **[訂閱類型]** 頁面中指定合併訂閱類型和衝突解決優先權。</span><span class="sxs-lookup"><span data-stu-id="3d209-103">Specify a merge subscription type and conflict resolution priority on the **Subscription Type** page of the New Subscription Wizard.</span></span> <span data-ttu-id="3d209-104">如需使用此精靈的詳細資訊，請參閱＜ [Create a Pull Subscription](create-a-pull-subscription.md) ＞和＜ [Create a Push Subscription](create-a-push-subscription.md)＞。</span><span class="sxs-lookup"><span data-stu-id="3d209-104">For more information about using this wizard, see [Create a Pull Subscription](create-a-pull-subscription.md) and [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="3d209-105">訂閱建立後即無法修改其類型，但可在 [訂閱屬性 - \<Publisher> \<PublicationDatabase>] 對話方塊中修改伺服器訂閱類型的優先權。</span><span class="sxs-lookup"><span data-stu-id="3d209-105">Subscription type cannot be modified after a subscription is created, but priority can be modified for the server subscription type in the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box.</span></span> <span data-ttu-id="3d209-106">如需有關存取這個對話方塊的詳細資訊，請參閱＜ [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) ＞與＜ [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="3d209-106">For more information about accessing this dialog box, see [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) and [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a><span data-ttu-id="3d209-107">若要指定合併訂閱類型與衝突解決優先權</span><span class="sxs-lookup"><span data-stu-id="3d209-107">To specify a merge subscription type and conflict resolution priority</span></span>  
  
1.  <span data-ttu-id="3d209-108">在「新增訂閱精靈」的 **[訂閱類型]** 頁面上，為 **[訂閱類型]** 選項選取 **[用戶端]** 或 **[伺服器]** 。</span><span class="sxs-lookup"><span data-stu-id="3d209-108">On the **Subscription Type** page of the New Subscription Wizard, select **Client** or **Server** for the **Subscription Type** option.</span></span>  
  
2.  <span data-ttu-id="3d209-109">如果您選取了 **[伺服器]** 訂閱類型，請同時輸入 **[衝突解決優先權]** 選項的值 (0.00 到 99.99)。</span><span class="sxs-lookup"><span data-stu-id="3d209-109">If you select a subscription type of **Server**, also enter a value (0.00 to 99.99) for the **Priority for Conflict Resolution** option.</span></span>  
  
### <a name="to-modify-the-conflict-resolution-priority"></a><span data-ttu-id="3d209-110">若要修改衝突解決優先權</span><span class="sxs-lookup"><span data-stu-id="3d209-110">To modify the conflict resolution priority</span></span>  
  
1.  <span data-ttu-id="3d209-111">在發行者端的 [訂閱屬性 - \<Publisher> \<PublicationDatabase>] 中，輸入 [優先權] 選項的值 (0.00 到 99.99)。</span><span class="sxs-lookup"><span data-stu-id="3d209-111">In the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** at the Publisher, enter a value (0.00 to 99.99) for the **Priority** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3d209-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d209-112">See Also</span></span>  
 <span data-ttu-id="3d209-113">[進階合併式複寫衝突偵測與解決](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="3d209-113">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="3d209-114">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="3d209-114">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
