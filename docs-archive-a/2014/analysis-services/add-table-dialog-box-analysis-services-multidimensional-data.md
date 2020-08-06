---
title: '[加入資料表] 對話方塊 (Analysis Services-多維度資料) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.addtable.f1
helpviewer_keywords:
- Add Table dialog box
ms.assetid: b93f841f-0164-4e37-bd08-085aa179ea1f
author: minewiskan
ms.author: owend
ms.openlocfilehash: c038e13706c44891bae021aaf35d04a10b715a97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593243"
---
# <a name="add-table-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="c0e92-102">[ 新增表格 ] 對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="c0e92-102">Add Table Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="c0e92-103">在 [建立具名查詢]\*\*\*\* 對話方塊、[建立輪詢查詢]\*\*\*\* 對話方塊或 [建立處理查詢]\*\*\*\* 對話方塊中建立查詢時，使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [加入資料表]\*\*\*\* 對話方塊，即可加入資料表。</span><span class="sxs-lookup"><span data-stu-id="c0e92-103">Use the **Add Table** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to add a table while creating a query in the **Create Named Query** dialog box, **Create Polling Query** dialog box, or **Create Processing Query** dialog box.</span></span> <span data-ttu-id="c0e92-104">按一下 [建立具名查詢]\*\*\*\* 對話方塊、[建立輪詢查詢]\*\*\*\* 對話方塊或 [建立處理查詢]\*\*\*\* 對話方塊中之 [工具列]\*\*\*\* 窗格的 [加入資料表]\*\*\*\*，即可顯示 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [加入資料表]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c0e92-104">You can display the **Add Table** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] by clicking **Add Table** from the **Toolbar** pane of the **Create Named Query** dialog box, **Create Polling Query** dialog box, or **Create Processing Query** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c0e92-105">選項</span><span class="sxs-lookup"><span data-stu-id="c0e92-105">Options</span></span>  
  
|<span data-ttu-id="c0e92-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="c0e92-106">Term</span></span>|<span data-ttu-id="c0e92-107">定義</span><span class="sxs-lookup"><span data-stu-id="c0e92-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="c0e92-108">**資料表**</span><span class="sxs-lookup"><span data-stu-id="c0e92-108">**Tables**</span></span>|<span data-ttu-id="c0e92-109">使用 [資料表]\*\*\*\* 索引標籤，即可顯示和選取要加入的資料表。</span><span class="sxs-lookup"><span data-stu-id="c0e92-109">Use the **Tables** tab to display and select a table to add.</span></span>|  
|<span data-ttu-id="c0e92-110">**檢視**</span><span class="sxs-lookup"><span data-stu-id="c0e92-110">**Views**</span></span>|<span data-ttu-id="c0e92-111">使用 [檢視]\*\*\*\* 索引標籤，即可顯示和選取要加入的檢視。</span><span class="sxs-lookup"><span data-stu-id="c0e92-111">Use the **Views** tab to display and select a view to add.</span></span>|  
|<span data-ttu-id="c0e92-112">**函式**</span><span class="sxs-lookup"><span data-stu-id="c0e92-112">**Functions**</span></span>|<span data-ttu-id="c0e92-113">使用 [函數]\*\*\*\* 索引標籤，即可顯示和選取要加入的函數或預存程序。</span><span class="sxs-lookup"><span data-stu-id="c0e92-113">Use the **Functions** tab to display and select a function or stored procedure to add.</span></span>|  
|<span data-ttu-id="c0e92-114">**同義字**</span><span class="sxs-lookup"><span data-stu-id="c0e92-114">**Synonyms**</span></span>|<span data-ttu-id="c0e92-115">使用 [同義字]\*\*\*\* 索引標籤，即可顯示和選取要加入的同義字。</span><span class="sxs-lookup"><span data-stu-id="c0e92-115">Use the **Synonyms** tab to display and select a synonym to add.</span></span>|  
|<span data-ttu-id="c0e92-116">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="c0e92-116">**Refresh**</span></span>|<span data-ttu-id="c0e92-117">按一下即可重新載入對話方塊上的所有索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c0e92-117">Click to reload all of the tabs on the dialog box.</span></span>|  
|<span data-ttu-id="c0e92-118">**加入**</span><span class="sxs-lookup"><span data-stu-id="c0e92-118">**Add**</span></span>|<span data-ttu-id="c0e92-119">按一下即可加入目前選取的項目。</span><span class="sxs-lookup"><span data-stu-id="c0e92-119">Click to add the currently selected item.</span></span> <span data-ttu-id="c0e92-120">**注意：** 只有選取專案時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="c0e92-120">**Note:**  This option is enabled only if an item is selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0e92-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0e92-121">See Also</span></span>  
 <span data-ttu-id="c0e92-122">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c0e92-122">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="c0e92-123">[建立或編輯已命名的查詢對話方塊 &#40;Analysis Services 多維度資料&#41;](create-or-edit-named-query-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c0e92-123">[Create or Edit Named Query Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](create-or-edit-named-query-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="c0e92-124">[[建立輪詢查詢] 對話方塊 &#40;Analysis Services-多維度資料&#41;](create-polling-query-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c0e92-124">[Create Polling Query Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](create-polling-query-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="c0e92-125">[[建立處理查詢] 對話方塊 &#40;Analysis Services-多維度資料&#41;](create-processing-query-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="c0e92-125">[Create Processing Query Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](create-processing-query-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
  
