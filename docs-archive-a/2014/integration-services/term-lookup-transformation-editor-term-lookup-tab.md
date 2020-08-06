---
title: 詞彙查閱轉換編輯器 (詞彙查閱] 索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookup.termlookup.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9bb8c0bd0477d9883640cc3e4d3cb25c2a3a8b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606411"
---
# <a name="term-lookup-transformation-editor-term-lookup-tab"></a><span data-ttu-id="a2ed7-102">詞彙查閱轉換編輯器 (詞彙查閱索引標籤)</span><span class="sxs-lookup"><span data-stu-id="a2ed7-102">Term Lookup Transformation Editor (Term Lookup Tab)</span></span>
  <span data-ttu-id="a2ed7-103">使用 **[詞彙查閱轉換編輯器]** 對話方塊的 **[詞彙查閱]** 索引標籤，即可將輸入資料行對應至參考資料表的查閱資料行，並提供每一個輸出資料行的別名。</span><span class="sxs-lookup"><span data-stu-id="a2ed7-103">Use the **Term Lookup** tab of the **Term Lookup Transformation Editor** dialog box to map an input column to a lookup column in a reference table and to provide an alias for each output column.</span></span>  
  
 <span data-ttu-id="a2ed7-104">若要深入了解模糊查閱轉換，請參閱＜ [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a2ed7-104">To learn more about the Term Lookup transformation, see [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a2ed7-105">選項。</span><span class="sxs-lookup"><span data-stu-id="a2ed7-105">Options</span></span>  
 <span data-ttu-id="a2ed7-106">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="a2ed7-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="a2ed7-107">使用核取方塊選取輸入資料行，即可讓這些輸入資料行在不變更的狀況下通過至輸出。</span><span class="sxs-lookup"><span data-stu-id="a2ed7-107">Using the check boxes, select input columns to pass through to the output unchanged.</span></span> <span data-ttu-id="a2ed7-108">將輸入資料行拖曳至 **[可用的參考資料行]** 清單，即可對應至參考資料表的查閱資料行。</span><span class="sxs-lookup"><span data-stu-id="a2ed7-108">Drag an input column to the **Available Reference Columns** list to map it to a lookup column in the reference table.</span></span> <span data-ttu-id="a2ed7-109">輸入和查閱資料行都必須有相符、受支援的資料類型，包括 DT_NTEXT 或 DT_WSTR。</span><span class="sxs-lookup"><span data-stu-id="a2ed7-109">The input and lookup columns must have matching, supported data types, either DT_NTEXT or DT_WSTR.</span></span> <span data-ttu-id="a2ed7-110">在 [ [建立關聯性](data-flow/transformations/create-relationships.md) ] 對話方塊中選取對應行，並以滑鼠右鍵按一下來編輯對應。</span><span class="sxs-lookup"><span data-stu-id="a2ed7-110">Select a mapping line and right-click to edit the mappings in the [Create Relationships](data-flow/transformations/create-relationships.md) dialog box.</span></span>  
  
 <span data-ttu-id="a2ed7-111">**[可用的參考資料行]**</span><span class="sxs-lookup"><span data-stu-id="a2ed7-111">**Available Reference Columns**</span></span>  
 <span data-ttu-id="a2ed7-112">檢視參考資料表中可用的資料行。</span><span class="sxs-lookup"><span data-stu-id="a2ed7-112">View the available columns in the reference table.</span></span> <span data-ttu-id="a2ed7-113">選擇包含要比對之詞彙清單的資料行。</span><span class="sxs-lookup"><span data-stu-id="a2ed7-113">Choose the column that contains the list of terms to match.</span></span>  
  
 <span data-ttu-id="a2ed7-114">**通過資料行**</span><span class="sxs-lookup"><span data-stu-id="a2ed7-114">**Pass-Through Column**</span></span>  
 <span data-ttu-id="a2ed7-115">從可用的輸入資料行清單中選取。</span><span class="sxs-lookup"><span data-stu-id="a2ed7-115">Select from the list of available input columns.</span></span> <span data-ttu-id="a2ed7-116">您的選擇會反映在 **[可用的輸入資料行]** 資料表的核取方塊選擇中。</span><span class="sxs-lookup"><span data-stu-id="a2ed7-116">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="a2ed7-117">**輸出資料行別名**</span><span class="sxs-lookup"><span data-stu-id="a2ed7-117">**Output Column Alias**</span></span>  
 <span data-ttu-id="a2ed7-118">輸入每一個輸出資料行的別名。</span><span class="sxs-lookup"><span data-stu-id="a2ed7-118">Type an alias for each output column.</span></span> <span data-ttu-id="a2ed7-119">預設為資料行的名稱；不過，您可以選擇任何唯一的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="a2ed7-119">The default is the name of the column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="a2ed7-120">**設定錯誤輸出**</span><span class="sxs-lookup"><span data-stu-id="a2ed7-120">**Configure Error Output**</span></span>  
 <span data-ttu-id="a2ed7-121">使用 [ [設定錯誤輸出](../../2014/integration-services/configure-error-output.md) ] 對話方塊，即可指定造成錯誤之資料列的錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="a2ed7-121">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling options for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ed7-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2ed7-122">See Also</span></span>  
 <span data-ttu-id="a2ed7-123">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a2ed7-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="a2ed7-124">[詞彙查閱轉換編輯器 &#40;參考資料表索引標籤&#41;](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md) </span><span class="sxs-lookup"><span data-stu-id="a2ed7-124">[Term Lookup Transformation Editor &#40;Reference Table Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md) </span></span>  
 <span data-ttu-id="a2ed7-125">[詞彙查閱轉換編輯器 &#40;[Advanced] 索引標籤&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="a2ed7-125">[Term Lookup Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="a2ed7-126">詞彙擷取轉換</span><span class="sxs-lookup"><span data-stu-id="a2ed7-126">Term Extraction Transformation</span></span>](data-flow/transformations/term-extraction-transformation.md)  
  
  
