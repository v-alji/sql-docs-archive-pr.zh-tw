---
title: 維度物件 (Analysis Services 多維資料) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], objects
ms.assetid: 7f3d55c7-cccb-4ad0-b6cb-3a2c9992dd68
author: minewiskan
ms.author: owend
ms.openlocfilehash: 02bb6a26b04a2fb79994e192c9c62a7cb362476c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607116"
---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a><span data-ttu-id="f9601-102">維度物件 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="f9601-102">Dimension Objects (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f9601-103">簡單 <xref:Microsoft.AnalysisServices.Dimension> 物件是由基本資訊、屬性和階層所組成。</span><span class="sxs-lookup"><span data-stu-id="f9601-103">A simple <xref:Microsoft.AnalysisServices.Dimension> object is composed of basic information, attributes, and hierarchies.</span></span> <span data-ttu-id="f9601-104">基本資訊包括維度的名稱、維度的類型、資料來源、儲存模式等等。</span><span class="sxs-lookup"><span data-stu-id="f9601-104">Basic information includes the name of the dimension, the type of the dimension, the data source, the storage mode, and others.</span></span> <span data-ttu-id="f9601-105">屬性會定義維度中的實際資料。</span><span class="sxs-lookup"><span data-stu-id="f9601-105">Attributes define the actual data in the dimension.</span></span> <span data-ttu-id="f9601-106">屬性不一定會屬於某個階層，但是階層會從屬性建立而來。</span><span class="sxs-lookup"><span data-stu-id="f9601-106">Attributes do not necessarily belong to a hierarchy, but hierarchies are built from attributes.</span></span> <span data-ttu-id="f9601-107">階層會建立排序的層級清單，並定義一個方式讓使用者可瀏覽維度。</span><span class="sxs-lookup"><span data-stu-id="f9601-107">A hierarchy creates ordered lists of levels, and defines the ways a user can explore the dimension.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f9601-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="f9601-108">In This Section</span></span>  
 <span data-ttu-id="f9601-109">下列主題提供有關如何設計及實作維度物件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f9601-109">The following topics provide more information about how to design and implement dimension objects.</span></span>  
  
|<span data-ttu-id="f9601-110">主題</span><span class="sxs-lookup"><span data-stu-id="f9601-110">Topic</span></span>|<span data-ttu-id="f9601-111">描述</span><span class="sxs-lookup"><span data-stu-id="f9601-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f9601-112">維度 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="f9601-112">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)|<span data-ttu-id="f9601-113">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，維度是 cube 的基礎元件。</span><span class="sxs-lookup"><span data-stu-id="f9601-113">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], dimensions are a fundamental component of cubes.</span></span> <span data-ttu-id="f9601-114">維度會以使用者希望了解的領域來組織資料，例如客戶、商店或員工。</span><span class="sxs-lookup"><span data-stu-id="f9601-114">Dimensions organize data with relation to an area of interest, such as customers, stores, or employees, to users.</span></span>|  
|[<span data-ttu-id="f9601-115">屬性和屬性階層</span><span class="sxs-lookup"><span data-stu-id="f9601-115">Attributes and Attribute Hierarchies</span></span>](attributes-and-attribute-hierarchies.md)|<span data-ttu-id="f9601-116">維度是屬性的集合，這些屬性會繫結至資料來源檢視中資料表或檢視內的一或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="f9601-116">Dimensions are collections of attributes, which are bound to one or more columns in a table or view in the data source view.</span></span>|  
|[<span data-ttu-id="f9601-117">屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="f9601-117">Attribute Relationships</span></span>](attribute-relationships.md)|<span data-ttu-id="f9601-118">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，維度內的屬性永遠都是直接或間接與索引鍵屬性相關。</span><span class="sxs-lookup"><span data-stu-id="f9601-118">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], attributes within a dimension are always related either directly or indirectly to the key attribute.</span></span> <span data-ttu-id="f9601-119">當您根據所有維度屬性都是衍生自相同關聯式資料表的星狀結構描述來定義維度時，便會在索引鍵屬性和維度的每個非索引鍵屬性之間，自動定義屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="f9601-119">When you define a dimension based on a star schema, which is where all dimension attributes are derived from the same relational table, an attribute relationship is automatically defined between the key attribute and each non-key attribute of the dimension.</span></span> <span data-ttu-id="f9601-120">而根據維度屬性是衍生自多個相關資料表的雪花式結構描述來定義維度時，便會自動定義下列的屬性關聯性：</span><span class="sxs-lookup"><span data-stu-id="f9601-120">When you define a dimension based on a snowflake schema, which is where dimension attributes are derived from multiple related tables, an attribute relationship is automatically defined as follows:</span></span><br /><br /> <span data-ttu-id="f9601-121">-索引鍵屬性和每個非索引鍵屬性之間，系結至主維度資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="f9601-121">-   Between the key attribute and each non-key attribute bound to columns in the main dimension table.</span></span><br /><span data-ttu-id="f9601-122">-在索引鍵屬性和系結至連結基礎維度資料表之輔助資料表中外鍵的屬性之間。</span><span class="sxs-lookup"><span data-stu-id="f9601-122">-   Between the key attribute and the attribute bound to the foreign key in the secondary table that links the underlying dimension tables.</span></span><br /><span data-ttu-id="f9601-123">-介於系結至次要資料表外鍵的屬性與從次要資料表系結至資料行的每個非索引鍵屬性之間。</span><span class="sxs-lookup"><span data-stu-id="f9601-123">-   Between the attribute bound to foreign key in the secondary table and each non-key attribute bound to columns from the secondary table.</span></span>|  
  
  
