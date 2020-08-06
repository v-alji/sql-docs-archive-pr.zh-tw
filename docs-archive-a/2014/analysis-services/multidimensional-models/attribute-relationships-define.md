---
title: 定義屬性關聯性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
ms.assetid: 9184d344-e96d-4025-ad6f-3f75129746df
author: minewiskan
ms.author: owend
ms.openlocfilehash: a694c68a55de2533c4ce7791d3be865008b6321f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585650"
---
# <a name="define-attribute-relationships"></a><span data-ttu-id="8e113-102">定義屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="8e113-102">Define Attribute Relationships</span></span>
  <span data-ttu-id="8e113-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，屬性是維度的基礎建立區塊。</span><span class="sxs-lookup"><span data-stu-id="8e113-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], attributes are the fundamental building block of a dimension.</span></span> <span data-ttu-id="8e113-104">維度包含一組根據屬性關聯性所組織的屬性。</span><span class="sxs-lookup"><span data-stu-id="8e113-104">A dimension contains a set of attributes that are organized based on attribute relationships.</span></span>  
  
 <span data-ttu-id="8e113-105">針對包含在維度中的每個資料表，有一種屬性關聯性可以建立資料表之重要屬性與該資料表中之其他屬性的關聯性。</span><span class="sxs-lookup"><span data-stu-id="8e113-105">For each table included in a dimension, there is an attribute relationship that relates the table's key attribute to other attributes from that table.</span></span> <span data-ttu-id="8e113-106">建立維度時，您可以建立這種關聯性。</span><span class="sxs-lookup"><span data-stu-id="8e113-106">You create this relationship when you create the dimension.</span></span>  
  
 <span data-ttu-id="8e113-107">屬性關聯性提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="8e113-107">An attribute relationship provides the following advantages:</span></span>  
  
-   <span data-ttu-id="8e113-108">減少維度處理所需的記憶體量。</span><span class="sxs-lookup"><span data-stu-id="8e113-108">Reduces the amount of memory needed for dimension processing.</span></span> <span data-ttu-id="8e113-109">這會加快維度、磁碟分割和查詢的處理速度。</span><span class="sxs-lookup"><span data-stu-id="8e113-109">This speeds up dimension, partition, and query processing.</span></span>  
  
-   <span data-ttu-id="8e113-110">由於儲存體存取速度更快，而且執行計劃的最佳化程度更好，因此可以增加查詢效能。</span><span class="sxs-lookup"><span data-stu-id="8e113-110">Increases query performance because storage access is faster and execution plans are better optimized.</span></span>  
  
-   <span data-ttu-id="8e113-111">假設已沿著關聯性路徑定義使用者自訂階層，則按照彙總設計演算法選取彙總時更有效率。</span><span class="sxs-lookup"><span data-stu-id="8e113-111">Results in the selection of more effective aggregates by the aggregation design algorithms, provided that user-defined hierarchies have been defined along the relationship paths.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8e113-112">如需定義和設定屬性關聯性之重要性和含意的詳細資訊，請參閱《 [SQL Server 2005 Analysis Services 效能指南》](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)中的「加強查詢效能」一節。</span><span class="sxs-lookup"><span data-stu-id="8e113-112">For more information about the importance and implications of defining and configuring attribute relationships, see the section, "Enhancing query performance," in the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
## <a name="attribute-relationship-considerations"></a><span data-ttu-id="8e113-113">屬性關聯性考量</span><span class="sxs-lookup"><span data-stu-id="8e113-113">Attribute Relationship Considerations</span></span>  
 <span data-ttu-id="8e113-114">當基礎資料支援屬性關聯性時，您也應該定義屬性之間的唯一屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="8e113-114">When the underlying data supports it, you should also define unique attribute relationships between attributes.</span></span> <span data-ttu-id="8e113-115">若要定義唯一屬性關聯性，使用 [維度設計師] 的 [屬性關聯性]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8e113-115">To define unique attribute relationships, use the **Attribute Relationships** tab of Dimension Designer.</span></span>  
  
 <span data-ttu-id="8e113-116">具有輸出關聯性的屬性必須具備相對於其相關聯屬性的唯一索引鍵。</span><span class="sxs-lookup"><span data-stu-id="8e113-116">Any attribute that has an outgoing relationship must have a unique key relative to its related attribute.</span></span> <span data-ttu-id="8e113-117">換句話說，來源屬性中的成員在相關聯的屬性中，必須識別一個 (而且只能識別一個) 成員。</span><span class="sxs-lookup"><span data-stu-id="8e113-117">In other words, a member in a source attribute must identify one and only one member in a related attribute.</span></span> <span data-ttu-id="8e113-118">例如，請考量 City -> State 的關聯性。</span><span class="sxs-lookup"><span data-stu-id="8e113-118">For example, consider the relationship, City -> State.</span></span> <span data-ttu-id="8e113-119">在此關聯性中，來源屬性為 [City]，而相關聯的屬性為 [State]。</span><span class="sxs-lookup"><span data-stu-id="8e113-119">In this relationship, the source attribute is City and the related attribute is State.</span></span> <span data-ttu-id="8e113-120">Source 屬性是「多」端，而相關端是多對一關聯性的「一」端。</span><span class="sxs-lookup"><span data-stu-id="8e113-120">The source attribute is the "many" side and the related side is the "one" side of the many-to-one relationship.</span></span> <span data-ttu-id="8e113-121">來源屬性的索引鍵將是 City + State。</span><span class="sxs-lookup"><span data-stu-id="8e113-121">The key for the source attribute would be City + State.</span></span> <span data-ttu-id="8e113-122">如需詳細資訊，請參閱 [建立、修改或刪除屬性關聯性](attribute-relationships-create-modify-or-delete-relationship.md)。</span><span class="sxs-lookup"><span data-stu-id="8e113-122">For more information, see [Create, Modify, or Delete an Attribute Relationship](attribute-relationships-create-modify-or-delete-relationship.md).</span></span>  
  
 <span data-ttu-id="8e113-123">如需屬性 (Attribute) 關聯性之屬性 (Property) 的詳細資訊，請參閱 [設定屬性 (Attribute) 關聯性屬性 (Property)](attribute-relationships-configure-attribute-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="8e113-123">For more information about properties of an attribute relationship, see [Configure Attribute Relationship Properties](attribute-relationships-configure-attribute-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e113-124">如果定義的屬性關聯性錯誤，可能導致查詢結果無效。</span><span class="sxs-lookup"><span data-stu-id="8e113-124">Defining attribute relationships incorrectly can cause invalid query results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e113-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e113-125">See Also</span></span>  
 [<span data-ttu-id="8e113-126">屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="8e113-126">Attribute Relationships</span></span>](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  
