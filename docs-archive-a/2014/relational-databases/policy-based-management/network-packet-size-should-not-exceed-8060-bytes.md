---
title: 網路封包大小不應超過 8060 個位元組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 01b500cbe65107767d73bc2901b6d5e028b94ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594002"
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a><span data-ttu-id="5973e-102">網路封包大小不應超過 8060 個位元組</span><span class="sxs-lookup"><span data-stu-id="5973e-102">Network Packet Size Should Not Exceed 8060 Bytes</span></span>
  <span data-ttu-id="5973e-103">如果為 sp_configure 'network packet size' 指定的值或是任何已登入使用者的網路封包大小超過 8060 個位元組， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會執行不同的記憶體配置作業。</span><span class="sxs-lookup"><span data-stu-id="5973e-103">If the value specified for sp_configure 'network packet size' or if the network packet size of any logged-in user is more than 8060 bytes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs different memory allocation operations.</span></span> <span data-ttu-id="5973e-104">這會造成未保留給緩衝集區的處理序虛擬位置空間增加。</span><span class="sxs-lookup"><span data-stu-id="5973e-104">This can cause an increase in the process virtual address space that is not reserved for the buffer pool.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="5973e-105">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="5973e-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="5973e-106">網路封包大小不應超過 8060 個位元組。</span><span class="sxs-lookup"><span data-stu-id="5973e-106">The network packet size should not exceed 8060 bytes.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="5973e-107">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="5973e-107">For More Information</span></span>  
 [<span data-ttu-id="5973e-108">Microsoft 知識庫文章 903002</span><span class="sxs-lookup"><span data-stu-id="5973e-108">Microsoft Knowledge Base article 903002</span></span>](https://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a><span data-ttu-id="5973e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5973e-109">See Also</span></span>  
 [<span data-ttu-id="5973e-110">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="5973e-110">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
