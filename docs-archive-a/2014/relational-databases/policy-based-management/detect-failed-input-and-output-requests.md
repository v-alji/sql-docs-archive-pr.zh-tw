---
title: 偵測失敗的輸入輸出要求 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 85373b2e-d9fe-42ef-9653-6e22fe5ecab0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6b3cdc219de06592924ca74cad33ed0027963ac3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686910"
---
# <a name="detect-failed-input-output-request"></a><span data-ttu-id="f83a6-102">偵測失敗的輸入輸出要求</span><span class="sxs-lookup"><span data-stu-id="f83a6-102">Detect Failed Input Output Request</span></span>
  <span data-ttu-id="f83a6-103">這個規則會檢查系統事件記錄檔中是否有 EventId 50。</span><span class="sxs-lookup"><span data-stu-id="f83a6-103">This rule checks the system event log for EventId 50.</span></span> <span data-ttu-id="f83a6-104">這個錯誤是因為失敗的 I/O 要求所造成。</span><span class="sxs-lookup"><span data-stu-id="f83a6-104">This error is caused by a failed I/O request.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="f83a6-105">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="f83a6-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="f83a6-106">如需有關如何排除此錯誤的詳細資訊，請檢閱下列 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知識庫文件：</span><span class="sxs-lookup"><span data-stu-id="f83a6-106">Review the following [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base articles for more information about how to troubleshoot this error:</span></span>  
  
-   [<span data-ttu-id="f83a6-107">Microsoft 知識庫文章 311081</span><span class="sxs-lookup"><span data-stu-id="f83a6-107">Microsoft Knowledge Base article 311081</span></span>](https://go.microsoft.com/fwlink/?linkid=117744)  
  
-   [<span data-ttu-id="f83a6-108">Microsoft 知識庫文章 885688</span><span class="sxs-lookup"><span data-stu-id="f83a6-108">Microsoft Knowledge Base article 885688</span></span>](https://go.microsoft.com/fwlink/?linkid=117745)  
  
  
