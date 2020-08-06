---
title: 層級屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
ms.assetid: dabb7335-887b-442a-b67c-4901ba1242b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 553503b9d35142bcc998b4ec12ad2e29d4c66318
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592307"
---
# <a name="level-properties"></a><span data-ttu-id="08fec-102">層級屬性</span><span class="sxs-lookup"><span data-stu-id="08fec-102">Level Properties</span></span> 
  <span data-ttu-id="08fec-103">下表列出並描述使用者自訂階層中的層級屬性。</span><span class="sxs-lookup"><span data-stu-id="08fec-103">The following table lists and describes the properties of a level in a user-defined hierarchy.</span></span>  
  
|<span data-ttu-id="08fec-104">屬性</span><span class="sxs-lookup"><span data-stu-id="08fec-104">Property</span></span>|<span data-ttu-id="08fec-105">描述</span><span class="sxs-lookup"><span data-stu-id="08fec-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="08fec-106">描述</span><span class="sxs-lookup"><span data-stu-id="08fec-106">Description</span></span>|<span data-ttu-id="08fec-107">包含層級的描述。</span><span class="sxs-lookup"><span data-stu-id="08fec-107">Contains the description of the level.</span></span>|  
|<span data-ttu-id="08fec-108">HideMemberIf</span><span class="sxs-lookup"><span data-stu-id="08fec-108">HideMemberIf</span></span>|<span data-ttu-id="08fec-109">指出是否應向用戶端應用程式隱藏層級中的成員，以及何時隱藏。</span><span class="sxs-lookup"><span data-stu-id="08fec-109">Indicates whether and when a member in a level should be hidden from client applications.</span></span> <span data-ttu-id="08fec-110">此屬性可以有下列的值：</span><span class="sxs-lookup"><span data-stu-id="08fec-110">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="08fec-111">永不</span><span class="sxs-lookup"><span data-stu-id="08fec-111">Never</span></span><br /> <span data-ttu-id="08fec-112">永不隱藏成員。</span><span class="sxs-lookup"><span data-stu-id="08fec-112">Members are never hidden.</span></span> <span data-ttu-id="08fec-113">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="08fec-113">This is the default value.</span></span><br /><br /> <span data-ttu-id="08fec-114">OnlyChildWithNoName</span><span class="sxs-lookup"><span data-stu-id="08fec-114">OnlyChildWithNoName</span></span><br /> <span data-ttu-id="08fec-115">當成員是其父系的唯一子系，且成員的名稱為空白時，就會隱藏成員。</span><span class="sxs-lookup"><span data-stu-id="08fec-115">A member is hidden when the member is the only child of its parent and the member's name is empty.</span></span><br /><br /> <span data-ttu-id="08fec-116">OnlyChildWithParentName</span><span class="sxs-lookup"><span data-stu-id="08fec-116">OnlyChildWithParentName</span></span><br /> <span data-ttu-id="08fec-117">當成員是其父系的唯一子系，且成員與其父系有相同的名稱時，就會隱藏成員。</span><span class="sxs-lookup"><span data-stu-id="08fec-117">A member is hidden when the member is the only child of its parent and the member's name is identical to that of its parent.</span></span><br /><br /> <span data-ttu-id="08fec-118">NoName</span><span class="sxs-lookup"><span data-stu-id="08fec-118">NoName</span></span><br /> <span data-ttu-id="08fec-119">當成員的名稱為空白時，就會隱藏成員。</span><span class="sxs-lookup"><span data-stu-id="08fec-119">A member is hidden when the member's name is empty.</span></span><br /><br /> <span data-ttu-id="08fec-120">ParentName</span><span class="sxs-lookup"><span data-stu-id="08fec-120">ParentName</span></span><br /> <span data-ttu-id="08fec-121">當成員與其父系有相同的名稱時，就會隱藏成員。</span><span class="sxs-lookup"><span data-stu-id="08fec-121">A member is hidden when the member's name is identical to that of its parent.</span></span>|  
|<span data-ttu-id="08fec-122">識別碼</span><span class="sxs-lookup"><span data-stu-id="08fec-122">ID</span></span>|<span data-ttu-id="08fec-123">包含層級的唯一識別碼 (ID)。</span><span class="sxs-lookup"><span data-stu-id="08fec-123">Contains the unique identifier (ID) of the level.</span></span>|  
|<span data-ttu-id="08fec-124">名稱</span><span class="sxs-lookup"><span data-stu-id="08fec-124">Name</span></span>|<span data-ttu-id="08fec-125">包含層級的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="08fec-125">Contains the friendly name of the level.</span></span> <span data-ttu-id="08fec-126">依預設，層級與來源屬性有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="08fec-126">By default, the name of a level is the same as the name of the source attribute.</span></span>|  
|<span data-ttu-id="08fec-127">SourceAttribute</span><span class="sxs-lookup"><span data-stu-id="08fec-127">SourceAttribute</span></span>|<span data-ttu-id="08fec-128">包含作為層級基礎之來源屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="08fec-128">Contains the name of the source attribute on which the level is based.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08fec-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08fec-129">See Also</span></span>  
 [<span data-ttu-id="08fec-130">使用者階層屬性</span><span class="sxs-lookup"><span data-stu-id="08fec-130">User Hierarchy Properties</span></span>](user-hierarchies-properties.md)  
  
  
