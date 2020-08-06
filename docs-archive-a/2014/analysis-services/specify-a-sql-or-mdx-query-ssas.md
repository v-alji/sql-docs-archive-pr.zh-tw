---
title: 指定 (SSAS) 的 SQL 或 MDX 查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.specsqlmdxquery.f1
ms.assetid: e4128221-3b46-48be-b0f1-d82477ce6782
author: minewiskan
ms.author: owend
ms.openlocfilehash: bce5e92aaed7a62311e989d6963e4fa5764028ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705477"
---
# <a name="specify-a-sql-or-mdx-query-ssas"></a><span data-ttu-id="66e1f-102">指定 SQL 或 MDX 查詢 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="66e1f-102">Specify a SQL or MDX Query (SSAS)</span></span>
  <span data-ttu-id="66e1f-103">**[資料表匯入精靈]** 的這個頁面可讓您使用 SQL 或 MDX 查詢匯入資料。</span><span class="sxs-lookup"><span data-stu-id="66e1f-103">This page of the **Table Import Wizard** enables you to import data by using a SQL or MDX query.</span></span> <span data-ttu-id="66e1f-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="66e1f-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="66e1f-105">此查詢可以操作已匯入的資料。</span><span class="sxs-lookup"><span data-stu-id="66e1f-105">The query can manipulate the data that is imported.</span></span> <span data-ttu-id="66e1f-106">例如，您可以加入不同資料表的資料，或只選取符合特定準則的資料列。</span><span class="sxs-lookup"><span data-stu-id="66e1f-106">For example, you could join data from different tables or select only rows that meet certain criteria.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="66e1f-107">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="66e1f-107">UI element list</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="66e1f-108">詞彙</span><span class="sxs-lookup"><span data-stu-id="66e1f-108">Term</span></span>|<span data-ttu-id="66e1f-109">定義</span><span class="sxs-lookup"><span data-stu-id="66e1f-109">Definition</span></span>|  
|<span data-ttu-id="66e1f-110">**易記查詢名稱**</span><span class="sxs-lookup"><span data-stu-id="66e1f-110">**Friendly Query Name**</span></span>|<span data-ttu-id="66e1f-111">為查詢輸入唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="66e1f-111">Type a unique name for the query.</span></span> <span data-ttu-id="66e1f-112">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="66e1f-112">This is a required field.</span></span>|  
|<span data-ttu-id="66e1f-113">**SQL 陳述式**</span><span class="sxs-lookup"><span data-stu-id="66e1f-113">**SQL Statement**</span></span>|<span data-ttu-id="66e1f-114">輸入或貼上 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="66e1f-114">Type or paste a SQL statement.</span></span>|  
|<span data-ttu-id="66e1f-115">**驗證**</span><span class="sxs-lookup"><span data-stu-id="66e1f-115">**Validate**</span></span>|<span data-ttu-id="66e1f-116">判斷此 SQL 陳述式是否有效。</span><span class="sxs-lookup"><span data-stu-id="66e1f-116">Determine if the SQL statement is valid.</span></span>|  
|<span data-ttu-id="66e1f-117">**設計**</span><span class="sxs-lookup"><span data-stu-id="66e1f-117">**Design**</span></span>|<span data-ttu-id="66e1f-118">使用查詢設計工具對話方塊來設計 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="66e1f-118">Design a SQL statement by using the query designer dialog box.</span></span> <span data-ttu-id="66e1f-119">如需詳細資訊，請參閱[關聯式查詢設計工具 &#40;SSAS&#41;](relational-query-designer-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="66e1f-119">For more information, see [Relational Query Designer &#40;SSAS&#41;](relational-query-designer-ssas.md).</span></span>|  
  
  
