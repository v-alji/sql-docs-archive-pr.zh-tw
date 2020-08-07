---
title: ODBC 來源編輯器 (資料行頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.columns.f1
ms.assetid: 565984eb-8318-4be7-bebc-262209cf5065
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a11ab6a86978366d07fbe63362f1702310b5d89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703190"
---
# <a name="odbc-source-editor-columns-page"></a><span data-ttu-id="d342c-102">ODBC 來源編輯器 (資料行頁面)</span><span class="sxs-lookup"><span data-stu-id="d342c-102">ODBC Source Editor (Columns Page)</span></span>
  <span data-ttu-id="d342c-103">使用 [ODBC 來源編輯器]\*\*\*\* 對話方塊的 [資料行]\*\*\*\* 頁面，即可將輸出資料行對應至每個外部 (來源) 資料行。</span><span class="sxs-lookup"><span data-stu-id="d342c-103">Use the **Columns** page of the **ODBC Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="d342c-104">若要了解有關 ODBC 來源的詳細資訊，請參閱＜ [ODBC Source](data-flow/odbc-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d342c-104">To learn more about the ODBC source, see [ODBC Source](data-flow/odbc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="d342c-105">工作清單</span><span class="sxs-lookup"><span data-stu-id="d342c-105">Task List</span></span>  
 <span data-ttu-id="d342c-106">**若要開啟 ODBC 來源編輯器的資料行頁面**</span><span class="sxs-lookup"><span data-stu-id="d342c-106">**To open the ODBC Source Editor Columns Page**</span></span>  
  
1.  <span data-ttu-id="d342c-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，開啟具有 ODBC 來源的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="d342c-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC source.</span></span>  
  
2.  <span data-ttu-id="d342c-108">在 [資料流程]\*\*\*\* 索引標籤上，按兩下 ODBC 來源。</span><span class="sxs-lookup"><span data-stu-id="d342c-108">On the **Data Flow** tab, double-click the ODBC source.</span></span>  
  
3.  <span data-ttu-id="d342c-109">在 **[ODBC 來源編輯器]** 中，按一下 **[資料行]**。</span><span class="sxs-lookup"><span data-stu-id="d342c-109">In the **ODBC Source Editor**, click **Columns**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d342c-110">選項。</span><span class="sxs-lookup"><span data-stu-id="d342c-110">Options</span></span>  
  
### <a name="available-external-columns"></a><span data-ttu-id="d342c-111">可用的外部資料行</span><span class="sxs-lookup"><span data-stu-id="d342c-111">Available External Columns</span></span>  
 <span data-ttu-id="d342c-112">資料來源中可用的外部資料行清單。</span><span class="sxs-lookup"><span data-stu-id="d342c-112">A list of available external columns in the data source.</span></span> <span data-ttu-id="d342c-113">您無法使用此資料表來加入或刪除資料行。</span><span class="sxs-lookup"><span data-stu-id="d342c-113">You cannot use this table to add or delete columns.</span></span> <span data-ttu-id="d342c-114">請從來源選取要使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="d342c-114">Select the columns to use from the source.</span></span> <span data-ttu-id="d342c-115">選取的資料行就會依照選取的順序加入至 **[外部資料行]** 清單。</span><span class="sxs-lookup"><span data-stu-id="d342c-115">The selected columns are added to the **External Column** list in the order they are selected.</span></span>  
  
 <span data-ttu-id="d342c-116">選取 **[全選]** 核取方塊，即可選取所有資料行。</span><span class="sxs-lookup"><span data-stu-id="d342c-116">Select the **Select All** check box to select all of the columns.</span></span>  
  
### <a name="external-column"></a><span data-ttu-id="d342c-117">外部資料行</span><span class="sxs-lookup"><span data-stu-id="d342c-117">External Column</span></span>  
 <span data-ttu-id="d342c-118">外部 (來源) 資料行的檢視，這些資料行會依照您在設定取用 ODBC 來源資料之元件時所看見的順序列出。</span><span class="sxs-lookup"><span data-stu-id="d342c-118">A view of the external (source) columns in the order that you see them when configuring components that consume data from the ODBC source.</span></span>  
  
### <a name="output-column"></a><span data-ttu-id="d342c-119">輸出資料行</span><span class="sxs-lookup"><span data-stu-id="d342c-119">Output Column</span></span>  
 <span data-ttu-id="d342c-120">為每個輸出資料行輸入唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="d342c-120">Enter a unique name for each output column.</span></span> <span data-ttu-id="d342c-121">預設值為選取的外部 (來源) 資料行的名稱；不過，您也可以選擇任何唯一的、描述性的名稱。</span><span class="sxs-lookup"><span data-stu-id="d342c-121">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="d342c-122">輸入的名稱就會顯示在 SSIS 設計師中。</span><span class="sxs-lookup"><span data-stu-id="d342c-122">The name entered is displayed in the SSIS Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d342c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d342c-123">See Also</span></span>  
 <span data-ttu-id="d342c-124">[ODBC 來源編輯器 &#40;連線管理員頁面&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="d342c-124">[ODBC Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="d342c-125">ODBC 來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="d342c-125">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  
