---
title: " (SSAS 表格式) 的觀點 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1f78c3a1-ce2c-4e7f-a277-71a657692bea
author: minewiskan
ms.author: owend
ms.openlocfilehash: e11f8be980b99c4e9bd824f281db31e9c3f7d9bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687203"
---
# <a name="perspectives-ssas-tabular"></a><span data-ttu-id="78a70-102">檢視方塊 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="78a70-102">Perspectives (SSAS Tabular)</span></span>
  <span data-ttu-id="78a70-103">表格式模型中的檢視方塊會定義可檢視之模型子集，以提供具體的特定商務或應用程式模型視點。</span><span class="sxs-lookup"><span data-stu-id="78a70-103">Perspectives, in tabular models, define viewable subsets of a model that provide focused, business-specific, or application-specific viewpoints of the model.</span></span>  
  
 <span data-ttu-id="78a70-104">本主題的章節：</span><span class="sxs-lookup"><span data-stu-id="78a70-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="78a70-105">優點</span><span class="sxs-lookup"><span data-stu-id="78a70-105">Benefits</span></span>](#bkmk_understanding)  
  
-   [<span data-ttu-id="78a70-106">測試檢視方塊</span><span class="sxs-lookup"><span data-stu-id="78a70-106">Testing Perspectives</span></span>](#bkmk_testpersp)  
  
-   [<span data-ttu-id="78a70-107">相關工作</span><span class="sxs-lookup"><span data-stu-id="78a70-107">Related Tasks</span></span>](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_understanding"></a> <span data-ttu-id="78a70-108">優點</span><span class="sxs-lookup"><span data-stu-id="78a70-108">Benefits</span></span>  
 <span data-ttu-id="78a70-109">對於要瀏覽的使用者而言，表格式模型可以是很複雜的。</span><span class="sxs-lookup"><span data-stu-id="78a70-109">Tabular models can be very complex for users to explore.</span></span> <span data-ttu-id="78a70-110">單一模型可能代表完整的資料倉儲內容，其中有許多資料表、量值和維度。</span><span class="sxs-lookup"><span data-stu-id="78a70-110">A single model can represent the contents of a complete data warehouse with many tables, measures, and dimensions.</span></span> <span data-ttu-id="78a70-111">對只需要與模型的一小部分進行互動即可滿足其商業智慧和報表需求的使用者而言，這樣的複雜性令人望而生畏。</span><span class="sxs-lookup"><span data-stu-id="78a70-111">Such complexity can be daunting to users who may only need to interact with a small part of the model in order to satisfy their business intelligence and reporting requirements.</span></span>  
  
 <span data-ttu-id="78a70-112">在檢視方塊中，資料表、資料行和量值 (包括 KPI) 是定義為欄位物件。</span><span class="sxs-lookup"><span data-stu-id="78a70-112">In a perspective, tables, columns, and measures (including KPIs) are defined as field objects.</span></span> <span data-ttu-id="78a70-113">您可以為每個檢視方塊選取可檢視的欄位。</span><span class="sxs-lookup"><span data-stu-id="78a70-113">You can select the viewable fields for each perspective.</span></span> <span data-ttu-id="78a70-114">例如，單一模型可以包含產品、銷售、財務、員工和地理資料。</span><span class="sxs-lookup"><span data-stu-id="78a70-114">For example, a single model may contain product, sales, financial, employee, and geographic data.</span></span> <span data-ttu-id="78a70-115">雖然銷售部門需要產品、銷售、促銷和地理資料，但可能不需要員工和財務資料。</span><span class="sxs-lookup"><span data-stu-id="78a70-115">While a sales department requires product, sales, promotions, and geography data, they likely do not require employee and financial data.</span></span> <span data-ttu-id="78a70-116">同樣地，人力資源部門不需要促銷和地理資料。</span><span class="sxs-lookup"><span data-stu-id="78a70-116">Similarly, a human resources department does not require data about sales promotions and geography.</span></span>  
  
 <span data-ttu-id="78a70-117">當使用者連接到具有已定義檢視方塊的模型 (做為資料來源) 時，可以選取要使用的檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="78a70-117">When a user connects to a model (as a data source) with defined perspectives, the user can select the perspective they want to use.</span></span> <span data-ttu-id="78a70-118">例如，當連接到 Excel 的模型資料來源時，人力資源使用者可以在 [資料連接精靈] 的 [選取資料表和檢視表] 頁面上選取 [人力資源] 檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="78a70-118">For example, when connecting to a model data source in Excel, users in Human Resources can select the Human Resources perspective on the Select Tables and Views page of the Data Connection Wizard.</span></span> <span data-ttu-id="78a70-119">只有為 [人力資源] 檢視方塊定義的欄位 (資料表、資料行及量值) 才會顯示在 [樞紐分析表欄位清單] 中。</span><span class="sxs-lookup"><span data-stu-id="78a70-119">Only fields (tables, columns, and measures) defined for the Human Resources perspective will be visible in the PivotTable Field List.</span></span>  
  
 <span data-ttu-id="78a70-120">檢視方塊並非用來做為安全性機制，而是用來提供較佳使用者體驗的工具。</span><span class="sxs-lookup"><span data-stu-id="78a70-120">Perspectives are not meant to be used as a security mechanism, but as a tool for providing a better user experience.</span></span> <span data-ttu-id="78a70-121">特定檢視方塊的所有安全性，都是繼承自基礎模型。</span><span class="sxs-lookup"><span data-stu-id="78a70-121">All security for a particular perspective is inherited from the underlying model.</span></span> <span data-ttu-id="78a70-122">如果使用者沒有模型物件的存取權，檢視方塊也無法提供這些存取權。</span><span class="sxs-lookup"><span data-stu-id="78a70-122">Perspectives cannot provide access to model objects to which a user does not already have access.</span></span> <span data-ttu-id="78a70-123">必須先解決模型資料庫的安全性，才能透過檢視方塊提供模型中物件的存取權。</span><span class="sxs-lookup"><span data-stu-id="78a70-123">Security for the model database must be resolved before access to objects in the model can be provided through a perspective.</span></span> <span data-ttu-id="78a70-124">您可使用安全性角色來保護模型中繼資料和資料的安全。</span><span class="sxs-lookup"><span data-stu-id="78a70-124">Security roles can be used to secure model metadata and data.</span></span> <span data-ttu-id="78a70-125">如需詳細資訊，請參閱 [角色 &#40;SSAS 表格式&#41;](roles-ssas-tabular.md)中撰寫的表格式模型專案。</span><span class="sxs-lookup"><span data-stu-id="78a70-125">For more information, see [Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
##  <a name="testing-perspectives"></a><a name="bkmk_testpersp"></a><span data-ttu-id="78a70-126">測試透視圖</span><span class="sxs-lookup"><span data-stu-id="78a70-126">Testing Perspectives</span></span>  
 <span data-ttu-id="78a70-127">在撰寫模型時，您可以使用模型設計師中的 [在 Excel 中進行分析] 功能，來測試所定義之檢視方塊的效率。</span><span class="sxs-lookup"><span data-stu-id="78a70-127">When authoring a model, you can use the Analyze in Excel feature in the model designer to test the efficacy of the perspectives you have defined.</span></span> <span data-ttu-id="78a70-128">請從模型設計師中的 **[模型]** 功能表，按一下 **[在 Excel 中進行分析]**， **[選擇認證和檢視方塊]** 對話方塊即會在 Excel 開啟前出現。</span><span class="sxs-lookup"><span data-stu-id="78a70-128">From the **Model** menu in the model designer, when you click **Analyze in Excel**, before Excel opens, the **Choose Credentials and Perspective** dialog box appears.</span></span> <span data-ttu-id="78a70-129">在這個對話方塊中，您可指定目前的使用者名稱、其他使用者、角色，以及您想用來連接至做為資料來源之模型工作空間資料庫並檢視資料的檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="78a70-129">In this dialog, you can specify the current username, a different user, a role, and a perspective with which you will use to connect to the model workspace database as a data source and view data.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> <span data-ttu-id="78a70-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="78a70-130">Related Tasks</span></span>  
  
|<span data-ttu-id="78a70-131">主題</span><span class="sxs-lookup"><span data-stu-id="78a70-131">Topic</span></span>|<span data-ttu-id="78a70-132">描述</span><span class="sxs-lookup"><span data-stu-id="78a70-132">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="78a70-133">建立及管理檢視方塊 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="78a70-133">Create and Manage Perspectives &#40;SSAS Tabular&#41;</span></span>](perspectives-ssas-tabular.md)|<span data-ttu-id="78a70-134">描述如何使用模型設計師中的 [檢視方塊] 對話方塊，以建立及管理檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="78a70-134">Describes how to create and manage perspectives using the Perspectives dialog box in the model designer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78a70-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78a70-135">See Also</span></span>  
 <span data-ttu-id="78a70-136">[&#40;SSAS 表格式&#41;的角色](roles-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="78a70-136">[Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="78a70-137">階層 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="78a70-137">Hierarchies &#40;SSAS Tabular&#41;</span></span>](hierarchies-ssas-tabular.md)  
  
  
