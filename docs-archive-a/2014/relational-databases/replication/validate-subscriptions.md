---
title: 驗證多個訂閱 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.subscriptions.f1
helpviewer_keywords:
- Validate Subscriptions dialog box
ms.assetid: 0ca39a35-f22c-46c5-82a4-342e34bf5d1b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a61e8b5417bf8312998b5051c47545b705b44c00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584375"
---
# <a name="validate-subscriptions"></a><span data-ttu-id="e06c4-102">驗證多個訂閱</span><span class="sxs-lookup"><span data-stu-id="e06c4-102">Validate Subscriptions</span></span>
  <span data-ttu-id="e06c4-103">使用 **[驗證訂閱]** 對話方塊即可指定交易式發行集的訂閱，需要在訂閱的散發代理程式下次執行時進行驗證。</span><span class="sxs-lookup"><span data-stu-id="e06c4-103">Use the **Validate Subscriptions** dialog box to specify that subscriptions to a transactional publication should be validated the next time the Distribution Agent for each subscription runs.</span></span> <span data-ttu-id="e06c4-104">驗證的結果會在複寫監視器中顯示。</span><span class="sxs-lookup"><span data-stu-id="e06c4-104">The results of validation are displayed in Replication Monitor.</span></span> <span data-ttu-id="e06c4-105">如需詳細資訊，請參閱 [Validate Data at the Subscriber](validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="e06c4-105">For more information, see [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e06c4-106">選項。</span><span class="sxs-lookup"><span data-stu-id="e06c4-106">Options</span></span>  
 <span data-ttu-id="e06c4-107">**驗證所有的 SQL Server 訂閱**</span><span class="sxs-lookup"><span data-stu-id="e06c4-107">**Validate all SQL Server subscriptions**</span></span>  
 <span data-ttu-id="e06c4-108">選取即可驗證此發行集之所有 SQL Server 訂閱的資料。</span><span class="sxs-lookup"><span data-stu-id="e06c4-108">Select to validate data for all SQL Server subscriptions to this publication.</span></span>  
  
 <span data-ttu-id="e06c4-109">**驗證下列訂閱**</span><span class="sxs-lookup"><span data-stu-id="e06c4-109">**Validate the following subscriptions**</span></span>  
 <span data-ttu-id="e06c4-110">如果您不要驗證所有訂閱，請進行選取。</span><span class="sxs-lookup"><span data-stu-id="e06c4-110">Select if you do not want to validate all subscriptions.</span></span> <span data-ttu-id="e06c4-111">從清單中選取您要驗證的訂閱。</span><span class="sxs-lookup"><span data-stu-id="e06c4-111">Select from the list the subscriptions you want to validate.</span></span>  
  
 <span data-ttu-id="e06c4-112">**驗證選項**</span><span class="sxs-lookup"><span data-stu-id="e06c4-112">**Validation Options**</span></span>  
 <span data-ttu-id="e06c4-113">按一下以存取 **[訂閱驗證選項]** 對話方塊，其中可讓您指定是否要使用資料列計數驗證或二進位總和檢查碼驗證。</span><span class="sxs-lookup"><span data-stu-id="e06c4-113">Click to access the **Subscription Validation Options** dialog box, which allows you to specify whether to use row count validation or binary checksum validation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e06c4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e06c4-114">See Also</span></span>  
 [<span data-ttu-id="e06c4-115">驗證複寫的資料</span><span class="sxs-lookup"><span data-stu-id="e06c4-115">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
