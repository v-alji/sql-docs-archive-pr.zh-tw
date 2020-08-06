---
title: 訂閱驗證選項 (合併訂閱) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.mergeoptions.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: 4958c4ab-2025-42ce-b836-6fb4e9e6f24d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 458da0387dbaa1b366348c374748c42946893feb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709118"
---
# <a name="subscription-validation-options-merge-subscriptions"></a><span data-ttu-id="64d05-102">訂閱驗證選項 (合併訂閱)</span><span class="sxs-lookup"><span data-stu-id="64d05-102">Subscription Validation Options (Merge Subscriptions)</span></span>
  <span data-ttu-id="64d05-103">使用 **[訂閱驗證選項]** 對話方塊來指定驗證應該只使用資料列計數，或使用資料列計數與二進位總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="64d05-103">Use the **Subscription Validation Options** dialog box to specify whether validation should use a row count only or a row count and a binary checksum.</span></span>  
  
## <a name="options"></a><span data-ttu-id="64d05-104">選項</span><span class="sxs-lookup"><span data-stu-id="64d05-104">Options</span></span>  
 <span data-ttu-id="64d05-105">**只確認資料列計數**</span><span class="sxs-lookup"><span data-stu-id="64d05-105">**Verify the row counts only**</span></span>  
 <span data-ttu-id="64d05-106">選取以驗證訂閱者端之資料表的資料列數目是否與發行者端之資料表的資料列數目相同。</span><span class="sxs-lookup"><span data-stu-id="64d05-106">Select to validate whether the table at the Subscriber has the same number of rows as the table at the Publisher.</span></span> <span data-ttu-id="64d05-107">此方法不會驗證資料列的內容是否相符。</span><span class="sxs-lookup"><span data-stu-id="64d05-107">This method does not validate that the content of the rows matches.</span></span> <span data-ttu-id="64d05-108">資料列計數驗證提供一種輕量型驗證方法，可讓您發現資料中的問題。</span><span class="sxs-lookup"><span data-stu-id="64d05-108">Row count validation provides a lightweight approach to validation that can make you aware of issues with your data.</span></span>  
  
 <span data-ttu-id="64d05-109">**確認資料列計數並比較總和檢查碼，來確認資料列資料**</span><span class="sxs-lookup"><span data-stu-id="64d05-109">**Verify the row counts and compare checksums to verify the row data**</span></span>  
 <span data-ttu-id="64d05-110">除了統計「發行者」與「訂閱者」上的資料列數量之外，也會使用二進位總和檢查碼演算法計算所有資料的總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="64d05-110">In addition to taking a count of rows at the Publisher and Subscriber, a checksum of all the data is calculated using the binary checksum algorithm.</span></span> <span data-ttu-id="64d05-111">如果資料列計數失敗，就不會執行總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="64d05-111">If the row count fails, the checksum is not performed.</span></span> <span data-ttu-id="64d05-112">此選項對無效 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="64d05-112">This option is not valid for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d05-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64d05-113">See Also</span></span>  
 <span data-ttu-id="64d05-114">[驗證訂閱者端的資料](validate-data-at-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="64d05-114">[Validate Data at the Subscriber](validate-data-at-the-subscriber.md) </span></span>  
 [<span data-ttu-id="64d05-115">驗證複寫的資料</span><span class="sxs-lookup"><span data-stu-id="64d05-115">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
