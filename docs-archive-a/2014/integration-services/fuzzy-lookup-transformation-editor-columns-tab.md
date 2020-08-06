---
title: 模糊查閱轉換編輯器 (資料行] 索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.columns.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: aaf45327-79e9-4760-9b4d-546ace91b5b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9294022b52536940916a381d7b811437eaa5814
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688029"
---
# <a name="fuzzy-lookup-transformation-editor-columns-tab"></a><span data-ttu-id="856d9-102">模糊查閱轉換編輯器 (資料行索引標籤)</span><span class="sxs-lookup"><span data-stu-id="856d9-102">Fuzzy Lookup Transformation Editor (Columns Tab)</span></span>
  <span data-ttu-id="856d9-103">使用 **[模糊查閱轉換編輯器]** 對話方塊的 **[資料行]** 索引標籤，即可設定輸入與輸出資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="856d9-103">Use the **Columns** tab of the **Fuzzy Lookup Transformation Editor** dialog box to set properties for input and output columns.</span></span>  
  
 <span data-ttu-id="856d9-104">若要深入了解模糊查閱轉換，請參閱＜ [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="856d9-104">To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="856d9-105">選項。</span><span class="sxs-lookup"><span data-stu-id="856d9-105">Options</span></span>  
 <span data-ttu-id="856d9-106">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="856d9-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="856d9-107">拖曳輸入資料行，即可將資料行連接到可用的查閱資料行。</span><span class="sxs-lookup"><span data-stu-id="856d9-107">Drag input columns to connect them to available lookup columns.</span></span> <span data-ttu-id="856d9-108">這些資料行必須擁有相符的、支援的資料類型。</span><span class="sxs-lookup"><span data-stu-id="856d9-108">These columns must have matching, supported data types.</span></span> <span data-ttu-id="856d9-109">在 [ [建立關聯性](data-flow/transformations/create-relationships.md) ] 對話方塊中選取對應行，並以滑鼠右鍵按一下來編輯對應。</span><span class="sxs-lookup"><span data-stu-id="856d9-109">Select a mapping line and right-click to edit the mappings in the [Create Relationships](data-flow/transformations/create-relationships.md) dialog box.</span></span>  
  
 <span data-ttu-id="856d9-110">**名稱**</span><span class="sxs-lookup"><span data-stu-id="856d9-110">**Name**</span></span>  
 <span data-ttu-id="856d9-111">檢視可用輸入資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="856d9-111">View the names of the available input columns.</span></span>  
  
 <span data-ttu-id="856d9-112">**通過**</span><span class="sxs-lookup"><span data-stu-id="856d9-112">**Pass Through**</span></span>  
 <span data-ttu-id="856d9-113">指定是否在轉換的輸出中包含輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="856d9-113">Specify whether to include the input columns in the output of the transformation.</span></span>  
  
 <span data-ttu-id="856d9-114">**可用的查閱資料行**</span><span class="sxs-lookup"><span data-stu-id="856d9-114">**Available Lookup Columns**</span></span>  
 <span data-ttu-id="856d9-115">使用核取方塊即可選取要執行模糊查閱作業的資料行。</span><span class="sxs-lookup"><span data-stu-id="856d9-115">Use the check boxes to select columns on which to perform fuzzy lookup operations.</span></span>  
  
 <span data-ttu-id="856d9-116">**查閱資料行**</span><span class="sxs-lookup"><span data-stu-id="856d9-116">**Lookup Column**</span></span>  
 <span data-ttu-id="856d9-117">從可用的參考資料表資料行清單中選取查閱資料行。</span><span class="sxs-lookup"><span data-stu-id="856d9-117">Select lookup columns from the list of available reference table columns.</span></span> <span data-ttu-id="856d9-118">您的選取項目會反映在 **[可用的查閱資料行]** 資料表的核取方塊選取項目中。</span><span class="sxs-lookup"><span data-stu-id="856d9-118">Your selections are reflected in the check box selections in the **Available Lookup Columns** table.</span></span> <span data-ttu-id="856d9-119">選取 **[可用的查閱資料行]** 資料表中的資料行會建立輸出資料行，其中包含傳回的每個相符資料列的參考資料表資料行值。</span><span class="sxs-lookup"><span data-stu-id="856d9-119">Selecting a column in the **Available Lookup Columns** table creates an output column that contains the reference table column value for each matching row returned.</span></span>  
  
 <span data-ttu-id="856d9-120">**輸出別名**</span><span class="sxs-lookup"><span data-stu-id="856d9-120">**Output Alias**</span></span>  
 <span data-ttu-id="856d9-121">輸入每個查閱資料行之輸出的別名。</span><span class="sxs-lookup"><span data-stu-id="856d9-121">Type an alias for the output for each lookup column.</span></span> <span data-ttu-id="856d9-122">預設值為附加數值索引值之查閱資料行的名稱；不過，您也可以選擇任何唯一的、描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="856d9-122">The default is the name of the lookup column with a numeric index value appended; however, you can choose any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="856d9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="856d9-123">See Also</span></span>  
 <span data-ttu-id="856d9-124">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="856d9-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="856d9-125">[[模糊查閱轉換編輯器] &#40;[參考資料表] 索引標籤&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span><span class="sxs-lookup"><span data-stu-id="856d9-125">[Fuzzy Lookup Transformation Editor &#40;Reference Table Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span></span>  
 [<span data-ttu-id="856d9-126">模糊查閱轉換編輯器 &#40;進階索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="856d9-126">Fuzzy Lookup Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  
