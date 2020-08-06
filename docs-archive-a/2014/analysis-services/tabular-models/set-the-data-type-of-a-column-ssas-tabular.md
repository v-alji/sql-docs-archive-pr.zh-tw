---
title: 設定資料行 (SSAS 表格式) 的資料類型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 34e2d508-7b64-4503-a4f0-c6c6ad5f8a44
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1d747f96e836a683ccce3aca3c5e3349ca633210
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686492"
---
# <a name="set-the-data-type-of-a-column-ssas-tabular"></a><span data-ttu-id="28c62-102">設定資料行的資料類型 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="28c62-102">Set the Data Type of a Column (SSAS Tabular)</span></span>
  <span data-ttu-id="28c62-103">當您將資料匯入或貼上模型時，模型設計師會自動偵測並套用資料類型。</span><span class="sxs-lookup"><span data-stu-id="28c62-103">When you import data or paste data into a model, the model designer will automatically detect and apply data types.</span></span> <span data-ttu-id="28c62-104">將資料加入至模型之後，您可以手動修改資料行的資料類型，以變更資料儲存的方式。</span><span class="sxs-lookup"><span data-stu-id="28c62-104">After you have added the data to the model, you can manually modify the data type of a column to change how data is stored.</span></span> <span data-ttu-id="28c62-105">如果您只要變更資料顯示方式的格式，而不要變更其儲存方式，可以只變更該顯示格式。</span><span class="sxs-lookup"><span data-stu-id="28c62-105">If you just want to change the format of how the data is displayed without changing the way it is stored, you can do that instead.</span></span>  
  
### <a name="to-change-the-data-type-or-display-format-for-a-column"></a><span data-ttu-id="28c62-106">若要變更資料行的資料類型或顯示格式</span><span class="sxs-lookup"><span data-stu-id="28c62-106">To change the data type or display format for a column</span></span>  
  
1.  <span data-ttu-id="28c62-107">在模型設計師中，選取您要變更資料類型或顯示格式的資料行。</span><span class="sxs-lookup"><span data-stu-id="28c62-107">In the model designer, select the column for which you want to change the data type or display format.</span></span>  
  
2.  <span data-ttu-id="28c62-108">在資料行 **[屬性]** 視窗中，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="28c62-108">In the column **Properties** window, do one of the following:</span></span>  
  
    -   <span data-ttu-id="28c62-109">在 **[資料格式]** 屬性中，選取其他資料格式。</span><span class="sxs-lookup"><span data-stu-id="28c62-109">In the **Data Format** property, select a different data format.</span></span>  
  
    -   <span data-ttu-id="28c62-110">在 **[資料類型]** 屬性中，選取其他資料類型。</span><span class="sxs-lookup"><span data-stu-id="28c62-110">In the **Data Type** property, select a different data type.</span></span>  
  
## <a name="considerations-when-changing-data-types"></a><span data-ttu-id="28c62-111">變更資料類型時的考量</span><span class="sxs-lookup"><span data-stu-id="28c62-111">Considerations when Changing Data Types</span></span>  
 <span data-ttu-id="28c62-112">有時當您嘗試變更資料行的資料類型或選取資料轉換時，可能會發生下列其中一項錯誤：</span><span class="sxs-lookup"><span data-stu-id="28c62-112">Sometimes when you try to change the data type of a column or select a data conversion, one of the following errors might occur:</span></span>  
  
-   <span data-ttu-id="28c62-113">無法變更資料類型</span><span class="sxs-lookup"><span data-stu-id="28c62-113">Failed to change data type</span></span>  
  
-   <span data-ttu-id="28c62-114">無法變更資料行資料類型</span><span class="sxs-lookup"><span data-stu-id="28c62-114">Failed to change column data type</span></span>  
  
 <span data-ttu-id="28c62-115">即使該資料類型以選項的形式出現在 [資料類型] 下拉式清單中提供使用，也可能會發生這些錯誤。</span><span class="sxs-lookup"><span data-stu-id="28c62-115">These errors might occur even if the data type is available as an option in the Data Type dropdown list.</span></span> <span data-ttu-id="28c62-116">本節將說明這些錯誤的原因及更正方法。</span><span class="sxs-lookup"><span data-stu-id="28c62-116">This section explains the cause of these errors and how you can correct them.</span></span>  
  
