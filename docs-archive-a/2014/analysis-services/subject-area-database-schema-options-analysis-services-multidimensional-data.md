---
title: 主題領域資料庫架構選項 (架構產生嚮導)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.schemagenwizard.subjectareaschemaopts.f1
ms.assetid: 4c109bb8-e19d-412b-908f-bfdd7f872439
author: minewiskan
ms.author: owend
ms.openlocfilehash: 98460332478d02de823addcd113fb9c1e87d6958
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594718"
---
# <a name="subject-area-database-schema-options-schema-generation-wizard-analysis-services---multidimensional-data"></a><span data-ttu-id="b0212-102">主題領域資料庫結構描述選項 (結構描述產生精靈) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="b0212-102">Subject Area Database Schema Options (Schema Generation Wizard) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="b0212-103">使用 **[主題領域資料庫結構描述選項]** 頁面來控制如何產生結構描述，以及定義如何保留資料。</span><span class="sxs-lookup"><span data-stu-id="b0212-103">Use the **Subject Area Database Schema Options** page to control how the schema is generated, as well as to define how data is preserved.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b0212-104">選項</span><span class="sxs-lookup"><span data-stu-id="b0212-104">Options</span></span>  
 <span data-ttu-id="b0212-105">**主控結構描述**</span><span class="sxs-lookup"><span data-stu-id="b0212-105">**Owning schema**</span></span>  
 <span data-ttu-id="b0212-106">指定新主題領域資料庫內之結構描述的名稱。</span><span class="sxs-lookup"><span data-stu-id="b0212-106">Specifies the name of the schema within the new subject area database.</span></span>  
  
 <span data-ttu-id="b0212-107">**在維度資料表上建立主索引鍵**</span><span class="sxs-lookup"><span data-stu-id="b0212-107">**Create primary keys on dimension tables**</span></span>  
 <span data-ttu-id="b0212-108">在產生的結構描述中，於維度資料表上建立主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b0212-108">Creates primary keys on the dimension tables in the generated schema.</span></span> <span data-ttu-id="b0212-109">如果您沒有選取此選項，將不會產生任何索引。</span><span class="sxs-lookup"><span data-stu-id="b0212-109">No index is generated if you do not select this option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b0212-110">如果您沒有選取此選項，將會強制執行參考完整性。</span><span class="sxs-lookup"><span data-stu-id="b0212-110">If you do not select this option, referential integrity is enforced.</span></span>  
  
 <span data-ttu-id="b0212-111">**建立索引**</span><span class="sxs-lookup"><span data-stu-id="b0212-111">**Create indexes**</span></span>  
 <span data-ttu-id="b0212-112">在產生的結構描述中，於外部索引鍵資料行上建立索引。</span><span class="sxs-lookup"><span data-stu-id="b0212-112">Creates indexes on foreign key columns in the generated schema.</span></span>  
  
 <span data-ttu-id="b0212-113">**強制執行參考完整性**</span><span class="sxs-lookup"><span data-stu-id="b0212-113">**Enforce referential integrity**</span></span>  
 <span data-ttu-id="b0212-114">在產生的結構描述中，強制執行參考完整性。</span><span class="sxs-lookup"><span data-stu-id="b0212-114">Enforces referential integrity within the generated schema.</span></span> <span data-ttu-id="b0212-115">如果您沒有選取此選項，將會建立關聯性但不會強制執行。</span><span class="sxs-lookup"><span data-stu-id="b0212-115">If you do not select this option, relationships are created but not enforced.</span></span>  
  
 <span data-ttu-id="b0212-116">**重新產生時保留資料**</span><span class="sxs-lookup"><span data-stu-id="b0212-116">**Preserve data on regeneration**</span></span>  
 <span data-ttu-id="b0212-117">當精靈完成時，保留主題領域資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="b0212-117">Retains data in the subject area database when the wizard finishes.</span></span> <span data-ttu-id="b0212-118">如果您沒有選取此選項，將會無預警清除主題領域資料庫中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="b0212-118">If you do not select this option, all the data in the subject area database may be erased without warning.</span></span>  
  
 <span data-ttu-id="b0212-119">**擴展時間資料表**</span><span class="sxs-lookup"><span data-stu-id="b0212-119">**Populate time table(s)**</span></span>  
 <span data-ttu-id="b0212-120">指定精靈如何擴展時間資料表。</span><span class="sxs-lookup"><span data-stu-id="b0212-120">Specifies how the wizard populates the time tables.</span></span> <span data-ttu-id="b0212-121">下表描述此選項的可能值。</span><span class="sxs-lookup"><span data-stu-id="b0212-121">The following table describes the possible values for this option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b0212-122">只有在專案模式中使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，從 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 專案中呼叫結構描述產生精靈時，才能啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="b0212-122">This option is enabled only if Schema Generation Wizard is called from an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] in project mode.</span></span>  
  
|<span data-ttu-id="b0212-123">值</span><span class="sxs-lookup"><span data-stu-id="b0212-123">Value</span></span>|<span data-ttu-id="b0212-124">描述</span><span class="sxs-lookup"><span data-stu-id="b0212-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b0212-125">擴展</span><span class="sxs-lookup"><span data-stu-id="b0212-125">Populate</span></span>|<span data-ttu-id="b0212-126">已擴展主題領域時間資料表。</span><span class="sxs-lookup"><span data-stu-id="b0212-126">The subject area time tables are populated.</span></span>|  
|<span data-ttu-id="b0212-127">不要擴展</span><span class="sxs-lookup"><span data-stu-id="b0212-127">Do not populate</span></span>|<span data-ttu-id="b0212-128">不擴展主題領域時間資料表。</span><span class="sxs-lookup"><span data-stu-id="b0212-128">The subject area time tables are not populated.</span></span>|  
|<span data-ttu-id="b0212-129">只有是空的時才擴展</span><span class="sxs-lookup"><span data-stu-id="b0212-129">Populate only if empty</span></span>|<span data-ttu-id="b0212-130">只有主題領域時間資料表是空的時才擴展。</span><span class="sxs-lookup"><span data-stu-id="b0212-130">The subject area time tables are populated only if they are empty.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0212-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0212-131">See Also</span></span>  
 [<span data-ttu-id="b0212-132">架構產生嚮導 F1 說明 &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="b0212-132">Schema Generation Wizard F1 Help &#40;Analysis Services - Multidimensional Data&#41;</span></span>](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md)  
  
  
