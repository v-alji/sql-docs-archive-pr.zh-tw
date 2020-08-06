---
title: 模糊群組轉換編輯器 (資料行] 索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.columns.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 24f4539f-2a9f-4acd-acc7-06228a07f7df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9d3aef9c30a81760b7f09378a8ecd66fee0dac62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688030"
---
# <a name="fuzzy-grouping-transformation-editor-columns-tab"></a><span data-ttu-id="e9b4c-102">模糊群組轉換編輯器 (資料行索引標籤)</span><span class="sxs-lookup"><span data-stu-id="e9b4c-102">Fuzzy Grouping Transformation Editor (Columns Tab)</span></span>
  <span data-ttu-id="e9b4c-103">使用 **[模糊群組轉換編輯器]** 對話方塊的 **[資料行]** 索引標籤，即可指定用於將具有重複值之資料列分組的資料行。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-103">Use the **Columns** tab of the **Fuzzy Grouping Transformation Editor** dialog box to specify the columns used to group rows with duplicate values.</span></span>  
  
 <span data-ttu-id="e9b4c-104">若要深入了解模糊群組轉換，請參閱＜ [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-104">To learn more about the Fuzzy Grouping transformation, see [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e9b4c-105">選項。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-105">Options</span></span>  
 <span data-ttu-id="e9b4c-106">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="e9b4c-107">從清單中選取輸入資料行，即可依據該資料行將具有重複值的資料列分組。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-107">Select from this list the input columns used to group rows with duplicate values.</span></span>  
  
 <span data-ttu-id="e9b4c-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-108">**Name**</span></span>  
 <span data-ttu-id="e9b4c-109">檢視可用之輸入資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-109">View the names of available input columns.</span></span>  
  
 <span data-ttu-id="e9b4c-110">**通過**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-110">**Pass Through**</span></span>  
 <span data-ttu-id="e9b4c-111">選取轉換的輸出是否包含輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-111">Select whether to include the input column in the output of the transformation.</span></span> <span data-ttu-id="e9b4c-112">用來分組的所有資料行，都會自動複製到輸出。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-112">All columns used for grouping are automatically copied to the output.</span></span> <span data-ttu-id="e9b4c-113">您可以核取此資料行來包含其他資料行。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-113">You can include additional columns by checking this column.</span></span>  
  
 <span data-ttu-id="e9b4c-114">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-114">**Input Column**</span></span>  
 <span data-ttu-id="e9b4c-115">選取先前在 [可用的輸入資料行]\*\*\*\* 清單中選取的其中一個輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-115">Select one of the input columns selected earlier in the **Available Input Columns** list.</span></span>  
  
 <span data-ttu-id="e9b4c-116">**輸出別名**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-116">**Output Alias**</span></span>  
 <span data-ttu-id="e9b4c-117">輸入對應之輸出資料行的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-117">Enter a descriptive name for the corresponding output column.</span></span> <span data-ttu-id="e9b4c-118">依預設，輸出資料行的名稱會與輸入資料行的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-118">By default, the output column name is the same as the input column name.</span></span>  
  
 <span data-ttu-id="e9b4c-119">**群組輸出別名**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-119">**Group Output Alias**</span></span>  
 <span data-ttu-id="e9b4c-120">輸入資料行的描述性名稱，資料行包含已分組重複項目的標準值。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-120">Enter a descriptive name for the column that will contain the canonical value for the grouped duplicates.</span></span> <span data-ttu-id="e9b4c-121">此輸出資料行的預設名稱，是輸入資料行的名稱後面附加「_clean」。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-121">The default name of this output column is the input column name with _clean appended.</span></span>  
  
 <span data-ttu-id="e9b4c-122">**比對類型**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-122">**Match Type**</span></span>  
 <span data-ttu-id="e9b4c-123">選取模糊相符或完全相符。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-123">Select fuzzy or exact matching.</span></span> <span data-ttu-id="e9b4c-124">如果資料列在具有模糊比對類型的所有資料行之間非常相似，資料列才會被視為重複項目。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-124">Rows are considered duplicates if they are sufficiently similar across all columns with a fuzzy match type.</span></span> <span data-ttu-id="e9b4c-125">如果您同時在特定資料行上指定完全相符，則只有當需要完全相符之資料行中的資料列值完全相同時，資料列才會被視為可能重複的項目。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-125">If you also specify exact matching on certain columns, only rows that contain identical values in the exact matching columns are considered as possible duplicates.</span></span> <span data-ttu-id="e9b4c-126">因此，如果您知道特定資料行不會有錯誤或不一致的情形，就可以在該資料行上指定完全相符，以提高其他資料行的模糊比對精確度。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-126">Therefore, if you know that a certain column contains no errors or inconsistencies, you can specify exact matching on that column to increase the accuracy of the fuzzy matching on other columns.</span></span>  
  
 <span data-ttu-id="e9b4c-127">**最小相似度**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-127">**Minimum Similarity**</span></span>  
 <span data-ttu-id="e9b4c-128">使用滑桿設定聯結層級的相似度臨界值。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-128">Set the similarity threshold at the join level by using the slider.</span></span> <span data-ttu-id="e9b4c-129">此值越接近 1，查閱值與來源值的相似度必須越接近才能認定為相符。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-129">The closer the value is to 1, the closer the resemblance of the lookup value to the source value must be to qualify as a match.</span></span> <span data-ttu-id="e9b4c-130">增加臨界值可改善比對速度，因為需要考慮的候選記錄越少。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-130">Increasing the threshold can improve the speed of matching since fewer candidate records need to be considered.</span></span>  
  
 <span data-ttu-id="e9b4c-131">**相似度輸出別名**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-131">**Similarity Output Alias**</span></span>  
 <span data-ttu-id="e9b4c-132">指定新輸出資料行的名稱，此資料行包含所選取聯結的相似度分數。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-132">Specify the name for a new output column that contains the similarity scores for the selected join.</span></span> <span data-ttu-id="e9b4c-133">如果您將此值保留空白，就不會建立輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-133">If you leave this value empty, the output column is not created.</span></span>  
  
 <span data-ttu-id="e9b4c-134">**數字**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-134">**Numerals**</span></span>  
 <span data-ttu-id="e9b4c-135">指定比較資料行資料時，開頭和尾端數字的顯著性。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-135">Specify the significance of leading and trailing numerals in comparing the column data.</span></span> <span data-ttu-id="e9b4c-136">例如，假設開頭數字屬於顯著，則 "123 Main Street" 和 "456 Main Street" 將不會被分到相同的群組中。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-136">For example, if leading numerals are significant, "123 Main Street" will not be grouped with "456 Main Street."</span></span>  
  
|<span data-ttu-id="e9b4c-137">值</span><span class="sxs-lookup"><span data-stu-id="e9b4c-137">Value</span></span>|<span data-ttu-id="e9b4c-138">描述</span><span class="sxs-lookup"><span data-stu-id="e9b4c-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9b4c-139">**兩者皆非**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-139">**Neither**</span></span>|<span data-ttu-id="e9b4c-140">開頭和尾端數字皆屬於不顯著。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-140">Leading and trailing numerals are not significant.</span></span>|  
|<span data-ttu-id="e9b4c-141">**開頭**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-141">**Leading**</span></span>|<span data-ttu-id="e9b4c-142">僅開頭數字屬於顯著。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-142">Only leading numerals are significant.</span></span>|  
|<span data-ttu-id="e9b4c-143">**尾端**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-143">**Trailing**</span></span>|<span data-ttu-id="e9b4c-144">僅尾端數字屬於顯著。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-144">Only trailing numerals are significant.</span></span>|  
|<span data-ttu-id="e9b4c-145">**LeadingAndTrailing**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-145">**LeadingAndTrailing**</span></span>|<span data-ttu-id="e9b4c-146">開頭和尾端數字皆屬於顯著。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-146">Both leading and trailing numerals are significant.</span></span>|  
  
 <span data-ttu-id="e9b4c-147">**比較旗標**</span><span class="sxs-lookup"><span data-stu-id="e9b4c-147">**Comparison Flags**</span></span>  
 <span data-ttu-id="e9b4c-148">如需字串比較選項的資訊，請參閱 [比較字串資料](data-flow/comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e9b4c-148">For information about the string comparison options, see [Comparing String Data](data-flow/comparing-string-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9b4c-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9b4c-149">See Also</span></span>  
 <span data-ttu-id="e9b4c-150">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e9b4c-150">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="e9b4c-151">使用模糊群組轉換來識別相似的資料列</span><span class="sxs-lookup"><span data-stu-id="e9b4c-151">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
