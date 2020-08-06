---
title: 將定義域或複合定義域附加至參考資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.refdata.f1
- sql12.dqs.dm.refcatalog.f1
ms.assetid: 36af981c-d0d0-4dc6-afe5-bbb3c97845dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d54dcb01823253eeda92cc3a576d73a45de4ef7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592276"
---
# <a name="attach-a-domain-or-composite-domain-to-reference-data"></a><span data-ttu-id="a84e6-102">將定義域或複合定義域附加至參考資料</span><span class="sxs-lookup"><span data-stu-id="a84e6-102">Attach a Domain or Composite Domain to Reference Data</span></span>
  <span data-ttu-id="a84e6-103">本主題描述如何將資料品質知識庫中的定義域/複合定義域附加至 Azure Marketplace 中的參考資料服務，以針對高品質的參考資料建立知識。</span><span class="sxs-lookup"><span data-stu-id="a84e6-103">This topic describes how to attach domains/composite domains in a data quality knowledge base to a reference data service in Azure Marketplace to build knowledge against the high-quality reference data.</span></span> <span data-ttu-id="a84e6-104">每一項參考資料服務都包含結構描述 (資料行)。</span><span class="sxs-lookup"><span data-stu-id="a84e6-104">Each reference data service contains a schema (data columns).</span></span> <span data-ttu-id="a84e6-105">將定義域或複合定義域附加至參考資料服務之後，您必須將附加的複合定義域內的附加定義域或個別定義域對應至參考資料服務結構描述中的適當資料行。</span><span class="sxs-lookup"><span data-stu-id="a84e6-105">After attaching a domain or a composite domain to a reference data service, you must map the attached domain or the individual domains within the attached composite domain to the appropriate columns in a reference data service schema.</span></span> <span data-ttu-id="a84e6-106">將複合定義域附加至參考資料服務可讓您只將一個定義域附加至參考資料服務，然後將複合定義域中的個別定義域對應至參考資料服務結構描述中的適當資料行。</span><span class="sxs-lookup"><span data-stu-id="a84e6-106">Attaching a composite domain to a reference data service enables you to attach just one domain to a reference data service, and then map the individual domains within the composite domain to appropriate columns in the reference data service schema.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a84e6-107">附加至參考資料服務的複合定義域可在將定義域對應至參考資料服務中的資料行時，於定義域下拉式清單中使用。</span><span class="sxs-lookup"><span data-stu-id="a84e6-107">The composite domain attached to a reference data service is available in the domains drop-down list while mapping domains to the columns in the reference data service schema.</span></span> <span data-ttu-id="a84e6-108">不要將複合定義域對應至參考資料服務結構描述中的資料行；您必須只將複合定義域內的個別定義域對應至參考資料服務結構描述中的適當資料行。</span><span class="sxs-lookup"><span data-stu-id="a84e6-108">Do not map the composite domain to a column in the reference data service schema; you must only map individual domains within a composite domain to the appropriate columns in the reference data service schema.</span></span> <span data-ttu-id="a84e6-109">否則，它將會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="a84e6-109">Otherwise, it will result in an error.</span></span>  
  
 <span data-ttu-id="a84e6-110">參考資料服務結構描述可以擁有強制性資料行，假設您選擇使用此參考資料服務，該資料行必須與適當的定義域對應。</span><span class="sxs-lookup"><span data-stu-id="a84e6-110">A reference data service schema can have a mandatory column that must be mapped with appropriate domain should you choose to use the reference data service.</span></span> <span data-ttu-id="a84e6-111">參考資料結構描述中的強制性資料行會使用 "(M)" 來向資料行名稱識別。</span><span class="sxs-lookup"><span data-stu-id="a84e6-111">The mandatory column in a reference data schema is identified with "(M)" against the column name.</span></span> <span data-ttu-id="a84e6-112">例如，**AddressLine** 是 **Melissa Data - Address Data** 中的強制性結構描述資料行，而 **CompanyName** 是 **Digital Trowel Inc. - Us companies and professional data for SQL users**中的強制性結構描述資料行。</span><span class="sxs-lookup"><span data-stu-id="a84e6-112">For example, **AddressLine** is the mandatory schema column in **Melissa Data - Address Data** and **CompanyName** is the mandatory schema column in **Digital Trowel Inc. - Us companies and professional data for SQL users**.</span></span>  
  
 <span data-ttu-id="a84e6-113">本主題中，我們將建立四個定義域：[地址行]\*\*\*\*、[縣/市]\*\*\*\*、[州/省]\*\*\*\* 和 [郵遞區號]\*\*\*\*，在複合定義域 [地址驗證]\*\*\*\* 下，將複合定義域附加至 **Melissa Data - Address Check** 參考資料服務，然後將複合定義域內的個別定義域對應至參考資料服務結構描述中適當的資料行。</span><span class="sxs-lookup"><span data-stu-id="a84e6-113">In this topic, we will create four domains: **Address Line**, **City**, **State**, and **Zip**, under a composite domain, **Address Verification**, attach the composite domain to the **Melissa Data - Address Check** reference data service, and then map the individual domains within the composite domain to appropriate columns in the reference data service schema.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="a84e6-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="a84e6-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="a84e6-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="a84e6-115">Prerequisites</span></span>  
 <span data-ttu-id="a84e6-116">您必須已設定 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS)，才能使用參考資料服務。</span><span class="sxs-lookup"><span data-stu-id="a84e6-116">You must have configured [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) to use reference data services.</span></span> <span data-ttu-id="a84e6-117">請參閱[設定 DQS 使用參考資料](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a84e6-117">See [Configure DQS to Use Reference Data](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a84e6-118">Security</span><span class="sxs-lookup"><span data-stu-id="a84e6-118">Security</span></span>  
  
#### <a name="permissions"></a><span data-ttu-id="a84e6-119">權限</span><span class="sxs-lookup"><span data-stu-id="a84e6-119">Permissions</span></span>  
 <span data-ttu-id="a84e6-120">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 角色，才能將定義域對應至參考資料。</span><span class="sxs-lookup"><span data-stu-id="a84e6-120">You must have the dqs_kb_editor role on the DQS_MAIN database to map domains to reference data.</span></span>  
  
##  <a name="map-domains-to-reference-data-from-melissa-data"></a><a name="Map"></a><span data-ttu-id="a84e6-121">將定義域對應至 Melissa 資料中的參考資料</span><span class="sxs-lookup"><span data-stu-id="a84e6-121">Map domains to reference data from Melissa Data</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="a84e6-122">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a84e6-122">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="a84e6-123">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面的 **[知識庫管理]** 底下，按一下 **[新增知識庫]**。</span><span class="sxs-lookup"><span data-stu-id="a84e6-123">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, under **Knowledge Base Management**, click **New knowledge base**.</span></span>  
  
3.  <span data-ttu-id="a84e6-124">在 **[新增知識庫]** 畫面中，輸入新知識庫的名稱，並按一下 **[定義域管理]** 活動，然後按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="a84e6-124">In the **New knowledge base** screen, type a name for the new knowledge base, click the **Domain Management** activity, and click **Create**.</span></span>  
  
4.  <span data-ttu-id="a84e6-125">在 **[定義域管理]** 畫面中，按一下 **[建立定義域]** 圖示建立定義域。</span><span class="sxs-lookup"><span data-stu-id="a84e6-125">In the **Domain Management** screen, click the **Create a domain** icon to create a domain.</span></span> <span data-ttu-id="a84e6-126">建立以下四個定義域： **[地址行]**、 **[縣/市]**、 **[省/市]** 和 **[郵遞區號]**。</span><span class="sxs-lookup"><span data-stu-id="a84e6-126">Create the following four domains: **Address Line**, **City**, **State**, and **Zip**.</span></span>  
  
5.  <span data-ttu-id="a84e6-127">按一下 **[建立複合定義域]** 圖示，建立複合定義域。</span><span class="sxs-lookup"><span data-stu-id="a84e6-127">Click the **Create a composite domain** icon to create a composite domain.</span></span> <span data-ttu-id="a84e6-128">在 **[建立複合定義域]** 對話方塊中，於 **[複合定義域名稱]** 方塊中輸入 **地址驗證** ，並在複合定義域中包含步驟 3 所建立的所有定義域。</span><span class="sxs-lookup"><span data-stu-id="a84e6-128">In the **Create a composite domain** dialog box, type **Address Verification** in the **Composite Domain Name** box, and include all the domains created in step 3 in the composite domain.</span></span> <span data-ttu-id="a84e6-129">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="a84e6-129">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="a84e6-130">在左邊的 **[定義域]** 窗格中選取複合定義域，方法是按一下 **[地址驗證]**，然後按一下右邊的 **[參考資料]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a84e6-130">In the **Domain** pane on the left side, select the composite domain by clicking **Address Verification**, and then click the **Reference Data** tab on the right side.</span></span>  
  
7.  <span data-ttu-id="a84e6-131">按一下 **[瀏覽]** 圖示。</span><span class="sxs-lookup"><span data-stu-id="a84e6-131">Click the **Browse** icon.</span></span>  
  
8.  <span data-ttu-id="a84e6-132">在 **[線上參考資料提供者目錄]** 對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="a84e6-132">In the **Online Reference Data Providers Catalog** dialog box:</span></span>  
  
    1.  <span data-ttu-id="a84e6-133">在 [DataMarket Data Quality Services]\*\*\*\* 底下，選取 [Melissa Data - 地址檢查]\*\*\*\* 方塊。</span><span class="sxs-lookup"><span data-stu-id="a84e6-133">Under **DataMarket Data Quality Services**, select the **Melissa Data - Address Check** box.</span></span>  
  
    2.  <span data-ttu-id="a84e6-134">將 [Melissa Data - Address Check] 參考資料服務與適當的定義域 ([地址行]、[縣/市]、[州/省] 和 [郵遞區號]) 相對應。</span><span class="sxs-lookup"><span data-stu-id="a84e6-134">Map the columns of the Melissa Data - Address Check reference data service with the appropriate domains (Address Line, City, State, and Zip).</span></span> <span data-ttu-id="a84e6-135">若要對應資料行，請在 **[RDS 結構描述]** 資料行中選取參考資料服務資料行，然後在 **[定義域]** 資料行中選取適當的定義域。</span><span class="sxs-lookup"><span data-stu-id="a84e6-135">You map the columns by selecting a reference data service column in the **RDS Schema** column, and then selecting the appropriate domain in the **Domain** column.</span></span> <span data-ttu-id="a84e6-136">若要在資料表中加入其他資料列，請按一下 **[加入結構描述項目]** 圖示。</span><span class="sxs-lookup"><span data-stu-id="a84e6-136">To add more rows in the table, click the **Add Schema Entry** icon.</span></span>  
  
    3.  <span data-ttu-id="a84e6-137">按一下 **[確定]** 儲存變更，並關閉 **[線上參考資料提供者目錄]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a84e6-137">Click **OK** to save the changes, and close the **Online Reference Data Providers Catalog** dialog box.</span></span>  
  
         <span data-ttu-id="a84e6-138">![線上參考資料提供者目錄對話方塊](../../2014/data-quality-services/media/dqs-onlinereferencedataproviderscatalog.gif "線上參考資料提供者目錄對話方塊")</span><span class="sxs-lookup"><span data-stu-id="a84e6-138">![Online Reference Data Providers Catalog dialog box](../../2014/data-quality-services/media/dqs-onlinereferencedataproviderscatalog.gif "Online Reference Data Providers Catalog dialog box")</span></span>  
  
        > [!NOTE]  
        >  -   <span data-ttu-id="a84e6-139">在 [**線上參考資料提供者目錄**] 對話方塊中，[ **DataMarket data Quality Services** ] 節點會顯示您在 Azure Marketplace 中訂閱的所有參考資料服務提供者。</span><span class="sxs-lookup"><span data-stu-id="a84e6-139">In the **Online Reference Data Providers Catalog** dialog box, the **DataMarket Data Quality Services** node displays all the reference data service providers that you have subscribed to in Azure Marketplace.</span></span> <span data-ttu-id="a84e6-140">如果您已在 DQS 中設定直接線上協力廠商參考資料服務提供者，這些提供者會出現在稱為 **[協力廠商直接上線提供者]** 的另一個節點底下 (現在不會出現這個節點，因為 DQS 中尚未設定直接線上協力廠商參考資料服務提供者)。</span><span class="sxs-lookup"><span data-stu-id="a84e6-140">If you have configured direct online third-party reference data service providers in DQS, they will appear under another node called **3rd Party Direct Online Providers** (not available now as no direct online third-party reference data service providers are configured in DQS).</span></span>  
  
9. <span data-ttu-id="a84e6-141">您將回到 [**參考資料**] 索引標籤。在 [**提供者設定**] 區域中，視需要變更下列方塊中的值：</span><span class="sxs-lookup"><span data-stu-id="a84e6-141">You will return to the **Reference Data** tab. In the **Provider Settings** area, change values in the following boxes, if required:</span></span>  
  
    -   <span data-ttu-id="a84e6-142">**自動校正臨界值**：如果參考資料服務提供之更正的信賴等級高於這個臨界值，將會自動執行更正。</span><span class="sxs-lookup"><span data-stu-id="a84e6-142">**Auto Correction Threshold**: Corrections from reference data service with confidence level above this threshold values will be automatically done.</span></span> <span data-ttu-id="a84e6-143">請使用對應百分比值的十進位表示法來輸入值。</span><span class="sxs-lookup"><span data-stu-id="a84e6-143">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="a84e6-144">例如，輸入 0.9 表示 90%。</span><span class="sxs-lookup"><span data-stu-id="a84e6-144">For example, enter 0.9 for 90%.</span></span>  
  
    -   <span data-ttu-id="a84e6-145">**建議的候選值**：要從參考資料服務中顯示的建議候選值數目。</span><span class="sxs-lookup"><span data-stu-id="a84e6-145">**Suggested Candidates**: Number of suggested candidates to display from the reference data service.</span></span>  
  
    -   <span data-ttu-id="a84e6-146">**最低信賴值**：如果參考資料服務提供之建議的信賴等級低於這個值，將會予以忽略。</span><span class="sxs-lookup"><span data-stu-id="a84e6-146">**Min Confidence**: Suggestions from reference data service with confidence level lower than this value will be ignored.</span></span> <span data-ttu-id="a84e6-147">請使用對應百分比值的十進位表示法來輸入值。</span><span class="sxs-lookup"><span data-stu-id="a84e6-147">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="a84e6-148">例如，輸入 0.6 表示 60%。</span><span class="sxs-lookup"><span data-stu-id="a84e6-148">For example, enter 0.6 for 60%.</span></span>  
  
10. <span data-ttu-id="a84e6-149">按一下 **[完成]** ，發行知識庫。</span><span class="sxs-lookup"><span data-stu-id="a84e6-149">Click **Finish** to publish the knowledge base.</span></span> <span data-ttu-id="a84e6-150">在成功發行知識庫之後，便會出現確認訊息。</span><span class="sxs-lookup"><span data-stu-id="a84e6-150">A confirmation message appears after the knowledge base is published successfully.</span></span>  
  
 <span data-ttu-id="a84e6-151">您現在可以將此知識庫用於資料品質專案中的清理活動，根據透過 Azure Marketplace Melissa 資料所提供的知識，在來源資料中標準化和清理美國位址。</span><span class="sxs-lookup"><span data-stu-id="a84e6-151">You can now use this knowledge base for cleansing activity in a data quality project to standardize and cleanse US addresses in your source data based on the knowledge provided by Melissa Data through Azure Marketplace.</span></span>  
  
##  <a name="follow-up-after-mapping-a-domain-to-reference-data"></a><a name="FollowUp"></a> <span data-ttu-id="a84e6-152">後續操作：將定義域對應至參考資料之後</span><span class="sxs-lookup"><span data-stu-id="a84e6-152">Follow Up: After Mapping a Domain to Reference Data</span></span>  
 <span data-ttu-id="a84e6-153">建立資料品質專案，並針對包含美國地址的來源資料執行清理活動，方法是將它與本主題建立的知識庫相比較。</span><span class="sxs-lookup"><span data-stu-id="a84e6-153">Create a data quality project, and run the cleansing activity on your source data containing US addresses by comparing it against the knowledge base created in this topic.</span></span> <span data-ttu-id="a84e6-154">請參閱[使用參考資料 &#40;外部&#41; 知識清理資料](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md)。</span><span class="sxs-lookup"><span data-stu-id="a84e6-154">See [Cleanse Data Using Reference Data &#40;External&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a84e6-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a84e6-155">See Also</span></span>  
 <span data-ttu-id="a84e6-156">[DQS 中的參考資料服務](../../2014/data-quality-services/reference-data-services-in-dqs.md) </span><span class="sxs-lookup"><span data-stu-id="a84e6-156">[Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md) </span></span>  
 [<span data-ttu-id="a84e6-157">資料清理</span><span class="sxs-lookup"><span data-stu-id="a84e6-157">Data Cleansing</span></span>](../../2014/data-quality-services/data-cleansing.md)  
  
  
