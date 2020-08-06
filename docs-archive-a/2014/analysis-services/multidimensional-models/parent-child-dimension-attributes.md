---
title: 父子式階層中的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data members [Analysis Services]
- nonleaf members
- MembersWithDataCaption property
- members [Analysis Services]
- members [Analysis Services], data
- leaf members
- parent-child dimensions [Analysis Services]
- MembersWithData property
ms.assetid: 249971cc-4bcd-44f1-8241-bdacc04d3d38
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c4a7e8ba43ac8ede0bd60409f84a6fa233ce182
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698614"
---
# <a name="attributes-in-parent-child-hierarchies"></a><span data-ttu-id="0f239-102">父子式階層中的屬性</span><span class="sxs-lookup"><span data-stu-id="0f239-102">Attributes in Parent-Child Hierarchies</span></span>
  <span data-ttu-id="0f239-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ，通常會對維度中的成員內容進行一般假設。</span><span class="sxs-lookup"><span data-stu-id="0f239-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], a general assumption is usually made about the content of members in a dimension.</span></span> <span data-ttu-id="0f239-104">分葉成員包含直接衍生自基礎資料來源的資料；非分葉成員包含衍生自對子成員執行的彙總。</span><span class="sxs-lookup"><span data-stu-id="0f239-104">Leaf members contain data derived directly from underlying data sources; nonleaf members contain data derived from aggregations performed on child members.</span></span>  
  
 <span data-ttu-id="0f239-105">不過，在父子式階層中，除了從子成員彙總的資料之外，有些非分葉成員也含有衍生自基礎資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="0f239-105">In a parent-child hierarchy, however, some nonleaf members may also have data derived from underlying data sources, in addition to data aggregated from child members.</span></span> <span data-ttu-id="0f239-106">對於在父子式階層中的這些非分葉成員，會建立特殊系統產生的子成員，它們包含基礎事實資料表資料。</span><span class="sxs-lookup"><span data-stu-id="0f239-106">For these nonleaf members in a parent-child hierarchy, special system-generated child members are created that contain the underlying fact table data.</span></span> <span data-ttu-id="0f239-107">它們稱為 *資料成員*，它們包含與非分葉成員直接關聯的值，此值與從非分葉成員之下階計算而來的摘要值無關。</span><span class="sxs-lookup"><span data-stu-id="0f239-107">Referred to as *data members*, they contain a value directly associated with a nonleaf member that is independent of the summary value calculated from the descendants of the nonleaf member.</span></span>  
  
 <span data-ttu-id="0f239-108">資料成員只可供含有父子式階層的維度使用，而且唯有父屬性允許時才會顯示出來。</span><span class="sxs-lookup"><span data-stu-id="0f239-108">Data members are available only to dimensions with parent-child hierarchies, and are visible only if allowed by the parent attribute.</span></span> <span data-ttu-id="0f239-109">您可以使用維度設計師來控制資料成員的可見性。</span><span class="sxs-lookup"><span data-stu-id="0f239-109">You can use Dimension Designer to control the visibility of data members.</span></span> <span data-ttu-id="0f239-110">若要公開資料成員，請將父屬性 (Attribute) 的 `MembersWithData` 屬性 (Property) 設定為 `NonLeafDataVisible.`。若要隱藏父屬性 (Attribute) 所包含的資料成員，請將父屬性 (Attribute) 上的 `MembersWithData` 屬性 (Property) 設定為 `NonLeafDataHidden`。</span><span class="sxs-lookup"><span data-stu-id="0f239-110">To expose data members, set the `MembersWithData` property for the parent attribute to `NonLeafDataVisible.` To hide data members contained by the parent attribute, set the `MembersWithData` property on the parent attribute to `NonLeafDataHidden`.</span></span>  
  
 <span data-ttu-id="0f239-111">這項設定不會覆寫非分葉成員的正常彙總行為；基於彙總用途，一律會將資料成員併入為子成員。</span><span class="sxs-lookup"><span data-stu-id="0f239-111">This setting does not override the normal aggregation behavior for nonleaf members; the data member is always included as a child member for the purposes of aggregation.</span></span> <span data-ttu-id="0f239-112">然而，可使用自訂積存公式來覆寫正常彙總行為。</span><span class="sxs-lookup"><span data-stu-id="0f239-112">However, a custom rollup formula can be used to override the normal aggregation behavior.</span></span> <span data-ttu-id="0f239-113">多維度運算式 (MDX) [DataMember](/sql/mdx/datamember-mdx)函數讓您能夠存取相關聯資料成員的值，而不論屬性的值為何 `MembersWithData` 。</span><span class="sxs-lookup"><span data-stu-id="0f239-113">The Multidimensional Expressions (MDX) [DataMember](/sql/mdx/datamember-mdx) function gives you the ability to access the value of the associated data member regardless of the value of the `MembersWithData` property.</span></span>  
  
 <span data-ttu-id="0f239-114">父屬性的 `MembersWithDataCaption` 屬性提供具名範本給 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]，用以產生資料成員的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="0f239-114">The `MembersWithDataCaption` property of the parent attribute provides [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] with the naming template used to generate member names for data members.</span></span>  
  
