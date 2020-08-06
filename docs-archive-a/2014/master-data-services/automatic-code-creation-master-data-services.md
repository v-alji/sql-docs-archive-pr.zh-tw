---
title: 自動建立代碼 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9adbd5e1-f28c-4fb5-afa7-082de2831f3e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9c12e000b2f6ff2ecad07bd62f8c6c05afa36f82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584625"
---
# <a name="automatic-code-creation-master-data-services"></a><span data-ttu-id="36a27-102">自動建立代碼 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="36a27-102">Automatic Code Creation (Master Data Services)</span></span>
  <span data-ttu-id="36a27-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以針對 Code 屬性，或針對其他任何數值屬性，自動產生數值。</span><span class="sxs-lookup"><span data-stu-id="36a27-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], numeric values can be automatically generated for the Code attribute, or for any other numeric attribute.</span></span> <span data-ttu-id="36a27-104">自動產生代碼時，系統不會防止您針對代碼輸入其他值，但是會自動設定初始值。</span><span class="sxs-lookup"><span data-stu-id="36a27-104">When codes are generated automatically, you are not prevented from entering other values for codes; rather an initial value is automatically set.</span></span>  
  
## <a name="generating-code-values"></a><span data-ttu-id="36a27-105">產生代碼值</span><span class="sxs-lookup"><span data-stu-id="36a27-105">Generating Code Values</span></span>  
 <span data-ttu-id="36a27-106">管理員可以編輯相關實體的屬性，藉以設定 Code 屬性的自動產生值。</span><span class="sxs-lookup"><span data-stu-id="36a27-106">Administrators can configure automatically-generated values for the Code attribute by editing the associated entity's properties.</span></span> <span data-ttu-id="36a27-107">他們可以指定一個初始值，而且每個後續的值以一遞增。</span><span class="sxs-lookup"><span data-stu-id="36a27-107">They can specify an initial value, and each subsequent value is increased by one.</span></span>  
  
 <span data-ttu-id="36a27-108">當您使用其中一種工具或暫存處理序，將 Code 值輸入至 MDS 時，可以將 Code 值留空，就會自動產生 Code 值。</span><span class="sxs-lookup"><span data-stu-id="36a27-108">When you enter Code values into MDS, either in one of the tools or by using the staging process, you can leave the Code value blank and a Code value will be automatically generated.</span></span> <span data-ttu-id="36a27-109">或者，您也可以指定自己選擇的 Code 值。</span><span class="sxs-lookup"><span data-stu-id="36a27-109">Or you can specify a Code value of your choice.</span></span>  
  
## <a name="generating-other-attribute-values"></a><span data-ttu-id="36a27-110">產生其他屬性值</span><span class="sxs-lookup"><span data-stu-id="36a27-110">Generating Other Attribute Values</span></span>  
 <span data-ttu-id="36a27-111">管理員可以透過建立商務規則，為 Code 以外的其他屬性自動產生值。</span><span class="sxs-lookup"><span data-stu-id="36a27-111">Administrators can automatically generate values for attributes other than Code by creating business rules.</span></span> <span data-ttu-id="36a27-112">他們可以指定一個初始值，而且可以指定每個後續值的遞增數目。</span><span class="sxs-lookup"><span data-stu-id="36a27-112">They can specify an initial value, and specify the number each subsequent value is incremented by.</span></span>  
  
 <span data-ttu-id="36a27-113">當您使用其中一種工具或暫存處理序，將屬性值輸入至 MDS 時，可以將屬性值留空。</span><span class="sxs-lookup"><span data-stu-id="36a27-113">When you enter attribute values into MDS, either in one of the tools or by using the staging process, you can leave the attribute value blank.</span></span> <span data-ttu-id="36a27-114">套用商務規則時，將會根據最高的現有值遞增這些值。</span><span class="sxs-lookup"><span data-stu-id="36a27-114">When business rules are applied, the values will be incremented based on the highest existing value.</span></span> <span data-ttu-id="36a27-115">例如，如果您的規則是「將屬性預設為從 1 開始產生，並以 4 遞增的值」，而且該屬性最高的目前值為 700，則新增之下一個成員的值將是 704。</span><span class="sxs-lookup"><span data-stu-id="36a27-115">For example, if your rule is "Default attribute to a generated value that starts at 1 and increments by 4" and the highest current value for the attribute is 700, the value for the next member that's added will be 704.</span></span>  
  
