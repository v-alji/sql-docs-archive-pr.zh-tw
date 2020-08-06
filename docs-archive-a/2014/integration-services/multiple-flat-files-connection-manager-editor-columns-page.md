---
title: 多個一般檔案連線管理員編輯器 (資料行頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multifile.columns.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: ad0cb668-0df2-4d4e-9a20-d20692a0b67a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a7f4936f0722754b414076820eda7dcf2dc8dc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592097"
---
# <a name="multiple-flat-files-connection-manager-editor-columns-page"></a><span data-ttu-id="50dab-102">多個一般檔案連接管理員編輯器 (資料行頁面)</span><span class="sxs-lookup"><span data-stu-id="50dab-102">Multiple Flat Files Connection Manager Editor (Columns Page)</span></span>
  <span data-ttu-id="50dab-103">使用 **[多個一般檔案連接管理員編輯器]** 對話方塊的 **[資料行]** 節點，來指定資料列與資料行資訊以及預覽第一個選取的檔案。</span><span class="sxs-lookup"><span data-stu-id="50dab-103">Use the **Columns** node of the **Multiple Flat Files Connection Manager Editor** dialog box to specify the row and column information, and to preview the first selected file.</span></span>  
  
 <span data-ttu-id="50dab-104">若要深入了解多個一般檔案連接管理員，請參閱＜ [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="50dab-104">To learn more about the Multiple Flat Files connection manager, see [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="50dab-105">靜態選項</span><span class="sxs-lookup"><span data-stu-id="50dab-105">Static Options</span></span>  
 <span data-ttu-id="50dab-106">**連線管理員名稱**</span><span class="sxs-lookup"><span data-stu-id="50dab-106">**Connection manager name**</span></span>  
 <span data-ttu-id="50dab-107">提供唯一的名稱給工作流程中的多個一般檔案連接。</span><span class="sxs-lookup"><span data-stu-id="50dab-107">Provide a unique name for the Multiple Flat Files connection in the workflow.</span></span> <span data-ttu-id="50dab-108">提供的名稱將顯示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師內。</span><span class="sxs-lookup"><span data-stu-id="50dab-108">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="50dab-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="50dab-109">**Description**</span></span>  
 <span data-ttu-id="50dab-110">描述連接。</span><span class="sxs-lookup"><span data-stu-id="50dab-110">Describe the connection.</span></span> <span data-ttu-id="50dab-111">最佳作法是以其用途描述連接，使封裝可以自我記錄並易於維護。</span><span class="sxs-lookup"><span data-stu-id="50dab-111">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
## <a name="flat-file-format-dynamic-options"></a><span data-ttu-id="50dab-112">一般檔案格式動態選項</span><span class="sxs-lookup"><span data-stu-id="50dab-112">Flat File Format Dynamic Options</span></span>  
  
### <a name="format--delimited"></a><span data-ttu-id="50dab-113">格式 = 使用分隔符號</span><span class="sxs-lookup"><span data-stu-id="50dab-113">Format = Delimited</span></span>  
 <span data-ttu-id="50dab-114">**資料列分隔符號**</span><span class="sxs-lookup"><span data-stu-id="50dab-114">**Row delimiter**</span></span>  
 <span data-ttu-id="50dab-115">從可用的資料列分隔符號清單中選取，或輸入分隔符號文字。</span><span class="sxs-lookup"><span data-stu-id="50dab-115">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="50dab-116">值</span><span class="sxs-lookup"><span data-stu-id="50dab-116">Value</span></span>|<span data-ttu-id="50dab-117">描述</span><span class="sxs-lookup"><span data-stu-id="50dab-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="50dab-118">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="50dab-118">**{CR}{LF}**</span></span>|<span data-ttu-id="50dab-119">資料列是以歸位字元和換行字元的組合分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-119">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="50dab-120">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="50dab-120">**{CR}**</span></span>|<span data-ttu-id="50dab-121">資料列是以歸位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-121">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="50dab-122">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="50dab-122">**{LF}**</span></span>|<span data-ttu-id="50dab-123">資料列是以換行字元分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-123">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="50dab-124">**分號 {;}**</span><span class="sxs-lookup"><span data-stu-id="50dab-124">**Semicolon {;}**</span></span>|<span data-ttu-id="50dab-125">資料列是以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-125">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="50dab-126">**冒號 {:}**</span><span class="sxs-lookup"><span data-stu-id="50dab-126">**Colon {:}**</span></span>|<span data-ttu-id="50dab-127">資料列是以冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-127">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="50dab-128">**逗號 {,}**</span><span class="sxs-lookup"><span data-stu-id="50dab-128">**Comma {,}**</span></span>|<span data-ttu-id="50dab-129">資料列是以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-129">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="50dab-130">**定位字元 {t}**</span><span class="sxs-lookup"><span data-stu-id="50dab-130">**Tab {t}**</span></span>|<span data-ttu-id="50dab-131">資料列是以定位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-131">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="50dab-132">**分隔號 {&#124;}**</span><span class="sxs-lookup"><span data-stu-id="50dab-132">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="50dab-133">資料列是以分隔號分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-133">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="50dab-134">**資料行分隔符號**</span><span class="sxs-lookup"><span data-stu-id="50dab-134">**Column delimiter**</span></span>  
 <span data-ttu-id="50dab-135">從可用的資料行分隔符號清單中選取，或輸入分隔符號文字。</span><span class="sxs-lookup"><span data-stu-id="50dab-135">Select from the list of available column delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="50dab-136">值</span><span class="sxs-lookup"><span data-stu-id="50dab-136">Value</span></span>|<span data-ttu-id="50dab-137">描述</span><span class="sxs-lookup"><span data-stu-id="50dab-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="50dab-138">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="50dab-138">**{CR}{LF}**</span></span>|<span data-ttu-id="50dab-139">資料行是以歸位字元和換行字元的組合分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-139">Columns are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="50dab-140">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="50dab-140">**{CR}**</span></span>|<span data-ttu-id="50dab-141">資料行是以歸位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-141">Columns are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="50dab-142">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="50dab-142">**{LF}**</span></span>|<span data-ttu-id="50dab-143">資料行是以換行字元分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-143">Columns are delimited by a line feed.</span></span>|  
|<span data-ttu-id="50dab-144">**分號 {;}**</span><span class="sxs-lookup"><span data-stu-id="50dab-144">**Semicolon {;}**</span></span>|<span data-ttu-id="50dab-145">資料行是以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-145">Columns are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="50dab-146">**冒號 {:}**</span><span class="sxs-lookup"><span data-stu-id="50dab-146">**Colon {:}**</span></span>|<span data-ttu-id="50dab-147">資料行是以冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-147">Columns are delimited by a colon.</span></span>|  
|<span data-ttu-id="50dab-148">**逗號 {,}**</span><span class="sxs-lookup"><span data-stu-id="50dab-148">**Comma {,}**</span></span>|<span data-ttu-id="50dab-149">資料行是以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-149">Columns are delimited by a comma.</span></span>|  
|<span data-ttu-id="50dab-150">**定位字元 {t}**</span><span class="sxs-lookup"><span data-stu-id="50dab-150">**Tab {t}**</span></span>|<span data-ttu-id="50dab-151">資料行是以定位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-151">Columns are delimited by a tab.</span></span>|  
|<span data-ttu-id="50dab-152">**分隔號 {&#124;}**</span><span class="sxs-lookup"><span data-stu-id="50dab-152">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="50dab-153">資料行是以分隔號分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-153">Columns are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="50dab-154">**重設資料行**</span><span class="sxs-lookup"><span data-stu-id="50dab-154">**Reset Columns**</span></span>  
 <span data-ttu-id="50dab-155">按一下 [重設資料行]，即可將原始資料行以外的資料行全部移除。</span><span class="sxs-lookup"><span data-stu-id="50dab-155">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--fixed-width"></a><span data-ttu-id="50dab-156">格式 = 固定寬度</span><span class="sxs-lookup"><span data-stu-id="50dab-156">Format = Fixed Width</span></span>  
 <span data-ttu-id="50dab-157">**字型**</span><span class="sxs-lookup"><span data-stu-id="50dab-157">**Font**</span></span>  
 <span data-ttu-id="50dab-158">選取要顯示預覽資料的字型。</span><span class="sxs-lookup"><span data-stu-id="50dab-158">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="50dab-159">**來源資料行**</span><span class="sxs-lookup"><span data-stu-id="50dab-159">**Source data columns**</span></span>  
 <span data-ttu-id="50dab-160">滑動垂直資料列標記，即可調整資料列的寬度，而按一下預覽視窗上方的尺規，即可調整資料行的寬度</span><span class="sxs-lookup"><span data-stu-id="50dab-160">Adjust the width of the row by sliding the vertical row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="50dab-161">**資料列寬度**</span><span class="sxs-lookup"><span data-stu-id="50dab-161">**Row width**</span></span>  
 <span data-ttu-id="50dab-162">為個別資料行加入分隔符號之前，請先指定資料列的長度。</span><span class="sxs-lookup"><span data-stu-id="50dab-162">Specify the length of the row before adding delimiters for individual columns.</span></span> <span data-ttu-id="50dab-163">或者，在預覽視窗中拖曳垂直線來標示資料列結尾。</span><span class="sxs-lookup"><span data-stu-id="50dab-163">Or, drag the vertical line in the preview window to mark the end of the row.</span></span> <span data-ttu-id="50dab-164">資料列寬度值會自動更新。</span><span class="sxs-lookup"><span data-stu-id="50dab-164">The row width value is automatically updated.</span></span>  
  
 <span data-ttu-id="50dab-165">**重設資料行**</span><span class="sxs-lookup"><span data-stu-id="50dab-165">**Reset Columns**</span></span>  
 <span data-ttu-id="50dab-166">按一下 [重設資料行]，即可將原始資料行以外的資料行全部移除。</span><span class="sxs-lookup"><span data-stu-id="50dab-166">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
### <a name="format--ragged-right"></a><span data-ttu-id="50dab-167">格式 = 不齊右</span><span class="sxs-lookup"><span data-stu-id="50dab-167">Format = Ragged Right</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50dab-168">不齊右檔案是除了最後一個資料行以外，每一個資料行都有固定寬度。</span><span class="sxs-lookup"><span data-stu-id="50dab-168">Ragged right files are those in which every column has a fixed width, except for the last column.</span></span> <span data-ttu-id="50dab-169">它是以資料列分隔符號分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-169">It is delimited by the row delimiter.</span></span>  
  
 <span data-ttu-id="50dab-170">**字型**</span><span class="sxs-lookup"><span data-stu-id="50dab-170">**Font**</span></span>  
 <span data-ttu-id="50dab-171">選取要顯示預覽資料的字型。</span><span class="sxs-lookup"><span data-stu-id="50dab-171">Select the font in which to display the preview data.</span></span>  
  
 <span data-ttu-id="50dab-172">**來源資料行**</span><span class="sxs-lookup"><span data-stu-id="50dab-172">**Source data columns**</span></span>  
 <span data-ttu-id="50dab-173">滑動垂直資料列標記，即可調整資料列的寬度，而按一下預覽視窗上方的尺規，即可調整資料行的寬度</span><span class="sxs-lookup"><span data-stu-id="50dab-173">Adjust the width of the row by sliding the vertical row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window</span></span>  
  
 <span data-ttu-id="50dab-174">**資料列分隔符號**</span><span class="sxs-lookup"><span data-stu-id="50dab-174">**Row delimiter**</span></span>  
 <span data-ttu-id="50dab-175">從可用的資料列分隔符號清單中選取，或輸入分隔符號文字。</span><span class="sxs-lookup"><span data-stu-id="50dab-175">Select from the list of available row delimiters, or enter the delimiter text.</span></span>  
  
|<span data-ttu-id="50dab-176">值</span><span class="sxs-lookup"><span data-stu-id="50dab-176">Value</span></span>|<span data-ttu-id="50dab-177">描述</span><span class="sxs-lookup"><span data-stu-id="50dab-177">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="50dab-178">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="50dab-178">**{CR}{LF}**</span></span>|<span data-ttu-id="50dab-179">資料列是以歸位字元和換行字元的組合分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-179">Rows are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="50dab-180">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="50dab-180">**{CR}**</span></span>|<span data-ttu-id="50dab-181">資料列是以歸位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-181">Rows are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="50dab-182">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="50dab-182">**{LF}**</span></span>|<span data-ttu-id="50dab-183">資料列是以換行字元分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-183">Rows are delimited by a line feed.</span></span>|  
|<span data-ttu-id="50dab-184">**分號 {;}**</span><span class="sxs-lookup"><span data-stu-id="50dab-184">**Semicolon {;}**</span></span>|<span data-ttu-id="50dab-185">資料列是以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-185">Rows are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="50dab-186">**冒號 {:}**</span><span class="sxs-lookup"><span data-stu-id="50dab-186">**Colon {:}**</span></span>|<span data-ttu-id="50dab-187">資料列是以冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-187">Rows are delimited by a colon.</span></span>|  
|<span data-ttu-id="50dab-188">**逗號 {,}**</span><span class="sxs-lookup"><span data-stu-id="50dab-188">**Comma {,}**</span></span>|<span data-ttu-id="50dab-189">資料列是以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-189">Rows are delimited by a comma.</span></span>|  
|<span data-ttu-id="50dab-190">**定位字元 {t}**</span><span class="sxs-lookup"><span data-stu-id="50dab-190">**Tab {t}**</span></span>|<span data-ttu-id="50dab-191">資料列是以定位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-191">Rows are delimited by a tab.</span></span>|  
|<span data-ttu-id="50dab-192">**分隔號 {&#124;}**</span><span class="sxs-lookup"><span data-stu-id="50dab-192">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="50dab-193">資料列是以分隔號分隔。</span><span class="sxs-lookup"><span data-stu-id="50dab-193">Rows are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="50dab-194">**重設資料行**</span><span class="sxs-lookup"><span data-stu-id="50dab-194">**Reset Columns**</span></span>  
 <span data-ttu-id="50dab-195">按一下 [重設資料行]，即可將原始資料行以外的資料行全部移除。</span><span class="sxs-lookup"><span data-stu-id="50dab-195">Remove all but the original columns by clicking **Reset Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50dab-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50dab-196">See Also</span></span>  
 <span data-ttu-id="50dab-197">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="50dab-197">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="50dab-198">[多個一般檔案連線管理員編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="50dab-198">[Multiple Flat Files Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="50dab-199">[多個一般檔案連線管理員編輯器 &#40;Advanced Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="50dab-199">[Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="50dab-200">多個一般檔案連線管理員編輯器 &#40;預覽頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="50dab-200">Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;</span></span>](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)  
  
  
