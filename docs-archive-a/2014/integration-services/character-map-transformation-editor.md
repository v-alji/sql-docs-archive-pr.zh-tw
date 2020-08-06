---
title: 字元對應轉換編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.charactermaptransformation.f1
helpviewer_keywords:
- Character Map Transformation Editor
ms.assetid: 3f1dbcf9-9cca-4606-bdcc-7ea6ad48cdf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c6cdcdba448dafc6ccf03774d4f611dee704b823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593508"
---
# <a name="character-map-transformation-editor"></a><span data-ttu-id="e33a4-102">字元對應表轉換編輯器</span><span class="sxs-lookup"><span data-stu-id="e33a4-102">Character Map Transformation Editor</span></span>
  <span data-ttu-id="e33a4-103">使用 [字元對應表轉換編輯器]\*\*\*\* 對話方塊，來選取要套用至資料行資料的字串函數，以及指定對應是就地變更或加入為新資料行。</span><span class="sxs-lookup"><span data-stu-id="e33a4-103">Use the **Character Map Transformation Editor** dialog box to select the string functions to apply to column data and to specify whether mapping is an in-place change or added as a new column.</span></span>  
  
 <span data-ttu-id="e33a4-104">若要深入了解字元對應表轉換，請參閱＜ [Character Map Transformation](data-flow/transformations/character-map-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e33a4-104">To learn more about the Character Map transformation, see [Character Map Transformation](data-flow/transformations/character-map-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e33a4-105">選項。</span><span class="sxs-lookup"><span data-stu-id="e33a4-105">Options</span></span>  
 <span data-ttu-id="e33a4-106">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="e33a4-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="e33a4-107">使用此對話方塊來選取要使用字串函數轉換的資料行。</span><span class="sxs-lookup"><span data-stu-id="e33a4-107">Use the check boxes to select the columns to transform using string functions.</span></span> <span data-ttu-id="e33a4-108">您的選擇會在下面的資料表中出現。</span><span class="sxs-lookup"><span data-stu-id="e33a4-108">Your selections appear in the table below.</span></span>  
  
 <span data-ttu-id="e33a4-109">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="e33a4-109">**Input Column**</span></span>  
 <span data-ttu-id="e33a4-110">從上述資料表檢視選取的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="e33a4-110">View input columns selected from the table above.</span></span> <span data-ttu-id="e33a4-111">您也可以藉由使用可用的輸入資料行之清單來變更或移除選擇。</span><span class="sxs-lookup"><span data-stu-id="e33a4-111">You can also change or remove a selection by using the list of available input columns.</span></span>  
  
 <span data-ttu-id="e33a4-112">**目的地**</span><span class="sxs-lookup"><span data-stu-id="e33a4-112">**Destination**</span></span>  
 <span data-ttu-id="e33a4-113">指定字串作業之結果的儲存方式為就地儲存、使用現有的資料行儲存，或將修改的資料儲存為新的資料行。</span><span class="sxs-lookup"><span data-stu-id="e33a4-113">Specify whether to save the results of the string operations in place, using the existing column, or to save the modified data as a new column.</span></span>  
  
|<span data-ttu-id="e33a4-114">值</span><span class="sxs-lookup"><span data-stu-id="e33a4-114">Value</span></span>|<span data-ttu-id="e33a4-115">描述</span><span class="sxs-lookup"><span data-stu-id="e33a4-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e33a4-116">新增資料行</span><span class="sxs-lookup"><span data-stu-id="e33a4-116">New column</span></span>|<span data-ttu-id="e33a4-117">將資料儲存在新的資料行中。</span><span class="sxs-lookup"><span data-stu-id="e33a4-117">Save the data in a new column.</span></span> <span data-ttu-id="e33a4-118">在 **[輸出別名]** 之下指派資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="e33a4-118">Assign the column name under **Output Alias**.</span></span>|  
|<span data-ttu-id="e33a4-119">就地變更</span><span class="sxs-lookup"><span data-stu-id="e33a4-119">In-place change</span></span>|<span data-ttu-id="e33a4-120">將修改的資料儲存在現有的資料行中。</span><span class="sxs-lookup"><span data-stu-id="e33a4-120">Save the modified data in the existing column.</span></span>|  
  
 <span data-ttu-id="e33a4-121">**作業**</span><span class="sxs-lookup"><span data-stu-id="e33a4-121">**Operation**</span></span>  
 <span data-ttu-id="e33a4-122">從字串函數要套用至資料行資料的清單中選取。</span><span class="sxs-lookup"><span data-stu-id="e33a4-122">Select from the list the string functions to apply to column data.</span></span>  
  
|<span data-ttu-id="e33a4-123">值</span><span class="sxs-lookup"><span data-stu-id="e33a4-123">Value</span></span>|<span data-ttu-id="e33a4-124">描述</span><span class="sxs-lookup"><span data-stu-id="e33a4-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e33a4-125">小寫</span><span class="sxs-lookup"><span data-stu-id="e33a4-125">Lowercase</span></span>|<span data-ttu-id="e33a4-126">轉換為小寫。</span><span class="sxs-lookup"><span data-stu-id="e33a4-126">Convert to lower case.</span></span>|  
|<span data-ttu-id="e33a4-127">大寫</span><span class="sxs-lookup"><span data-stu-id="e33a4-127">Uppercase</span></span>|<span data-ttu-id="e33a4-128">轉換為大寫。</span><span class="sxs-lookup"><span data-stu-id="e33a4-128">Convert to upper case.</span></span>|  
|<span data-ttu-id="e33a4-129">位元組反轉</span><span class="sxs-lookup"><span data-stu-id="e33a4-129">Byte reversal</span></span>|<span data-ttu-id="e33a4-130">藉由反轉位元組的順序來進行轉換。</span><span class="sxs-lookup"><span data-stu-id="e33a4-130">Convert by reversing byte order.</span></span>|  
|<span data-ttu-id="e33a4-131">平假名</span><span class="sxs-lookup"><span data-stu-id="e33a4-131">Hiragana</span></span>|<span data-ttu-id="e33a4-132">將日文片假名字元轉換為平假名。</span><span class="sxs-lookup"><span data-stu-id="e33a4-132">Convert Japanese katakana characters to hiragana.</span></span>|  
|<span data-ttu-id="e33a4-133">片假名</span><span class="sxs-lookup"><span data-stu-id="e33a4-133">Katakana</span></span>|<span data-ttu-id="e33a4-134">將日文平假名字元轉換為片假名。</span><span class="sxs-lookup"><span data-stu-id="e33a4-134">Convert Japanese hiragana characters to katakana.</span></span>|  
|<span data-ttu-id="e33a4-135">半形</span><span class="sxs-lookup"><span data-stu-id="e33a4-135">Half width</span></span>|<span data-ttu-id="e33a4-136">將全形字元轉換為半形。</span><span class="sxs-lookup"><span data-stu-id="e33a4-136">Convert full-width characters to half width.</span></span>|  
|<span data-ttu-id="e33a4-137">全形</span><span class="sxs-lookup"><span data-stu-id="e33a4-137">Full width</span></span>|<span data-ttu-id="e33a4-138">將半形字元轉換為全形。</span><span class="sxs-lookup"><span data-stu-id="e33a4-138">Convert half-width characters to full width.</span></span>|  
|<span data-ttu-id="e33a4-139">語言大小寫</span><span class="sxs-lookup"><span data-stu-id="e33a4-139">Linguistic casing</span></span>|<span data-ttu-id="e33a4-140">套用大小寫的語言規則 (突厥語系和其他地區設定的 Unicode 簡單大小寫對應) 來取代系統規則。</span><span class="sxs-lookup"><span data-stu-id="e33a4-140">Apply linguistic rules of casing (Unicode simple case mapping for Turkic and other locales) instead of the system rules.</span></span>|  
|<span data-ttu-id="e33a4-141">簡體中文</span><span class="sxs-lookup"><span data-stu-id="e33a4-141">Simplified Chinese</span></span>|<span data-ttu-id="e33a4-142">將繁體中文字元轉換為簡體中文。</span><span class="sxs-lookup"><span data-stu-id="e33a4-142">Convert traditional Chinese characters to simplified Chinese.</span></span>|  
|<span data-ttu-id="e33a4-143">繁體中文</span><span class="sxs-lookup"><span data-stu-id="e33a4-143">Traditional Chinese</span></span>|<span data-ttu-id="e33a4-144">將簡體中文字元轉換為繁體中文。</span><span class="sxs-lookup"><span data-stu-id="e33a4-144">Convert simplified Chinese characters to traditional Chinese.</span></span>|  
  
 <span data-ttu-id="e33a4-145">**輸出別名**</span><span class="sxs-lookup"><span data-stu-id="e33a4-145">**Output Alias**</span></span>  
 <span data-ttu-id="e33a4-146">輸入每一個輸出資料行的別名。</span><span class="sxs-lookup"><span data-stu-id="e33a4-146">Type an alias for each output column.</span></span> <span data-ttu-id="e33a4-147">預設為輸入資料行的名稱，後面接著 **[的副本]** ；但是您也可以選擇任何唯一的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="e33a4-147">The default is **Copy of** followed by the input column name; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="e33a4-148">**設定錯誤輸出**</span><span class="sxs-lookup"><span data-stu-id="e33a4-148">**Configure Error Output**</span></span>  
 <span data-ttu-id="e33a4-149">使用 [設定錯誤輸出](../../2014/integration-services/configure-error-output.md) 對話方塊，即可指定此轉換的錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="e33a4-149">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling options for this transformation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e33a4-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e33a4-150">See Also</span></span>  
 [<span data-ttu-id="e33a4-151">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="e33a4-151">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