## <a name="deleting-automatically-generated-values"></a><span data-ttu-id="36a27-116">刪除自動產生的值</span><span class="sxs-lookup"><span data-stu-id="36a27-116">Deleting Automatically Generated Values</span></span>  
 <span data-ttu-id="36a27-117">在管理員為 Code 屬性啟用自動產生的值時，使用者可能會不小心刪除擁有他們要重複使用之 Code 值的成員。</span><span class="sxs-lookup"><span data-stu-id="36a27-117">After an administrator enables automatically generated values for the Code attribute, users may accidentally delete a member that had a Code value they want to reuse.</span></span> <span data-ttu-id="36a27-118">將會顯示「已刪除的成員已使用成員代碼」錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="36a27-118">The error message "The member code is already used by a member that was deleted" will be displayed.</span></span> <span data-ttu-id="36a27-119">有兩種可能的解決方法：</span><span class="sxs-lookup"><span data-stu-id="36a27-119">There are two possible solutions:</span></span>  
  
-   <span data-ttu-id="36a27-120">在 [**版本管理**] 功能區域中，系統管理員可以反轉刪除成員時所發生的交易。</span><span class="sxs-lookup"><span data-stu-id="36a27-120">In the **Version Management** functional area, an administrator can reverse the transaction that occurred when the member was deleted.</span></span> <span data-ttu-id="36a27-121">不過，這表示會還原所有先前成員的屬性和階層和集合中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="36a27-121">However, this means that all of the former member's attributes and membership in hierarchies and collections is restored.</span></span> <span data-ttu-id="36a27-122">如需詳細資訊，請參閱[反轉交易 &#40;Master Data Services&#41;](reverse-a-transaction-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="36a27-122">For more information, see [Reverse a Transaction &#40;Master Data Services&#41;](reverse-a-transaction-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="36a27-123">管理員可以使用暫存處理序永久刪除成員。</span><span class="sxs-lookup"><span data-stu-id="36a27-123">An administrator can use the staging process to permanently delete the member.</span></span> <span data-ttu-id="36a27-124">如需詳細資訊，請參閱[使用暫存進程停用或刪除成員 &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="36a27-124">For more information, see [Deactivate or Delete Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="36a27-125">相關工作</span><span class="sxs-lookup"><span data-stu-id="36a27-125">Related Tasks</span></span>  
  
|<span data-ttu-id="36a27-126">工作描述</span><span class="sxs-lookup"><span data-stu-id="36a27-126">Task Description</span></span>|<span data-ttu-id="36a27-127">主題</span><span class="sxs-lookup"><span data-stu-id="36a27-127">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="36a27-128">自動為 Code 屬性產生值。</span><span class="sxs-lookup"><span data-stu-id="36a27-128">Automatically generate values for the Code attribute.</span></span>|[<span data-ttu-id="36a27-129">自動產生 Code 屬性值 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="36a27-129">Automatically Generate Code Attribute Values &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/automatically-generate-code-attribute-values-master-data-services.md)|  
|<span data-ttu-id="36a27-130">自動為其他屬性產生值。</span><span class="sxs-lookup"><span data-stu-id="36a27-130">Automatically generate values for other attributes.</span></span>|[<span data-ttu-id="36a27-131">自動產生 Code 以外的屬性值 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="36a27-131">Automatically Generate Attribute Values Other Than Code &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="36a27-132">相關內容</span><span class="sxs-lookup"><span data-stu-id="36a27-132">Related Content</span></span>  
  
-   [<span data-ttu-id="36a27-133">Master Data Services 概觀</span><span class="sxs-lookup"><span data-stu-id="36a27-133">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
-   [<span data-ttu-id="36a27-134">商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="36a27-134">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="36a27-135">實體 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="36a27-135">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)  
  
  
