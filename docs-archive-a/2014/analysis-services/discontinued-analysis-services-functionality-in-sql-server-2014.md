---
title: SQL Server 2014 中已停止的 Analysis Services 功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, backward compatibility
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
- discontinued functionality [Analysis Services]
- unsupported features [Analysis Services]
ms.assetid: 39406be1-9819-4629-9c29-b32fb20bab2e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5414344eb65c907593c9077ee2ba5610b8b397c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606485"
---
# <a name="discontinued-analysis-services-functionality-in-sql-server-2014"></a><span data-ttu-id="9ac7c-102">SQL Server 2014 中已停止的 Analysis Services 功能</span><span class="sxs-lookup"><span data-stu-id="9ac7c-102">Discontinued Analysis Services Functionality in SQL Server 2014</span></span>
  <span data-ttu-id="9ac7c-103">本主題描述 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中不再可用的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="9ac7c-103">This topic describes [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] features that are no longer available in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
## <a name="discontinued-features-in-sssql14"></a><span data-ttu-id="9ac7c-104">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ac7c-104">Discontinued Features in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span></span>  
  
|<span data-ttu-id="9ac7c-105">類別</span><span class="sxs-lookup"><span data-stu-id="9ac7c-105">Category</span></span>|<span data-ttu-id="9ac7c-106">已被取代的功能</span><span class="sxs-lookup"><span data-stu-id="9ac7c-106">Deprecated feature</span></span>|<span data-ttu-id="9ac7c-107">取代</span><span class="sxs-lookup"><span data-stu-id="9ac7c-107">Replacement</span></span>|  
|--------------|------------------------|-----------------|  
|<span data-ttu-id="9ac7c-108">本機 Cube</span><span class="sxs-lookup"><span data-stu-id="9ac7c-108">Local cubes</span></span>|<span data-ttu-id="9ac7c-109">InsertInto 連接字串屬性</span><span class="sxs-lookup"><span data-stu-id="9ac7c-109">InsertInto connection string property</span></span>|<span data-ttu-id="9ac7c-110">填入本機 Cube 的原始連接字串語法已被 Create Global Cube 陳述式取代。</span><span class="sxs-lookup"><span data-stu-id="9ac7c-110">Original connection string syntax for populating local cubes is replaced by the Create Global Cube statement.</span></span> <span data-ttu-id="9ac7c-111">如需詳細資訊，請參閱[CREATE GLOBAL CUBE 語句 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube)。</span><span class="sxs-lookup"><span data-stu-id="9ac7c-111">For more information, see [CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube).</span></span>|  
|<span data-ttu-id="9ac7c-112">本機 Cube</span><span class="sxs-lookup"><span data-stu-id="9ac7c-112">Local cubes</span></span>|<span data-ttu-id="9ac7c-113">CreateCube 連接字串屬性</span><span class="sxs-lookup"><span data-stu-id="9ac7c-113">CreateCube connection string property</span></span>|<span data-ttu-id="9ac7c-114">填入本機 Cube 的原始連接字串語法已被 Create Global Cube 陳述式取代。</span><span class="sxs-lookup"><span data-stu-id="9ac7c-114">Original connection string syntax for populating local cubes is replaced by the Create Global Cube statement.</span></span> <span data-ttu-id="9ac7c-115">如需詳細資訊，請參閱[CREATE GLOBAL CUBE 語句 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube)。</span><span class="sxs-lookup"><span data-stu-id="9ac7c-115">For more information, see [CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube).</span></span>|  
|<span data-ttu-id="9ac7c-116">資料採礦</span><span class="sxs-lookup"><span data-stu-id="9ac7c-116">Data Mining</span></span>|<span data-ttu-id="9ac7c-117">SQL Server 2000 PMML</span><span class="sxs-lookup"><span data-stu-id="9ac7c-117">SQL Server 2000 PMML</span></span>|<span data-ttu-id="9ac7c-118">SQL Server 2000 PMML 功能會產生擁有專屬延伸模組的一種 PMML，以支援由資料採礦演算法所提供，而在 PMML 規格中沒有的獨特功能。</span><span class="sxs-lookup"><span data-stu-id="9ac7c-118">The SQL Server 2000 PMML feature produced a form of PMML that had proprietary extensions to support unique features provided by Data Mining algorithms that were not available in the PMML specification.</span></span> <span data-ttu-id="9ac7c-119">在 SQL Server 2005 中，Analysis Services 已將 PMML 功能更新為較新的 PMML 2.1 標準。</span><span class="sxs-lookup"><span data-stu-id="9ac7c-119">In SQL Server 2005, Analysis Services updated the PMML feature to the newer PMML 2.1 standard.</span></span> <span data-ttu-id="9ac7c-120">因此不再需要 SQL Server 2000 中加入的專屬延伸模組 (不過，在這個版本中仍支援)。</span><span class="sxs-lookup"><span data-stu-id="9ac7c-120">As a result, the proprietary extensions added in SQL Server 2000 are no longer needed, although they are still supported in this release.</span></span>|  
|<span data-ttu-id="9ac7c-121">MDX 陳述式</span><span class="sxs-lookup"><span data-stu-id="9ac7c-121">MDX Statement</span></span>|<span data-ttu-id="9ac7c-122">Create Action 陳述式</span><span class="sxs-lookup"><span data-stu-id="9ac7c-122">Create Action statement</span></span>|<span data-ttu-id="9ac7c-123">包含此陳述式是為了回溯相容性 (Backward Compatibility) 的需要。</span><span class="sxs-lookup"><span data-stu-id="9ac7c-123">This statement is included for backwards compatibility.</span></span> <span data-ttu-id="9ac7c-124">此陳述式已被 Action 物件取代。</span><span class="sxs-lookup"><span data-stu-id="9ac7c-124">It is replaced by the Action object.</span></span> <span data-ttu-id="9ac7c-125">如需如何在最新版本中建立動作的詳細資訊 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，請參閱[&#40;Analysis Services 多維度資料&#41;的動作](multidimensional-models/actions-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="9ac7c-125">For more information about how to create actions in recent versions of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="discontinued-features-in-previous-releases"></a><span data-ttu-id="9ac7c-126">之前的版本已停止的功能</span><span class="sxs-lookup"><span data-stu-id="9ac7c-126">Discontinued Features in Previous Releases</span></span>  
 <span data-ttu-id="9ac7c-127">已不再使用移轉精靈 (用來將 SQL Server 2000 Analysis Services 資料庫移轉至較新版本)，因為已不再支援 SQL Server 2000。</span><span class="sxs-lookup"><span data-stu-id="9ac7c-127">Migration Wizard, used to migrate SQL Server 2000 Analysis Services databases to newer versions, is discontinued because SQL Server 2000 is no longer supported.</span></span>  
  
 <span data-ttu-id="9ac7c-128">此外，也已不再使用決策支援物件 (DSO) 程式庫 (可提供與 SQL Server 2000 Analysis Services 的相容性)，並且此部分從 SQL Server 中剔除。</span><span class="sxs-lookup"><span data-stu-id="9ac7c-128">Decision Support Objects (DSO) library that provided compatibility with SQL Server 2000 Analysis Services databases is also discontinued and no longer part of SQL Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac7c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ac7c-129">See Also</span></span>  
 [<span data-ttu-id="9ac7c-130">Analysis Services 回溯相容性</span><span class="sxs-lookup"><span data-stu-id="9ac7c-130">Analysis Services Backward Compatibility</span></span>](analysis-services-backward-compatibility.md)  
  
  
