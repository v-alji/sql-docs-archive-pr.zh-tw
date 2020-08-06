---
title: 累加式更新對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.incrementalupdate.f1
ms.assetid: d5a5ae27-44e7-4179-b9e2-efbf21d6c5f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6115a5123fd6e72cee0ebccaac5f539be8aebfbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605920"
---
# <a name="incremental-update-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="fe440-102">累加式更新對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="fe440-102">Incremental Update Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="fe440-103">使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的 [累加式更新]\*\*\*\* 對話方塊，即可定義累加更新量值群組與資料分割時使用的設定。</span><span class="sxs-lookup"><span data-stu-id="fe440-103">Use the **Incremental Update** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to define the settings that are used when measure groups and partitions are incrementally updated.</span></span> <span data-ttu-id="fe440-104">在 [處理]\*\*\*\* 對話方塊裡的 [物件清單]\*\*\*\* 方格中，按一下 [設定值]\*\*\*\* 資料行中的 [設定]\*\*\*\*，即可顯示 [累加式更新]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fe440-104">You can display the **Incremental Update** dialog box by clicking **Configure** in the **Settings** column of the **Object list** grid in the **Process** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fe440-105">選項</span><span class="sxs-lookup"><span data-stu-id="fe440-105">Options</span></span>  
  
|<span data-ttu-id="fe440-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="fe440-106">Term</span></span>|<span data-ttu-id="fe440-107">定義</span><span class="sxs-lookup"><span data-stu-id="fe440-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="fe440-108">**量值群組**</span><span class="sxs-lookup"><span data-stu-id="fe440-108">**Measure Group**</span></span>|<span data-ttu-id="fe440-109">選取要進行累加式更新的量值群組。</span><span class="sxs-lookup"><span data-stu-id="fe440-109">Select the measure group to incrementally update.</span></span><br /><br /> <span data-ttu-id="fe440-110">注意：唯有累加地更新 Cube 時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="fe440-110">Note: This option is enabled only if you are incrementally updating a cube.</span></span> <span data-ttu-id="fe440-111">如果您正在累加地更新量值群組或資料分割，則此選項會停用。</span><span class="sxs-lookup"><span data-stu-id="fe440-111">If you are incrementally updating a measure group or partition, this option is disabled.</span></span>|  
|<span data-ttu-id="fe440-112">**資料分割**</span><span class="sxs-lookup"><span data-stu-id="fe440-112">**Partition**</span></span>|<span data-ttu-id="fe440-113">選取要更新的資料分割。</span><span class="sxs-lookup"><span data-stu-id="fe440-113">Select the partition to update.</span></span><br /><br /> <span data-ttu-id="fe440-114">注意：唯有累加地更新 Cube 時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="fe440-114">Note: This option is enabled only if you are incrementally updating a cube.</span></span> <span data-ttu-id="fe440-115">如果您正在累加地更新量值群組或資料分割，則此選項會停用。</span><span class="sxs-lookup"><span data-stu-id="fe440-115">If you are incrementally updating a measure group or partition, this option is disabled.</span></span>|  
|<span data-ttu-id="fe440-116">**資料表**</span><span class="sxs-lookup"><span data-stu-id="fe440-116">**Table**</span></span>|<span data-ttu-id="fe440-117">按一下即可更新來自資料表的物件。</span><span class="sxs-lookup"><span data-stu-id="fe440-117">Click to update the object from a table.</span></span>|  
|<span data-ttu-id="fe440-118">**資料來源或檢視**</span><span class="sxs-lookup"><span data-stu-id="fe440-118">**Data source or view**</span></span>|<span data-ttu-id="fe440-119">選取來源資料表所在的資料來源或資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="fe440-119">Select the data source or data source view in which the source table is located.</span></span><br /><br /> <span data-ttu-id="fe440-120">注意：只有選取 [資料表]\*\*\*\* 時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="fe440-120">Note: This option is enabled only if **Table** is selected.</span></span>|  
|<span data-ttu-id="fe440-121">**資料表結構描述和名稱**</span><span class="sxs-lookup"><span data-stu-id="fe440-121">**Table schema and name**</span></span>|<span data-ttu-id="fe440-122">選取用來擷取資料的來源資料表，以累加地更新 Cube、量值群組，或資料分割。</span><span class="sxs-lookup"><span data-stu-id="fe440-122">Select the source table used to retrieve data for incrementally updating the cube, measure group, or partition.</span></span><br /><br /> <span data-ttu-id="fe440-123">注意：只有選取 [資料表]\*\*\*\* 時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="fe440-123">Note: This option is enabled only if **Table** is selected.</span></span>|  
|<span data-ttu-id="fe440-124">**查詢**</span><span class="sxs-lookup"><span data-stu-id="fe440-124">**Query**</span></span>|<span data-ttu-id="fe440-125">按一下即可更新來自查詢的物件。</span><span class="sxs-lookup"><span data-stu-id="fe440-125">Click to update the object from a query.</span></span>|  
|<span data-ttu-id="fe440-126">**資料來源**</span><span class="sxs-lookup"><span data-stu-id="fe440-126">**Data Source**</span></span>|<span data-ttu-id="fe440-127">選取要查詢之資料表所在的資料來源。</span><span class="sxs-lookup"><span data-stu-id="fe440-127">Select the data source in which the tables to be queried are located.</span></span><br /><br /> <span data-ttu-id="fe440-128">注意：只有選取 [查詢]\*\*\*\* 時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="fe440-128">Note: This option is enabled only if **Query** is selected.</span></span>|  
|<span data-ttu-id="fe440-129">**查詢的文字**</span><span class="sxs-lookup"><span data-stu-id="fe440-129">**Text of the query**</span></span>|<span data-ttu-id="fe440-130">輸入用來擷取資料的查詢文字，以累加地更新 Cube、量值群組，或資料分割。</span><span class="sxs-lookup"><span data-stu-id="fe440-130">Type the text of the query used to retrieve data for incrementally updating the cube, measure group, or partition.</span></span><br /><br /> <span data-ttu-id="fe440-131">注意：只有選取 [查詢]\*\*\*\* 時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="fe440-131">Note: This option is enabled only if **Query** is selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe440-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe440-132">See Also</span></span>  
 <span data-ttu-id="fe440-133">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fe440-133">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="fe440-134">進程對話方塊 &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="fe440-134">Process Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
