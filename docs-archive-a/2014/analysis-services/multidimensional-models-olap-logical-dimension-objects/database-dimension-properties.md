---
title: 資料庫維度屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- metadata [Analysis Services]
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 075548ef-08a3-413c-8ee0-4a074c276fcc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 504e190f4c513a8c999c4d7d7ab9eaabb83298c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598032"
---
# <a name="database-dimension-properties"></a><span data-ttu-id="ae819-102">資料庫維度屬性</span><span class="sxs-lookup"><span data-stu-id="ae819-102">Database Dimension Properties</span></span>
  <span data-ttu-id="ae819-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，維度的特性是由維度的中繼資料所定義，根據各種維度屬性的設定，以及維度所包含的屬性或階層。</span><span class="sxs-lookup"><span data-stu-id="ae819-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the characteristics of a dimension are defined by the metadata for the dimension, based on the settings of various dimension properties, and on the attributes or hierarchies that are contained by the dimension.</span></span> <span data-ttu-id="ae819-104">下表描述 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的維度屬性。</span><span class="sxs-lookup"><span data-stu-id="ae819-104">The following table describes the dimension properties in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="ae819-105">屬性</span><span class="sxs-lookup"><span data-stu-id="ae819-105">Property</span></span>|<span data-ttu-id="ae819-106">描述</span><span class="sxs-lookup"><span data-stu-id="ae819-106">Description</span></span>|  
