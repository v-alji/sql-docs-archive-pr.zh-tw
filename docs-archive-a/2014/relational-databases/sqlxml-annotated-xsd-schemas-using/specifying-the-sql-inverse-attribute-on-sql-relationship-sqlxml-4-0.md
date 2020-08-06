---
title: 在 sql： relationship (SQLXML 4.0) 上指定 sql：反向屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- bulk load [SQLXML]
- inverse attribute
- relationships [SQLXML], inverse orders
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- updategrams [SQLXML], relationships
- sql:inverse
ms.assetid: 08904cbd-9c86-493d-90c3-f5e1d13ce59d
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b0781102371b98cced72a5a0edee70c9567c372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595901"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a><span data-ttu-id="e3220-102">針對 sql:relationship 指定 sql:inverse 屬性 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="e3220-102">Specifying the sql:inverse Attribute on sql:relationship (SQLXML 4.0)</span></span>
  <span data-ttu-id="e3220-103">只有當 XSD 結構描述用於大量載入或由 Updategram 所使用時，`sql:inverse` 屬性才有用。</span><span class="sxs-lookup"><span data-stu-id="e3220-103">The `sql:inverse` attribute is useful only when the XSD schema is used for either bulk load or by an updategram.</span></span> <span data-ttu-id="e3220-104">`sql:inverse`屬性可以在元素上指定 **\<sql:relationship>** 。</span><span class="sxs-lookup"><span data-stu-id="e3220-104">The `sql:inverse` attribute can be specified on the **\<sql:relationship>** element.</span></span> <span data-ttu-id="e3220-105">在 Updategram 中，Updategram 邏輯會解譯結構描述，以便判斷 Updategram 作業所更新的資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="e3220-105">In updategrams, the updategram logic interprets the schema in determining the tables and columns that are updated by the updategram operation.</span></span> <span data-ttu-id="e3220-106">在結構描述中指定的父子式關聯性會判斷修改記錄 (插入或刪除) 的順序。</span><span class="sxs-lookup"><span data-stu-id="e3220-106">The parent-child relationships that are specified in the schema determine the order in which the records are modified (inserted or deleted).</span></span>  
  
 <span data-ttu-id="e3220-107">如果您有 XSD 結構描述，而且其父子式關聯性是以對應資料庫資料行之間主索引鍵/外部索引鍵關聯性的反向順序所指定，則插入或刪除 Updategram 作業將會由於主索引鍵/外部索引鍵違規而失敗。</span><span class="sxs-lookup"><span data-stu-id="e3220-107">If you have an XSD schema in which the parent-child relationship is specified in the inverse order of the primary-key/foreign-key relationship between the corresponding database columns, the insert or delete updategram operation will fail because of the primary-key/foreign-key violation.</span></span> <span data-ttu-id="e3220-108">在這種情況下， `sql:inverse` 屬性會在專案中指定 (`sql:inverse="true"`) **\<sql:relationship>** ，而 updategram 邏輯則會反轉其在架構中指定之父子式關聯性的轉譯。</span><span class="sxs-lookup"><span data-stu-id="e3220-108">In such cases, the `sql:inverse` attribute is specified (`sql:inverse="true"`) in the **\<sql:relationship>** element, and the updategram logic inverses its interpretation of the parent-child relationship specified in the schema.</span></span>  
  
 <span data-ttu-id="e3220-109">`sql:inverse` 屬性會接受布林值 (0 = false，1 = true)。</span><span class="sxs-lookup"><span data-stu-id="e3220-109">The `sql:inverse` attribute takes a Boolean value (0=false, 1=true).</span></span> <span data-ttu-id="e3220-110">可接受的值為 0、1、true 和 false。</span><span class="sxs-lookup"><span data-stu-id="e3220-110">The acceptable values are 0, 1, true, and false.</span></span>  
  
 <span data-ttu-id="e3220-111">如需使用批註的實用範例 `sql:inverse` ，請參閱[在 Updategram 中指定批註式對應架構](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="e3220-111">For a working sample using the `sql:inverse` annotation, see [Specifying an Annotated Mapping Schema in an Updategram](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3220-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3220-112">See Also</span></span>  
 [<span data-ttu-id="e3220-113">使用 sql： relationship 指定關聯性 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e3220-113">Specifying Relationships Using sql:relationship &#40;SQLXML 4.0&#41;</span></span>](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
