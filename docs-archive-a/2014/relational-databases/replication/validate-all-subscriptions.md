---
title: 驗證所有訂閱 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.allsubscriptions.f1
helpviewer_keywords:
- Validate All Subscriptions dialog box
ms.assetid: 32e31469-36e4-42d9-a57a-12388bfd229d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27a7a4f5e5c3c303d5a1cbe257c0a0e9b531e824
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598266"
---
# <a name="validate-all-subscriptions"></a><span data-ttu-id="e0270-102">驗證所有訂閱</span><span class="sxs-lookup"><span data-stu-id="e0270-102">Validate All Subscriptions</span></span>
  <span data-ttu-id="e0270-103">使用 **[驗證所有訂閱]** 對話方塊來指定下次執行每個訂閱的合併代理程式時，應驗證合併發行集的所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="e0270-103">Use the **Validate All Subscriptions** dialog box to specify that all subscriptions to a merge publication should be validated the next time the Merge Agent for each subscription runs.</span></span> <span data-ttu-id="e0270-104">驗證的結果會在複寫監視器中顯示。</span><span class="sxs-lookup"><span data-stu-id="e0270-104">The results of validation are displayed in Replication Monitor.</span></span> <span data-ttu-id="e0270-105">如需詳細資訊，請參閱 [Validate Data at the Subscriber](validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="e0270-105">For more information, see [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).</span></span>  
  
 <span data-ttu-id="e0270-106">您也可以用滑鼠右鍵按一下 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的訂閱，然後按一下 **[驗證訂閱]** ，藉以驗證單一訂閱。</span><span class="sxs-lookup"><span data-stu-id="e0270-106">It is also possible to validate a single subscription by right-clicking a subscription in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and clicking **Validate Subscription**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e0270-107">選項。</span><span class="sxs-lookup"><span data-stu-id="e0270-107">Options</span></span>  
 <span data-ttu-id="e0270-108">**只確認資料列計數**</span><span class="sxs-lookup"><span data-stu-id="e0270-108">**Verify the row counts only**</span></span>  
 <span data-ttu-id="e0270-109">選取以驗證訂閱者端之資料表的資料列數目是否與發行者端之資料表的資料列數目相同。</span><span class="sxs-lookup"><span data-stu-id="e0270-109">Select to validate whether the table at the Subscriber has the same number of rows as the table at the Publisher.</span></span> <span data-ttu-id="e0270-110">此方法不會驗證資料列的內容是否相符。</span><span class="sxs-lookup"><span data-stu-id="e0270-110">This method does not validate that the content of the rows matches.</span></span> <span data-ttu-id="e0270-111">資料列計數驗證提供一種輕量型驗證方法，可讓您發現資料中的問題。</span><span class="sxs-lookup"><span data-stu-id="e0270-111">Row count validation provides a lightweight approach to validation that can make you aware of issues with your data.</span></span>  
  
 <span data-ttu-id="e0270-112">**確認資料列計數並比較總和檢查碼，來確認資料列資料**</span><span class="sxs-lookup"><span data-stu-id="e0270-112">**Verify the row counts and compare checksums to verify the row data**</span></span>  
 <span data-ttu-id="e0270-113">除了統計「發行者」與「訂閱者」上的資料列數量之外，也會使用二進位總和檢查碼演算法計算所有資料的總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="e0270-113">In addition to taking a count of rows at the Publisher and Subscriber, a checksum of all the data is calculated using the binary checksum algorithm.</span></span> <span data-ttu-id="e0270-114">如果資料列計數失敗，就不會執行總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="e0270-114">If the row count fails, the checksum is not performed.</span></span> <span data-ttu-id="e0270-115">這個選項對於 [!INCLUDE[ssEW](../../includes/ssew-md.md)]無效。</span><span class="sxs-lookup"><span data-stu-id="e0270-115">This option is not valid for [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0270-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0270-116">See Also</span></span>  
 [<span data-ttu-id="e0270-117">驗證複寫的資料</span><span class="sxs-lookup"><span data-stu-id="e0270-117">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
