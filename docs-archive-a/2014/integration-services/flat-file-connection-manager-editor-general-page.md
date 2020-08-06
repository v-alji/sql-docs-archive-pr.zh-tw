---
title: 一般檔案連線管理員編輯器 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.general.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 77296024-5c1a-4f6a-9665-0b50d45d744c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 478c7bcf56e300b47af93862bf66409a3c94b5f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592157"
---
# <a name="flat-file-connection-manager-editor-general-page"></a><span data-ttu-id="6a4f9-102">一般檔案連接管理員編輯器 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="6a4f9-102">Flat File Connection Manager Editor (General Page)</span></span>
  <span data-ttu-id="6a4f9-103">使用 **[一般檔案連接管理員編輯器]** 對話方塊的 **[一般]** 頁面，來選取檔案和資料格式。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-103">Use the **General** page of the **Flat File Connection Manager Editor** dialog box to select a file and data format.</span></span> <span data-ttu-id="6a4f9-104">一般檔案連接可以讓封裝連接到文字檔。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-104">A flat file connection enables a package to connect to a text file.</span></span>  
  
 <span data-ttu-id="6a4f9-105">若要深入了解一般檔案連接管理員，請參閱＜ [Flat File Connection Manager](connection-manager/file-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-105">To learn more about the Flat File connection manager, see [Flat File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="6a4f9-106">選項。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-106">Options</span></span>  
 <span data-ttu-id="6a4f9-107">**連線管理員名稱**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-107">**Connection manager name**</span></span>  
 <span data-ttu-id="6a4f9-108">提供唯一的名稱給工作流程中的一般檔案連接。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-108">Provide a unique name for the flat file connection in the workflow.</span></span> <span data-ttu-id="6a4f9-109">提供的名稱將顯示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師內。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-109">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="6a4f9-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-110">**Description**</span></span>  
 <span data-ttu-id="6a4f9-111">描述連接。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-111">Describe the connection.</span></span> <span data-ttu-id="6a4f9-112">最佳作法是以其用途描述連接，使封裝可以自我記錄並易於維護。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-112">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="6a4f9-113">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-113">**File name**</span></span>  
 <span data-ttu-id="6a4f9-114">輸入在一般檔案連接中要使用的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-114">Type the path and file name to use in the flat file connection.</span></span>  
  
 <span data-ttu-id="6a4f9-115">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-115">**Browse**</span></span>  
 <span data-ttu-id="6a4f9-116">尋找在一般檔案連接中要使用的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-116">Locate the file name to use in the flat file connection.</span></span>  
  
 <span data-ttu-id="6a4f9-117">**地區設定**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-117">**Locale**</span></span>  
 <span data-ttu-id="6a4f9-118">指定地區設定以提供排序以及日期和時間格式的特定語言資訊。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-118">Specify the locale to provide language-specific information for ordering and for date and time formats.</span></span>  
  
 <span data-ttu-id="6a4f9-119">**Unicode**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-119">**Unicode**</span></span>  
 <span data-ttu-id="6a4f9-120">指出是否使用 Unicode。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-120">Indicate whether to use Unicode.</span></span> <span data-ttu-id="6a4f9-121">如果使用 Unicode，您就無法指定字碼頁。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-121">If you use Unicode, you cannot specify a code page.</span></span>  
  
 <span data-ttu-id="6a4f9-122">**字碼頁**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-122">**Code page**</span></span>  
 <span data-ttu-id="6a4f9-123">指定非 Unicode 文字的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-123">Specify the code page for non-Unicode text.</span></span>  
  
 <span data-ttu-id="6a4f9-124">**格式**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-124">**Format**</span></span>  
 <span data-ttu-id="6a4f9-125">指出檔案是要使用分隔符號、固定寬度或不齊右的格式。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-125">Indicate whether the file uses delimited, fixed width, or ragged right formatting.</span></span>  
  
|<span data-ttu-id="6a4f9-126">值</span><span class="sxs-lookup"><span data-stu-id="6a4f9-126">Value</span></span>|<span data-ttu-id="6a4f9-127">描述</span><span class="sxs-lookup"><span data-stu-id="6a4f9-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6a4f9-128">Delimited (分隔檔)</span><span class="sxs-lookup"><span data-stu-id="6a4f9-128">Delimited</span></span>|<span data-ttu-id="6a4f9-129">資料行是以分隔符號隔開，分隔符號是在 **[資料行]** 頁面上指定的。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-129">Columns are separated by delimiters, specified on the **Columns** page.</span></span>|  
|<span data-ttu-id="6a4f9-130">固定寬度</span><span class="sxs-lookup"><span data-stu-id="6a4f9-130">Fixed width</span></span>|<span data-ttu-id="6a4f9-131">資料行具有固定寬度。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-131">Columns have a fixed width.</span></span>|  
|<span data-ttu-id="6a4f9-132">不齊右</span><span class="sxs-lookup"><span data-stu-id="6a4f9-132">Ragged right</span></span>|<span data-ttu-id="6a4f9-133">不齊右檔案就是除了最後一個資料行之外，其他所有資料行都有固定寬度的檔案。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-133">Ragged right files are files in which every column has a fixed width, except for the last column.</span></span> <span data-ttu-id="6a4f9-134">它是以資料列分隔符號分隔。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-134">It is delimited by the row delimiter.</span></span>|  
  
 <span data-ttu-id="6a4f9-135">**文字定位項**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-135">**Text qualifier**</span></span>  
 <span data-ttu-id="6a4f9-136">指定要使用的文字限定詞。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-136">Specify the text qualifier to use.</span></span> <span data-ttu-id="6a4f9-137">例如，您可以指定文字欄位加上引號。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-137">For example, you can specify that text fields are enclosed in quotation marks.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6a4f9-138">選取文字限定詞之後，就無法重新選取 [無]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-138">After you select a text qualifier, you cannot re-select the **None** option.</span></span> <span data-ttu-id="6a4f9-139">輸入 **None** 即可取消選取文字限定詞。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-139">Type **None** to de-select the text qualifier.</span></span>  
  
 <span data-ttu-id="6a4f9-140">**標頭資料列分隔符號**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-140">**Header row delimiter**</span></span>  
 <span data-ttu-id="6a4f9-141">從標頭資料列的分隔符號清單中選取，或輸入分隔符號文字。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-141">Select from the list of delimiters for header rows, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="6a4f9-142">值</span><span class="sxs-lookup"><span data-stu-id="6a4f9-142">Value</span></span>|<span data-ttu-id="6a4f9-143">描述</span><span class="sxs-lookup"><span data-stu-id="6a4f9-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6a4f9-144">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-144">**{CR}{LF}**</span></span>|<span data-ttu-id="6a4f9-145">標頭資料列是以歸位字元和換行字元的組合分隔。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-145">The header row is delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="6a4f9-146">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-146">**{CR}**</span></span>|<span data-ttu-id="6a4f9-147">標頭資料列是以歸位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-147">The header row is delimited by a carriage return.</span></span>|  
|<span data-ttu-id="6a4f9-148">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-148">**{LF}**</span></span>|<span data-ttu-id="6a4f9-149">標頭資料列是以換行字元分隔。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-149">The header row is delimited by a line feed.</span></span>|  
|<span data-ttu-id="6a4f9-150">**分號 {;}**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-150">**Semicolon {;}**</span></span>|<span data-ttu-id="6a4f9-151">標頭資料列是以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-151">The header row is delimited by a semicolon.</span></span>|  
|<span data-ttu-id="6a4f9-152">**冒號 {:}**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-152">**Colon {:}**</span></span>|<span data-ttu-id="6a4f9-153">標頭資料列是以冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-153">The header row is delimited by a colon.</span></span>|  
|<span data-ttu-id="6a4f9-154">**逗號 {,}**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-154">**Comma {,}**</span></span>|<span data-ttu-id="6a4f9-155">標頭資料列是以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-155">The header row is delimited by a comma.</span></span>|  
|<span data-ttu-id="6a4f9-156">**定位字元 {t}**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-156">**Tab {t}**</span></span>|<span data-ttu-id="6a4f9-157">標頭資料列是以定位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-157">The header row is delimited by a tab.</span></span>|  
|<span data-ttu-id="6a4f9-158">**分隔號 {&#124;}**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-158">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="6a4f9-159">標頭資料列是以分隔號 (&#124;) 分隔。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-159">The header row is delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="6a4f9-160">**略過的標頭資料列數**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-160">**Header rows to skip**</span></span>  
 <span data-ttu-id="6a4f9-161">指定要略過的標頭資料列數或初始資料列數 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-161">Specify the number of header rows or initial data rows to skip, if any.</span></span>  
  
 <span data-ttu-id="6a4f9-162">**第一個資料列的資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="6a4f9-162">**Column names in the first data row**</span></span>  
 <span data-ttu-id="6a4f9-163">指出在第一個資料列中，是否為資料行名稱或需要提供資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="6a4f9-163">Indicate whether to expect or provide column names in the first data row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a4f9-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a4f9-164">See Also</span></span>  
 <span data-ttu-id="6a4f9-165">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="6a4f9-165">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="6a4f9-166">[一般檔案連接管理員編輯器 &#40;資料行] 頁面&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="6a4f9-166">[Flat File Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md) </span></span>  
 <span data-ttu-id="6a4f9-167">[一般檔案連線管理員編輯器 &#40;Advanced Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="6a4f9-167">[Flat File Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="6a4f9-168">一般檔案連線管理員編輯器 &#40;預覽頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="6a4f9-168">Flat File Connection Manager Editor &#40;Preview Page&#41;</span></span>](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)  
  
  
