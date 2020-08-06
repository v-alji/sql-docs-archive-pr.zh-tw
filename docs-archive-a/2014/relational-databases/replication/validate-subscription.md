---
title: 驗證訂閱 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.validateandresynch.f1
helpviewer_keywords:
- Validate Subscription dialog box
ms.assetid: 74bdf5e1-b886-4284-b5fb-332bf79ae083
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 010b5b2e9778ccf37133b0a84796373c012290f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593920"
---
# <a name="validate-subscription"></a><span data-ttu-id="b75dc-102">驗證訂閱</span><span class="sxs-lookup"><span data-stu-id="b75dc-102">Validate Subscription</span></span>
  <span data-ttu-id="b75dc-103">使用 **[驗證訂閱]** 對話方塊以指定下次執行訂閱的合併代理程式時，應驗證合併式發行集的訂閱。</span><span class="sxs-lookup"><span data-stu-id="b75dc-103">Use the **Validate Subscription** dialog box to specify that a subscription to a merge publication should be validated the next time the Merge Agent for the subscription runs.</span></span> <span data-ttu-id="b75dc-104">驗證的結果會在複寫監視器中顯示。</span><span class="sxs-lookup"><span data-stu-id="b75dc-104">The results of validation are displayed in Replication Monitor.</span></span> <span data-ttu-id="b75dc-105">如需詳細資訊，請參閱 [Validate Data at the Subscriber](validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="b75dc-105">For more information, see [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).</span></span>  
  
 <span data-ttu-id="b75dc-106">也可以在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下發行集，然後按一下 [驗證所有訂閱]  來驗證合併式發行集的所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="b75dc-106">It is also possible to validate all subscriptions to a merge publication by right-clicking a publication in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and clicking **Validate All Subscriptions**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b75dc-107">選項。</span><span class="sxs-lookup"><span data-stu-id="b75dc-107">Options</span></span>  
 <span data-ttu-id="b75dc-108">**上一次嘗試驗證的日期**</span><span class="sxs-lookup"><span data-stu-id="b75dc-108">**Date of the last attempted validation**</span></span>  
 <span data-ttu-id="b75dc-109">合併代理程式工作階段上一次進行訂閱驗證的日期，無論驗證成功與否。</span><span class="sxs-lookup"><span data-stu-id="b75dc-109">The date of the last Merge Agent session that included subscription validation, whether or not that validation was successful.</span></span>  
  
 <span data-ttu-id="b75dc-110">**上一次成功驗證的日期**</span><span class="sxs-lookup"><span data-stu-id="b75dc-110">**Date of the last successful validation**</span></span>  
 <span data-ttu-id="b75dc-111">合併代理程式工作階段上一次成功驗證訂閱的日期。</span><span class="sxs-lookup"><span data-stu-id="b75dc-111">The date of the last Merge Agent session that included a successful subscription validation.</span></span>  
  
 <span data-ttu-id="b75dc-112">**驗證此訂閱**</span><span class="sxs-lookup"><span data-stu-id="b75dc-112">**Validate this subscription**</span></span>  
 <span data-ttu-id="b75dc-113">選取即可驗證訂閱。</span><span class="sxs-lookup"><span data-stu-id="b75dc-113">Select to validate the subscription.</span></span>  
  
 <span data-ttu-id="b75dc-114">**選項**</span><span class="sxs-lookup"><span data-stu-id="b75dc-114">**Options**</span></span>  
 <span data-ttu-id="b75dc-115">按一下以存取 **[訂閱驗證選項]** 對話方塊，其中可讓您指定是否要使用資料列計數驗證或二進位總和檢查碼驗證。</span><span class="sxs-lookup"><span data-stu-id="b75dc-115">Click to access the **Subscription Validation Options** dialog box, which allows you to specify whether to use row count validation or binary checksum validation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b75dc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b75dc-116">See Also</span></span>  
 [<span data-ttu-id="b75dc-117">驗證複寫的資料</span><span class="sxs-lookup"><span data-stu-id="b75dc-117">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