## <a name="using-data-members"></a><span data-ttu-id="0f239-115">使用資料成員</span><span class="sxs-lookup"><span data-stu-id="0f239-115">Using Data Members</span></span>  
 <span data-ttu-id="0f239-116">彙總量值與具有父子式階層的組織維度時，資料成員非常有用。</span><span class="sxs-lookup"><span data-stu-id="0f239-116">Data members are useful when aggregating measures along organizational dimensions that have parent-child hierarchies.</span></span> <span data-ttu-id="0f239-117">例如，下圖顯示具有三個層級的維度，而這個維度代表產品的銷售毛額。</span><span class="sxs-lookup"><span data-stu-id="0f239-117">For example, the following diagram shows a dimension that has three levels, representing the gross sales volume of products.</span></span> <span data-ttu-id="0f239-118">第一層顯示所有業務員的銷售毛額。</span><span class="sxs-lookup"><span data-stu-id="0f239-118">The first level shows the gross sales volume for all salespersons.</span></span> <span data-ttu-id="0f239-119">第二層包含依銷售經理分組之所有銷售成員的銷售毛額，而第三層包含依銷售員分組之所有銷售成員的銷售毛額。</span><span class="sxs-lookup"><span data-stu-id="0f239-119">The second level contains the gross sales volume for all sales staff grouped by sales manager, and the third level contains the gross sales volume for all sales staff grouped by salesperson.</span></span>  
  
 <span data-ttu-id="0f239-120">![具有三個層級的銷售毛額維度](../media/agdatamember1.gif "具有三個層級的銷售毛額維度")</span><span class="sxs-lookup"><span data-stu-id="0f239-120">![Gross sales volume dimension with three levels](../media/agdatamember1.gif "Gross sales volume dimension with three levels")</span></span>  
  
 <span data-ttu-id="0f239-121">Sales Manager 1 成員的值通常是彙總 Salesperson 1 和 Salesperson 2 成員的值而衍生。</span><span class="sxs-lookup"><span data-stu-id="0f239-121">Ordinarily, the value of the Sales Manager 1 member would be derived by aggregating the values of the Salesperson 1 and Salesperson 2 members.</span></span> <span data-ttu-id="0f239-122">然而，因為 Sales Manager 1 也可以銷售產品，因此事實資料表中可能會有與 Sales Manager 1 相關的銷售毛額，所以該成員也包含衍生自事實資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="0f239-122">However, because Sales Manager 1 also can sell products, that member may also contain data derived from the fact table, because there may be gross sales associated with Sales Manager 1.</span></span>  
  
 <span data-ttu-id="0f239-123">甚至，每位銷售成員的個別佣金也會不同。</span><span class="sxs-lookup"><span data-stu-id="0f239-123">Moreover, the individual commissions for each sales staff member can vary.</span></span> <span data-ttu-id="0f239-124">在此情況下，銷售經理的佣金計算方式會採用個別銷售毛額佔其銷售員產生之總銷售毛額的兩個不同比率來計算。</span><span class="sxs-lookup"><span data-stu-id="0f239-124">In this case, two different scales are used to compute commissions for the individual gross sales of the sales managers, as opposed to the total of gross sales generated by their salespersons.</span></span> <span data-ttu-id="0f239-125">因此，非分葉成員可存取基礎事實資料表資料就變得非常重要。</span><span class="sxs-lookup"><span data-stu-id="0f239-125">Therefore, it is important to be able to access the underlying fact table data for nonleaf members.</span></span> <span data-ttu-id="0f239-126">在提供與成員相關之銷售員的銷售毛額的前提下，MDX `DataMember` 函數可用來擷取 Sales Manager 1 成員的個人銷售毛額，而自訂積存運算式則可用來從 Sales Manager 1 成員的彙總值中排除該資料成員。</span><span class="sxs-lookup"><span data-stu-id="0f239-126">The MDX `DataMember` function can be used to retrieve the individual gross sales volume of the Sales Manager 1 member, and a custom rollup expression can be used to exclude the data member from the aggregated value of the Sales Manager 1 member, providing the gross sales volume of the salespersons associated with that member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f239-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f239-127">See Also</span></span>  
 <span data-ttu-id="0f239-128">[維度屬性屬性參考](dimension-attribute-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0f239-128">[Dimension Attribute Properties Reference](dimension-attribute-properties-reference.md) </span></span>  
 [<span data-ttu-id="0f239-129">父子式階層</span><span class="sxs-lookup"><span data-stu-id="0f239-129">Parent-Child Hierarchy</span></span>](parent-child-dimension.md)  
  
  
