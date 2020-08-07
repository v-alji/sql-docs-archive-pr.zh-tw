---
title: 導覽存取權 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7af3c16d98320b6fea3d4611e9e4c6d37c6015bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584603"
---
# <a name="navigational-access-master-data-services"></a><span data-ttu-id="dbdfb-102">導覽存取權 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="dbdfb-102">Navigational Access (Master Data Services)</span></span>
  <span data-ttu-id="dbdfb-103">導覽存取權會套用至模型物件安全性 (在 **[模型]** 索引標籤上指派)。</span><span class="sxs-lookup"><span data-stu-id="dbdfb-103">Navigational access applies to model object security, which is assigned on the **Models** tab.</span></span>  
  
 <span data-ttu-id="dbdfb-104">導覽存取權就是比您已指派安全性之層級還高的層級存取權。</span><span class="sxs-lookup"><span data-stu-id="dbdfb-104">Navigational access is the access you get to levels higher than where you've assigned security.</span></span>  
  
 <span data-ttu-id="dbdfb-105">在此範例中，權限會指派給實體，因此導覽存取權是在模型層級授與。</span><span class="sxs-lookup"><span data-stu-id="dbdfb-105">In this example, permissions are assigned to an entity, and so navigational access is granted at the model level.</span></span>  
  
 <span data-ttu-id="dbdfb-106">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span><span class="sxs-lookup"><span data-stu-id="dbdfb-106">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span></span>  
  
 <span data-ttu-id="dbdfb-107">**實體**</span><span class="sxs-lookup"><span data-stu-id="dbdfb-107">**Entities**</span></span>  
  
 <span data-ttu-id="dbdfb-108">當您指派權限給實體、其分葉成員或其合併成員時，導覽存取權就表示您可以讀取或更新所有成員的名稱和程式碼。</span><span class="sxs-lookup"><span data-stu-id="dbdfb-108">When you assign permission to an entity, its leaf members, or its consolidated members, navigational access means you can read or update the name and code for all members.</span></span> <span data-ttu-id="dbdfb-109">您也可以讀取模型名稱。</span><span class="sxs-lookup"><span data-stu-id="dbdfb-109">You can also read the model name.</span></span>  
  
 <span data-ttu-id="dbdfb-110">**屬性**</span><span class="sxs-lookup"><span data-stu-id="dbdfb-110">**Attributes**</span></span>  
  
 <span data-ttu-id="dbdfb-111">當您指派權限給屬性時，導覽存取權就表示您可以讀取或更新實體中所有成員的名稱和程式碼。</span><span class="sxs-lookup"><span data-stu-id="dbdfb-111">When you assign permission to an attribute, navigational access means you can read or update the name and code for all members in the entity.</span></span> <span data-ttu-id="dbdfb-112">您也可以讀取模型名稱。</span><span class="sxs-lookup"><span data-stu-id="dbdfb-112">You can also read the model name.</span></span>  
  
 <span data-ttu-id="dbdfb-113">**集合**</span><span class="sxs-lookup"><span data-stu-id="dbdfb-113">**Collections**</span></span>  
  
 <span data-ttu-id="dbdfb-114">當您指派權限給集合時，您可以讀取或更新名稱、程式碼、描述和擁有者識別碼。</span><span class="sxs-lookup"><span data-stu-id="dbdfb-114">When you assign permissions to collections, you can read or update the name, code, description and owner ID.</span></span> <span data-ttu-id="dbdfb-115">您也可以讀取模型名稱。</span><span class="sxs-lookup"><span data-stu-id="dbdfb-115">You can also read the model name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbdfb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbdfb-116">See Also</span></span>  
 [<span data-ttu-id="dbdfb-117">如何決定權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="dbdfb-117">How Permissions Are Determined &#40;Master Data Services&#41;</span></span>](how-permissions-are-determined-master-data-services.md)  
  
  
