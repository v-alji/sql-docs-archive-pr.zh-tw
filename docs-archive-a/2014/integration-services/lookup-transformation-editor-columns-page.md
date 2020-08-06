---
title: 查閱轉換編輯器 (資料行頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.columns.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: 690ffef5-fd59-4e95-a27d-4fcf0d6b1c0b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b768076d8acbcaef8cbff21783a7697020e027eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596106"
---
# <a name="lookup-transformation-editor-columns-page"></a><span data-ttu-id="5f77b-102">查閱轉換編輯器 (資料行頁面)</span><span class="sxs-lookup"><span data-stu-id="5f77b-102">Lookup Transformation Editor (Columns Page)</span></span>
  <span data-ttu-id="5f77b-103">使用 **[查閱轉換編輯器]** 對話方塊的 **[資料行]** 頁面，即可指定來源資料表和參考資料表之間的聯結，以及從參考資料表中選取查閱資料行。</span><span class="sxs-lookup"><span data-stu-id="5f77b-103">Use the **Columns** page of the **Lookup Transformation Editor** dialog box to specify the join between the source table and the reference table, and to select lookup columns from the reference table.</span></span>  
  
 <span data-ttu-id="5f77b-104">若要深入了解查閱轉換，請參閱＜ [Lookup Transformation](data-flow/transformations/lookup-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5f77b-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5f77b-105">選項。</span><span class="sxs-lookup"><span data-stu-id="5f77b-105">Options</span></span>  
 <span data-ttu-id="5f77b-106">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="5f77b-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="5f77b-107">檢視可用的輸入資料行清單。</span><span class="sxs-lookup"><span data-stu-id="5f77b-107">View the list of available input columns.</span></span> <span data-ttu-id="5f77b-108">輸入資料行是連接來源的資料流程中的資料行。</span><span class="sxs-lookup"><span data-stu-id="5f77b-108">The input columns are the columns in the data flow from a connected source.</span></span> <span data-ttu-id="5f77b-109">輸入資料行和查閱資料行必須有相符的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5f77b-109">The input columns and lookup column must have matching data types.</span></span>  
  
 <span data-ttu-id="5f77b-110">使用拖放作業，即可將可用的輸入資料行對應到查閱資料行。</span><span class="sxs-lookup"><span data-stu-id="5f77b-110">Use a drag-and-drop operation to map available input columns to lookup columns.</span></span>  
  
 <span data-ttu-id="5f77b-111">您也可以藉由在 **[可用的輸入資料行]** 資料表中反白顯示資料行，按下應用程式鍵，然後按一下 **[編輯對應]**，使用鍵盤將輸入資料行對應到查閱資料行。</span><span class="sxs-lookup"><span data-stu-id="5f77b-111">You can also map input columns to lookup columns using the keyboard, by highlighting a column in the **Available Input Columns** table, pressing the Application key, and then clicking **Edit Mappings**.</span></span>  
  
 <span data-ttu-id="5f77b-112">**可用的查閱資料行**</span><span class="sxs-lookup"><span data-stu-id="5f77b-112">**Available Lookup Columns**</span></span>  
 <span data-ttu-id="5f77b-113">檢視查閱資料行清單。</span><span class="sxs-lookup"><span data-stu-id="5f77b-113">View the list of lookup columns.</span></span> <span data-ttu-id="5f77b-114">查閱資料行是參考資料表中的資料行，您可在其中查閱符合輸入資料行的值。</span><span class="sxs-lookup"><span data-stu-id="5f77b-114">The lookup columns are columns in the reference table in which you want to look up values that match the input columns.</span></span>  
  
 <span data-ttu-id="5f77b-115">使用拖放作業，即可將可用的查閱資料行對應到輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="5f77b-115">Use a drag-and-drop operation to map available lookup columns to input columns.</span></span>  
  
 <span data-ttu-id="5f77b-116">使用核取方塊即可在參考資料表中，選取要執行查閱作業的查閱資料行。</span><span class="sxs-lookup"><span data-stu-id="5f77b-116">Use the check boxes to select lookup columns in the reference table on which to perform lookup operations.</span></span>  
  
 <span data-ttu-id="5f77b-117">您也可以藉由在 **[可用的查閱資料行]** 資料表中反白顯示資料行，按下應用程式鍵，然後按一下 **[編輯對應]**，使用鍵盤將查閱資料行對應到輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="5f77b-117">You can also map lookup columns to input columns using the keyboard, by highlighting a column in the **Available Lookup Columns** table, pressing the Application key, and then clicking **Edit Mappings**.</span></span>  
  
 <span data-ttu-id="5f77b-118">**查閱資料行**</span><span class="sxs-lookup"><span data-stu-id="5f77b-118">**Lookup Column**</span></span>  
 <span data-ttu-id="5f77b-119">檢視選取的查閱資料行。</span><span class="sxs-lookup"><span data-stu-id="5f77b-119">View the selected lookup columns.</span></span> <span data-ttu-id="5f77b-120">您的選擇會反映在 **[可用的查閱資料行]** 資料表的核取方塊選擇中。</span><span class="sxs-lookup"><span data-stu-id="5f77b-120">The selections are reflected in the check box selections in the **Available Lookup Columns** table.</span></span>  
  
 <span data-ttu-id="5f77b-121">**查閱作業**</span><span class="sxs-lookup"><span data-stu-id="5f77b-121">**Lookup Operation**</span></span>  
 <span data-ttu-id="5f77b-122">從清單中選取要在查閱資料行上執行的查閱作業。</span><span class="sxs-lookup"><span data-stu-id="5f77b-122">Select a lookup operation from the list to perform on the lookup column.</span></span>  
  
 <span data-ttu-id="5f77b-123">**輸出別名**</span><span class="sxs-lookup"><span data-stu-id="5f77b-123">**Output Alias**</span></span>  
 <span data-ttu-id="5f77b-124">輸入每個查閱資料行之輸出的別名。</span><span class="sxs-lookup"><span data-stu-id="5f77b-124">Type an alias for the output for each lookup column.</span></span> <span data-ttu-id="5f77b-125">預設是查閱資料行的名稱；但是，您可以選取任何唯一的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="5f77b-125">The default is the name of the lookup column; however, you can select any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f77b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f77b-126">See Also</span></span>  
 <span data-ttu-id="5f77b-127">[查閱轉換編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="5f77b-127">[Lookup Transformation Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="5f77b-128">[查閱轉換編輯器 &#40;連接頁面&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="5f77b-128">[Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span></span>  
 <span data-ttu-id="5f77b-129">[查閱轉換編輯器 &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="5f77b-129">[Lookup Transformation Editor &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span></span>  
 <span data-ttu-id="5f77b-130">[查閱轉換編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="5f77b-130">[Lookup Transformation Editor &#40;Error Output Page&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="5f77b-131">模糊查閱轉換</span><span class="sxs-lookup"><span data-stu-id="5f77b-131">Fuzzy Lookup Transformation</span></span>](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
