---
title: 保留字 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c54bb371cd8f797cfb36f015387e0e21339c0426
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596754"
---
# <a name="reserved-words-master-data-services"></a><span data-ttu-id="b573f-102">保留字 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b573f-102">Reserved Words (Master Data Services)</span></span>
  <span data-ttu-id="b573f-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，當您建立模型物件或成員時，無法使用某些字詞。</span><span class="sxs-lookup"><span data-stu-id="b573f-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], when you create model objects or members, some words cannot be used.</span></span> <span data-ttu-id="b573f-104">使用這些字詞可能會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="b573f-104">Using these words may cause errors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b573f-105">您也應該對使用特殊字元 (符號、連字號等) 加以限制。</span><span class="sxs-lookup"><span data-stu-id="b573f-105">You should also limit your use of special characters (symbols, hyphenation, etc.).</span></span>  
  
-   [<span data-ttu-id="b573f-106">模型</span><span class="sxs-lookup"><span data-stu-id="b573f-106">Models</span></span>](#models)  
  
-   [<span data-ttu-id="b573f-107">實體</span><span class="sxs-lookup"><span data-stu-id="b573f-107">Entities</span></span>](#entities)  
  
-   [<span data-ttu-id="b573f-108">明確階層</span><span class="sxs-lookup"><span data-stu-id="b573f-108">Explicit Hierarchies</span></span>](#exhierarchies)  
  
-   [<span data-ttu-id="b573f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b573f-109">Attributes</span></span>](#attributes)  
  
-   [<span data-ttu-id="b573f-110">成員</span><span class="sxs-lookup"><span data-stu-id="b573f-110">Members</span></span>](#members)  
  
##  <a name="models"></a><a name="models"></a><span data-ttu-id="b573f-111">機型</span><span class="sxs-lookup"><span data-stu-id="b573f-111">Models</span></span>  
 <span data-ttu-id="b573f-112">如果您建立一個名稱設定為 **Name**的模型，請勿選取 **[建立與模型同名的實體]** ，因為 **Name** 無法用於實體的名稱。</span><span class="sxs-lookup"><span data-stu-id="b573f-112">If you create a model with the name set to **Name**, do not select **Create entity with same name as model** because **Name** cannot be used for the name of an entity.</span></span>  
  
##  <a name="entities"></a><a name="entities"></a><span data-ttu-id="b573f-113">條目</span><span class="sxs-lookup"><span data-stu-id="b573f-113">Entities</span></span>  
 <span data-ttu-id="b573f-114">您無法針對實體名稱使用 **Name** 或 **Code**。</span><span class="sxs-lookup"><span data-stu-id="b573f-114">For entity names, you cannot use **Name** or **Code**.</span></span>  
  
##  <a name="explicit-hierarchies"></a><a name="exhierarchies"></a><span data-ttu-id="b573f-115">明確階層</span><span class="sxs-lookup"><span data-stu-id="b573f-115">Explicit Hierarchies</span></span>  
 <span data-ttu-id="b573f-116">您無法針對明確階層名稱使用 **Name** 或 **Code**。</span><span class="sxs-lookup"><span data-stu-id="b573f-116">For explicit hierarchy names, you cannot use **Name** or **Code**.</span></span>  
  
##  <a name="attributes"></a><a name="attributes"></a><span data-ttu-id="b573f-117">特性</span><span class="sxs-lookup"><span data-stu-id="b573f-117">Attributes</span></span>  
  
-   <span data-ttu-id="b573f-118">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="b573f-118">**ID**</span></span>  
  
-   <span data-ttu-id="b573f-119">**Code**</span><span class="sxs-lookup"><span data-stu-id="b573f-119">**Code**</span></span>  
  
-   <span data-ttu-id="b573f-120">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b573f-120">**Name**</span></span>  
  
-   <span data-ttu-id="b573f-121">**EnterDTM**</span><span class="sxs-lookup"><span data-stu-id="b573f-121">**EnterDTM**</span></span>  
  
-   <span data-ttu-id="b573f-122">**EnterUserID**</span><span class="sxs-lookup"><span data-stu-id="b573f-122">**EnterUserID**</span></span>  
  
-   <span data-ttu-id="b573f-123">**EnterUserName**</span><span class="sxs-lookup"><span data-stu-id="b573f-123">**EnterUserName**</span></span>  
  
-   <span data-ttu-id="b573f-124">**LastChgDTM**</span><span class="sxs-lookup"><span data-stu-id="b573f-124">**LastChgDTM**</span></span>  
  
-   <span data-ttu-id="b573f-125">**LastChgUserID**</span><span class="sxs-lookup"><span data-stu-id="b573f-125">**LastChgUserID**</span></span>  
  
-   <span data-ttu-id="b573f-126">**Status_ID**</span><span class="sxs-lookup"><span data-stu-id="b573f-126">**Status_ID**</span></span>  
  
-   <span data-ttu-id="b573f-127">**ValidationStatus_ID**</span><span class="sxs-lookup"><span data-stu-id="b573f-127">**ValidationStatus_ID**</span></span>  
  
-   <span data-ttu-id="b573f-128">**Version_ID**</span><span class="sxs-lookup"><span data-stu-id="b573f-128">**Version_ID**</span></span>  
  
##  <a name="members"></a><a name="members"></a><span data-ttu-id="b573f-129">屬於</span><span class="sxs-lookup"><span data-stu-id="b573f-129">Members</span></span>  
 <span data-ttu-id="b573f-130">對於成員而言，您無法針對 **[Code]** 屬性值使用 **MDMMemberStatus** 或 **ROOT** 。</span><span class="sxs-lookup"><span data-stu-id="b573f-130">For members, you cannot use **MDMMemberStatus** or **ROOT** for the **Code** attribute value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b573f-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b573f-131">See Also</span></span>  
 [<span data-ttu-id="b573f-132">Master Data Services 概觀</span><span class="sxs-lookup"><span data-stu-id="b573f-132">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
  
