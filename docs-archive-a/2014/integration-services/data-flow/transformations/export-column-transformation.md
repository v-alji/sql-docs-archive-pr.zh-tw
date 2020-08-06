---
title: 匯出資料行轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exportcolumntrans.f1
helpviewer_keywords:
- exporting data
- append options [Integration Services]
- Export Column transformation [Integration Services]
- columns [Integration Services], exporting
- inserting data
- truncate options [Integration Services]
ms.assetid: 678d2dfc-e40c-4fbb-b2cc-42fffc44478a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7ed2bef02d75b72870514e2333d2fa58720fb60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592782"
---
# <a name="export-column-transformation"></a><span data-ttu-id="2ac1b-102">匯出資料行轉換</span><span class="sxs-lookup"><span data-stu-id="2ac1b-102">Export Column Transformation</span></span>
  <span data-ttu-id="2ac1b-103">「匯出資料行」轉換會讀取資料流程中的資料，並將資料插入檔案中。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-103">The Export Column transformation reads data in a data flow and inserts the data into a file.</span></span> <span data-ttu-id="2ac1b-104">例如，如果資料流程包含產品資訊 (例如每一項產品的圖片)，則可使用「匯出資料行」轉換將影像儲存到檔案中。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-104">For example, if the data flow contains product information, such as a picture of each product, you could use the Export Column transformation to save the images to files.</span></span>  
  
## <a name="append-and-truncate-options"></a><span data-ttu-id="2ac1b-105">附加和截斷選項</span><span class="sxs-lookup"><span data-stu-id="2ac1b-105">Append and Truncate Options</span></span>  
 <span data-ttu-id="2ac1b-106">下表說明附加和截斷選項的設定影響結果的方式。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-106">The following table describes how the settings for the append and truncate options affect results.</span></span>  
  
|<span data-ttu-id="2ac1b-107">附加</span><span class="sxs-lookup"><span data-stu-id="2ac1b-107">Append</span></span>|<span data-ttu-id="2ac1b-108">Truncate</span><span class="sxs-lookup"><span data-stu-id="2ac1b-108">Truncate</span></span>|<span data-ttu-id="2ac1b-109">檔案存在</span><span class="sxs-lookup"><span data-stu-id="2ac1b-109">File exists</span></span>|<span data-ttu-id="2ac1b-110">結果</span><span class="sxs-lookup"><span data-stu-id="2ac1b-110">Results</span></span>|  
|------------|--------------|-----------------|-------------|  
|<span data-ttu-id="2ac1b-111">False</span><span class="sxs-lookup"><span data-stu-id="2ac1b-111">False</span></span>|<span data-ttu-id="2ac1b-112">False</span><span class="sxs-lookup"><span data-stu-id="2ac1b-112">False</span></span>|<span data-ttu-id="2ac1b-113">否</span><span class="sxs-lookup"><span data-stu-id="2ac1b-113">No</span></span>|<span data-ttu-id="2ac1b-114">轉換會建立新檔案，並將資料寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-114">The transformation creates a new file and writes the data to the file.</span></span>|  
|<span data-ttu-id="2ac1b-115">True</span><span class="sxs-lookup"><span data-stu-id="2ac1b-115">True</span></span>|<span data-ttu-id="2ac1b-116">False</span><span class="sxs-lookup"><span data-stu-id="2ac1b-116">False</span></span>|<span data-ttu-id="2ac1b-117">否</span><span class="sxs-lookup"><span data-stu-id="2ac1b-117">No</span></span>|<span data-ttu-id="2ac1b-118">轉換會建立新檔案，並將資料寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-118">The transformation creates a new file and writes the data to the file.</span></span>|  
|<span data-ttu-id="2ac1b-119">False</span><span class="sxs-lookup"><span data-stu-id="2ac1b-119">False</span></span>|<span data-ttu-id="2ac1b-120">True</span><span class="sxs-lookup"><span data-stu-id="2ac1b-120">True</span></span>|<span data-ttu-id="2ac1b-121">否</span><span class="sxs-lookup"><span data-stu-id="2ac1b-121">No</span></span>|<span data-ttu-id="2ac1b-122">轉換會建立新檔案，並將資料寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-122">The transformation creates a new file and writes the data to the file.</span></span>|  
|<span data-ttu-id="2ac1b-123">True</span><span class="sxs-lookup"><span data-stu-id="2ac1b-123">True</span></span>|<span data-ttu-id="2ac1b-124">True</span><span class="sxs-lookup"><span data-stu-id="2ac1b-124">True</span></span>|<span data-ttu-id="2ac1b-125">否</span><span class="sxs-lookup"><span data-stu-id="2ac1b-125">No</span></span>|<span data-ttu-id="2ac1b-126">轉換未通過設計階段驗證。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-126">The transformation fails design time validation.</span></span> <span data-ttu-id="2ac1b-127">將兩個屬性都設定為 `true` 是無效的。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-127">It is not valid to set both properties to `true`.</span></span>|  
|<span data-ttu-id="2ac1b-128">False</span><span class="sxs-lookup"><span data-stu-id="2ac1b-128">False</span></span>|<span data-ttu-id="2ac1b-129">False</span><span class="sxs-lookup"><span data-stu-id="2ac1b-129">False</span></span>|<span data-ttu-id="2ac1b-130">是</span><span class="sxs-lookup"><span data-stu-id="2ac1b-130">Yes</span></span>|<span data-ttu-id="2ac1b-131">發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-131">A run-time error occurs.</span></span> <span data-ttu-id="2ac1b-132">檔案存在，但轉換無法寫入該檔案。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-132">The file exists, but the transformation cannot write to it.</span></span>|  
|<span data-ttu-id="2ac1b-133">False</span><span class="sxs-lookup"><span data-stu-id="2ac1b-133">False</span></span>|<span data-ttu-id="2ac1b-134">True</span><span class="sxs-lookup"><span data-stu-id="2ac1b-134">True</span></span>|<span data-ttu-id="2ac1b-135">是</span><span class="sxs-lookup"><span data-stu-id="2ac1b-135">Yes</span></span>|<span data-ttu-id="2ac1b-136">轉換會刪除並重新建立檔案，然後將資料寫入該檔案中。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-136">The transformation deletes and re-creates the file and writes the data to the file.</span></span>|  
|<span data-ttu-id="2ac1b-137">True</span><span class="sxs-lookup"><span data-stu-id="2ac1b-137">True</span></span>|<span data-ttu-id="2ac1b-138">False</span><span class="sxs-lookup"><span data-stu-id="2ac1b-138">False</span></span>|<span data-ttu-id="2ac1b-139">是</span><span class="sxs-lookup"><span data-stu-id="2ac1b-139">Yes</span></span>|<span data-ttu-id="2ac1b-140">轉換會開啟該檔案，並將資料寫入檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-140">The transformation opens the file and writes the data at the end of the file.</span></span>|  
|<span data-ttu-id="2ac1b-141">True</span><span class="sxs-lookup"><span data-stu-id="2ac1b-141">True</span></span>|<span data-ttu-id="2ac1b-142">True</span><span class="sxs-lookup"><span data-stu-id="2ac1b-142">True</span></span>|<span data-ttu-id="2ac1b-143">是</span><span class="sxs-lookup"><span data-stu-id="2ac1b-143">Yes</span></span>|<span data-ttu-id="2ac1b-144">轉換未通過設計階段驗證。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-144">The transformation fails design time validation.</span></span> <span data-ttu-id="2ac1b-145">將兩個屬性都設定為 `true` 是無效的。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-145">It is not valid to set both properties to `true`.</span></span>|  
  
