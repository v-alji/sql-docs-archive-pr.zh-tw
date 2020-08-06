---
title: 排序轉換編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sorttransformation.f1
helpviewer_keywords:
- Sort Transformation Editor
ms.assetid: 8ae23970-49a9-4d6d-9f15-c7074783347c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f48c366f4337af29b03877f6bb20b804457a293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709710"
---
# <a name="sort-transformation-editor"></a><span data-ttu-id="8e89c-102">排序轉換編輯器</span><span class="sxs-lookup"><span data-stu-id="8e89c-102">Sort Transformation Editor</span></span>
  <span data-ttu-id="8e89c-103">使用 **[排序轉換編輯器]** 對話方塊，即可選取要排序的資料行、設定排序順序和指定是否要移除重複的項目。</span><span class="sxs-lookup"><span data-stu-id="8e89c-103">Use the **Sort Transformation Editor** dialog box to select the columns to sort, set the sort order, and specify whether duplicates are removed.</span></span>  
  
 <span data-ttu-id="8e89c-104">若要深入了解排序轉換，請參閱＜ [Sort Transformation](data-flow/transformations/sort-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8e89c-104">To learn more about the Sort transformation, see [Sort Transformation](data-flow/transformations/sort-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8e89c-105">選項。</span><span class="sxs-lookup"><span data-stu-id="8e89c-105">Options</span></span>  
 <span data-ttu-id="8e89c-106">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="8e89c-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="8e89c-107">使用核取方塊來指定要排序的資料行。</span><span class="sxs-lookup"><span data-stu-id="8e89c-107">Using the check boxes, specify the columns to sort.</span></span>  
  
 <span data-ttu-id="8e89c-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="8e89c-108">**Name**</span></span>  
 <span data-ttu-id="8e89c-109">檢視每個可用輸入資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="8e89c-109">View the name of each available input column.</span></span>  
  
 <span data-ttu-id="8e89c-110">**通過**</span><span class="sxs-lookup"><span data-stu-id="8e89c-110">**Passthrough**</span></span>  
 <span data-ttu-id="8e89c-111">指出排序的輸出中是否包含資料行。</span><span class="sxs-lookup"><span data-stu-id="8e89c-111">Indicate whether to include the column in the sorted output.</span></span>  
  
 <span data-ttu-id="8e89c-112">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="8e89c-112">**Input Column**</span></span>  
 <span data-ttu-id="8e89c-113">從每個資料列的可用輸入資料行清單中選取。</span><span class="sxs-lookup"><span data-stu-id="8e89c-113">Select from the list of available input columns for each row.</span></span> <span data-ttu-id="8e89c-114">您的選擇會反映在 **[可用的輸入資料行]** 資料表的核取方塊選擇中。</span><span class="sxs-lookup"><span data-stu-id="8e89c-114">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="8e89c-115">**輸出別名**</span><span class="sxs-lookup"><span data-stu-id="8e89c-115">**Output Alias**</span></span>  
 <span data-ttu-id="8e89c-116">輸入每一個輸出資料行的別名。</span><span class="sxs-lookup"><span data-stu-id="8e89c-116">Type an alias for each output column.</span></span> <span data-ttu-id="8e89c-117">預設是輸入資料行的名稱；但是，您可以選擇任何唯一的、描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="8e89c-117">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="8e89c-118">**排序類型**</span><span class="sxs-lookup"><span data-stu-id="8e89c-118">**Sort Type**</span></span>  
 <span data-ttu-id="8e89c-119">指出是要依遞增或遞減的順序來排序。</span><span class="sxs-lookup"><span data-stu-id="8e89c-119">Indicate whether to sort in ascending or descending order.</span></span>  
  
 <span data-ttu-id="8e89c-120">**排序次序**</span><span class="sxs-lookup"><span data-stu-id="8e89c-120">**Sort Order**</span></span>  
 <span data-ttu-id="8e89c-121">指出資料行的排序順序。</span><span class="sxs-lookup"><span data-stu-id="8e89c-121">Indicate the order in which to sort columns.</span></span> <span data-ttu-id="8e89c-122">必須以手動的方式為每個資料行設定。</span><span class="sxs-lookup"><span data-stu-id="8e89c-122">This must be set manually for each column.</span></span>  
  
 <span data-ttu-id="8e89c-123">**比較旗標**</span><span class="sxs-lookup"><span data-stu-id="8e89c-123">**Comparison Flags**</span></span>  
 <span data-ttu-id="8e89c-124">如需字串比較選項的資訊，請參閱 [比較字串資料](data-flow/comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8e89c-124">For information about the string comparison options, see [Comparing String Data](data-flow/comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="8e89c-125">**移除排序值重複的資料列**</span><span class="sxs-lookup"><span data-stu-id="8e89c-125">**Remove rows with duplicate sort values**</span></span>  
 <span data-ttu-id="8e89c-126">指出轉換是否將重複的資料列複製到轉換輸出，或依據指定的字串比較選項為所有重複的資料列建立單一項目。</span><span class="sxs-lookup"><span data-stu-id="8e89c-126">Indicate whether the transformation copies duplicate rows to the transformation output, or creates a single entry for all duplicates, based on the specified string comparison options.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e89c-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e89c-127">See Also</span></span>  
 [<span data-ttu-id="8e89c-128">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="8e89c-128">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