### <a name="understanding-automatically-determined-data-types"></a><span data-ttu-id="28c62-117">了解自動判斷的資料類型</span><span class="sxs-lookup"><span data-stu-id="28c62-117">Understanding Automatically Determined Data Types</span></span>  
 <span data-ttu-id="28c62-118">當您將資料加入至模型時，模型設計師會檢查資料的資料行，以查看每個資料行所包含的資料類型。</span><span class="sxs-lookup"><span data-stu-id="28c62-118">When you add data to a model, the model designer checks the columns of data to see what data types each column contains.</span></span> <span data-ttu-id="28c62-119">如果該資料行中的資料是一致的，就會指派最精確的資料類型至該資料行。</span><span class="sxs-lookup"><span data-stu-id="28c62-119">If the data in that column is consistent, is assigns the most precise data type to the column.</span></span>  
  
 <span data-ttu-id="28c62-120">但是，如果加入的資料是來自 Excel 或其他不強制在每個資料行內使用單一資料類型的來源時，模型設計師將指派可適合此資料行內所有值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="28c62-120">However, if you add data from Excel or another source that does not enforce the use of a single data type within each column, the model designer will assign a data type that accommodates all values within the column.</span></span> <span data-ttu-id="28c62-121">因此，如果資料行包含不同類型的數字 (如整數、長數字和貨幣)，模型設計師會使用十進位資料類型。</span><span class="sxs-lookup"><span data-stu-id="28c62-121">Therefore, if a column contains numbers of different types, such as integers, long numbers, and currency, the model designer will use a decimal data type.</span></span> <span data-ttu-id="28c62-122">或者，如果資料行中混合數字和文字，則模型設計師會使用文字資料類型。</span><span class="sxs-lookup"><span data-stu-id="28c62-122">Alternatively, if a column mixes numbers and text, the model designer will use the text data type.</span></span> <span data-ttu-id="28c62-123">模型設計師不提供與 Excel「通用格式」資料類型類似的資料類型。</span><span class="sxs-lookup"><span data-stu-id="28c62-123">The model designer does not provide a data type similar to the General data type available in Excel.</span></span>  
  
 <span data-ttu-id="28c62-124">因此，如果資料行同時包含數字和文字值，您便無法將此資料行轉換成數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="28c62-124">Therefore, if a column contains both numbers and text values, you will not be able to convert the column to a numeric data type.</span></span>  
  
 <span data-ttu-id="28c62-125">下列是商業智慧語意模型中可用的資料類型：</span><span class="sxs-lookup"><span data-stu-id="28c62-125">The following data types are available in business intelligence semantic models:</span></span>  
  
|<span data-ttu-id="28c62-126">模型資料類型</span><span class="sxs-lookup"><span data-stu-id="28c62-126">Model data types</span></span>|  
|----------------------|  
|<span data-ttu-id="28c62-127">Text</span><span class="sxs-lookup"><span data-stu-id="28c62-127">Text</span></span><br /><br /> <span data-ttu-id="28c62-128">十進位數字</span><span class="sxs-lookup"><span data-stu-id="28c62-128">Decimal Number</span></span><br /><br /> <span data-ttu-id="28c62-129">整數</span><span class="sxs-lookup"><span data-stu-id="28c62-129">Whole Number</span></span><br /><br /> <span data-ttu-id="28c62-130">貨幣</span><span class="sxs-lookup"><span data-stu-id="28c62-130">Currency</span></span><br /><br /> <span data-ttu-id="28c62-131">TRUE/FALSE</span><span class="sxs-lookup"><span data-stu-id="28c62-131">TRUE/FALSE</span></span><br /><br /> <span data-ttu-id="28c62-132">Date</span><span class="sxs-lookup"><span data-stu-id="28c62-132">Date</span></span>|  
  
 <span data-ttu-id="28c62-133">如果發現資料的資料類型錯誤，或是與您想要的資料類型不同，您有幾個選擇：</span><span class="sxs-lookup"><span data-stu-id="28c62-133">If you find that your data has a wrong data type, or at least a different one than you wanted, you have several options:</span></span>  
  