|--------------|-----------------|  
|`AttributeAllMemberName`|<span data-ttu-id="ae819-107">針對維度中的屬性，指定所有成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="ae819-107">Specifies the name of the All member for attributes in a dimension.</span></span>|  
|`Collation`|<span data-ttu-id="ae819-108">決定維度使用的定序。</span><span class="sxs-lookup"><span data-stu-id="ae819-108">Determines the collation used by the dimension.</span></span>|  
|`CurrentStorageMode`|<span data-ttu-id="ae819-109">包含維度的目前儲存模式。</span><span class="sxs-lookup"><span data-stu-id="ae819-109">Contains the current storage mode for the dimension.</span></span>|  
|`DependsOnDimension`|<span data-ttu-id="ae819-110">包含維度所相依之其他維度的識別碼，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="ae819-110">Contains the ID of another dimension on which the dimension depends, if any.</span></span>|  
|`Description`|<span data-ttu-id="ae819-111">包含維度的描述。</span><span class="sxs-lookup"><span data-stu-id="ae819-111">Contains the description of the dimension.</span></span>|  
|`ErrorConfiguration`|<span data-ttu-id="ae819-112">用來處理重複的索引鍵、未知的索引鍵、錯誤限制、發生錯誤時的動作、錯誤記錄檔，以及 Null 索引鍵處理之可設定的錯誤處理設定。</span><span class="sxs-lookup"><span data-stu-id="ae819-112">Configurable error handling settings for handling of duplicate keys, unknown keys, error limits, action upon error detection, error log file, and null key handling.</span></span>|  
|`ID`|<span data-ttu-id="ae819-113">包含維度的唯一識別碼 (ID)。</span><span class="sxs-lookup"><span data-stu-id="ae819-113">Contains the unique identifier (ID) of the dimension.</span></span>|  
|`Language`|<span data-ttu-id="ae819-114">指定維度的預設語言。</span><span class="sxs-lookup"><span data-stu-id="ae819-114">Specifies the default language for the dimension.</span></span>|  
|`MdxMissingMemberMode`|<span data-ttu-id="ae819-115">決定如何處理多維度運算式 (MDX) 陳述式的遺漏成員。</span><span class="sxs-lookup"><span data-stu-id="ae819-115">Determines how missing members are handled for Multidimensional Expressions (MDX) statements.</span></span>|  
|`MiningModelID`|<span data-ttu-id="ae819-116">包含與資料採礦維度相關之採礦模型的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ae819-116">Contains the ID of the mining model with which the data mining dimension is associated.</span></span> <span data-ttu-id="ae819-117">只有在維度是採礦模型維度時，才可使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ae819-117">This property is applicable only if the dimension is a mining model dimension.</span></span>|  
|`Name`|<span data-ttu-id="ae819-118">指定維度的名稱。</span><span class="sxs-lookup"><span data-stu-id="ae819-118">Specifies the name of the dimension.</span></span>|  
|`ProactiveCaching`|<span data-ttu-id="ae819-119">定義維度的主動式快取設定。</span><span class="sxs-lookup"><span data-stu-id="ae819-119">Defines the proactive cache settings for the dimension.</span></span>|  
|`ProcessingGroup`|<span data-ttu-id="ae819-120">指定處理群組。</span><span class="sxs-lookup"><span data-stu-id="ae819-120">Specifies the processing group.</span></span> <span data-ttu-id="ae819-121">值為 ByAttribute 或 ByTable。</span><span class="sxs-lookup"><span data-stu-id="ae819-121">Values are ByAttribute or ByTable.</span></span> <span data-ttu-id="ae819-122">預設為 `ByAttribute`。</span><span class="sxs-lookup"><span data-stu-id="ae819-122">Default is `ByAttribute`.</span></span>|  
|`ProcessingMode`|<span data-ttu-id="ae819-123">指出是否應在處理期間或處理之後，進行索引和彙總 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ae819-123">Indicates whether [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] should index and aggregate during or after processing.</span></span>|  
|`ProcessingPriority`|<span data-ttu-id="ae819-124">決定背景作業期間之維度的處理優先權 (例如，延遲彙總、索引或叢集)。</span><span class="sxs-lookup"><span data-stu-id="ae819-124">Determines the processing priority of the dimension during background operations such as lazy aggregation, indexing, or clustering.</span></span>|  
|`Source`|<span data-ttu-id="ae819-125">識別維度所繫結的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="ae819-125">Identifies the data source view to which the dimension is bound.</span></span>|  
|`StorageMode`|<span data-ttu-id="ae819-126">決定維度的儲存模式。</span><span class="sxs-lookup"><span data-stu-id="ae819-126">Determines the storage mode for the dimension.</span></span>|  
|`Type`|<span data-ttu-id="ae819-127">指定維度的類型。</span><span class="sxs-lookup"><span data-stu-id="ae819-127">Specifies the type of the dimension.</span></span>|  
|`UnknownMember`|<span data-ttu-id="ae819-128">指出未知的成員是否可見。</span><span class="sxs-lookup"><span data-stu-id="ae819-128">Indicates whether the unknown member is visible.</span></span>|  
|`UnknownMemberName`|<span data-ttu-id="ae819-129">指定維度之未知成員的標題，而這個標題會以維度的預設語言顯示。</span><span class="sxs-lookup"><span data-stu-id="ae819-129">Specifies the caption, in the default language of the dimension, for the unknown member of the dimension.</span></span>|  
|`WriteEnabled`|<span data-ttu-id="ae819-130">指出是否可以使用維度回寫 (受限於安全性權限)。</span><span class="sxs-lookup"><span data-stu-id="ae819-130">Indicates whether dimension writebacks are available (subject to security permissions).</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="ae819-131">如需在使用 null 值和其他資料完整性問題時設定 ErrorConfiguration 和 UnknownMember 屬性值的詳細資訊，請參閱[處理 Analysis Services 2005 中的資料完整性問題](https://go.microsoft.com/fwlink/?LinkId=81891)。</span><span class="sxs-lookup"><span data-stu-id="ae819-131">For more information about setting values for the ErrorConfiguration and UnknownMember properties when working with null values and other data integrity issues, see [Handling Data Integrity Issues in Analysis Services 2005](https://go.microsoft.com/fwlink/?LinkId=81891).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae819-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae819-132">See Also</span></span>  
 <span data-ttu-id="ae819-133">[屬性和屬性階層](attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="ae819-133">[Attributes and Attribute Hierarchies](attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="ae819-134">[使用者階層](user-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="ae819-134">[User Hierarchies](user-hierarchies.md) </span></span>  
 <span data-ttu-id="ae819-135">[維度關聯性](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="ae819-135">[Dimension Relationships](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 [<span data-ttu-id="ae819-136">維度 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="ae819-136">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)  
  
  