## <a name="configuration-of-the-export-column-transformation"></a><span data-ttu-id="2ac1b-146">設定匯出資料行轉換</span><span class="sxs-lookup"><span data-stu-id="2ac1b-146">Configuration of the Export Column Transformation</span></span>  
 <span data-ttu-id="2ac1b-147">您可以利用下列方式設定「匯出資料行」轉換：</span><span class="sxs-lookup"><span data-stu-id="2ac1b-147">You can configure the Export Column transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="2ac1b-148">指定資料的資料行，以及包含要寫入資料的檔案路徑的資料行。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-148">Specify the data columns and the columns that contain the path of files to which to write the data.</span></span>  
  
-   <span data-ttu-id="2ac1b-149">指定資料插入作業應附加或截斷現有檔案。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-149">Specify whether the data-insertion operation appends or truncates existing files.</span></span>  
  
-   <span data-ttu-id="2ac1b-150">指定是否要將位元組順序標記 (BOM) 寫入該檔案。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-150">Specify whether a byte-order mark (BOM) is written to the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2ac1b-151">BOM 只有在資料未附加至現有檔案，且資料類型為 DT_NTEXT 時才寫入。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-151">A BOM is written only when the data is not appended to an existing file and the data has the DT_NTEXT data type.</span></span>  
  
 <span data-ttu-id="2ac1b-152">轉換使用成對的輸入資料行：一個資料行包含一個檔案名稱，另一個資料行則包含資料。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-152">The transformation uses pairs of input columns: One column contains a file name, and the other column contains data.</span></span> <span data-ttu-id="2ac1b-153">資料集中的每一個資料列都可指定不同的檔案。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-153">Each row in the data set can specify a different file.</span></span> <span data-ttu-id="2ac1b-154">當轉換處理資料列時，會將資料插入指定的檔案中。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-154">As the transformation processes a row, the data is inserted into the specified file.</span></span> <span data-ttu-id="2ac1b-155">在執行階段，轉換會建立檔案 (如果檔案不存在)，然後將資料寫入這些檔案中。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-155">At run time, the transformation creates the files, if they do not already exist, and then the transformation writes the data to the files.</span></span> <span data-ttu-id="2ac1b-156">要寫入的資料的資料類型必須為 DT_TEXT、DT_NTEXT 或 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-156">The data to be written must have a DT_TEXT, DT_NTEXT, or DT_IMAGE data type.</span></span> <span data-ttu-id="2ac1b-157">如需詳細資訊，請參閱 [Integration Services 資料類型](../integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-157">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="2ac1b-158">這個轉換有一個輸入、一個輸出與一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-158">This transformation has one input, one output, and one error output.</span></span>  
  
 <span data-ttu-id="2ac1b-159">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-159">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="2ac1b-160">如需可在 [匯出資料行轉換編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請參閱[匯出資料行轉換編輯器 &#40;資料行頁面&#41;](../../export-column-transformation-editor-columns-page.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-160">For more information about the properties that you can set in the **Export Column Transformation Editor** dialog box, see [Export Column Transformation Editor &#40;Columns Page&#41;](../../export-column-transformation-editor-columns-page.md).</span></span>  
  
 <span data-ttu-id="2ac1b-161">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-161">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="2ac1b-162">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="2ac1b-162">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="2ac1b-163">Common Properties</span><span class="sxs-lookup"><span data-stu-id="2ac1b-163">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="2ac1b-164">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="2ac1b-164">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="2ac1b-165">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac1b-165">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
