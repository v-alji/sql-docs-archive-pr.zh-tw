---
title: 正確的親和性遮罩和相似性輸入輸出遮罩重迭 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 486b4441a20db7630082344fb1f277bba053f3ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710582"
---
# <a name="correct-affinity-mask-and-affinity-input-output-mask-overlap"></a><span data-ttu-id="3f1bf-102">正確的親和性遮罩和相似性輸入輸出遮罩重迭</span><span class="sxs-lookup"><span data-stu-id="3f1bf-102">Correct Affinity Mask and Affinity Input Output Mask Overlap</span></span>
  <span data-ttu-id="3f1bf-103">這個規則會檢查 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體是否有一或多個指派給搭配 affinity mask 和 affinity I/O mask 選項使用的處理器。</span><span class="sxs-lookup"><span data-stu-id="3f1bf-103">This rule checks whether the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has one or more processors that are assigned to be used with both the affinity mask and the affinity I/O mask options.</span></span> <span data-ttu-id="3f1bf-104">在具有一個以上處理器的電腦中，affinity mask 和 affinity I/O mask 選項是用來指派 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所使用的 CPU。</span><span class="sxs-lookup"><span data-stu-id="3f1bf-104">On a computer that has more than one processor, the affinity mask and the affinity I/O mask options are used to designate which CPUs are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3f1bf-105">使用 affinity mask 和 affinity I/O mask 來啟用 CPU 可能會強制處理器過度使用而使效能變慢。</span><span class="sxs-lookup"><span data-stu-id="3f1bf-105">Enabling a CPU with both the affinity mask and the affinity I/O mask can slow performance by forcing the processor to be overused.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="3f1bf-106">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="3f1bf-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="3f1bf-107">當您指定 affinity mask 或 affinity I/O mask 選項時，您應該指定這兩者，但是每一個 CPU 不能啟用超過一次。</span><span class="sxs-lookup"><span data-stu-id="3f1bf-107">When you specify either the affinity mask or the affinity I/O mask options, you should specify both, but only enable each CPU no more than once.</span></span>  
  
 <span data-ttu-id="3f1bf-108">請勿同時在 affinity mask 選項和 affinity I/O mask 選項內啟用相同的 CPU。</span><span class="sxs-lookup"><span data-stu-id="3f1bf-108">Do not enable the same CPU in both the affinity mask option and the affinity I/O mask option.</span></span> <span data-ttu-id="3f1bf-109">對應到每個 CPU 的位元應屬於下列三種情況之一：</span><span class="sxs-lookup"><span data-stu-id="3f1bf-109">The bits that correspond to each CPU should be in one of the following states:</span></span>  
  
-   <span data-ttu-id="3f1bf-110">affinity mask 選項和 affinity I/O mask 選項內的 0</span><span class="sxs-lookup"><span data-stu-id="3f1bf-110">0 in both the affinity mask option and the affinity I/O mask option</span></span>  
  
-   <span data-ttu-id="3f1bf-111">affinity mask 選項內的 0 和 affinity I/O mask 選項內的 1</span><span class="sxs-lookup"><span data-stu-id="3f1bf-111">0 in the affinity mask option and 1 in the affinity I/O mask option</span></span>  
  
-   <span data-ttu-id="3f1bf-112">affinity mask 選項內的 1 和 affinity I/O mask 選項內的 0</span><span class="sxs-lookup"><span data-stu-id="3f1bf-112">1 in the affinity mask option and 0 in the affinity I/O mask option</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="3f1bf-113">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="3f1bf-113">For More Information</span></span>  
 [<span data-ttu-id="3f1bf-114">affinity mask 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="3f1bf-114">affinity mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)  
  
 [<span data-ttu-id="3f1bf-115">affinity Input-Output mask 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="3f1bf-115">affinity Input-Output mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)  
  
 [<span data-ttu-id="3f1bf-116">affinity64 mask 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="3f1bf-116">affinity64 mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md)  
  
 [<span data-ttu-id="3f1bf-117">affinity64 輸入輸出伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="3f1bf-117">affinity64 Input-Output mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="3f1bf-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f1bf-118">See Also</span></span>  
 [<span data-ttu-id="3f1bf-119">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="3f1bf-119">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