-   <span data-ttu-id="28c62-134">您可以重新匯入資料。</span><span class="sxs-lookup"><span data-stu-id="28c62-134">You can re-import the data.</span></span> <span data-ttu-id="28c62-135">若要重新匯入，請開啟與資料來源之間的現有連接，然後重新匯入資料行。</span><span class="sxs-lookup"><span data-stu-id="28c62-135">To do this, open the existing connection to the data source and re-import the column.</span></span> <span data-ttu-id="28c62-136">根據資料來源類型而定，您也許可以在匯入期間套用篩選來移除有問題的值。</span><span class="sxs-lookup"><span data-stu-id="28c62-136">Depending on the data source type, you might be able to apply a filter during import to remove problem values.</span></span>  
  
-   <span data-ttu-id="28c62-137">您可以在導出資料行中建立 DAX 公式來建立屬於所需資料類型的新值</span><span class="sxs-lookup"><span data-stu-id="28c62-137">You can create a DAX formula in a calculated column to create a new value of the desired data type.</span></span> <span data-ttu-id="28c62-138">例如，可以使用 TRUNC 函數將十進位數字變更為整數，或者可以結合資訊函數和邏輯函數來測試及轉換值。</span><span class="sxs-lookup"><span data-stu-id="28c62-138">For example, the TRUNC function can be used to change a decimal number to a whole integer, or you can combine information functions and logical functions to test and convert values.</span></span>  
  
### <a name="understanding-data-conversion"></a><span data-ttu-id="28c62-139">了解資料轉換</span><span class="sxs-lookup"><span data-stu-id="28c62-139">Understanding Data Conversion</span></span>  
 <span data-ttu-id="28c62-140">如果您在選取資料轉換選項時發生錯誤，可能是目前資料行的資料類型不支援所選取的轉換。</span><span class="sxs-lookup"><span data-stu-id="28c62-140">If an error occurs when you select a data conversion option, it might be that the current data type of the column does not support the selected conversion.</span></span> <span data-ttu-id="28c62-141">並非所有資料類型都允許所有轉換。</span><span class="sxs-lookup"><span data-stu-id="28c62-141">Not all conversions are allowed for all data types.</span></span> <span data-ttu-id="28c62-142">例如，如果目前資料行的資料類型為數字 (整數或十進位) 或文字，您只能將資料行變更為布林值資料類型。</span><span class="sxs-lookup"><span data-stu-id="28c62-142">For example, you can only change a column to a Boolean data type if the current data type of the column is either a number (whole or decimal) or text.</span></span> <span data-ttu-id="28c62-143">因此，您必須針對資料行中的資料選擇適當的資料類型。</span><span class="sxs-lookup"><span data-stu-id="28c62-143">Therefore, you must choose an appropriate data type for the data in the column.</span></span>  
  
 <span data-ttu-id="28c62-144">當您選擇適當的資料類型之後，模型設計師會警告您可能發生的資料變更，例如失去精確度或截斷。</span><span class="sxs-lookup"><span data-stu-id="28c62-144">After you choose an appropriate data type, the model designer will warn you about possible changes to your data, such as loss of precision, or truncation.</span></span> <span data-ttu-id="28c62-145">請按一下 [確定] 接受，然後將資料變更為新的資料類型。</span><span class="sxs-lookup"><span data-stu-id="28c62-145">Click OK to accept and change your data to the new data type.</span></span>  
  
 <span data-ttu-id="28c62-146">如果資料類型受到支援，但是模型設計師卻發現不受新資料類型支援的值，您會接到另一項錯誤，並將需要修正資料值，才能再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="28c62-146">If the data type is supported, but the model designer finds values that are not supported within the new data type, you will get another error, and will need to correct the data values before proceeding.</span></span>  
  
 <span data-ttu-id="28c62-147">如需商業智慧語意模型中使用的資料類型、如何以隱含方式轉換這些資料類型，以及如何在公式內使用不同資料類型等的詳細資訊，請參閱 [支援的資料類型 &#40;SSAS 表格式&#41;](data-types-supported-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="28c62-147">For detailed information about the data types used in business intelligence semantic models, how they are implicitly converted, and how different data types are used in formulas, see [Data Types Supported &#40;SSAS Tabular&#41;](data-types-supported-ssas-tabular.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c62-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28c62-148">See Also</span></span>  
 [<span data-ttu-id="28c62-149">支援的資料類型 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="28c62-149">Data Types Supported &#40;SSAS Tabular&#41;</span></span>](data-types-supported-ssas-tabular.md)  
  
  
