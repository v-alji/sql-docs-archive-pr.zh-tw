---
title: 一般檔案連線管理員編輯器 (資料行頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.columns.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 40ce7537-abd0-4973-97fd-6ccb90fddfa0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f6ce579f73922d2eaa2c48e98a98f52cd5836f5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592155"
---
# <a name="flat-file-connection-manager-editor-columns-page"></a><span data-ttu-id="6987a-102">一般檔案連接管理員編輯器 (資料行頁面)</span><span class="sxs-lookup"><span data-stu-id="6987a-102">Flat File Connection Manager Editor (Columns Page)</span></span>
  <span data-ttu-id="6987a-103">使用 **[一般檔案連接管理員編輯器]** 對話方塊的 **[資料行]** 頁面來指定資料列和資料行資訊，以及預覽檔案。</span><span class="sxs-lookup"><span data-stu-id="6987a-103">Use the **Columns** page of the **Flat File Connection Manager Editor** dialog box to specify the row and column information, and to preview the file.</span></span>  
  
 <span data-ttu-id="6987a-104">若要深入了解一般檔案連接管理員，請參閱＜ [Flat File Connection Manager](connection-manager/file-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="6987a-104">To learn more about the Flat File connection manager, see [Flat File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="6987a-105">靜態選項</span><span class="sxs-lookup"><span data-stu-id="6987a-105">Static Options</span></span>  
 <span data-ttu-id="6987a-106">**連線管理員名稱**</span><span class="sxs-lookup"><span data-stu-id="6987a-106">**Connection manager name**</span></span>  
 <span data-ttu-id="6987a-107">提供唯一的名稱給工作流程中的一般檔案連接。</span><span class="sxs-lookup"><span data-stu-id="6987a-107">Provide a unique name for the Flat File connection in the workflow.</span></span> <span data-ttu-id="6987a-108">提供的名稱將顯示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師內。</span><span class="sxs-lookup"><span data-stu-id="6987a-108">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="6987a-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="6987a-109">**Description**</span></span>  
 <span data-ttu-id="6987a-110">描述連接。</span><span class="sxs-lookup"><span data-stu-id="6987a-110">Describe the connection.</span></span> <span data-ttu-id="6987a-111">最佳作法是以其用途描述連接，使封裝可以自我記錄並易於維護。</span><span class="sxs-lookup"><span data-stu-id="6987a-111">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
## <a name="flat-file-format-dynamic-options"></a><span data-ttu-id="6987a-112">一般檔案格式動態選項</span><span class="sxs-lookup"><span data-stu-id="6987a-112">Flat File Format Dynamic Options</span></span>  
  
### <a name="format--delimited"></a><span data-ttu-id="6987a-113">格式 = 使用分隔符號</span><span class="sxs-lookup"><span data-stu-id="6987a-113">Format = Delimited</span></span>  
 <span data-ttu-id="6987a-114">**資料列分隔符號**</span><span class="sxs-lookup"><span data-stu-id="6987a-114">**Row delimiter**</span></span>  
 <span data-ttu-id="6987a-115">從可用的資料列分隔符號清單中選取，或輸入分隔符號文字。</span><span class="sxs-lookup"><span data-stu-id="6987a-115">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="6987a-116">值</span><span class="sxs-lookup"><span data-stu-id="6987a-116">Value</span></span>|<span data-ttu-id="6987a-117">描述</span><span class="sxs-lookup"><span data-stu-id="6987a-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6987a-118">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="6987a-118">**{CR}{LF}**</span></span>|<span data-ttu-id="6987a-119">資料列是以歸位字元和換行字元的組合分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-119">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="6987a-120">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="6987a-120">**{CR}**</span></span>|<span data-ttu-id="6987a-121">資料列是以歸位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-121">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="6987a-122">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="6987a-122">**{LF}**</span></span>|<span data-ttu-id="6987a-123">資料列是以換行字元分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-123">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="6987a-124">**分號 {;}**</span><span class="sxs-lookup"><span data-stu-id="6987a-124">**Semicolon {;}**</span></span>|<span data-ttu-id="6987a-125">資料列是以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-125">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="6987a-126">**冒號 {:}**</span><span class="sxs-lookup"><span data-stu-id="6987a-126">**Colon {:}**</span></span>|<span data-ttu-id="6987a-127">資料列是以冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-127">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="6987a-128">**逗號 {,}**</span><span class="sxs-lookup"><span data-stu-id="6987a-128">**Comma {,}**</span></span>|<span data-ttu-id="6987a-129">資料列是以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-129">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="6987a-130">**定位字元 {t}**</span><span class="sxs-lookup"><span data-stu-id="6987a-130">**Tab {t}**</span></span>|<span data-ttu-id="6987a-131">資料列是以定位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-131">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="6987a-132">**分隔號 {&#124;}**</span><span class="sxs-lookup"><span data-stu-id="6987a-132">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="6987a-133">資料列是以分隔號分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-133">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="6987a-134">**資料行分隔符號**</span><span class="sxs-lookup"><span data-stu-id="6987a-134">**Column delimiter**</span></span>  
 <span data-ttu-id="6987a-135">從可用的資料行分隔符號清單中選取，或輸入分隔符號文字。</span><span class="sxs-lookup"><span data-stu-id="6987a-135">Select from the list of available column delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="6987a-136">值</span><span class="sxs-lookup"><span data-stu-id="6987a-136">Value</span></span>|<span data-ttu-id="6987a-137">描述</span><span class="sxs-lookup"><span data-stu-id="6987a-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6987a-138">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="6987a-138">**{CR}{LF}**</span></span>|<span data-ttu-id="6987a-139">資料行是以歸位字元和換行字元的組合分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-139">Columns are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="6987a-140">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="6987a-140">**{CR}**</span></span>|<span data-ttu-id="6987a-141">資料行是以歸位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-141">Columns are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="6987a-142">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="6987a-142">**{LF}**</span></span>|<span data-ttu-id="6987a-143">資料行是以換行字元分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-143">Columns are delimited by a line feed.</span></span>|  
|<span data-ttu-id="6987a-144">**分號 {;}**</span><span class="sxs-lookup"><span data-stu-id="6987a-144">**Semicolon {;}**</span></span>|<span data-ttu-id="6987a-145">資料行是以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-145">Columns are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="6987a-146">**冒號 {:}**</span><span class="sxs-lookup"><span data-stu-id="6987a-146">**Colon {:}**</span></span>|<span data-ttu-id="6987a-147">資料行是以冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-147">Columns are delimited by a colon.</span></span>|  
|<span data-ttu-id="6987a-148">**逗號 {,}**</span><span class="sxs-lookup"><span data-stu-id="6987a-148">**Comma {,}**</span></span>|<span data-ttu-id="6987a-149">資料行是以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-149">Columns are delimited by a comma.</span></span>|  
|<span data-ttu-id="6987a-150">**定位字元 {t}**</span><span class="sxs-lookup"><span data-stu-id="6987a-150">**Tab {t}**</span></span>|<span data-ttu-id="6987a-151">資料行是以定位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-151">Columns are delimited by a tab.</span></span>|  
|<span data-ttu-id="6987a-152">**分隔號 {&#124;}**</span><span class="sxs-lookup"><span data-stu-id="6987a-152">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="6987a-153">資料行是以分隔號分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-153">Columns are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="6987a-154">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="6987a-154">**Refresh**</span></span>  
 <span data-ttu-id="6987a-155">按一下 [重新整理]\*\*\*\*，即可檢視變更要略過之分隔符號的影響。</span><span class="sxs-lookup"><span data-stu-id="6987a-155">View the effect of changing the delimiters to skip by clicking **Refresh**.</span></span> <span data-ttu-id="6987a-156">僅在您已變更其他連接選項之後，才會看見此按鈕。</span><span class="sxs-lookup"><span data-stu-id="6987a-156">This button only becomes visible after you have changed other connection options.</span></span>  
  
 <span data-ttu-id="6987a-157">**預覽資料列**</span><span class="sxs-lookup"><span data-stu-id="6987a-157">**Preview rows**</span></span>  
 <span data-ttu-id="6987a-158">檢視一般檔案中的範例資料，使用選取的選項將資料分為資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="6987a-158">View sample data in the flat file, divided into columns and rows by using the options selected.</span></span>  
  
 <span data-ttu-id="6987a-159">**重設資料行**</span><span class="sxs-lookup"><span data-stu-id="6987a-159">**Reset Columns**</span></span>  
 <span data-ttu-id="6987a-160">按一下 [重設資料行]，即可將原始資料行以外的資料行全部移除。</span><span class="sxs-lookup"><span data-stu-id="6987a-160">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--fixed-width"></a><span data-ttu-id="6987a-161">格式 = 固定寬度</span><span class="sxs-lookup"><span data-stu-id="6987a-161">Format = Fixed Width</span></span>  
 <span data-ttu-id="6987a-162">**字型**</span><span class="sxs-lookup"><span data-stu-id="6987a-162">**Font**</span></span>  
 <span data-ttu-id="6987a-163">選取要顯示預覽資料的字型。</span><span class="sxs-lookup"><span data-stu-id="6987a-163">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="6987a-164">**來源資料行**</span><span class="sxs-lookup"><span data-stu-id="6987a-164">**Source data columns**</span></span>  
 <span data-ttu-id="6987a-165">滑動垂直紅色資料列標記，即可調整資料列的寬度；而按一下預覽視窗上方的尺規，即可調整資料行的寬度</span><span class="sxs-lookup"><span data-stu-id="6987a-165">Adjust the width of the row by sliding the vertical red row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="6987a-166">**資料列寬度**</span><span class="sxs-lookup"><span data-stu-id="6987a-166">**Row width**</span></span>  
 <span data-ttu-id="6987a-167">為個別資料行加入分隔符號之前，請先指定資料列的長度。</span><span class="sxs-lookup"><span data-stu-id="6987a-167">Specify the length of the row before adding delimiters for individual columns.</span></span> <span data-ttu-id="6987a-168">或者，在預覽視窗中拖曳垂直紅線來標示資料列結尾。</span><span class="sxs-lookup"><span data-stu-id="6987a-168">Or, drag the vertical red line in the preview window to mark the end of the row.</span></span> <span data-ttu-id="6987a-169">資料列寬度值會自動更新。</span><span class="sxs-lookup"><span data-stu-id="6987a-169">The row width value is automatically updated.</span></span>  
  
 <span data-ttu-id="6987a-170">**重設資料行**</span><span class="sxs-lookup"><span data-stu-id="6987a-170">**Reset Columns**</span></span>  
 <span data-ttu-id="6987a-171">按一下 [重設資料行]，即可將原始資料行以外的資料行全部移除。</span><span class="sxs-lookup"><span data-stu-id="6987a-171">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--ragged-right"></a><span data-ttu-id="6987a-172">格式 = 不齊右</span><span class="sxs-lookup"><span data-stu-id="6987a-172">Format = Ragged Right</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6987a-173">不齊右檔案就是除了最後一個資料行之外，其他所有資料行都有固定寬度的檔案。</span><span class="sxs-lookup"><span data-stu-id="6987a-173">Ragged right files are files in which every column has a fixed width, except for the last column.</span></span> <span data-ttu-id="6987a-174">它是以資料列分隔符號分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-174">It is delimited by the row delimiter.</span></span>  
  
 <span data-ttu-id="6987a-175">**字型**</span><span class="sxs-lookup"><span data-stu-id="6987a-175">**Font**</span></span>  
 <span data-ttu-id="6987a-176">選取要顯示預覽資料的字型。</span><span class="sxs-lookup"><span data-stu-id="6987a-176">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="6987a-177">**來源資料行**</span><span class="sxs-lookup"><span data-stu-id="6987a-177">**Source data columns**</span></span>  
 <span data-ttu-id="6987a-178">滑動垂直紅色資料列標記，即可調整資料列的寬度；而按一下預覽視窗上方的尺規，即可調整資料行的寬度</span><span class="sxs-lookup"><span data-stu-id="6987a-178">Adjust the width of the row by sliding the vertical red row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="6987a-179">**資料列分隔符號**</span><span class="sxs-lookup"><span data-stu-id="6987a-179">**Row delimiter**</span></span>  
 <span data-ttu-id="6987a-180">從可用的資料列分隔符號清單中選取，或輸入分隔符號文字。</span><span class="sxs-lookup"><span data-stu-id="6987a-180">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="6987a-181">值</span><span class="sxs-lookup"><span data-stu-id="6987a-181">Value</span></span>|<span data-ttu-id="6987a-182">描述</span><span class="sxs-lookup"><span data-stu-id="6987a-182">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6987a-183">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="6987a-183">**{CR}{LF}**</span></span>|<span data-ttu-id="6987a-184">資料列是以歸位字元和換行字元的組合分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-184">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="6987a-185">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="6987a-185">**{CR}**</span></span>|<span data-ttu-id="6987a-186">資料列是以歸位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-186">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="6987a-187">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="6987a-187">**{LF}**</span></span>|<span data-ttu-id="6987a-188">資料列是以換行字元分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-188">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="6987a-189">**分號 {;}**</span><span class="sxs-lookup"><span data-stu-id="6987a-189">**Semicolon {;}**</span></span>|<span data-ttu-id="6987a-190">資料列是以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-190">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="6987a-191">**冒號 {:}**</span><span class="sxs-lookup"><span data-stu-id="6987a-191">**Colon {:}**</span></span>|<span data-ttu-id="6987a-192">資料列是以冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-192">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="6987a-193">**逗號 {,}**</span><span class="sxs-lookup"><span data-stu-id="6987a-193">**Comma {,}**</span></span>|<span data-ttu-id="6987a-194">資料列是以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-194">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="6987a-195">**定位字元 {t}**</span><span class="sxs-lookup"><span data-stu-id="6987a-195">**Tab {t}**</span></span>|<span data-ttu-id="6987a-196">資料列是以定位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-196">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="6987a-197">**分隔號 {&#124;}**</span><span class="sxs-lookup"><span data-stu-id="6987a-197">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="6987a-198">資料列是以分隔號分隔。</span><span class="sxs-lookup"><span data-stu-id="6987a-198">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="6987a-199">**重設資料行**</span><span class="sxs-lookup"><span data-stu-id="6987a-199">**Reset Columns**</span></span>  
 <span data-ttu-id="6987a-200">按一下 [重設資料行]，即可將原始資料行以外的資料行全部移除。</span><span class="sxs-lookup"><span data-stu-id="6987a-200">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6987a-201">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6987a-201">See Also</span></span>  
 <span data-ttu-id="6987a-202">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="6987a-202">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="6987a-203">[一般檔案連線管理員編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="6987a-203">[Flat File Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="6987a-204">[一般檔案連線管理員編輯器 &#40;Advanced Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="6987a-204">[Flat File Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="6987a-205">一般檔案連線管理員編輯器 &#40;預覽頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="6987a-205">Flat File Connection Manager Editor &#40;Preview Page&#41;</span></span>](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)  
  
  
