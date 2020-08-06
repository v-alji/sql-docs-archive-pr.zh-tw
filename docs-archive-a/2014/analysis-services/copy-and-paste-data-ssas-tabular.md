---
title: 複製並貼上資料 (SSAS 表格式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.pastepreviewdb.f1
ms.assetid: 2f8d8b3d-810b-4c31-98f2-341015e13da8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30df733377f3cb6f7583d380fbb8e92a0ea69e88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592997"
---
# <a name="copy-and-paste-data-ssas-tabular"></a><span data-ttu-id="00a38-102">複製及貼上資料 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="00a38-102">Copy and Paste Data (SSAS Tabular)</span></span>
  <span data-ttu-id="00a38-103">您可以從外部應用程式複製資料表的資料，並將其貼入模型設計師中新的資料表或現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="00a38-103">You can copy table data from external applications and paste it into a new or existing table in the model designer.</span></span> <span data-ttu-id="00a38-104">您從 [剪貼簿] 貼入的資料必須是 HTML 格式，例如從 Excel 或 Word 複製的資料。</span><span class="sxs-lookup"><span data-stu-id="00a38-104">The data that you paste from the Clipboard must be in HTML format, for example, data that is copied from Excel or Word.</span></span> <span data-ttu-id="00a38-105">模型設計師將會自動偵測並套用資料類型至貼上的資料。</span><span class="sxs-lookup"><span data-stu-id="00a38-105">The model designer will automatically detect and apply data types to the pasted data.</span></span> <span data-ttu-id="00a38-106">您也可以手動修改資料類型或資料行的顯示格式設定。</span><span class="sxs-lookup"><span data-stu-id="00a38-106">You can also manually modify the data type or display formatting of a column.</span></span>  
  
 <span data-ttu-id="00a38-107">與含資料來源連接的資料表不同的是，貼上的資料表不具備連接名稱或來源資料屬性。</span><span class="sxs-lookup"><span data-stu-id="00a38-107">Unlike tables with a data source connection, pasted tables do not have a Connection Name or Source Data property.</span></span> <span data-ttu-id="00a38-108">貼上的資料保存於 Model.bim 檔中。</span><span class="sxs-lookup"><span data-stu-id="00a38-108">Pasted data is persisted in the Model.bim file.</span></span> <span data-ttu-id="00a38-109">儲存專案或 Model.bim 檔時，也會儲存貼上的資料。</span><span class="sxs-lookup"><span data-stu-id="00a38-109">When the project or Model.bim file is saved, the pasted data is also saved.</span></span>  
  
 <span data-ttu-id="00a38-110">當部署模型時，無論部署是否處理該模型，也會一併部署貼上的資料。</span><span class="sxs-lookup"><span data-stu-id="00a38-110">When a model is deployed, pasted data will also be deployed with it regardless if the model is processed with the deployment.</span></span>  
  
 <span data-ttu-id="00a38-111">本主題的章節：</span><span class="sxs-lookup"><span data-stu-id="00a38-111">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="00a38-112">先決條件</span><span class="sxs-lookup"><span data-stu-id="00a38-112">Prerequisites</span></span>](#bkmk_prerequisites)  
  
-   [<span data-ttu-id="00a38-113">貼上資料</span><span class="sxs-lookup"><span data-stu-id="00a38-113">Paste Data</span></span>](#bkmk_paste_data)  
  
-   [<span data-ttu-id="00a38-114">貼上預覽對話方塊</span><span class="sxs-lookup"><span data-stu-id="00a38-114">Paste Preview Dialog Box</span></span>](#bkmk_paste_preview)  
  
##  <a name="prerequisites"></a><a name="bkmk_prerequisites"></a> <span data-ttu-id="00a38-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="00a38-115">Prerequisites</span></span>  
 <span data-ttu-id="00a38-116">貼上資料時有一些限制：</span><span class="sxs-lookup"><span data-stu-id="00a38-116">There are some restrictions when pasting data:</span></span>  
  
-   <span data-ttu-id="00a38-117">貼上的資料表不能超過 10,000 個資料列。</span><span class="sxs-lookup"><span data-stu-id="00a38-117">Pasted tables cannot have more than 10,000 rows.</span></span>  
  
-   <span data-ttu-id="00a38-118">貼上的資料表不能進行資料分割。</span><span class="sxs-lookup"><span data-stu-id="00a38-118">Pasted tables cannot be partitioned.</span></span>  
  
-   <span data-ttu-id="00a38-119">DirectQuery 模式不支援貼上的資料表。</span><span class="sxs-lookup"><span data-stu-id="00a38-119">Pasted tables are not supported in DirectQuery mode.</span></span>  
  
-   <span data-ttu-id="00a38-120">只有當處理的資料表原先是透過從 [剪貼簿] 貼上資料而建立時，才可以使用 **[貼上新增]** 和 **[貼上取代]** 選項。</span><span class="sxs-lookup"><span data-stu-id="00a38-120">The **Paste Append** and **Paste Replace** options are only available when working with a table that was initially created by pasting data from the Clipboard.</span></span> <span data-ttu-id="00a38-121">您無法使用 **[貼上新增]** 和 **[貼上取代]** ，將資料加入其他資料來源類型之匯入資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="00a38-121">You cannot use **Paste Append** or **Paste Replace** to add data into a table of imported data from another type of data source.</span></span>  
  
-   <span data-ttu-id="00a38-122">當您使用 **[貼上新增]** 或 **[貼上取代]** 時，新的資料必須與原始資料的資料行數目完全相同。</span><span class="sxs-lookup"><span data-stu-id="00a38-122">When you use **Paste Append** or **Paste Replace**, the new data must contain exactly the same number of columns as the original data.</span></span> <span data-ttu-id="00a38-123">您貼上或附加的資料行，最好也與目的地資料表是相同或相容的資料類型。</span><span class="sxs-lookup"><span data-stu-id="00a38-123">Preferably, the columns of data that you paste or append should also be of the same or compatible data type as those in the destination table.</span></span> <span data-ttu-id="00a38-124">在某些情況下，您可以使用不同的資料類型，但會顯示 **類型不符** 的錯誤。</span><span class="sxs-lookup"><span data-stu-id="00a38-124">In some cases you can use a different data type, but a **Type mismatch** error may be displayed.</span></span>  
  
##  <a name="paste-data"></a><a name="bkmk_paste_data"></a> <span data-ttu-id="00a38-125">貼上資料</span><span class="sxs-lookup"><span data-stu-id="00a38-125">Paste Data</span></span>  
  
#### <a name="to-paste-data-into-the-designer"></a><span data-ttu-id="00a38-126">將資料貼入設計師</span><span class="sxs-lookup"><span data-stu-id="00a38-126">To paste data into the designer</span></span>  
  
-   <span data-ttu-id="00a38-127">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，按一下 **[編輯]** 功能表，然後按一下下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="00a38-127">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Edit** menu, and then clicke of the following:</span></span>  
  
    -   <span data-ttu-id="00a38-128">按一下 **[貼上]** ，將 [剪貼簿] 中的內容貼入新的資料表中。</span><span class="sxs-lookup"><span data-stu-id="00a38-128">Click **Paste** to paste the contents of the Clipboard into a new table.</span></span>  
  
    -   <span data-ttu-id="00a38-129">按一下 **[貼上新增]** ，將 [剪貼簿] 的內容當做額外的資料列貼入選取的資料表中。</span><span class="sxs-lookup"><span data-stu-id="00a38-129">Click **Paste Append** to paste the contents of the Clipboard as additional rows into the selected table.</span></span> <span data-ttu-id="00a38-130">新的資料列將會加入至資料表的結尾。</span><span class="sxs-lookup"><span data-stu-id="00a38-130">The new rows will be added to the end of the table.</span></span>  
  
    -   <span data-ttu-id="00a38-131">按一下 **[貼上取代]** ，以 [剪貼簿] 的內容取代選取的資料表。</span><span class="sxs-lookup"><span data-stu-id="00a38-131">Click **Paste Replace** to replace the selected table with the contents of the Clipboard.</span></span> <span data-ttu-id="00a38-132">所有現有的資料行標頭名稱依然會在資料表中，並且保留關聯性。</span><span class="sxs-lookup"><span data-stu-id="00a38-132">All existing column header names will remain in the table, and relationships are preserved.</span></span>  
  
##  <a name="paste-preview-dialog-box"></a><a name="bkmk_paste_preview"></a><span data-ttu-id="00a38-133">貼上預覽對話方塊</span><span class="sxs-lookup"><span data-stu-id="00a38-133">Paste Preview Dialog Box</span></span>  
 <span data-ttu-id="00a38-134">**[貼上預覽]** 對話方塊可讓您查看已複製到設計師視窗之資料的預覽，並確認資料已正確複製。</span><span class="sxs-lookup"><span data-stu-id="00a38-134">The **Paste Preview** dialog box enables you to see a preview of data that is copied into the designer window and to ensure that the data is copied correctly.</span></span> <span data-ttu-id="00a38-135">若要存取此對話方塊，請將以資料表為基礎的 HTML 格式資料複製到剪貼簿，然後在設計師中，按一下 [編輯]\*\*\*\* 功能表，再按一下 [貼上]\*\*\*\*、[貼上新增]\*\*\*\* 或 [貼上取代]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="00a38-135">To access this dialog box, copy table-based data in the HTML format to the clipboard, and then in the designer, click on the **Edit** menu, and then click **Paste**, **Paste Append**, or **Paste Replace**.</span></span> <span data-ttu-id="00a38-136">只有在透過從剪貼簿複製並貼上而建立的資料表中加入或取代資料時，才可以使用 **[貼上新增]** 和 **[取代貼上]** 選項。</span><span class="sxs-lookup"><span data-stu-id="00a38-136">The **Paste Append** and **Paste Replace** options are only available when you add or replace data in a table that was created by copying and pasting from the Clipboard.</span></span> <span data-ttu-id="00a38-137">您不能使用 **[貼上新增]** 或 **[取代貼上]** ，將資料加入至匯入資料的資料表中。</span><span class="sxs-lookup"><span data-stu-id="00a38-137">You cannot use **Paste Append** or **Paste Replace** to add data into a table of imported data.</span></span>  
  
 <span data-ttu-id="00a38-138">根據您是將資料貼入全新的資料表、貼入現有的資料表並以新資料取代現有資料，或附加到現有資料表，此對話方塊的選項都不同。</span><span class="sxs-lookup"><span data-stu-id="00a38-138">The options for this dialog box are different depending on whether you paste data into a completely new table, paste data into an existing table and then replace the existing data with the new data, or whether you append data to an existing table.</span></span>  
  
### <a name="paste-to-new-table"></a><span data-ttu-id="00a38-139">貼入新資料表</span><span class="sxs-lookup"><span data-stu-id="00a38-139">Paste to New Table</span></span>  
 <span data-ttu-id="00a38-140">**資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="00a38-140">**Table name**</span></span>  
 <span data-ttu-id="00a38-141">指定將會在設計師中建立之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="00a38-141">Specify the name of the table that will be created in the designer.</span></span>  
  
 <span data-ttu-id="00a38-142">**要貼上的資料**</span><span class="sxs-lookup"><span data-stu-id="00a38-142">**Data to be pasted**</span></span>  
 <span data-ttu-id="00a38-143">顯示將加入到目的地資料表的 [剪貼簿] 內容範例。</span><span class="sxs-lookup"><span data-stu-id="00a38-143">Shows a sample of the Clipboard contents that will be added to the destination table.</span></span>  
  
### <a name="paste-append"></a><span data-ttu-id="00a38-144">[貼上新增]</span><span class="sxs-lookup"><span data-stu-id="00a38-144">Paste Append</span></span>  
 <span data-ttu-id="00a38-145">**資料表中的現有資料**</span><span class="sxs-lookup"><span data-stu-id="00a38-145">**Existing data in the table**</span></span>  
 <span data-ttu-id="00a38-146">顯示資料表中現有資料的範例，以便讓您確認資料行、資料類型等。</span><span class="sxs-lookup"><span data-stu-id="00a38-146">Shows a sample of the existing data in the table so that you can verify the columns, data types, etc.</span></span>  
  
 <span data-ttu-id="00a38-147">**要貼上的資料**</span><span class="sxs-lookup"><span data-stu-id="00a38-147">**Data to be pasted**</span></span>  
 <span data-ttu-id="00a38-148">顯示剪貼簿內容的範例。</span><span class="sxs-lookup"><span data-stu-id="00a38-148">Shows a sample of the Clipboard contents.</span></span> <span data-ttu-id="00a38-149">此資料將會附加現有資料。</span><span class="sxs-lookup"><span data-stu-id="00a38-149">The existing data will be appended by this data.</span></span>  
  
### <a name="paste-replace"></a><span data-ttu-id="00a38-150">[貼上取代]</span><span class="sxs-lookup"><span data-stu-id="00a38-150">Paste Replace</span></span>  
 <span data-ttu-id="00a38-151">**資料表中的現有資料**</span><span class="sxs-lookup"><span data-stu-id="00a38-151">**Existing data in the table**</span></span>  
 <span data-ttu-id="00a38-152">顯示資料表中現有資料的範例，以便讓您確認資料行、資料類型等。</span><span class="sxs-lookup"><span data-stu-id="00a38-152">Shows a sample of the existing data in the table so that you can verify the columns, data types, etc.</span></span>  
  
 <span data-ttu-id="00a38-153">**要貼上的資料**</span><span class="sxs-lookup"><span data-stu-id="00a38-153">**Data to be pasted**</span></span>  
 <span data-ttu-id="00a38-154">顯示剪貼簿內容的範例。</span><span class="sxs-lookup"><span data-stu-id="00a38-154">Shows a sample of the Clipboard contents.</span></span> <span data-ttu-id="00a38-155">目的地資料表中的現有資料將會遭到刪除，並將新資料列插入資料表中。</span><span class="sxs-lookup"><span data-stu-id="00a38-155">The existing data in the destination table will be deleted and the new rows will be inserted into the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a38-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00a38-156">See Also</span></span>  
 <span data-ttu-id="00a38-157">[將資料匯入 &#40;SSAS 表格式&#41;](import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="00a38-157">[Import Data &#40;SSAS Tabular&#41;](import-data-ssas-tabular.md) </span></span>  
 <span data-ttu-id="00a38-158">[&#40;SSAS 表格式&#41;支援的資料來源](tabular-models/data-sources-supported-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="00a38-158">[Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="00a38-159">設定資料行的資料類型 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="00a38-159">Set the Data Type of a Column &#40;SSAS Tabular&#41;</span></span>](tabular-models/set-the-data-type-of-a-column-ssas-tabular.md)  
  
  
