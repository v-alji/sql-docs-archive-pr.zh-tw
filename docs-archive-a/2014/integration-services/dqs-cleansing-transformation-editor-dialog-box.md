---
title: DQS 清理轉換編輯器對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssdqs.designer.cleansing.f1
- SQL12.SSDQS.DESIGNER.DQCONNECTION.F1
ms.assetid: 07e79641-71ee-45d0-a9ba-ed6f9f68f333
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e97cd138bb17ce3cfe476496e5bc576875728224
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585510"
---
# <a name="dqs-cleansing-transformation-editor-dialog-box"></a><span data-ttu-id="fde3e-102">DQS 清理轉換編輯器對話方塊</span><span class="sxs-lookup"><span data-stu-id="fde3e-102">DQS Cleansing Transformation Editor Dialog Box</span></span>
  <span data-ttu-id="fde3e-103">使用 [DQS 清理轉換編輯器]\*\*\*\* 對話方塊，即可更正使用 Data Quality Services (DQS) 的資料。</span><span class="sxs-lookup"><span data-stu-id="fde3e-103">Use the **DQS Cleansing Transformation Editor** dialog box to correct data using Data Quality Services (DQS).</span></span> <span data-ttu-id="fde3e-104">如需詳細資訊，請參閱 [Data Quality Services Concepts](../../2014/data-quality-services/data-quality-services-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="fde3e-104">For more information, see [Data Quality Services Concepts](../../2014/data-quality-services/data-quality-services-concepts.md).</span></span>  
  
 <span data-ttu-id="fde3e-105">若要了解有關轉換的詳細資訊，請參閱＜ [DQS Cleansing Transformation](data-flow/transformations/dqs-cleansing-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fde3e-105">To learn more about the transformation, see [DQS Cleansing Transformation](data-flow/transformations/dqs-cleansing-transformation.md).</span></span>  
  
 <span data-ttu-id="fde3e-106">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="fde3e-106">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="fde3e-107">開啟 DQS 清理轉換編輯器</span><span class="sxs-lookup"><span data-stu-id="fde3e-107">Open the DQS Cleansing Transformation Editor</span></span>](#open)  
  
-   <span data-ttu-id="fde3e-108">[設定 [連接管理員] 索引標籤上的選項](#connection)</span><span class="sxs-lookup"><span data-stu-id="fde3e-108">[Set options on the Connection Manager tab](#connection)</span></span>  
  
-   [<span data-ttu-id="fde3e-109">設定對應索引標籤上的選項</span><span class="sxs-lookup"><span data-stu-id="fde3e-109">Set options on the Mapping tab</span></span>](#mapping)  
  
-   [<span data-ttu-id="fde3e-110">設定進階索引標籤上的選項</span><span class="sxs-lookup"><span data-stu-id="fde3e-110">Set options on the Advanced tab</span></span>](#advanced)  
  
-   <span data-ttu-id="fde3e-111">[設定 [DQS 清理連接管理員] 對話方塊中的選項](#manager)</span><span class="sxs-lookup"><span data-stu-id="fde3e-111">[Set the options in the DQS Cleansing Connection Manager dialog box](#manager)</span></span>  
  
##  <a name="open-the-dqs-cleansing-transformation-editor"></a><a name="open"></a><span data-ttu-id="fde3e-112">開啟 DQS 清理轉換編輯器</span><span class="sxs-lookup"><span data-stu-id="fde3e-112">Open the DQS Cleansing Transformation Editor</span></span>  
  
1.  <span data-ttu-id="fde3e-113">在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中，將 DQS 清理轉換加入至 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]封裝。</span><span class="sxs-lookup"><span data-stu-id="fde3e-113">Add the DQS Cleansing Transformation to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="fde3e-114">以滑鼠右鍵按一下此元件，然後按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="fde3e-114">Right-click the component and then click **Edit**.</span></span>  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> <span data-ttu-id="fde3e-115">設定連接管理員索引標籤上的選項</span><span class="sxs-lookup"><span data-stu-id="fde3e-115">Set options on the Connection Manager tab</span></span>  
 <span data-ttu-id="fde3e-116">**資料品質連接管理員**</span><span class="sxs-lookup"><span data-stu-id="fde3e-116">**Data quality connection manager**</span></span>  
 <span data-ttu-id="fde3e-117">從清單中選取現有的 DQS 連線管理員，或按一下 [新增]\*\*\*\* 建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="fde3e-117">Select an existing DQS connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="fde3e-118">**新增**</span><span class="sxs-lookup"><span data-stu-id="fde3e-118">**New**</span></span>  
 <span data-ttu-id="fde3e-119">使用 [DQS 清理連線管理員]\*\*\*\* 對話方塊來建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="fde3e-119">Create a new connection manager by using the **DQS Cleansing Connection Manager** dialog box.</span></span> <span data-ttu-id="fde3e-120">請參閱[設定 DQS 清理連線管理員對話方塊中的選項](#manager)</span><span class="sxs-lookup"><span data-stu-id="fde3e-120">See [Set the options in the DQS Cleansing Connection Manager dialog box](#manager)</span></span>  
  
 <span data-ttu-id="fde3e-121">**資料品質知識庫**</span><span class="sxs-lookup"><span data-stu-id="fde3e-121">**Data Quality Knowledge Base**</span></span>  
 <span data-ttu-id="fde3e-122">針對連接的資料來源選取現有的 DQS 知識庫。</span><span class="sxs-lookup"><span data-stu-id="fde3e-122">Select an existing DQS knowledge base for the connected data source.</span></span> <span data-ttu-id="fde3e-123">如需有關 DQS 知識庫的詳細資訊，請參閱＜ [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fde3e-123">For more information about the DQS knowledge base, see [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
 <span data-ttu-id="fde3e-124">**加密連線**</span><span class="sxs-lookup"><span data-stu-id="fde3e-124">**Encrypt connection**</span></span>  
 <span data-ttu-id="fde3e-125">指定是否要加密連接，以便加密 DQS 伺服器與之間的資料傳輸 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fde3e-125">specify whether to encrypt the connection, in order to encrypt the data transfer between the DQS Server and [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="fde3e-126">**可用的定義域**</span><span class="sxs-lookup"><span data-stu-id="fde3e-126">**Available domains**</span></span>  
 <span data-ttu-id="fde3e-127">針對選取的知識庫列出可用的定義域。</span><span class="sxs-lookup"><span data-stu-id="fde3e-127">Lists the available domains for the selected knowledge base.</span></span> <span data-ttu-id="fde3e-128">定義域有二種類型：單一定義域以及包含兩個或多個單一定義域的複合定義域。</span><span class="sxs-lookup"><span data-stu-id="fde3e-128">There are two types of domains: single domains, and composite domains that contain two or more single domains.</span></span>  
  
 <span data-ttu-id="fde3e-129">如需有關如何將資料行對應至複合定義域的詳細資訊，請參閱＜ [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fde3e-129">For information on how to map columns to composite domains, see [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md).</span></span>  
  
 <span data-ttu-id="fde3e-130">如需有關定義域的詳細資訊，請參閱＜ [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fde3e-130">For more information about domains, see [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
 <span data-ttu-id="fde3e-131">**設定錯誤輸出**</span><span class="sxs-lookup"><span data-stu-id="fde3e-131">**Configure Error Output**</span></span>  
 <span data-ttu-id="fde3e-132">指定如何處理資料列層級錯誤。</span><span class="sxs-lookup"><span data-stu-id="fde3e-132">Specify how to handle row-level errors.</span></span> <span data-ttu-id="fde3e-133">當轉換更正來自所連接之資料來源資料所含的非預期資料值或驗證條件約束時，可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="fde3e-133">Errors can occur when the transformation corrects data from the connected data source, due to unexpected data values or validation constraints.</span></span>  
  
 <span data-ttu-id="fde3e-134">有效的值如下：</span><span class="sxs-lookup"><span data-stu-id="fde3e-134">The following are the valid values:</span></span>  
  
-   <span data-ttu-id="fde3e-135">**[失敗元件]**，指出轉換失敗，且輸入資料未插入 Data Quality Services 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="fde3e-135">**Fail Component**, which indicates that the transformation fails and the input data is not inserted into the Data Quality Services database.</span></span> <span data-ttu-id="fde3e-136">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="fde3e-136">This is the default value.</span></span>  
  
-   <span data-ttu-id="fde3e-137">**[重新導向資料列]**，指出輸入資料未插入 Data Quality Services 資料庫，並會重新導向至錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="fde3e-137">**Redirect Row**, which indicates that the input data is not inserted into the Data Quality Services database and is redirected to the error output.</span></span>  
  
##  <a name="set-options-on-the-mapping-tab"></a><a name="mapping"></a><span data-ttu-id="fde3e-138">在 [對應] 索引標籤上設定選項</span><span class="sxs-lookup"><span data-stu-id="fde3e-138">Set options on the Mapping tab</span></span>  
 <span data-ttu-id="fde3e-139">如需有關如何將資料行對應至複合定義域的詳細資訊，請參閱＜ [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fde3e-139">For information on how to map columns to composite domains, see [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md).</span></span>  
  
 <span data-ttu-id="fde3e-140">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="fde3e-140">**Available Input Columns**</span></span>  
 <span data-ttu-id="fde3e-141">從連接的資料來源列出資料行。</span><span class="sxs-lookup"><span data-stu-id="fde3e-141">Lists the columns from the connected data source.</span></span> <span data-ttu-id="fde3e-142">選取一個或多個包含您想要更正之資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="fde3e-142">Select one or more columns that contain data that you want to correct.</span></span>  
  
 <span data-ttu-id="fde3e-143">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="fde3e-143">**Input Column**</span></span>  
 <span data-ttu-id="fde3e-144">列出您在 [可用的輸入資料行]\*\*\*\* 區域中選取的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="fde3e-144">Lists an input column that you selected in the **Available Input Columns** area.</span></span>  
  
 <span data-ttu-id="fde3e-145">**網域**</span><span class="sxs-lookup"><span data-stu-id="fde3e-145">**Domain**</span></span>  
 <span data-ttu-id="fde3e-146">選取要對應至輸入資料行的定義域。</span><span class="sxs-lookup"><span data-stu-id="fde3e-146">Select a domain to map to the input column.</span></span>  
  
 <span data-ttu-id="fde3e-147">**來源別名**</span><span class="sxs-lookup"><span data-stu-id="fde3e-147">**Source Alias**</span></span>  
 <span data-ttu-id="fde3e-148">列出包含原始資料行值的來源資料行。</span><span class="sxs-lookup"><span data-stu-id="fde3e-148">Lists the source column that contains the original column value.</span></span>  
  
 <span data-ttu-id="fde3e-149">按一下欄位以修改資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="fde3e-149">Click in the field to modify the column name.</span></span>  
  
 <span data-ttu-id="fde3e-150">**輸出別名**</span><span class="sxs-lookup"><span data-stu-id="fde3e-150">**Output Alias**</span></span>  
 <span data-ttu-id="fde3e-151">列出 [DQS 清理轉換]\*\*\*\* 所輸出的資料行。</span><span class="sxs-lookup"><span data-stu-id="fde3e-151">Lists the column that is outputted by the **DQS Cleansing Transformation**.</span></span> <span data-ttu-id="fde3e-152">此資料行包含原始資料行值或更正的值。</span><span class="sxs-lookup"><span data-stu-id="fde3e-152">The column contains the original column value or the corrected value.</span></span>  
  
 <span data-ttu-id="fde3e-153">按一下欄位以修改資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="fde3e-153">Click in the field to modify the column name.</span></span>  
  
 <span data-ttu-id="fde3e-154">**狀態別名**</span><span class="sxs-lookup"><span data-stu-id="fde3e-154">**Status Alias**</span></span>  
 <span data-ttu-id="fde3e-155">列出包含更正資料之狀態資訊的資料行。</span><span class="sxs-lookup"><span data-stu-id="fde3e-155">Lists the column that contains status information for the corrected data.</span></span> <span data-ttu-id="fde3e-156">按一下欄位以修改資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="fde3e-156">Click in the field to modify the column name.</span></span>  
  
##  <a name="set-options-on-the-advanced-tab"></a><a name="advanced"></a><span data-ttu-id="fde3e-157">設定 [Advanced] 索引標籤上的選項</span><span class="sxs-lookup"><span data-stu-id="fde3e-157">Set options on the Advanced tab</span></span>  
 <span data-ttu-id="fde3e-158">**標準化輸出**</span><span class="sxs-lookup"><span data-stu-id="fde3e-158">**Standardize output**</span></span>  
 <span data-ttu-id="fde3e-159">指出是否要根據針對定義域所定義的輸出格式，以標準化格式輸出資料。</span><span class="sxs-lookup"><span data-stu-id="fde3e-159">Indicate whether to output the data in the standardized format based on the output format defined for domains.</span></span> <span data-ttu-id="fde3e-160">如需標準化格式的詳細資訊，請參閱 [資料清理](../../2014/data-quality-services/data-cleansing.md)。</span><span class="sxs-lookup"><span data-stu-id="fde3e-160">For more information about standardized format, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md).</span></span>  
  
 <span data-ttu-id="fde3e-161">**信心百倍**</span><span class="sxs-lookup"><span data-stu-id="fde3e-161">**Confidence**</span></span>  
 <span data-ttu-id="fde3e-162">指出是否要針對更正的資料包含信心層級。</span><span class="sxs-lookup"><span data-stu-id="fde3e-162">Indicate whether to include the confidence level for corrected data.</span></span> <span data-ttu-id="fde3e-163">信心層級表示 DQS 對更正或建議的確定程度。</span><span class="sxs-lookup"><span data-stu-id="fde3e-163">The confidence level indicates the extend of certainty of DQS for the correction or suggestion.</span></span> <span data-ttu-id="fde3e-164">如需信賴等級的詳細資訊，請參閱 [資料清理](../../2014/data-quality-services/data-cleansing.md)。</span><span class="sxs-lookup"><span data-stu-id="fde3e-164">For more information about confidence levels, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md).</span></span>  
  
 <span data-ttu-id="fde3e-165">**原因**</span><span class="sxs-lookup"><span data-stu-id="fde3e-165">**Reason**</span></span>  
 <span data-ttu-id="fde3e-166">指出是否要包含資料更正的原因。</span><span class="sxs-lookup"><span data-stu-id="fde3e-166">Indicate whether to include the reason for the data correction.</span></span>  
  
 <span data-ttu-id="fde3e-167">**附加的資料**</span><span class="sxs-lookup"><span data-stu-id="fde3e-167">**Appended Data**</span></span>  
 <span data-ttu-id="fde3e-168">指出是否要輸出從現有參考資料提供者收到的其他資料。</span><span class="sxs-lookup"><span data-stu-id="fde3e-168">Indicate whether to output additional data that is received from an existing reference data provider.</span></span> <span data-ttu-id="fde3e-169">如需詳細資訊，請參閱 [Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md)。</span><span class="sxs-lookup"><span data-stu-id="fde3e-169">For more information, see [Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md).</span></span>  
  
 <span data-ttu-id="fde3e-170">**附加的資料結構描述**</span><span class="sxs-lookup"><span data-stu-id="fde3e-170">**Appended Data Schema**</span></span>  
 <span data-ttu-id="fde3e-171">指出是否要輸出資料結構描述。</span><span class="sxs-lookup"><span data-stu-id="fde3e-171">Indicate whether to output the data schema.</span></span> <span data-ttu-id="fde3e-172">如需詳細資訊，請參閱[將定義域或複合定義域附加至參考資料](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)。</span><span class="sxs-lookup"><span data-stu-id="fde3e-172">For more information, see [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>  
  
##  <a name="set-the-options-in-the-dqs-cleansing-connection-manager-dialog-box"></a><a name="manager"></a><span data-ttu-id="fde3e-173">設定 [DQS 清理連接管理員] 對話方塊中的選項</span><span class="sxs-lookup"><span data-stu-id="fde3e-173">Set the options in the DQS Cleansing Connection Manager dialog box</span></span>  
 <span data-ttu-id="fde3e-174">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="fde3e-174">**Server name**</span></span>  
 <span data-ttu-id="fde3e-175">選取或輸入您想要連接之 DQS 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="fde3e-175">Select or type the name of the DQS server that you want to connect to.</span></span> <span data-ttu-id="fde3e-176">如需有關伺服器的詳細資訊，請參閱＜ [DQS Administration](../../2014/data-quality-services/dqs-administration.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fde3e-176">For more information about the server, see [DQS Administration](../../2014/data-quality-services/dqs-administration.md).</span></span>  
  
 <span data-ttu-id="fde3e-177">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="fde3e-177">**Test Connection**</span></span>  
 <span data-ttu-id="fde3e-178">按一下以確認您指定的連接是否可用。</span><span class="sxs-lookup"><span data-stu-id="fde3e-178">Click to confirm that the connection that you specified is viable.</span></span>  
  
 <span data-ttu-id="fde3e-179">您也可以透過執行下列步驟，從連接區域開啟 **[DQS 清理連接管理員]** 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="fde3e-179">You can also open the **DQS Cleansing Connection Manager** dialog box from the connections area, by doing the following:</span></span>  
  
1.  <span data-ttu-id="fde3e-180">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟現有的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案，或建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="fde3e-180">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project or create a new one.</span></span>  
  
2.  <span data-ttu-id="fde3e-181">以滑鼠右鍵按一下連接區域、按一下 [新增連接]\*\*\*\*，然後按一下 [DQS]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fde3e-181">Right-click in the connections area, click **New Connection**, and then click **DQS**.</span></span>  
  
3.  <span data-ttu-id="fde3e-182">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="fde3e-182">Click **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde3e-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fde3e-183">See Also</span></span>  
 [<span data-ttu-id="fde3e-184">將資料品質規則套用至資料來源</span><span class="sxs-lookup"><span data-stu-id="fde3e-184">Apply Data Quality Rules to Data Source</span></span>](data-flow/transformations/apply-data-quality-rules-to-data-source.md)  
  
  
