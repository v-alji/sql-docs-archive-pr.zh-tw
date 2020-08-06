---
title: 系統資料庫上的對稱金鑰 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 28e25ae3-d3dc-45ec-b316-f219512a1a47
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 81c657ededc694ed87df99e0739ff74b1eb9e39b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606239"
---
# <a name="symmetric-keys-on-system-databases"></a><span data-ttu-id="d1ac5-102">系統資料庫上的對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="d1ac5-102">Symmetric Keys on System Databases</span></span>
  <span data-ttu-id="d1ac5-103">此規則會檢查 master、msdb、model 和 tempdb 資料庫中是否有使用者建立的對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="d1ac5-103">This rule checks for user-created symmetric keys in the master, msdb, model, and tempdb databases.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="d1ac5-104">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="d1ac5-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="d1ac5-105">請勿在系統資料庫中建立對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="d1ac5-105">Do not create symmetric keys in the system databases.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="d1ac5-106">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="d1ac5-106">For More Information</span></span>  
 [<span data-ttu-id="d1ac5-107">選擇加密演算法</span><span class="sxs-lookup"><span data-stu-id="d1ac5-107">Choose an Encryption Algorithm</span></span>](../security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a><span data-ttu-id="d1ac5-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1ac5-108">See Also</span></span>  
 [<span data-ttu-id="d1ac5-109">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="d1ac5-109">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
