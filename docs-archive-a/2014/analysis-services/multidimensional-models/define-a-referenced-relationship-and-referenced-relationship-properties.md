---
title: 定義參考的關聯性及參考的關聯性屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- referenced dimension relationship
- relationships [Analysis Services], referenced dimensions
ms.assetid: 5bb44b41-635b-4398-8fe9-0bfbb142553e
author: minewiskan
ms.author: owend
ms.openlocfilehash: a84cf2ed95ab3660c5a6b3c039dc58351dc43264
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700381"
---
# <a name="define-a-referenced-relationship-and-referenced-relationship-properties"></a><span data-ttu-id="58968-102">定義參考的關聯性及參考的關聯性屬性</span><span class="sxs-lookup"><span data-stu-id="58968-102">Define a Referenced Relationship and Referenced Relationship Properties</span></span>
  <span data-ttu-id="58968-103">參考維度關聯性是在 Cube 設計師的 [維度使用方式]\*\*\*\* 索引標籤上定義的。</span><span class="sxs-lookup"><span data-stu-id="58968-103">A reference dimension relationship is defined on the **Dimension Usage** tab of Cube Designer.</span></span> <span data-ttu-id="58968-104">透過指定下列項目即可定義參考維度關聯性：</span><span class="sxs-lookup"><span data-stu-id="58968-104">The reference dimension relationship is defined by specifying the following:</span></span>  
  
-   <span data-ttu-id="58968-105">要聯結的中繼維度。</span><span class="sxs-lookup"><span data-stu-id="58968-105">The intermediate dimension to which to join.</span></span> <span data-ttu-id="58968-106">這可以是一般維度或另一個參考維度。</span><span class="sxs-lookup"><span data-stu-id="58968-106">This can be a regular dimension or another reference dimension.</span></span>  
  
-   <span data-ttu-id="58968-107">在量值群組方面，定義可用於彙總之維度最低層級的參考維度屬性。</span><span class="sxs-lookup"><span data-stu-id="58968-107">A reference dimension attribute that defines the lowest level that the dimension is available for aggregation with regard to the measure group.</span></span>  
  
-   <span data-ttu-id="58968-108">對應到參考維度屬性之中繼維度中的 (外部索引鍵) 屬性。</span><span class="sxs-lookup"><span data-stu-id="58968-108">The (foreign key) attribute in the intermediate dimension that corresponds to the reference dimension attribute.</span></span>  
  
 <span data-ttu-id="58968-109">請注意，將參考維度連結到事實資料表的資料行 (通常是參考維度中的索引鍵屬性)，在中繼維度中也必須定義為屬性。</span><span class="sxs-lookup"><span data-stu-id="58968-109">Notice that the column that links the reference dimension to the fact table, which is generally the key attribute in the reference dimension, must also be defined as an attribute in the intermediate dimension.</span></span> <span data-ttu-id="58968-110">當您建立參考維度的鏈結時，請從在鏈結的第一個維度和量值群組之間建立一般關聯性開始。</span><span class="sxs-lookup"><span data-stu-id="58968-110">When you create a chain of reference dimensions, start by creating the regular relationship between the first dimension in the chain and the measure group.</span></span> <span data-ttu-id="58968-111">然後依序建立每一個額外的參考關聯性。</span><span class="sxs-lookup"><span data-stu-id="58968-111">Then create each additional referenced relationship in order.</span></span> <span data-ttu-id="58968-112">只有在維度與量值群組之間具有現有關聯性時，才可建立該維度的參考關聯性。</span><span class="sxs-lookup"><span data-stu-id="58968-112">A referenced relationship can only be made to a dimension that has an existing relationship to the measure group.</span></span>  
  
 <span data-ttu-id="58968-113">當您建立參考維度關聯性時，依預設會具體化維度屬性連結。</span><span class="sxs-lookup"><span data-stu-id="58968-113">When you create a reference dimension relationship, the dimension attribute link is materialized by default.</span></span> <span data-ttu-id="58968-114">在處理期間，具體化維度屬性連結會造成事實資料表與每個資料列的參考維度之間的連結值，在維度的 MOLAP 結構中進行具體化或儲存。</span><span class="sxs-lookup"><span data-stu-id="58968-114">Materializing a dimension attribute link causes the value of the link between the fact table and the reference dimension for each row to be materialized, or stored, in the MOLAP structure for the dimension during processing.</span></span> <span data-ttu-id="58968-115">這對於處理效能和儲存體需求會有些許影響，但可增加查詢效能。</span><span class="sxs-lookup"><span data-stu-id="58968-115">This will have a minor effect on processing performance and storage requirements, but will improve query performance.</span></span>  
  
 <span data-ttu-id="58968-116">在參考維度中，識別在參考維度與對應到維度之主資料表的量值群組之間定義關聯性的屬性，即可指定資料粒度。</span><span class="sxs-lookup"><span data-stu-id="58968-116">In a reference dimension, granularity is specified by identifying the attribute that defines the relationship between a reference dimension and the measure group corresponding to the main table of the dimension.</span></span> <span data-ttu-id="58968-117">當多個參考維度鏈結在一起時，參考是定義從最外層維度到量值群組的關聯性。</span><span class="sxs-lookup"><span data-stu-id="58968-117">When multiple reference dimensions are chained together, the references define the relationship from the outermost dimension to the measure group.</span></span>  
  
  
