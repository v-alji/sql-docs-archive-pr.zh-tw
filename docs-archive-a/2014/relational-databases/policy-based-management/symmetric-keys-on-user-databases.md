---
title: 使用者資料庫上的對稱金鑰 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ca0fb62ccb32ce244e1087281997dcd9929df89c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594001"
---
# <a name="symmetric-keys-on-user-databases"></a><span data-ttu-id="a4e18-102">使用者資料庫上的對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="a4e18-102">Symmetric Keys on User Databases</span></span>
  <span data-ttu-id="a4e18-103">此規則會檢查長度少於 128 個位元組的金鑰是否不使用 RC2 或 RC4 加密演算法。</span><span class="sxs-lookup"><span data-stu-id="a4e18-103">This rule checks whether keys that have a length of less than 128 bytes do not use the RC2 or RC4 encryption algorithm.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="a4e18-104">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="a4e18-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="a4e18-105">使用 AES 128 位元或更大的位元來建立對稱金鑰進行資料加密。</span><span class="sxs-lookup"><span data-stu-id="a4e18-105">Use AES 128 bit or larger to create symmetric keys for data encryption.</span></span> <span data-ttu-id="a4e18-106">如果作業系統不支援 AES，請使用 3DES。</span><span class="sxs-lookup"><span data-stu-id="a4e18-106">If AES is not supported by your operating system, use 3DES.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="a4e18-107">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="a4e18-107">For More Information</span></span>  
 [<span data-ttu-id="a4e18-108">選擇加密演算法</span><span class="sxs-lookup"><span data-stu-id="a4e18-108">Choose an Encryption Algorithm</span></span>](../security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4e18-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4e18-109">See Also</span></span>  
 [<span data-ttu-id="a4e18-110">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="a4e18-110">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
