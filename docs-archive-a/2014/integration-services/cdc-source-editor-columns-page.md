---
title: CDC 來源編輯器 (資料行頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.columns.f1
ms.assetid: bcf3030e-98d8-4445-967c-33c3f8ecb4fc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa30defb5e6873ea05e8e41c733477cf50d0dc4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599630"
---
# <a name="cdc-source-editor-columns-page"></a><span data-ttu-id="6aeb6-102">CDC 來源編輯器 (資料行頁面)</span><span class="sxs-lookup"><span data-stu-id="6aeb6-102">CDC Source Editor (Columns Page)</span></span>
  <span data-ttu-id="6aeb6-103">使用 [CDC 來源編輯器]  對話方塊的 [資料行]  頁面，即可將輸出資料行對應至每個外部 (來源) 資料行。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-103">Use the **Columns** page of the **CDC Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="6aeb6-104">若要了解有關 CDC 來源的詳細資訊，請參閱＜ [CDC Source](data-flow/cdc-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-104">To learn more about the CDC source, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="6aeb6-105">工作清單</span><span class="sxs-lookup"><span data-stu-id="6aeb6-105">Task List</span></span>  
 <span data-ttu-id="6aeb6-106">**若要開啟 CDC 來源編輯器的資料行頁面**</span><span class="sxs-lookup"><span data-stu-id="6aeb6-106">**To open the CDC Source Editor Columns Page**</span></span>  
  
1.  <span data-ttu-id="6aeb6-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，開啟具有 CDC 來源的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the CDC source.</span></span>  
  
2.  <span data-ttu-id="6aeb6-108">在 [資料流程]  索引標籤中，按兩下 CDC 來源。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-108">On the **Data Flow** tab, double-click the CDC source.</span></span>  
  
3.  <span data-ttu-id="6aeb6-109">在 **[CDC 來源編輯器]** 中，按一下 **[資料行]** 。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-109">In the **CDC Source Editor**, click **Columns**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6aeb6-110">選項。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-110">Options</span></span>  
 <span data-ttu-id="6aeb6-111">**可用的外部資料行**</span><span class="sxs-lookup"><span data-stu-id="6aeb6-111">**Available External Columns**</span></span>  
 <span data-ttu-id="6aeb6-112">資料來源中可用的外部資料行清單。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-112">A list of available external columns in the data source.</span></span> <span data-ttu-id="6aeb6-113">您無法使用此資料表來加入或刪除資料行。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-113">You cannot use this table to add or delete columns.</span></span> <span data-ttu-id="6aeb6-114">請在來源中選取要使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-114">Select the columns to use in the source.</span></span> <span data-ttu-id="6aeb6-115">選取的資料行就會依照選取的順序加入至 **[外部資料行]** 清單。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-115">The selected columns are added to the **External Column** list in the order they are selected.</span></span>  
  
 <span data-ttu-id="6aeb6-116">**[外部資料行]**</span><span class="sxs-lookup"><span data-stu-id="6aeb6-116">**External Column**</span></span>  
 <span data-ttu-id="6aeb6-117">外部 (來源) 資料行的檢視，這些資料行會依照您在設定取用 CDC 來源資料之元件時所看見的順序列出。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-117">A view of the external (source) columns in the order that you see them when configuring components that consume data from the CDC source.</span></span> <span data-ttu-id="6aeb6-118">若要變更此順序，請先清除 **[可用的外部資料行]** 清單中的選取資料行，然後依照不同的順序，從清單選取外部資料行。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-118">To change this order, first clear the selected columns in the **Available External Columns** list, and then select external columns from the list in a different order.</span></span> <span data-ttu-id="6aeb6-119">選取的資料行就會依照您選取的順序加入至 **[外部資料行]** 清單。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-119">The selected columns are added to the **External Column** list in the order you select them.</span></span>  
  
 <span data-ttu-id="6aeb6-120">**輸出資料行**</span><span class="sxs-lookup"><span data-stu-id="6aeb6-120">**Output Column**</span></span>  
 <span data-ttu-id="6aeb6-121">為每個輸出資料行輸入唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-121">Enter a unique name for each output column.</span></span> <span data-ttu-id="6aeb6-122">預設值為選取之外部 (來源) 資料行的名稱。不過，您也可以選擇任何唯一的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-122">The default is the name of the selected external (source) column, however you can choose any unique, descriptive name.</span></span> <span data-ttu-id="6aeb6-123">輸入的名稱就會顯示在 SSIS 設計師中。</span><span class="sxs-lookup"><span data-stu-id="6aeb6-123">The name entered is displayed in the SSIS Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aeb6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6aeb6-124">See Also</span></span>  
 <span data-ttu-id="6aeb6-125">[CDC 來源編輯器 &#40;連線管理員頁面&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="6aeb6-125">[CDC Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="6aeb6-126">CDC 來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="6aeb6-126">CDC Source Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/cdc-source-editor-error-output-page.md)  
  
  
