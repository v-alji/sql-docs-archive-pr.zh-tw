---
title: 結果詳細檢視對話方塊 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.results.f1
- sql12.swb.dmf.policy.resultdetails.f1
ms.assetid: 366f0ff8-722a-40a9-934f-854147e4933d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1c4d669fb1546d27eb8b6ae78e0de8dea5975f24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708222"
---
# <a name="results-detailed-view-dialog-box"></a><span data-ttu-id="edaa6-102">結果詳細檢視對話方塊</span><span class="sxs-lookup"><span data-stu-id="edaa6-102">Results Detailed View Dialog Box</span></span>
  <span data-ttu-id="edaa6-103">當您使用 **[評估原則]** 對話方塊來執行原則並按一下 **[評估]** 之後，此對話方塊會顯示原則評估的結果。</span><span class="sxs-lookup"><span data-stu-id="edaa6-103">This dialog box shows the results of policy evaluation after you have run a policy by using the **Evaluate Policies** dialog box and clicked **Evaluate**.</span></span> <span data-ttu-id="edaa6-104">此對話方塊是唯讀的，而且可幫助您了解哪一個部分的屬性運算式可能失敗。</span><span class="sxs-lookup"><span data-stu-id="edaa6-104">This dialog box is read-only, and helps you understand which part of a property expression might be failing.</span></span>  
  
## <a name="options"></a><span data-ttu-id="edaa6-105">選項。</span><span class="sxs-lookup"><span data-stu-id="edaa6-105">Options</span></span>  
 <span data-ttu-id="edaa6-106">**AndOr**</span><span class="sxs-lookup"><span data-stu-id="edaa6-106">**AndOr**</span></span>  
 <span data-ttu-id="edaa6-107">當有一個以上的屬性運算式存在時，指出屬性運算式為累積或替代式。</span><span class="sxs-lookup"><span data-stu-id="edaa6-107">When more than one property expression is present, indicates whether the property expressions are cumulative or alternative.</span></span>  
  
 <span data-ttu-id="edaa6-108">**結果**</span><span class="sxs-lookup"><span data-stu-id="edaa6-108">**Result**</span></span>  
 <span data-ttu-id="edaa6-109">指出屬性運算式為成功或失敗的圖示。</span><span class="sxs-lookup"><span data-stu-id="edaa6-109">Icon that represents the success or failure of the property expression.</span></span>  
  
 <span data-ttu-id="edaa6-110">**欄位**</span><span class="sxs-lookup"><span data-stu-id="edaa6-110">**Field**</span></span>  
 <span data-ttu-id="edaa6-111">正在模型化之 Facet 的屬性。</span><span class="sxs-lookup"><span data-stu-id="edaa6-111">The property of the facet that is being modeled.</span></span>  
  
 <span data-ttu-id="edaa6-112">**運算子**</span><span class="sxs-lookup"><span data-stu-id="edaa6-112">**Operator**</span></span>  
 <span data-ttu-id="edaa6-113">運算式的運算子，例如 **=** 或 **Like**。</span><span class="sxs-lookup"><span data-stu-id="edaa6-113">The operator for the expression, for example **=** or **Like**.</span></span>  
  
 <span data-ttu-id="edaa6-114">**預期的值**</span><span class="sxs-lookup"><span data-stu-id="edaa6-114">**Expected Value**</span></span>  
 <span data-ttu-id="edaa6-115">將使得屬性運算式成功之欄位的值。</span><span class="sxs-lookup"><span data-stu-id="edaa6-115">The value for the field that will cause the property expression to be successful.</span></span>  
  
 <span data-ttu-id="edaa6-116">**實際值**</span><span class="sxs-lookup"><span data-stu-id="edaa6-116">**Actual Value**</span></span>  
 <span data-ttu-id="edaa6-117">此原則所偵測之欄位的值。</span><span class="sxs-lookup"><span data-stu-id="edaa6-117">The value for the field that was detected by the policy.</span></span>  
  
 <span data-ttu-id="edaa6-118">**原則描述**</span><span class="sxs-lookup"><span data-stu-id="edaa6-118">**Policy description**</span></span>  
 <span data-ttu-id="edaa6-119">此原則的描述。</span><span class="sxs-lookup"><span data-stu-id="edaa6-119">The description of the policy.</span></span>  
  
 <span data-ttu-id="edaa6-120">**其他說明**</span><span class="sxs-lookup"><span data-stu-id="edaa6-120">**Additional help**</span></span>  
 <span data-ttu-id="edaa6-121">按一下此超連結可開啟與此原則相關的網頁。</span><span class="sxs-lookup"><span data-stu-id="edaa6-121">Click the hyperlink to open a Web page that is related to this policy.</span></span> <span data-ttu-id="edaa6-122">當建立此原則，而此原則可能為空白或無法使用時，會設定 [其他說明] 超連結。</span><span class="sxs-lookup"><span data-stu-id="edaa6-122">The Additional Help hyperlink is configured when the policy is created and might be blank or unavailable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edaa6-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edaa6-123">See Also</span></span>  
 <span data-ttu-id="edaa6-124">[原則管理節點 &#40;物件總管&#41;](../../ssms/object/object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="edaa6-124">[Policy Management Node &#40;Object Explorer&#41;](../../ssms/object/object-explorer.md) </span></span>  
 [<span data-ttu-id="edaa6-125">使用原則式管理來管理伺服器</span><span class="sxs-lookup"><span data-stu-id="edaa6-125">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
