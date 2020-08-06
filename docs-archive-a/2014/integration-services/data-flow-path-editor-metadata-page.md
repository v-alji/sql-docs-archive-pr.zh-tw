---
title: 資料流程路徑編輯器 (中繼資料頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.patheditor.metadata.f1
helpviewer_keywords:
- Data Flow Path Editor dialog box
ms.assetid: b30bb9d7-ebc0-4b1a-8d0f-ee006b32e841
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c2c314707d8baa2fb0f853438f6486acf2a10a37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688105"
---
# <a name="data-flow-path-editor-metadata-page"></a><span data-ttu-id="5db0e-102">資料流程路徑編輯器 (中繼資料頁面)</span><span class="sxs-lookup"><span data-stu-id="5db0e-102">Data Flow Path Editor (Metadata Page)</span></span>
  <span data-ttu-id="5db0e-103">使用 [資料流程路徑編輯器]\*\*\*\* 對話方塊的 [中繼資料]\*\*\*\* 頁面，即可檢視路徑資料行的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5db0e-103">Use the **Metadata** page of the **Data Flow Path Editor** dialog box to view the metadata of the path columns.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5db0e-104">選項</span><span class="sxs-lookup"><span data-stu-id="5db0e-104">Options</span></span>  
 <span data-ttu-id="5db0e-105">**路徑中繼資料**</span><span class="sxs-lookup"><span data-stu-id="5db0e-105">**Path metadata**</span></span>  
 <span data-ttu-id="5db0e-106">列出資料行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5db0e-106">Lists column metadata.</span></span> <span data-ttu-id="5db0e-107">按一下資料行標題來排序資料行資料。</span><span class="sxs-lookup"><span data-stu-id="5db0e-107">Click the column headings to sort column data.</span></span>  
  
 <span data-ttu-id="5db0e-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="5db0e-108">**Name**</span></span>  
 <span data-ttu-id="5db0e-109">列出資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="5db0e-109">Lists the column name.</span></span>  
  
 <span data-ttu-id="5db0e-110">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="5db0e-110">**Data Type**</span></span>  
 <span data-ttu-id="5db0e-111">列出資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5db0e-111">Lists the data type of the column.</span></span>  
  
 <span data-ttu-id="5db0e-112">**有效位數**</span><span class="sxs-lookup"><span data-stu-id="5db0e-112">**Precision**</span></span>  
 <span data-ttu-id="5db0e-113">列出數值中的位數。</span><span class="sxs-lookup"><span data-stu-id="5db0e-113">Lists the number of digits in a numeric value.</span></span>  
  
 <span data-ttu-id="5db0e-114">**縮放比例**</span><span class="sxs-lookup"><span data-stu-id="5db0e-114">**Scale**</span></span>  
 <span data-ttu-id="5db0e-115">列出數值中之小數點右邊的位數。</span><span class="sxs-lookup"><span data-stu-id="5db0e-115">List the number of digits to the right of the decimal point in a numeric value.</span></span>  
  
 <span data-ttu-id="5db0e-116">**長度**</span><span class="sxs-lookup"><span data-stu-id="5db0e-116">**Length**</span></span>  
 <span data-ttu-id="5db0e-117">列出資料行的目前長度。</span><span class="sxs-lookup"><span data-stu-id="5db0e-117">Lists the current length of the column.</span></span>  
  
 <span data-ttu-id="5db0e-118">**字碼頁**</span><span class="sxs-lookup"><span data-stu-id="5db0e-118">**Code Page**</span></span>  
 <span data-ttu-id="5db0e-119">列出資料行的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="5db0e-119">Lists the code page of the column.</span></span> <span data-ttu-id="5db0e-120">值為 **0** 時，指出資料行不使用字碼頁。</span><span class="sxs-lookup"><span data-stu-id="5db0e-120">The value **0** indicates that the column does not use a code page.</span></span> <span data-ttu-id="5db0e-121">這是在資料為 Unicode 格式，或資料具有數值、日期或時間等資料類型時才會發生。</span><span class="sxs-lookup"><span data-stu-id="5db0e-121">This occurs when data is in Unicode, or has a numeric, date, or time data type.</span></span>  
  
 <span data-ttu-id="5db0e-122">**排序索引鍵位置**</span><span class="sxs-lookup"><span data-stu-id="5db0e-122">**Sort Key Position**</span></span>  
 <span data-ttu-id="5db0e-123">列出資料行的排序索引鍵位置。</span><span class="sxs-lookup"><span data-stu-id="5db0e-123">Lists the sort key position of the column.</span></span> <span data-ttu-id="5db0e-124">值為 **0** 時，指出資料行並未排序。</span><span class="sxs-lookup"><span data-stu-id="5db0e-124">The value **0** indicates the column is not sorted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5db0e-125">減號 (-) 前置詞指出資料行是以遞減的順序來排序。</span><span class="sxs-lookup"><span data-stu-id="5db0e-125">A minus (-) prefix indicates the column is sorted in descending order.</span></span>  
  
 <span data-ttu-id="5db0e-126">**比較旗標**</span><span class="sxs-lookup"><span data-stu-id="5db0e-126">**Comparison Flags**</span></span>  
 <span data-ttu-id="5db0e-127">列出套用至資料行的比較旗標。</span><span class="sxs-lookup"><span data-stu-id="5db0e-127">Lists the comparison flags that apply to the column.</span></span>  
  
 <span data-ttu-id="5db0e-128">**來源元件**</span><span class="sxs-lookup"><span data-stu-id="5db0e-128">**Source Component**</span></span>  
 <span data-ttu-id="5db0e-129">列出是資料行來源的資料流程元件。</span><span class="sxs-lookup"><span data-stu-id="5db0e-129">Lists the data flow component that is the source of the column.</span></span>  
  
 <span data-ttu-id="5db0e-130">**複製至剪貼簿**</span><span class="sxs-lookup"><span data-stu-id="5db0e-130">**Copy to Clipboard**</span></span>  
 <span data-ttu-id="5db0e-131">將資料行中繼資料複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="5db0e-131">Copy the column metadata to the clipboard.</span></span> <span data-ttu-id="5db0e-132">依預設，所有中繼資料列都會加以複製，就像依目前顯示的順序加以排序一般。</span><span class="sxs-lookup"><span data-stu-id="5db0e-132">By default, all metadata rows are copied as sorted in the order currently displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db0e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5db0e-133">See Also</span></span>  
 <span data-ttu-id="5db0e-134">[[資料流程路徑編輯器] &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="5db0e-134">[Data Flow Path Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="5db0e-135">[資料檢視器頁面 &#40;的資料流程路徑編輯器&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md) </span><span class="sxs-lookup"><span data-stu-id="5db0e-135">[Data Flow Path Editor &#40;Data Viewers Page&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md) </span></span>  
 <span data-ttu-id="5db0e-136">[資料流程](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="5db0e-136">[Data Flow](data-flow/data-flow.md) </span></span>  
 [<span data-ttu-id="5db0e-137">使用封裝中的註解</span><span class="sxs-lookup"><span data-stu-id="5db0e-137">Use Annotations in Packages</span></span>](use-annotations-in-packages.md)  
  
  
