---
title: 匯出資料行轉換編輯器 (資料行頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 404b404e2328228049ae46fb1c3089b0b4089f0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594123"
---
# <a name="export-column-transformation-editor-columns-page"></a><span data-ttu-id="5d296-102">匯出資料行轉換編輯器 (資料行頁面)</span><span class="sxs-lookup"><span data-stu-id="5d296-102">Export Column Transformation Editor (Columns Page)</span></span>
  <span data-ttu-id="5d296-103">使用 **[匯出資料行轉換編輯器]** 對話方塊的 **[資料行]** 頁面，即可指定資料流程中要擷取至檔案的資料行。</span><span class="sxs-lookup"><span data-stu-id="5d296-103">Use the **Columns** page of the **Export Column Transformation Editor** dialog box to specify columns in the data flow to extract to files.</span></span> <span data-ttu-id="5d296-104">您可以指定匯出資料行轉換將資料附加至檔案或複寫現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="5d296-104">You can specify whether the Export Column transformation appends data to a file or overwrites an existing file.</span></span>  
  
 <span data-ttu-id="5d296-105">若要深入了解匯出資料行轉換，請參閱＜ [Export Column Transformation](data-flow/transformations/export-column-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5d296-105">To learn more about the Export Column transformation, see [Export Column Transformation](data-flow/transformations/export-column-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5d296-106">選項</span><span class="sxs-lookup"><span data-stu-id="5d296-106">Options</span></span>  
 <span data-ttu-id="5d296-107">**擷取資料行**</span><span class="sxs-lookup"><span data-stu-id="5d296-107">**Extract Column**</span></span>  
 <span data-ttu-id="5d296-108">從包含文字或影像資料的輸入資料行清單中選取。</span><span class="sxs-lookup"><span data-stu-id="5d296-108">Select from the list of input columns that contain text or image data.</span></span> <span data-ttu-id="5d296-109">所有資料列應有 **[擷取資料行]** 和 **[檔案路徑資料行]** 的定義。</span><span class="sxs-lookup"><span data-stu-id="5d296-109">All rows should have definitions for **Extract Column** and **File Path Column**.</span></span>  
  
 <span data-ttu-id="5d296-110">**[檔案路徑資料行]**</span><span class="sxs-lookup"><span data-stu-id="5d296-110">**File Path Column**</span></span>  
 <span data-ttu-id="5d296-111">從包含檔案路徑和檔案名稱的輸入資料行清單中選取。</span><span class="sxs-lookup"><span data-stu-id="5d296-111">Select from the list of input columns that contain file paths and file names.</span></span> <span data-ttu-id="5d296-112">所有資料列應有 **[擷取資料行]** 和 **[檔案路徑資料行]** 的定義。</span><span class="sxs-lookup"><span data-stu-id="5d296-112">All rows should have definitions for **Extract Column** and **File Path Column**.</span></span>  
  
 <span data-ttu-id="5d296-113">**允許附加**</span><span class="sxs-lookup"><span data-stu-id="5d296-113">**Allow Append**</span></span>  
 <span data-ttu-id="5d296-114">指定轉換是否將資料附加至現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="5d296-114">Specify whether the transformation appends data to existing files.</span></span> <span data-ttu-id="5d296-115">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="5d296-115">The default is `false`.</span></span>  
  
 <span data-ttu-id="5d296-116">**強制截斷**</span><span class="sxs-lookup"><span data-stu-id="5d296-116">**Force Truncate**</span></span>  
 <span data-ttu-id="5d296-117">指定轉換是否在寫入資料之前刪除現有檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="5d296-117">Specify whether the transformation deletes the contents of existing files before writing data.</span></span> <span data-ttu-id="5d296-118">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="5d296-118">The default is `false`.</span></span>  
  
 <span data-ttu-id="5d296-119">**寫入 BOM**</span><span class="sxs-lookup"><span data-stu-id="5d296-119">**Write BOM**</span></span>  
 <span data-ttu-id="5d296-120">指定是否將位元組順序標記 (BOM) 寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="5d296-120">Specify whether to write a byte-order mark (BOM) to the file.</span></span> <span data-ttu-id="5d296-121">當資料擁有 `DT_NTEXT` 或 DT_WSTR 資料類型，且未附加至現有的資料檔時，才會寫入 BOM。</span><span class="sxs-lookup"><span data-stu-id="5d296-121">A BOM is only written if the data has the `DT_NTEXT` or DT_WSTR data type and is not appended to an existing data file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d296-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d296-122">See Also</span></span>  
 <span data-ttu-id="5d296-123">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="5d296-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="5d296-124">匯出資料行轉換編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="5d296-124">Export Column Transformation Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)  
  
  
