---
title: 定義資料庫維度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], defining
ms.assetid: fe84588b-66a3-4100-a1cf-59b21b7adf01
author: minewiskan
ms.author: owend
ms.openlocfilehash: ad5334e71b0f133f80933a7d1702d8ada7565501
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687289"
---
# <a name="define-database-dimensions"></a><span data-ttu-id="9d15a-102">定義資料庫維度</span><span class="sxs-lookup"><span data-stu-id="9d15a-102">Define Database Dimensions</span></span>
  <span data-ttu-id="9d15a-103">使用中的 [維度設計師] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 來設定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案或資料庫中的現有資料庫維度。</span><span class="sxs-lookup"><span data-stu-id="9d15a-103">Use Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to configure an existing database dimension in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="9d15a-104">您可以使用 [維度設計師] 執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9d15a-104">You can use Dimension Designer to do the following:</span></span>  
  
-   <span data-ttu-id="9d15a-105">設定維度層級屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="9d15a-105">Configure the dimension-level properties.</span></span>  
  
-   <span data-ttu-id="9d15a-106">加入及設定維度屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="9d15a-106">Add and configure dimension attributes.</span></span>  
  
-   <span data-ttu-id="9d15a-107">定義及設定使用者自訂階層。</span><span class="sxs-lookup"><span data-stu-id="9d15a-107">Define and configure user-defined hierarchies.</span></span>  
  
-   <span data-ttu-id="9d15a-108">定義及設定屬性 (Attribute) 之間關聯性。</span><span class="sxs-lookup"><span data-stu-id="9d15a-108">Define and configure relationships between attributes.</span></span>  
  
-   <span data-ttu-id="9d15a-109">定義維度翻譯。</span><span class="sxs-lookup"><span data-stu-id="9d15a-109">Define dimension translations.</span></span>  
  
-   <span data-ttu-id="9d15a-110">如果是已處理的維度，您可以瀏覽此維度結構及檢視資料。</span><span class="sxs-lookup"><span data-stu-id="9d15a-110">For processed dimensions, you can browse the dimension structure and view data.</span></span>  
  
 <span data-ttu-id="9d15a-111">修改維度、屬性或階層之後，必須處理該維度，才能檢視變更。</span><span class="sxs-lookup"><span data-stu-id="9d15a-111">After you modify a dimension, attribute, or hierarchy, you must process that dimension to view the changes.</span></span> <span data-ttu-id="9d15a-112">在專案模式下工作時，要在處理之前部署變更至 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9d15a-112">When working in project mode, you deploy the changes to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance before processing.</span></span>  
  
 <span data-ttu-id="9d15a-113">如需如何在維度設計師中開啟維度的詳細資訊，請參閱 [在方案總管中修改或刪除資料庫維度](database-dimensions-modify-or-delete-a-database-dimension-in-solution-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="9d15a-113">For more information about how to open a dimension in Dimension Designer, see [Modify or Delete a Database Dimension in Solution Explorer](database-dimensions-modify-or-delete-a-database-dimension-in-solution-explorer.md).</span></span>  
  
 <span data-ttu-id="9d15a-114">維度設計師有三個不同的索引標籤，下表就是這些索引標籤的描述。</span><span class="sxs-lookup"><span data-stu-id="9d15a-114">Dimension Designer has three different tabs, which are described in the following table.</span></span>  
  
|<span data-ttu-id="9d15a-115">索引標籤</span><span class="sxs-lookup"><span data-stu-id="9d15a-115">Tab</span></span>|<span data-ttu-id="9d15a-116">描述</span><span class="sxs-lookup"><span data-stu-id="9d15a-116">Description</span></span>|  
|---------|-----------------|  
|<span data-ttu-id="9d15a-117">**維度結構**</span><span class="sxs-lookup"><span data-stu-id="9d15a-117">**Dimension Structure**</span></span>|<span data-ttu-id="9d15a-118">使用此索引標籤來處理維度的結構-以檢查或建立維度的資料來源視圖架構、使用屬性，以及組織使用者自訂階層中的屬性。</span><span class="sxs-lookup"><span data-stu-id="9d15a-118">Use this tab to work with the structure of a dimension-to examine or create the data source view schema for a dimension, to work with attributes, and to organize attributes in user-defined hierarchies.</span></span>|  
|<span data-ttu-id="9d15a-119">**屬性關聯性**</span><span class="sxs-lookup"><span data-stu-id="9d15a-119">**Attribute Relationships**</span></span>|<span data-ttu-id="9d15a-120">使用這個索引標籤，即可建立、修改或刪除維度的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="9d15a-120">Use this tab to create, modify, or delete the attribute relationships of a dimension.</span></span>|  
|<span data-ttu-id="9d15a-121">**翻譯**</span><span class="sxs-lookup"><span data-stu-id="9d15a-121">**Translations**</span></span>|<span data-ttu-id="9d15a-122">使用此索引標籤，以不同語言加入及編輯維度中繼資料的翻譯。</span><span class="sxs-lookup"><span data-stu-id="9d15a-122">Use this tab to add and edit translations of dimension metadata in different languages.</span></span>|  
|<span data-ttu-id="9d15a-123">**瀏覽器**</span><span class="sxs-lookup"><span data-stu-id="9d15a-123">**Browser**</span></span>|<span data-ttu-id="9d15a-124">使用此索引標籤，檢查已處理維度的成員，以及檢閱維度中繼資料的翻譯。</span><span class="sxs-lookup"><span data-stu-id="9d15a-124">Use this tab to examine the members of a processed dimension and to review translations of dimension metadata.</span></span>|  
  
 <span data-ttu-id="9d15a-125">下列主題描述可以在 [維度設計師] 中執行的工作。</span><span class="sxs-lookup"><span data-stu-id="9d15a-125">The following topics describe the tasks that you can perform in Dimension Designer.</span></span>  
  
 [<span data-ttu-id="9d15a-126">維度屬性 (attribute) 屬性 (property) 參考</span><span class="sxs-lookup"><span data-stu-id="9d15a-126">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
 <span data-ttu-id="9d15a-127">描述如何定義及設定維度屬性。</span><span class="sxs-lookup"><span data-stu-id="9d15a-127">Describes how to define and configure a dimension attribute.</span></span>  
  
 [<span data-ttu-id="9d15a-128">建立使用者定義階層</span><span class="sxs-lookup"><span data-stu-id="9d15a-128">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)  
 <span data-ttu-id="9d15a-129">描述如何定義及設定使用者自訂階層。</span><span class="sxs-lookup"><span data-stu-id="9d15a-129">Describes how to define and configure a user-defined hierarchy.</span></span>  
  
 [<span data-ttu-id="9d15a-130">定義屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="9d15a-130">Define Attribute Relationships</span></span>](attribute-relationships-define.md)  
 <span data-ttu-id="9d15a-131">描述如何定義及設定屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="9d15a-131">Describes how to define and configure an attribute relationship.</span></span>  
  
 [<span data-ttu-id="9d15a-132">使用商業智慧精靈增強維度</span><span class="sxs-lookup"><span data-stu-id="9d15a-132">Use the Business Intelligence Wizard to Enhance Dimensions</span></span>](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
 <span data-ttu-id="9d15a-133">描述如何使用「商業智慧精靈」來增強維度。</span><span class="sxs-lookup"><span data-stu-id="9d15a-133">Describes how to use the Business Intelligence Wizard to enhance a dimension.</span></span>  
  
  
