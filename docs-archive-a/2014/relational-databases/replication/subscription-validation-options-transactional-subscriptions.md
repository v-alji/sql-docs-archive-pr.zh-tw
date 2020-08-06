---
title: 訂閱驗證選項 (交易式訂閱) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 40a617dd1beff24f8f072f5d139bec7c1ca65f33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709114"
---
# <a name="subscription-validation-options-transactional-subscriptions"></a><span data-ttu-id="3eb5b-102">訂閱驗證選項 (交易式訂閱)</span><span class="sxs-lookup"><span data-stu-id="3eb5b-102">Subscription Validation Options (Transactional Subscriptions)</span></span>
  <span data-ttu-id="3eb5b-103">使用 [**訂閱驗證選項**] 對話方塊，即可指定驗證應該只使用資料列計數，或資料列計數與二進位總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="3eb5b-103">Use the **Subscription Validation Options** dialog box to specify whether validation should use a row count only, or a row count and a binary checksum.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3eb5b-104">選項</span><span class="sxs-lookup"><span data-stu-id="3eb5b-104">Options</span></span>  
 <span data-ttu-id="3eb5b-105">**確認訂閱者與發行者的複寫資料列數相同。**</span><span class="sxs-lookup"><span data-stu-id="3eb5b-105">**Verify that the Subscriber has the same number of rows of replicated data as the Publisher**</span></span>  
 <span data-ttu-id="3eb5b-106">選取要執行之資料列計數驗證的類型。</span><span class="sxs-lookup"><span data-stu-id="3eb5b-106">Select the type of row count validation to perform.</span></span> <span data-ttu-id="3eb5b-107">對於 Oracle 發行集，唯一可用的選項是 **[直接查詢資料表來計算實際資料列計數]**。</span><span class="sxs-lookup"><span data-stu-id="3eb5b-107">For Oracle publications, the only available option is **Compute an actual row count by querying the tables directly**.</span></span>  
  
 <span data-ttu-id="3eb5b-108">**比較總和檢查碼來確認資料列資料**</span><span class="sxs-lookup"><span data-stu-id="3eb5b-108">**Compare checksums to verify row data**</span></span>  
 <span data-ttu-id="3eb5b-109">除了統計「發行者」與「訂閱者」上的資料列數量之外，也會使用二進位總和檢查碼演算法計算所有資料的總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="3eb5b-109">In addition to taking a count of rows at the Publisher and Subscriber, a checksum of all the data is calculated using the binary checksum algorithm.</span></span> <span data-ttu-id="3eb5b-110">如果資料列計數失敗，就不會執行總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="3eb5b-110">If the row count fails, the checksum is not performed.</span></span>  
  
 <span data-ttu-id="3eb5b-111">**完成驗證之後停止散發代理程式。**</span><span class="sxs-lookup"><span data-stu-id="3eb5b-111">**Stop the Distribution Agent after the validation has completed**</span></span>  
 <span data-ttu-id="3eb5b-112">依預設，散發代理程式會持續執行。</span><span class="sxs-lookup"><span data-stu-id="3eb5b-112">By default, the Distribution Agent runs continuously.</span></span> <span data-ttu-id="3eb5b-113">選取此選項即可在執行驗證之後停止代理程式。</span><span class="sxs-lookup"><span data-stu-id="3eb5b-113">Select this option to stop the agent after validation is performed.</span></span> <span data-ttu-id="3eb5b-114">此選項可以讓您在繼續複寫資料至訂閱者之前，先檢查驗證是否已成功。</span><span class="sxs-lookup"><span data-stu-id="3eb5b-114">This allows you to check whether validation was successful before continuing to replicate data to the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb5b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eb5b-115">See Also</span></span>  
 <span data-ttu-id="3eb5b-116">[驗證訂閱者端的資料](validate-data-at-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="3eb5b-116">[Validate Data at the Subscriber](validate-data-at-the-subscriber.md) </span></span>  
 [<span data-ttu-id="3eb5b-117">驗證複寫的資料</span><span class="sxs-lookup"><span data-stu-id="3eb5b-117">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
