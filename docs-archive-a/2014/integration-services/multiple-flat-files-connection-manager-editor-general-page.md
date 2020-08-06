---
title: 多個一般檔案連線管理員編輯器 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multifile.general.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: 00129d43-2772-413b-bdf8-ac5de81cf4a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f30a422794723f216d30e05f0750fb1e974e0920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705261"
---
# <a name="multiple-flat-files-connection-manager-editor-general-page"></a><span data-ttu-id="8af17-102">多個一般檔案連線管理員編輯器 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="8af17-102">Multiple Flat Files Connection Manager Editor (General Page)</span></span>
  <span data-ttu-id="8af17-103">使用 **[多個一般檔案連線管理員編輯器]** 對話方塊的 **[一般]** 頁面，即可選取一組具有相同資料格式的檔案，並指定其資料格式。</span><span class="sxs-lookup"><span data-stu-id="8af17-103">Use the **General** page of the **Multiple Flat Files Connection Manager Editor** dialog box to select a group of files that have the same data format, and to specify their data format.</span></span> <span data-ttu-id="8af17-104">多個一般檔案連接，可以讓封裝連接到一組具有相同格式的文字檔。</span><span class="sxs-lookup"><span data-stu-id="8af17-104">A multiple flat files connection enables a package to connect to a group of text files that have the same format.</span></span>  
  
 <span data-ttu-id="8af17-105">若要深入了解多個一般檔案連接管理員，請參閱＜ [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8af17-105">To learn more about the Multiple Flat Files connection manager, see [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8af17-106">選項。</span><span class="sxs-lookup"><span data-stu-id="8af17-106">Options</span></span>  
 <span data-ttu-id="8af17-107">**連線管理員名稱**</span><span class="sxs-lookup"><span data-stu-id="8af17-107">**Connection manager name**</span></span>  
 <span data-ttu-id="8af17-108">提供唯一的名稱給工作流程中的多個一般檔案連接。</span><span class="sxs-lookup"><span data-stu-id="8af17-108">Provide a unique name for the Multiple Flat Files connection in the workflow.</span></span> <span data-ttu-id="8af17-109">提供的名稱將顯示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師內。</span><span class="sxs-lookup"><span data-stu-id="8af17-109">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="8af17-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="8af17-110">**Description**</span></span>  
 <span data-ttu-id="8af17-111">描述連接。</span><span class="sxs-lookup"><span data-stu-id="8af17-111">Describe the connection.</span></span> <span data-ttu-id="8af17-112">最佳作法是以其用途描述連接，使封裝可以自我記錄並易於維護。</span><span class="sxs-lookup"><span data-stu-id="8af17-112">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="8af17-113">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="8af17-113">**File names**</span></span>  
 <span data-ttu-id="8af17-114">輸入路徑和檔案名稱，以便於多個一般檔案連接中使用。</span><span class="sxs-lookup"><span data-stu-id="8af17-114">Type the path and file names to use in the Multiple Flat Files connection.</span></span> <span data-ttu-id="8af17-115">您可以使用萬用字元來指定多個檔案，例如 "C:\\*.txt"，或者使用分隔號 (|) 來分隔多個檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="8af17-115">You can specify multiple files by using wildcard characters, as in the example "C:\\*.txt", or by using the vertical pipe character (|) to separate multiple file names.</span></span> <span data-ttu-id="8af17-116">所有檔案必須有相同的資料格式。</span><span class="sxs-lookup"><span data-stu-id="8af17-116">All files must have the same data format.</span></span>  
  
 <span data-ttu-id="8af17-117">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="8af17-117">**Browse**</span></span>  
 <span data-ttu-id="8af17-118">瀏覽檔案名稱，以便於多個一般檔案連接中使用。</span><span class="sxs-lookup"><span data-stu-id="8af17-118">Browse the file names to use in the Multiple Flat Files connection.</span></span> <span data-ttu-id="8af17-119">您可以選取多個檔案。</span><span class="sxs-lookup"><span data-stu-id="8af17-119">You can select multiple files.</span></span> <span data-ttu-id="8af17-120">所有檔案必須有相同的資料格式。</span><span class="sxs-lookup"><span data-stu-id="8af17-120">All files must have the same data format.</span></span>  
  
 <span data-ttu-id="8af17-121">**地區設定**</span><span class="sxs-lookup"><span data-stu-id="8af17-121">**Locale**</span></span>  
 <span data-ttu-id="8af17-122">指定地區，以提供排序以及時間和日期的轉換資訊。</span><span class="sxs-lookup"><span data-stu-id="8af17-122">Specify the location to provide information for ordering and for date and time conversion.</span></span>  
  
 <span data-ttu-id="8af17-123">**Unicode**</span><span class="sxs-lookup"><span data-stu-id="8af17-123">**Unicode**</span></span>  
 <span data-ttu-id="8af17-124">指出是否使用 Unicode。</span><span class="sxs-lookup"><span data-stu-id="8af17-124">Indicate whether to use Unicode.</span></span> <span data-ttu-id="8af17-125">使用 Unicode 即無需指定字碼頁。</span><span class="sxs-lookup"><span data-stu-id="8af17-125">Using Unicode precludes specifying a code page.</span></span>  
  
 <span data-ttu-id="8af17-126">**字碼頁**</span><span class="sxs-lookup"><span data-stu-id="8af17-126">**Code page**</span></span>  
 <span data-ttu-id="8af17-127">指定非 Unicode 文字的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="8af17-127">Specify the code page for non-Unicode text.</span></span>  
  
 <span data-ttu-id="8af17-128">**格式**</span><span class="sxs-lookup"><span data-stu-id="8af17-128">**Format**</span></span>  
 <span data-ttu-id="8af17-129">指出是要使用分隔符號、固定寬度或不齊右的格式。</span><span class="sxs-lookup"><span data-stu-id="8af17-129">Indicate whether to use delimited, fixed width, or ragged right formatting.</span></span> <span data-ttu-id="8af17-130">所有檔案必須有相同的資料格式。</span><span class="sxs-lookup"><span data-stu-id="8af17-130">All files must have the same data format.</span></span>  
  
|<span data-ttu-id="8af17-131">值</span><span class="sxs-lookup"><span data-stu-id="8af17-131">Value</span></span>|<span data-ttu-id="8af17-132">描述</span><span class="sxs-lookup"><span data-stu-id="8af17-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8af17-133">Delimited (分隔檔)</span><span class="sxs-lookup"><span data-stu-id="8af17-133">Delimited</span></span>|<span data-ttu-id="8af17-134">資料行是以分隔符號隔開，分隔符號是在 **[資料行]** 頁面上指定的。</span><span class="sxs-lookup"><span data-stu-id="8af17-134">Columns are separated by delimiters, specified on the **Columns** page.</span></span>|  
|<span data-ttu-id="8af17-135">固定寬度</span><span class="sxs-lookup"><span data-stu-id="8af17-135">Fixed width</span></span>|<span data-ttu-id="8af17-136">資料行具有固定寬度，由 **[資料行]** 頁面上的拖曳標記線所指定。</span><span class="sxs-lookup"><span data-stu-id="8af17-136">Columns have a fixed width, specified by dragging marker lines on the **Columns** page.</span></span>|  
|<span data-ttu-id="8af17-137">不齊右</span><span class="sxs-lookup"><span data-stu-id="8af17-137">Ragged right</span></span>|<span data-ttu-id="8af17-138">不齊右檔案就是除了最後一個資料行是由資料列分隔符號所分隔之外，其他所有資料行都有在 **[資料行]** 頁面上所指定之固定寬度的檔案。</span><span class="sxs-lookup"><span data-stu-id="8af17-138">Ragged right files are files in which every column has a fixed width, except for the last column, which is delimited by the row delimiter, specified on the **Columns** page.</span></span>|  
  
 <span data-ttu-id="8af17-139">**文字定位項**</span><span class="sxs-lookup"><span data-stu-id="8af17-139">**Text qualifier**</span></span>  
 <span data-ttu-id="8af17-140">指定要使用的文字限定詞。</span><span class="sxs-lookup"><span data-stu-id="8af17-140">Specify the text qualifier to use.</span></span> <span data-ttu-id="8af17-141">例如，您可以指定文字必須加上引號。</span><span class="sxs-lookup"><span data-stu-id="8af17-141">For example, you can specify to enclose text with quotation marks.</span></span>  
  
 <span data-ttu-id="8af17-142">**標頭資料列分隔符號**</span><span class="sxs-lookup"><span data-stu-id="8af17-142">**Header row delimiter**</span></span>  
 <span data-ttu-id="8af17-143">從標頭資料列的分隔符號清單中選取，或輸入分隔符號文字。</span><span class="sxs-lookup"><span data-stu-id="8af17-143">Select from the list of delimiters for header rows, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="8af17-144">值</span><span class="sxs-lookup"><span data-stu-id="8af17-144">Value</span></span>|<span data-ttu-id="8af17-145">描述</span><span class="sxs-lookup"><span data-stu-id="8af17-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8af17-146">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="8af17-146">**{CR}{LF}**</span></span>|<span data-ttu-id="8af17-147">標頭資料列是以歸位字元和換行字元的組合分隔。</span><span class="sxs-lookup"><span data-stu-id="8af17-147">The header row is delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="8af17-148">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="8af17-148">**{CR}**</span></span>|<span data-ttu-id="8af17-149">標頭資料列是以歸位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="8af17-149">The header row is delimited by a carriage return.</span></span>|  
|<span data-ttu-id="8af17-150">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="8af17-150">**{LF}**</span></span>|<span data-ttu-id="8af17-151">標頭資料列是以換行字元分隔。</span><span class="sxs-lookup"><span data-stu-id="8af17-151">The header row is delimited by a line feed.</span></span>|  
|<span data-ttu-id="8af17-152">**分號 {;}**</span><span class="sxs-lookup"><span data-stu-id="8af17-152">**Semicolon {;}**</span></span>|<span data-ttu-id="8af17-153">標頭資料列是以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="8af17-153">The header row is delimited by a semicolon.</span></span>|  
|<span data-ttu-id="8af17-154">**冒號 {:}**</span><span class="sxs-lookup"><span data-stu-id="8af17-154">**Colon {:}**</span></span>|<span data-ttu-id="8af17-155">標頭資料列是以冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="8af17-155">The header row is delimited by a colon.</span></span>|  
|<span data-ttu-id="8af17-156">**逗號 {,}**</span><span class="sxs-lookup"><span data-stu-id="8af17-156">**Comma {,}**</span></span>|<span data-ttu-id="8af17-157">標頭資料列是以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="8af17-157">The header row is delimited by a comma.</span></span>|  
|<span data-ttu-id="8af17-158">**定位字元 {t}**</span><span class="sxs-lookup"><span data-stu-id="8af17-158">**Tab {t}**</span></span>|<span data-ttu-id="8af17-159">標頭資料列是以定位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="8af17-159">The header row is delimited by a tab.</span></span>|  
|<span data-ttu-id="8af17-160">**分隔號 {&#124;}**</span><span class="sxs-lookup"><span data-stu-id="8af17-160">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="8af17-161">標頭資料列是以分隔號 (&#124;) 分隔。</span><span class="sxs-lookup"><span data-stu-id="8af17-161">The header row is delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="8af17-162">**略過的標頭資料列數**</span><span class="sxs-lookup"><span data-stu-id="8af17-162">**Header rows to skip**</span></span>  
 <span data-ttu-id="8af17-163">指定要略過的標頭列數 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="8af17-163">Specify the number of header rows to skip, if any.</span></span>  
  
 <span data-ttu-id="8af17-164">**第一個資料列的資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="8af17-164">**Column names in the first data row**</span></span>  
 <span data-ttu-id="8af17-165">指出在第一個資料列中，是否為資料行名稱或需要提供資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="8af17-165">Indicate whether to expect or provide column names in the first data row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8af17-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8af17-166">See Also</span></span>  
 <span data-ttu-id="8af17-167">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8af17-167">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="8af17-168">[多個一般檔案連線管理員編輯器 &#40;資料行頁面&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="8af17-168">[Multiple Flat Files Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md) </span></span>  
 <span data-ttu-id="8af17-169">[多個一般檔案連線管理員編輯器 &#40;Advanced Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="8af17-169">[Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="8af17-170">多個一般檔案連線管理員編輯器 &#40;預覽頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="8af17-170">Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;</span></span>](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)  
  
  
