---
title: 連接到一般檔案 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connflatfile.f1
ms.assetid: a365991e-eded-4cd8-89c0-0daf6d658d15
author: minewiskan
ms.author: owend
ms.openlocfilehash: e6bee3c8f7f4b255e6985e8d783365bc8a47599e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593026"
---
# <a name="connect-to-a-flat-file-ssas"></a><span data-ttu-id="fe745-102">連接到一般檔案 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="fe745-102">Connect to a Flat File (SSAS)</span></span>
  <span data-ttu-id="fe745-103">[資料表匯入精靈]\*\*\*\* 的這個頁面可讓您連接到一般檔案 (.txt)、Tab 分隔的檔案 (.tab) 或逗號分隔的檔案 (.csv)。</span><span class="sxs-lookup"><span data-stu-id="fe745-103">This page of the **Table Import Wizard** enables you to connect to a flat file (.txt), tab-separated file (.tab), or a comma-separated file (.csv).</span></span> <span data-ttu-id="fe745-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="fe745-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="fe745-105">若要連接至一般檔案，您必須先在電腦上安裝適當的 ACE 提供者。</span><span class="sxs-lookup"><span data-stu-id="fe745-105">To connect to a flat file, you must have the ACE provider installed on your computer.</span></span> <span data-ttu-id="fe745-106">如需詳細資訊，請參閱[支援的資料來源 &#40;SSAS 表格式&#41;](tabular-models/data-sources-supported-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="fe745-106">For more information, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe745-107">在這個頁面中選取檔案時，會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="fe745-107">The credentials of the current user are used when selecting a file in this page.</span></span> <span data-ttu-id="fe745-108">不過，如果在 [模擬資訊] 頁面中指定的使用者未具備從所選檔案讀取的權限，則匯入將不會成功。</span><span class="sxs-lookup"><span data-stu-id="fe745-108">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected file.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="fe745-109">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="fe745-109">UI element list</span></span>  
 <span data-ttu-id="fe745-110">**易記連接名稱**</span><span class="sxs-lookup"><span data-stu-id="fe745-110">**Friendly connection name**</span></span>  
 <span data-ttu-id="fe745-111">為此資料來源連接輸入唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="fe745-111">Type a unique name for this data source connection.</span></span> <span data-ttu-id="fe745-112">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="fe745-112">This is a required field.</span></span>  
  
 <span data-ttu-id="fe745-113">**檔案路徑**</span><span class="sxs-lookup"><span data-stu-id="fe745-113">**File Path**</span></span>  
 <span data-ttu-id="fe745-114">指定檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="fe745-114">Specify a full path for the file.</span></span>  
  
 <span data-ttu-id="fe745-115">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="fe745-115">**Browse**</span></span>  
 <span data-ttu-id="fe745-116">導覽至可以使用檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="fe745-116">Navigate to a location where a file is available.</span></span>  
  
 <span data-ttu-id="fe745-117">**資料行分隔符號**</span><span class="sxs-lookup"><span data-stu-id="fe745-117">**Column Separator**</span></span>  
 <span data-ttu-id="fe745-118">從可用資料行分隔符號的清單中選取。</span><span class="sxs-lookup"><span data-stu-id="fe745-118">Select from a list of available column separators.</span></span> <span data-ttu-id="fe745-119">請選擇不太可能會在文字中出現的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="fe745-119">Choose a separator that is not likely to occur in the text.</span></span>  
  
|<span data-ttu-id="fe745-120">值</span><span class="sxs-lookup"><span data-stu-id="fe745-120">Value</span></span>|<span data-ttu-id="fe745-121">描述</span><span class="sxs-lookup"><span data-stu-id="fe745-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fe745-122">定位字元 (t)</span><span class="sxs-lookup"><span data-stu-id="fe745-122">Tab (t)</span></span>|<span data-ttu-id="fe745-123">資料行是以定位字元 (t) 分隔。</span><span class="sxs-lookup"><span data-stu-id="fe745-123">Columns are separated by a tab (t).</span></span>|  
|<span data-ttu-id="fe745-124">逗號 (,)</span><span class="sxs-lookup"><span data-stu-id="fe745-124">Comma (,)</span></span>|<span data-ttu-id="fe745-125">資料行是以逗號 (,) 分隔。</span><span class="sxs-lookup"><span data-stu-id="fe745-125">Columns are separated by a comma (,).</span></span>|  
|<span data-ttu-id="fe745-126">分號 (;)</span><span class="sxs-lookup"><span data-stu-id="fe745-126">Semicolon (;)</span></span>|<span data-ttu-id="fe745-127">資料行是以分號 (;) 分隔。</span><span class="sxs-lookup"><span data-stu-id="fe745-127">Columns are separated by a semicolon (;).</span></span>|  
|<span data-ttu-id="fe745-128">空格 ( )</span><span class="sxs-lookup"><span data-stu-id="fe745-128">Space ( )</span></span>|<span data-ttu-id="fe745-129">資料行是以空格 ( ) 分隔。</span><span class="sxs-lookup"><span data-stu-id="fe745-129">Columns are separated by a space ( ).</span></span>|  
|<span data-ttu-id="fe745-130">冒號 (:)</span><span class="sxs-lookup"><span data-stu-id="fe745-130">Colon (:)</span></span>|<span data-ttu-id="fe745-131">資料行是以冒號 (:) 分隔。</span><span class="sxs-lookup"><span data-stu-id="fe745-131">Columns are separated by a colon (:).</span></span>|  
|<span data-ttu-id="fe745-132">分隔號 (&#124;)</span><span class="sxs-lookup"><span data-stu-id="fe745-132">Vertical Bar (&#124;)</span></span>|<span data-ttu-id="fe745-133">資料行是以分隔號 (&#124;) 分隔。</span><span class="sxs-lookup"><span data-stu-id="fe745-133">Columns are separated by a vertical bar (&#124;).</span></span>|  
  
 <span data-ttu-id="fe745-134">**進階**</span><span class="sxs-lookup"><span data-stu-id="fe745-134">**Advanced**</span></span>  
 <span data-ttu-id="fe745-135">指定一般檔案的編碼方式和地區設定選項。</span><span class="sxs-lookup"><span data-stu-id="fe745-135">Specify the encoding and locale options for the flat file.</span></span>  
  
 <span data-ttu-id="fe745-136">**使用第一個資料列做為資料行標頭**</span><span class="sxs-lookup"><span data-stu-id="fe745-136">**Use first row as column headers**</span></span>  
 <span data-ttu-id="fe745-137">指定是否要使用第一個資料列做為目的地資料表的資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="fe745-137">Specify whether to use the first data row as the column headers of the destination table.</span></span>  
  
 <span data-ttu-id="fe745-138">**資料預覽**</span><span class="sxs-lookup"><span data-stu-id="fe745-138">**Data preview**</span></span>  
 <span data-ttu-id="fe745-139">預覽所選檔案中的資料，然後使用下列選項修改資料匯入。</span><span class="sxs-lookup"><span data-stu-id="fe745-139">Preview the data in the selected file, and use the following options to modify the data import.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe745-140">只有檔案中的前 50 個資料列會顯示在這個預覽中。</span><span class="sxs-lookup"><span data-stu-id="fe745-140">Only the first 50 rows in the file are displayed in this preview.</span></span>  
  
|<span data-ttu-id="fe745-141">選項</span><span class="sxs-lookup"><span data-stu-id="fe745-141">Option</span></span>|<span data-ttu-id="fe745-142">描述</span><span class="sxs-lookup"><span data-stu-id="fe745-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="fe745-143">**資料行標頭中的核取方塊**</span><span class="sxs-lookup"><span data-stu-id="fe745-143">**Checkbox in the column header**</span></span>|<span data-ttu-id="fe745-144">選取核取方塊可將資料行納入資料匯入作業。</span><span class="sxs-lookup"><span data-stu-id="fe745-144">Select the checkbox to include the column in the data import.</span></span> <span data-ttu-id="fe745-145">清除核取方塊可從資料匯入作業排除資料行。</span><span class="sxs-lookup"><span data-stu-id="fe745-145">Clear the checkbox to remove the column from the data import.</span></span>|  
|<span data-ttu-id="fe745-146">**資料行標頭中的向下箭號按鈕**</span><span class="sxs-lookup"><span data-stu-id="fe745-146">**Down-arrow button in the column header**</span></span>|<span data-ttu-id="fe745-147">排序及篩選資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="fe745-147">Sort and filter data in the column.</span></span>|  
  
 <span data-ttu-id="fe745-148">**清除資料列篩選**</span><span class="sxs-lookup"><span data-stu-id="fe745-148">**Clear Row Filters**</span></span>  
 <span data-ttu-id="fe745-149">移除已經套用到資料行中資料的所有篩選。</span><span class="sxs-lookup"><span data-stu-id="fe745-149">Remove all filters that were applied to the data in the columns.</span></span>  
  
  
