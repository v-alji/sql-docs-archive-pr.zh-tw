---
title: 使用參考資料 (外部) 知識清理資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 158009e9-8069-4741-8085-c14a5518d3fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 107fd3bbf3c6f14e50cb6527400697aab7c7d6a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687176"
---
# <a name="cleanse-data-using-reference-data-external-knowledge"></a><span data-ttu-id="95169-102">使用參考資料 (外部) 知識清理資料</span><span class="sxs-lookup"><span data-stu-id="95169-102">Cleanse Data Using Reference Data (External) Knowledge</span></span>
  <span data-ttu-id="95169-103">本主題描述如何使用參考資料提供者的知識來清理資料。</span><span class="sxs-lookup"><span data-stu-id="95169-103">This topic describes how to cleanse data using knowledge from the reference data providers.</span></span> <span data-ttu-id="95169-104">對於使用參考資料提供者的知識來清理資料而言，雖然執行清理活動的所有步驟仍與[使用 DQS &#40;內部&#41; 知識清理資料](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)中所說明的步驟相同，不過本主題將針對在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中使用 Reference Data Service 進行資料清理提供特定資訊。</span><span class="sxs-lookup"><span data-stu-id="95169-104">While all the steps of running a cleansing activity remains the same for cleansing your data using knowledge from the reference data providers as explained in the [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md), this topic provides information specific to data cleansing using reference data service in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span>

 <span data-ttu-id="95169-105">當您使用 DQS 中的參考資料服務功能來清理資料時，DQS 清理處理序會以批次要求的形式，將對應的定義域值傳送至參考資料服務提供者。</span><span class="sxs-lookup"><span data-stu-id="95169-105">When you use the reference data service feature in DQS to cleanse your data, the DQS cleansing process sends the mapped domain values to the reference data service provider as a batch request.</span></span> <span data-ttu-id="95169-106">參考資料服務會使用下列資訊來回應：</span><span class="sxs-lookup"><span data-stu-id="95169-106">The reference data service responds with the following information:</span></span>

-   <span data-ttu-id="95169-107">建議的更正</span><span class="sxs-lookup"><span data-stu-id="95169-107">Suggested correction</span></span>

-   <span data-ttu-id="95169-108">信賴度</span><span class="sxs-lookup"><span data-stu-id="95169-108">Confidence</span></span>

-   <span data-ttu-id="95169-109">有關對應定義域的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="95169-109">Additional information about the mapped domain.</span></span> <span data-ttu-id="95169-110">參考資料也可以使用其他資料來標準化、剖析或充實來源。</span><span class="sxs-lookup"><span data-stu-id="95169-110">Reference data can also standardize, parse, or enrich the source with additional data.</span></span> <span data-ttu-id="95169-111">這項資訊是在回應的其他欄位中提供。</span><span class="sxs-lookup"><span data-stu-id="95169-111">This information is provided in additional fields in the response.</span></span>

 <span data-ttu-id="95169-112">從參考資料服務取得回應之後，DQS 就會在清理活動期間進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="95169-112">After getting the response from reference data service, the following happens in DQS during the cleansing activity:</span></span>

-   <span data-ttu-id="95169-113">根據將定義域對應至參考資料服務期間指定的 **[自動校正臨界值]** 和 **[最低信賴值]** 值，依照信賴等級自動更正或建議定義域值。</span><span class="sxs-lookup"><span data-stu-id="95169-113">Based on the **Auto Correction Threshold** and **Min Confidence** values specified during mapping of the domains with reference data service, domain values are automatically corrected or suggested based on the confidence level.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="95169-114">使用參考資料服務中的知識來清理資料時，系統會套用您在將定義域對應至參考資料服務期間指定的臨界值，而非 **[組態]** 區段之 **[一般設定]** 索引標籤中指定的臨界值。</span><span class="sxs-lookup"><span data-stu-id="95169-114">The threshold values that you specify during mapping a domain to a reference data service are applied while cleansing data using the knowledge in reference data service, and not the ones that are specified in the **General Settings** tab in the **Configuration** section.</span></span> <span data-ttu-id="95169-115">如需指定參考資料清理之臨界值的相關資訊，請參閱[將定義域或複合定義域附加至參考資料](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)中的步驟9。</span><span class="sxs-lookup"><span data-stu-id="95169-115">For information about specifying threshold values for reference data cleansing, see step 9 in [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>

-   <span data-ttu-id="95169-116">定義域值的分類方式如下： **[建議]**、 **[新增]**、 **[無效]**、 **[更正]** 和 **[正確]**。</span><span class="sxs-lookup"><span data-stu-id="95169-116">Domain values are categorized into the following: **Suggested**, **New**, **Invalid**, **Corrected**, and **Correct**.</span></span>

-   <span data-ttu-id="95169-117">其他資料會附加至來源，而且這項資訊可與清理的資料一起匯出。</span><span class="sxs-lookup"><span data-stu-id="95169-117">Additional data is appended to the source, and the information is available along with the cleansed data for exporting.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="95169-118">開始之前</span><span class="sxs-lookup"><span data-stu-id="95169-118">Before You Begin</span></span>

###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="95169-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="95169-119">Prerequisites</span></span>
 <span data-ttu-id="95169-120">您必須已經將 DQS 知識庫中已對應且必要的定義域對應至適當的參考資料服務。</span><span class="sxs-lookup"><span data-stu-id="95169-120">You must have mapped required domains in a DQS knowledge base to the appropriate reference data service.</span></span> <span data-ttu-id="95169-121">此外，知識庫必須包含您想要清理之資料類型的相關知識。</span><span class="sxs-lookup"><span data-stu-id="95169-121">Additionally, the knowledge base must contain knowledge about the type of data that you want to cleanse.</span></span> <span data-ttu-id="95169-122">例如，如果您想要清理包含美國地址的來源資料，就必須將定義域對應至提供「高品質」美國地址資料的參考資料服務提供者。</span><span class="sxs-lookup"><span data-stu-id="95169-122">For example, if you want to cleanse your source data that contains US addresses, you must map your domains to a reference data service provider that provides high-quality" data for US addresses.</span></span> <span data-ttu-id="95169-123">如需詳細資訊，請參閱[將定義域或複合定義域附加至參考資料](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)。</span><span class="sxs-lookup"><span data-stu-id="95169-123">For more information, see [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>

###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="95169-124">Security</span><span class="sxs-lookup"><span data-stu-id="95169-124">Security</span></span>

####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="95169-125">權限</span><span class="sxs-lookup"><span data-stu-id="95169-125">Permissions</span></span>
 <span data-ttu-id="95169-126">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 或 dqs_kb_operator 角色，才能執行資料清理。</span><span class="sxs-lookup"><span data-stu-id="95169-126">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to perform data cleansing.</span></span>

##  <a name="cleanse-your-data-using-reference-data-knowledge"></a><a name="Cleanse"></a> <span data-ttu-id="95169-127">使用參考資料知識清理您的資料</span><span class="sxs-lookup"><span data-stu-id="95169-127">Cleanse Your Data Using Reference Data Knowledge</span></span>
 <span data-ttu-id="95169-128">我們將繼續使用在上一個主題中所對應的網域、[將定義域或複合定義域附加至參考資料](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)，以及 Azure Marketplace 中的 Melissa 資料服務的相同範例。</span><span class="sxs-lookup"><span data-stu-id="95169-128">We will continue with the same example of using the domains that we mapped in the previous topic, [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md), with the Melissa Data service in Azure Marketplace.</span></span> <span data-ttu-id="95169-129">現在，我們將會使用相同的定義域來清理一些美國地址樣本。</span><span class="sxs-lookup"><span data-stu-id="95169-129">Now, we will use the same domains to cleanse some sample US addresses.</span></span> <span data-ttu-id="95169-130">清理資料的步驟一如[使用 DQS &#40;內部&#41; 知識清理資料](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="95169-130">The steps to cleanse data are the same as described in [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).</span></span> <span data-ttu-id="95169-131">不過，我們會在此程序中視需要吸引您的注意。</span><span class="sxs-lookup"><span data-stu-id="95169-131">However, we will draw you attention wherever necessary during the process.</span></span>

1.  <span data-ttu-id="95169-132">建立資料品質專案，然後選取 **[清理]** 活動。</span><span class="sxs-lookup"><span data-stu-id="95169-132">Create a data quality project, and select the **Cleansing** activity.</span></span> <span data-ttu-id="95169-133">請參閱 [Create a Data Quality Project](../../2014/data-quality-services/create-a-data-quality-project.md)。</span><span class="sxs-lookup"><span data-stu-id="95169-133">See [Create a Data Quality Project](../../2014/data-quality-services/create-a-data-quality-project.md).</span></span>

2.  <span data-ttu-id="95169-134">在 **[對應]** 頁面上，將下列 4 定義域對應至來源資料中的適當資料行： **[地址行]**、 **[縣/市]**、 **[省/市]** 和 **[郵遞區號]**。</span><span class="sxs-lookup"><span data-stu-id="95169-134">On the **Map** page, map the following 4 domains with appropriate columns in your source data: **Address Line**, **City**, **State**, and **Zip**.</span></span> <span data-ttu-id="95169-135">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="95169-135">Click **Next**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="95169-136">因為我們已經對應了 **[地址驗證]** 複合定義域中的所有定義域，所以資料清理現在將針對複合定義域層級進行，而非針對個別定義域層級進行。</span><span class="sxs-lookup"><span data-stu-id="95169-136">As you have mapped all the 4 domains within the **Address Verification** composite domain, the data cleansing will now be done at the composite domain level, and not at the individual domain level.</span></span>

3.  <span data-ttu-id="95169-137">在 **[清理]** 頁面上，按一下 **[開始]**，藉以執行電腦輔助的清理處理序。</span><span class="sxs-lookup"><span data-stu-id="95169-137">On the **Cleanse** page, run the computer-assisted cleansing process by clicking **Start**.</span></span> <span data-ttu-id="95169-138">清理處理序結束之後，請按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="95169-138">After the cleansing process is over, click **Next**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="95169-139">在 **[清理]** 頁面上，DQS 會以下列兩種方式顯示附加至參考資料服務之定義域的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="95169-139">On the **Cleanse** page, DQS displays information about the domains that are attached to reference data service in the following two ways:</span></span>
    > 
    >  -   <span data-ttu-id="95169-140">[開始] 按鈕底下會顯示一則訊息： **「** 網域 \<Domain1> ， \<Domain2> ,... \<DomainN>是使用參考資料服務提供者所清理的。」</span><span class="sxs-lookup"><span data-stu-id="95169-140">A message is displayed below the **Start** button: "Domains \<Domain1>, \<Domain2>,... \<DomainN> are cleansed using reference data service provider."</span></span> <span data-ttu-id="95169-141">在此範例中，則會顯示下列訊息：「使用參考資料服務提供者清理了網域位址驗證」。</span><span class="sxs-lookup"><span data-stu-id="95169-141">In this example, the following message will be displayed: "Domain Address Verification is cleansed using reference data service provider."</span></span>
    > -   <span data-ttu-id="95169-142">針對附加至參考資料服務提供者的定義域，會在 [分析工具 **] 區域中**顯示圖示 [![網域已附加至 RDS](../../2014/data-quality-services/media/dqs-rdsindicator.JPG "定義域已附加至 RDS")]。</span><span class="sxs-lookup"><span data-stu-id="95169-142">An icon, ![Domain is attached to RDS](../../2014/data-quality-services/media/dqs-rdsindicator.JPG "Domain is attached to RDS"), is displayed in the **Profiler** area against the domains attached to reference data service provider.</span></span> <span data-ttu-id="95169-143">在此範例中，該圖示會顯示在 **[地址驗證]** 複合定義域旁邊。</span><span class="sxs-lookup"><span data-stu-id="95169-143">In this example, the icon will be displayed against the **Address Verification** composite domain.</span></span>

4.  <span data-ttu-id="95169-144">在 **[管理和檢視結果]** 頁面上，檢閱您的定義域值。</span><span class="sxs-lookup"><span data-stu-id="95169-144">On the **Manage and view results** page, review your domain values.</span></span> <span data-ttu-id="95169-145">根據將定義域對應至參考資料服務期間在 **[建議的候選值]** 方塊中指定的最大建議數目，參考資料服務可能會針對一個值顯示多項建議 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="95169-145">The reference data service can display more than one suggestion, if available, for a value depending upon the maximum number of suggestions specified in the **Suggested Candidates** box during the mapping of the domain to the reference data service.</span></span> <span data-ttu-id="95169-146">例如，下列美國地址會顯示兩項建議：</span><span class="sxs-lookup"><span data-stu-id="95169-146">For example, two suggestions are displayed for the following US address:</span></span>

     <span data-ttu-id="95169-147">**原始值：**</span><span class="sxs-lookup"><span data-stu-id="95169-147">**Original value:**</span></span>

    |<span data-ttu-id="95169-148">[地址行]</span><span class="sxs-lookup"><span data-stu-id="95169-148">Address Line</span></span>|<span data-ttu-id="95169-149">城市</span><span class="sxs-lookup"><span data-stu-id="95169-149">City</span></span>|<span data-ttu-id="95169-150">州</span><span class="sxs-lookup"><span data-stu-id="95169-150">State</span></span>|<span data-ttu-id="95169-151">Zip</span><span class="sxs-lookup"><span data-stu-id="95169-151">Zip</span></span>|
    |------------------|----------|-----------|---------|
    |<span data-ttu-id="95169-152">1 msft way</span><span class="sxs-lookup"><span data-stu-id="95169-152">1 msft way</span></span>|<span data-ttu-id="95169-153">Redmond</span><span class="sxs-lookup"><span data-stu-id="95169-153">Redmond</span></span>||<span data-ttu-id="95169-154">98052</span><span class="sxs-lookup"><span data-stu-id="95169-154">98052</span></span>|

     <span data-ttu-id="95169-155">**建議的值：**</span><span class="sxs-lookup"><span data-stu-id="95169-155">**Suggested values:**</span></span>

    |<span data-ttu-id="95169-156">[地址行]</span><span class="sxs-lookup"><span data-stu-id="95169-156">Address Line</span></span>|<span data-ttu-id="95169-157">城市</span><span class="sxs-lookup"><span data-stu-id="95169-157">City</span></span>|<span data-ttu-id="95169-158">州</span><span class="sxs-lookup"><span data-stu-id="95169-158">State</span></span>|<span data-ttu-id="95169-159">Zip</span><span class="sxs-lookup"><span data-stu-id="95169-159">Zip</span></span>|
    |------------------|----------|-----------|---------|
    |<span data-ttu-id="95169-160">1 Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="95169-160">1 Microsoft Way</span></span>|<span data-ttu-id="95169-161">Redmond</span><span class="sxs-lookup"><span data-stu-id="95169-161">Redmond</span></span>|<span data-ttu-id="95169-162">WA</span><span class="sxs-lookup"><span data-stu-id="95169-162">WA</span></span>|<span data-ttu-id="95169-163">98052</span><span class="sxs-lookup"><span data-stu-id="95169-163">98052</span></span>|
    |<span data-ttu-id="95169-164">PO Box 1</span><span class="sxs-lookup"><span data-stu-id="95169-164">PO Box 1</span></span>|<span data-ttu-id="95169-165">Redmond</span><span class="sxs-lookup"><span data-stu-id="95169-165">Redmond</span></span>|<span data-ttu-id="95169-166">WA</span><span class="sxs-lookup"><span data-stu-id="95169-166">WA</span></span>|<span data-ttu-id="95169-167">98073</span><span class="sxs-lookup"><span data-stu-id="95169-167">98073</span></span>|

     <span data-ttu-id="95169-168">![使用參考資料服務清理](../../2014/data-quality-services/media/dqs-rdscleansing.JPG "使用參考資料服務清理")</span><span class="sxs-lookup"><span data-stu-id="95169-168">![Cleansing using reference data service](../../2014/data-quality-services/media/dqs-rdscleansing.JPG "Cleansing using reference data service")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="95169-169">若為複合定義域，DQS 也會以不同的色彩反白顯示在電腦輔助清理處理序期間更正的個別定義域。</span><span class="sxs-lookup"><span data-stu-id="95169-169">For composite domains, DQS also highlights the individual domains in a different color that were corrected during the computer-assisted cleansing process.</span></span> <span data-ttu-id="95169-170">例如，此本例中， **[地址行]** 和 **[省/市]** 定義域已更正，因此會以青色反白顯示。</span><span class="sxs-lookup"><span data-stu-id="95169-170">For example, in this case, the **Address Line** and **State** domains were corrected, and therefore highlighted in cyan.</span></span>

5.  <span data-ttu-id="95169-171">完成所有定義域值的檢閱之後，請按 **[下一步]** 匯出資料。</span><span class="sxs-lookup"><span data-stu-id="95169-171">After you are done with reviewing all the domain values, click **Next** to export the data.</span></span>

6.  <span data-ttu-id="95169-172">在 **[匯出]** 頁面上，您將會發現除了有關每個定義域之清理活動的一般資訊 (來源、原因、信賴和狀態) 以外，還有 Melissa Data 參考資料服務針對地址資料所提供的其他資訊，例如地址的緯度和經度、國家/地區名稱、地址類型 (大樓、街道) 等等。</span><span class="sxs-lookup"><span data-stu-id="95169-172">On the **Export** page, you will notice that apart from the regular information about the cleansing activity for each domain (Source, Reason, Confidence, and Status), there is additional information provided by the Melissa Data reference data service about your address data, such as latitude and longitude of your address, county name, address type (highrise, street, etc.), and so on.</span></span>

7.  <span data-ttu-id="95169-173">將您的資料匯出至所需的目的地 (SQL Server、CSV 或 Excel)，然後按一下 **[完成]** 關閉專案。</span><span class="sxs-lookup"><span data-stu-id="95169-173">Export your data to the required destination (SQL Server, CSV, or Excel), and click **Finish** to close the project.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="95169-174">如果您要使用 64 位元版本的 Excel，就無法將清理的資料匯出到 Excel 檔案，只能匯出到 SQL Server 資料庫或 .csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="95169-174">If you are using 64-bit version of Excel, you cannot export the cleansed data to an Excel file; you can export only to a SQL Server database or to a .csv file.</span></span>


