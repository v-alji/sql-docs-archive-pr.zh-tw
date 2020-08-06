---
title: 從 (SSAS 表格式) 的資料摘要匯入 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0686e519-67c2-4f9b-8cd2-84a4871499ee
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7e5446effdcd01a3fe0eeb5dd14a1a61e97c417b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606478"
---
# <a name="import-from-a-data-feed-ssas-tabular"></a><span data-ttu-id="d854d-102">從資料摘要匯入 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="d854d-102">Import from a Data Feed (SSAS Tabular)</span></span>
  <span data-ttu-id="d854d-103">資料摘要是從線上資料來源產生並串流至目的地文件或應用程式的一個或多個 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="d854d-103">Data feeds are one or more XML data streams that are generated from an online data source and streamed to a destination document or application.</span></span> <span data-ttu-id="d854d-104">您可以使用 [資料表匯入精靈]，將資料從資料摘要匯入模型。</span><span class="sxs-lookup"><span data-stu-id="d854d-104">You can import data from a data feed into your model by using the Table Import Wizard.</span></span>  
  
 <span data-ttu-id="d854d-105">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="d854d-105">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="d854d-106">了解從資料摘要匯入</span><span class="sxs-lookup"><span data-stu-id="d854d-106">Understanding import from a data feed</span></span>](#prereq)  
  
-   [<span data-ttu-id="d854d-107">從 Azure DataMarket 資料集匯入資料</span><span class="sxs-lookup"><span data-stu-id="d854d-107">Import data from an Azure DataMarket dataset</span></span>](#azure)  
  
-   [<span data-ttu-id="d854d-108">從公用或公司資料來源匯入資料摘要</span><span class="sxs-lookup"><span data-stu-id="d854d-108">Import data feeds from public or corporate data sources</span></span>](#importdata)  
  
-   [<span data-ttu-id="d854d-109">從 SharePoint 清單匯入資料摘要</span><span class="sxs-lookup"><span data-stu-id="d854d-109">Import data feeds from SharePoint lists</span></span>](#importlist)  
  
-   [<span data-ttu-id="d854d-110">從 Reporting Services 報表匯入資料摘要</span><span class="sxs-lookup"><span data-stu-id="d854d-110">Import data feeds from Reporting Services Reports</span></span>](#importreport)  
  
##  <a name="understanding-import-from-a-data-feed"></a><a name="prereq"></a><span data-ttu-id="d854d-111">瞭解從資料摘要匯入</span><span class="sxs-lookup"><span data-stu-id="d854d-111">Understanding import from a data feed</span></span>  
 <span data-ttu-id="d854d-112">您可以從下列類型的資料摘要，將資料匯入表格式模型：</span><span class="sxs-lookup"><span data-stu-id="d854d-112">You can import data into a Tabular Model from the following types of data feeds:</span></span>  
  
 <span data-ttu-id="d854d-113">**Reporting Services 報表**</span><span class="sxs-lookup"><span data-stu-id="d854d-113">**Reporting Services Report**</span></span>  
 <span data-ttu-id="d854d-114">您可以使用已經發行到 SharePoint 網站或報表伺服器的 Reporting Services 報表，做為模型中的資料來源。</span><span class="sxs-lookup"><span data-stu-id="d854d-114">You can use a Reporting Services report that has been published to a SharePoint site or a report server as a data source in a model.</span></span> <span data-ttu-id="d854d-115">從 Reporting Services 報表匯入資料時，您必須指定一個報表定義 (.rdl) 檔案做為資料來源。</span><span class="sxs-lookup"><span data-stu-id="d854d-115">When importing data from a Reporting Services Report, you must specify a report definition (.rdl) file as a data source.</span></span>  
  
 <span data-ttu-id="d854d-116">**Azure DataMarket 資料集**</span><span class="sxs-lookup"><span data-stu-id="d854d-116">**Azure DataMarket Dataset**</span></span>  
 <span data-ttu-id="d854d-117">Azure DataMarket 是一種提供單一服務商場及資訊傳遞通道 (如雲端服務) 的服務。</span><span class="sxs-lookup"><span data-stu-id="d854d-117">Azure DataMarket is a service that provides a single marketplace and delivery channel for information as cloud services.</span></span> <span data-ttu-id="d854d-118">Azure DataMarket 資料集需要的是帳號金鑰，而不是 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d854d-118">Azure DataMarket datasets require an account key instead of a Windows user account.</span></span>  
  
 <span data-ttu-id="d854d-119">**Atom 摘要**</span><span class="sxs-lookup"><span data-stu-id="d854d-119">**Atom feeds**</span></span>  
 <span data-ttu-id="d854d-120">摘要必須是 Atom 摘要，</span><span class="sxs-lookup"><span data-stu-id="d854d-120">The feed must be an Atom feed.</span></span> <span data-ttu-id="d854d-121">不支援 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="d854d-121">RSS feeds are not supported.</span></span> <span data-ttu-id="d854d-122">摘要必須是可公開使用，或者您必須擁有權限可以使用目前登入的 Windows 帳戶連接到該摘要。</span><span class="sxs-lookup"><span data-stu-id="d854d-122">The feed must either be publicly available or you must have permission to connect to it under the Windows account with which you are currently logged in.</span></span>  
  
 <span data-ttu-id="d854d-123">在匯入期間，資料摘要的資料只會加入模型一次。</span><span class="sxs-lookup"><span data-stu-id="d854d-123">Data from a data feed is added into a model once during import.</span></span> <span data-ttu-id="d854d-124">若要從摘要取得已更新的資料，您可從模型設計師重新整理資料，或者在將模型部署到 Analysis Services 的實際執行個體之後，為模型設定資料重新整理排程。</span><span class="sxs-lookup"><span data-stu-id="d854d-124">To get updated data from the feed, you can either refresh the data from the model designer, or configure a data refresh schedule for the model after it is deployed to a production instance of Analysis Services.</span></span> <span data-ttu-id="d854d-125">如需詳細資訊，請參閱 [處理資料 &#40;SSAS 表格式&#41;](process-data-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="d854d-125">For more information, see [Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md).</span></span>  
  
##  <a name="import-data-from-an-azure-datamarket-dataset"></a><a name="azure"></a><span data-ttu-id="d854d-126">從 Azure DataMarket 資料集匯入資料</span><span class="sxs-lookup"><span data-stu-id="d854d-126">Import data from an Azure DataMarket dataset</span></span>  
 <span data-ttu-id="d854d-127">您可以從 Azure DataMarket 匯入資料做為模型中的資料表。</span><span class="sxs-lookup"><span data-stu-id="d854d-127">You can import data from an Azure DataMarket as a table in your model.</span></span>  
  
#### <a name="to-import-data-from-an-azure-datamarket-dataset"></a><span data-ttu-id="d854d-128">從 Azure DataMarket 資料集匯入資料</span><span class="sxs-lookup"><span data-stu-id="d854d-128">To import data from an Azure DataMarket dataset</span></span>  
  
1.  <span data-ttu-id="d854d-129">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-129">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span> <span data-ttu-id="d854d-130">[資料表匯入精靈] 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d854d-130">The Table Import Wizard opens.</span></span>  
  
2.  <span data-ttu-id="d854d-131">在 **[連接到資料來源]** 頁面上，選取 **[資料摘要]** 底下的 **[Azure DataMarket 資料集]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-131">On the **Connect to a Data Source** page, under **Data Feeds**, select **Azure DataMarket Dataset**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="d854d-132">在 **[連接到 Azure DataMarket 資料集]** 頁面的 **[易記名稱]** 中，輸入所要存取之摘要的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="d854d-132">On the **Connect to an Azure DataMarket dataset** page, in **Friendly Name**, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="d854d-133">如果您要匯入多個摘要或資料來源，使用連接描述性名稱可有助於記住連接的使用方式。</span><span class="sxs-lookup"><span data-stu-id="d854d-133">If you are importing multiple feeds or data sources, using descriptive names for the connection can help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="d854d-134">在 **[資料摘要 URL]** 中，輸入資料摘要的位址。</span><span class="sxs-lookup"><span data-stu-id="d854d-134">In **Data Feed URL**, type the address for the data feed.</span></span>  
  
5.  <span data-ttu-id="d854d-135">在 **[安全性設定]** 的 **[帳號金鑰]** 中，輸入帳號金鑰。</span><span class="sxs-lookup"><span data-stu-id="d854d-135">In **Security Settings**, in **Account Key**, type an account key.</span></span> <span data-ttu-id="d854d-136">Analysis Services 會使用帳號金鑰來存取 DataMarket 訂閱。</span><span class="sxs-lookup"><span data-stu-id="d854d-136">Account keys are used by Analysis Services to access the DataMarket subscriptions.</span></span>  
  
6.  <span data-ttu-id="d854d-137">按一下 **[測試連接]** 確認可以使用摘要。</span><span class="sxs-lookup"><span data-stu-id="d854d-137">Click **Test Connection** to make sure the feed is available.</span></span> <span data-ttu-id="d854d-138">或者，您也可以按一下 **[進階]** ，以確認「基礎 URL」或「服務文件 URL」包含提供摘要的查詢或服務文件。</span><span class="sxs-lookup"><span data-stu-id="d854d-138">Alternatively, you can also click **Advanced** to confirm that the Base URL or Service Document URL contains the query or service document that provides the feed.</span></span>  
  
7.  <span data-ttu-id="d854d-139">按 **[下一步]** 繼續執行匯入作業。</span><span class="sxs-lookup"><span data-stu-id="d854d-139">Click **Next** to continue with the import.</span></span>  
  
8.  <span data-ttu-id="d854d-140">在 **[模擬資訊]** 頁面中，指定 Analysis Services 在重新整理資料時將用來連接資料來源的憑證，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-140">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span> <span data-ttu-id="d854d-141">這些憑證和帳號金鑰不同。</span><span class="sxs-lookup"><span data-stu-id="d854d-141">These credentials are different from the Account Key.</span></span>  
  
9. <span data-ttu-id="d854d-142">在精靈的 **[選取資料表和檢視表]** 頁面中，在 **[易記名稱]** 欄位輸入描述性名稱，讓該名稱指出匯入之後將包含此資料的資料表以便於識別。</span><span class="sxs-lookup"><span data-stu-id="d854d-142">In the **Select Tables and Views** page of the wizard, in the **Friendly Name** field, type a descriptive name that identifies the table that will contain this data after it is imported</span></span>  
  
10. <span data-ttu-id="d854d-143">按一下 **[預覽和篩選]** 來檢閱資料和變更資料行選取項目。</span><span class="sxs-lookup"><span data-stu-id="d854d-143">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="d854d-144">您不能限制匯入報表資料摘要中的資料列，但是可以藉由清除核取方塊移除資料行。</span><span class="sxs-lookup"><span data-stu-id="d854d-144">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="d854d-145">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d854d-145">Click **OK**.</span></span>  
  
11. <span data-ttu-id="d854d-146">在 **[選取資料表和檢視表]** 頁面中，按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-146">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
##  <a name="import-data-feeds-from-public-or-corporate-data-sources"></a><a name="importdata"></a><span data-ttu-id="d854d-147">從公用或公司資料來源匯入資料摘要</span><span class="sxs-lookup"><span data-stu-id="d854d-147">Import data feeds from public or corporate data sources</span></span>  
 <span data-ttu-id="d854d-148">您可以存取公用摘要，或建立自訂摘要服務，從專屬或舊版資料庫系統產生 Atom 摘要。</span><span class="sxs-lookup"><span data-stu-id="d854d-148">You can access public feeds or build custom data services that generate Atom feeds from proprietary or legacy database systems.</span></span>  
  
#### <a name="to-import-data-from-public-or-corporate-data-feeds"></a><span data-ttu-id="d854d-149">從公用或公司資料摘要匯入資料</span><span class="sxs-lookup"><span data-stu-id="d854d-149">To import data from public or corporate data feeds</span></span>  
  
1.  <span data-ttu-id="d854d-150">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-150">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span> <span data-ttu-id="d854d-151">[資料表匯入精靈] 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d854d-151">The Table Import Wizard opens.</span></span>  
  
2.  <span data-ttu-id="d854d-152">在 **[連接到資料來源]** 頁面上，選取 **[資料摘要]** 底下的 **[其他摘要]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-152">On the **Connect to a Data Source** page, under **Data Feeds**, select **Other Feeds**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="d854d-153">在 **[連接到資料摘要]** 頁面中，輸入所要存取之摘要的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="d854d-153">On the **Connect to a Data Feed** page, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="d854d-154">如果您要匯入多個摘要或資料來源，使用連接描述性名稱可有助於記住連接的使用方式。</span><span class="sxs-lookup"><span data-stu-id="d854d-154">If you are importing multiple feeds or data sources, using descriptive names for the connection can help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="d854d-155">在 **[資料摘要 URL]** 中，輸入資料摘要的位址。</span><span class="sxs-lookup"><span data-stu-id="d854d-155">In **Data Feed URL**, type the address for the data feed.</span></span> <span data-ttu-id="d854d-156">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="d854d-156">Valid values include the following:</span></span>  
  
    1.  <span data-ttu-id="d854d-157">包含 Atom 資料的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="d854d-157">An XML document that contains the Atom data.</span></span> <span data-ttu-id="d854d-158">例如，下列 URL 會指向 Open Government Data Initiative 網站上的公用摘要：</span><span class="sxs-lookup"><span data-stu-id="d854d-158">For example, the following URL points to a public feed on the Open Government Data Initiative web site:</span></span>  
  
        ```  
        http://ogdi.cloudapp.net/v1/dc/banklocations/  
        ```  
  
    2.  <span data-ttu-id="d854d-159">指定一個或多個摘要的 .atomsvc 文件。</span><span class="sxs-lookup"><span data-stu-id="d854d-159">An .atomsvc document that specifies one or more feeds.</span></span> <span data-ttu-id="d854d-160">.atomsvc 文件會指向提供一個或多個摘要的服務或應用程式。</span><span class="sxs-lookup"><span data-stu-id="d854d-160">An .atomsvc document points to a service or application that provides one or more feeds.</span></span> <span data-ttu-id="d854d-161">每個摘要都指定為傳回結果集的基本查詢。</span><span class="sxs-lookup"><span data-stu-id="d854d-161">Each feed is specified as a base query that returns the result set.</span></span>  
  
         <span data-ttu-id="d854d-162">您可以指定位於 Web 伺服器上之 .atomsvc 文件的 URL 位址，也可以從電腦上的共用或本機資料夾開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="d854d-162">You can specify a URL address to an .atomsvc document that is on a web server or you can open the file from a shared or local folder on your computer.</span></span> <span data-ttu-id="d854d-163">如果在匯出 Reporting Services 報表時，曾經儲存一份 .atomsvc 文件至電腦中，您即會有一份該文件；或者，如果有人曾為您的 SharePoint 網站建立了資料摘要文件庫，那麼在該文件庫中就可能有多份 .atomsvc 文件。</span><span class="sxs-lookup"><span data-stu-id="d854d-163">You might have an .atomsvc document if you saved one to your computer while exporting a Reporting Services report, or you might have .atomsvc documents in a data feed library that someone created for your SharePoint site.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d854d-164">建議您指定可以透過 URL 位址或共用資料夾存取的 .atomsvc 文件，因為這樣可以讓您在將來，將活頁簿發行至 SharePoint 之後，為活頁簿設定自動資料重新整理。</span><span class="sxs-lookup"><span data-stu-id="d854d-164">Specifying an .atomsvc document that can be accessed through a URL address or shared folder is recommended because it gives you the option of configuring automatic data refresh for the workbook later, after the workbook is published to SharePoint.</span></span> <span data-ttu-id="d854d-165">如果您指定的不是位於您電腦上的本機位置，伺服器可以重複使用相同的 URL 位址或網路資料夾以重新整理資料。</span><span class="sxs-lookup"><span data-stu-id="d854d-165">The server can re-use the same URL address or network folder to refresh data if you specify a location that is not local to your computer.</span></span>  
  
5.  <span data-ttu-id="d854d-166">按一下 **[測試連接]** 確認可以使用摘要。</span><span class="sxs-lookup"><span data-stu-id="d854d-166">Click **Test Connection** to make sure the feed is available.</span></span> <span data-ttu-id="d854d-167">或者，您也可以按一下 **[進階]** ，以確認「基礎 URL」或「服務文件 URL」包含提供摘要的查詢或服務文件。</span><span class="sxs-lookup"><span data-stu-id="d854d-167">Alternatively, you can also click **Advanced** to confirm that the Base URL or Service Document URL contains the query or service document that provides the feed.</span></span>  
  
6.  <span data-ttu-id="d854d-168">按 **[下一步]** 繼續執行匯入作業。</span><span class="sxs-lookup"><span data-stu-id="d854d-168">Click **Next** to continue with the import.</span></span>  
  
7.  <span data-ttu-id="d854d-169">在 **[模擬資訊]** 頁面中，指定 Analysis Services 在重新整理資料時將用來連接資料來源的憑證，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-169">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="d854d-170">在精靈的 **[選取資料表和檢視表]** 頁面中，以描述性名稱取代 **[易記名稱]** 欄位中的「資料摘要內容」，讓該名稱指出匯入之後將包含此資料的資料表以便於識別。</span><span class="sxs-lookup"><span data-stu-id="d854d-170">In the **Select Tables and Views** page of the wizard, in the **Friendly Name** field, replace Data Feed Content with a descriptive name that identifies the table that will contain this data after it is imported</span></span>  
  
9. <span data-ttu-id="d854d-171">按一下 **[預覽和篩選]** 來檢閱資料和變更資料行選取項目。</span><span class="sxs-lookup"><span data-stu-id="d854d-171">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="d854d-172">您不能限制匯入報表資料摘要中的資料列，但是可以藉由清除核取方塊移除資料行。</span><span class="sxs-lookup"><span data-stu-id="d854d-172">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="d854d-173">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d854d-173">Click **OK**.</span></span>  
  
10. <span data-ttu-id="d854d-174">在 **[選取資料表和檢視表]** 頁面中，按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-174">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
##  <a name="import-data-feeds-from-sharepoint-lists"></a><a name="importlist"></a><span data-ttu-id="d854d-175">從 SharePoint 清單匯入資料摘要</span><span class="sxs-lookup"><span data-stu-id="d854d-175">Import data feeds from SharePoint lists</span></span>  
 <span data-ttu-id="d854d-176">您可以匯入 (SharePoint) 功能區上有 [匯出為資料摘要]\*\*\*\* 按鈕的任何 SharePoint 清單。</span><span class="sxs-lookup"><span data-stu-id="d854d-176">You can import any SharePoint list that has an **Export as Data Feed** button on the (SharePoint) ribbon.</span></span> <span data-ttu-id="d854d-177">您可以按一下此按鈕，將清單匯出為摘要。</span><span class="sxs-lookup"><span data-stu-id="d854d-177">You can click this button to export the list as a feed.</span></span>  
  
#### <a name="to-import-data-feeds-from-a-sharepoint-list"></a><span data-ttu-id="d854d-178">從 SharePoint 清單匯入資料摘要</span><span class="sxs-lookup"><span data-stu-id="d854d-178">To import data feeds from a SharePoint list</span></span>  
  
1.  <span data-ttu-id="d854d-179">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-179">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="d854d-180">在 **[連接到資料來源]** 頁面上，選取 **[資料摘要]** 底下的 **[其他資料摘要]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-180">On the **Connect to a Data Source** page, under **Data Feeds**, select **Other Data Feeds**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="d854d-181">在 **[連接到資料摘要]** 頁面中，輸入所要存取之摘要的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="d854d-181">On the **Connect to a Data Feed** page, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="d854d-182">如果您要匯入多個摘要或資料來源，使用連接描述性名稱可能有助於記住連接的使用方式。</span><span class="sxs-lookup"><span data-stu-id="d854d-182">If you are importing multiple feeds or data sources, using descriptive names for the connection might help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="d854d-183">在 [資料摘要 URL] 中，輸入清單資料服務的位址， \<server-name> 並以 SharePoint 伺服器的實際名稱取代：</span><span class="sxs-lookup"><span data-stu-id="d854d-183">In Data Feed URL, type an address to the list data service, replacing \<server-name> with the actual name of your SharePoint server:</span></span>  
  
    ```  
    http://<server-name>/_vti_bin/listdata.svc  
    ```  
  
5.  <span data-ttu-id="d854d-184">按一下 **[測試連接]** 確認可以使用摘要。</span><span class="sxs-lookup"><span data-stu-id="d854d-184">Click **Test Connection** to make sure the feed is available.</span></span> <span data-ttu-id="d854d-185">或者，您也可以按一下 **[進階]** ，以確認「服務文件 URL」包含清單資料服務的位址。</span><span class="sxs-lookup"><span data-stu-id="d854d-185">Alternatively, you can also click **Advanced** to confirm that the Service Document URL contains an address to the list data service.</span></span>  
  
6.  <span data-ttu-id="d854d-186">按 **[下一步]** 繼續執行匯入作業。</span><span class="sxs-lookup"><span data-stu-id="d854d-186">Click **Next** to continue with the import.</span></span>  
  
7.  <span data-ttu-id="d854d-187">在 **[模擬資訊]** 頁面中，指定 Analysis Services 在重新整理資料時將用來連接資料來源的憑證，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-187">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="d854d-188">在精靈的 **[選取資料表和檢視表]** 頁面中，選取您要匯入的清單。</span><span class="sxs-lookup"><span data-stu-id="d854d-188">In the **Select Tables and Views** page of the wizard, select the lists you want to import.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d854d-189">您只能匯入包含資料行的清單。</span><span class="sxs-lookup"><span data-stu-id="d854d-189">You can only import lists that contain columns.</span></span>  
  
9. <span data-ttu-id="d854d-190">按一下 **[預覽和篩選]** 來檢閱資料和變更資料行選取項目。</span><span class="sxs-lookup"><span data-stu-id="d854d-190">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="d854d-191">您不能限制匯入報表資料摘要中的資料列，但是可以藉由清除核取方塊移除資料行。</span><span class="sxs-lookup"><span data-stu-id="d854d-191">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="d854d-192">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d854d-192">Click **OK**.</span></span>  
  
10. <span data-ttu-id="d854d-193">在 **[選取資料表和檢視表]** 頁面中，按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-193">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
##  <a name="import-data-feeds-from-reporting-services-reports"></a><a name="importreport"></a><span data-ttu-id="d854d-194">從 Reporting Services 報表匯入資料摘要</span><span class="sxs-lookup"><span data-stu-id="d854d-194">Import data feeds from Reporting Services Reports</span></span>  
 <span data-ttu-id="d854d-195">如果您具備 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Reporting Services 部署，則可以使用 Atom 轉譯延伸模組，從現有的報表中產生資料摘要。</span><span class="sxs-lookup"><span data-stu-id="d854d-195">If you have a deployment of [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Reporting Services, you can use the Atom rendering extension to generate a data feed from an existing report.</span></span>  
  
#### <a name="to-import-report-data-from-a-published-reporting-services-report"></a><span data-ttu-id="d854d-196">從已發行的 Reporting Services 報表匯入報表資料</span><span class="sxs-lookup"><span data-stu-id="d854d-196">To import report data from a published Reporting Services report</span></span>  
  
1.  <span data-ttu-id="d854d-197">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-197">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="d854d-198">在 **[連接到資料來源]** 頁面上，選取 **[資料摘要]** 底下的 **[報表]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-198">On the **Connect to a Data Source** page, under **Data Feeds**, select **Report**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="d854d-199">在 [連接到 Microsoft SQL Server Reporting Services 報表] 頁面的 [易記連接名稱] 中，輸入所要存取之摘要的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="d854d-199">On the Connect to a Microsoft SQL Server Reporting Services Report page, in Friendly Connection Name, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="d854d-200">如果您要匯入多個資料來源，使用連接的描述性名稱可能有助於記住連接的使用方式。</span><span class="sxs-lookup"><span data-stu-id="d854d-200">If you are importing multiple data sources, using descriptive names for the connection might help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="d854d-201">按一下 **[瀏覽]** 以選取報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="d854d-201">Click **Browse** and select a report server.</span></span>  
  
     <span data-ttu-id="d854d-202">如果您定期使用報表伺服器上的報表，該伺服器可能會列在 **[最近使用的網站和伺服器]** 中。</span><span class="sxs-lookup"><span data-stu-id="d854d-202">If you regularly use reports on a report server, the server might be listed in **Recent Sites and Servers**.</span></span> <span data-ttu-id="d854d-203">否則，在 [名稱] 中輸入報表伺服器的位址，然後按一下 **[開啟]** 來瀏覽報表伺服器網站上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d854d-203">Otherwise, in Name, type an address to a report server and click **Open** to browse the folders on the report server site.</span></span> <span data-ttu-id="d854d-204">報表伺服器的範例位址可能是 HTTP:// \<computername> /reportserver。</span><span class="sxs-lookup"><span data-stu-id="d854d-204">An example address for a report server might be http://\<computername>/reportserver.</span></span>  
  
5.  <span data-ttu-id="d854d-205">選取報表，並按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-205">Select the report and click **Open**.</span></span> <span data-ttu-id="d854d-206">或者，您可以在 **[名稱]** 文字方塊中貼上報表的連結，包括完整的路徑和報表名稱。</span><span class="sxs-lookup"><span data-stu-id="d854d-206">Alternatively, you can paste a link to the report, including the full path and report name, in the **Name** text box.</span></span> <span data-ttu-id="d854d-207">「資料表匯入精靈」會連接到報表，並在預覽區域中呈現出來。</span><span class="sxs-lookup"><span data-stu-id="d854d-207">The Table Import wizard connects to the report and renders it in the preview area.</span></span>  
  
     <span data-ttu-id="d854d-208">如果報表有使用參數，您就必須指定參數，否則就無法建立報表連接。</span><span class="sxs-lookup"><span data-stu-id="d854d-208">If the report uses parameters, you must specify a parameter or you cannot create the report connection.</span></span> <span data-ttu-id="d854d-209">這樣做的時候，只有與參數值相關的資料列才會匯入到資料摘要中。</span><span class="sxs-lookup"><span data-stu-id="d854d-209">When you do so, only the rows related to the parameter value are imported in the data feed.</span></span>  
  
    1.  <span data-ttu-id="d854d-210">使用清單方塊，或是在報表中提供的下拉式方塊來選擇參數。</span><span class="sxs-lookup"><span data-stu-id="d854d-210">Choose a parameter using the list box or combo box provided in the report.</span></span>  
  
    2.  <span data-ttu-id="d854d-211">按一下 **[檢視報表]** 更新資料。</span><span class="sxs-lookup"><span data-stu-id="d854d-211">Click **View Report** to update the data.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d854d-212">檢視報表將您所選取的參數和資料摘要定義儲存在一起。</span><span class="sxs-lookup"><span data-stu-id="d854d-212">Viewing the report saves the parameters that you selected together with the data feed definition.</span></span>  
  
     <span data-ttu-id="d854d-213">選擇性地按一下 [進階]\*\*\*\*，為報表設定提供者專屬的屬性。</span><span class="sxs-lookup"><span data-stu-id="d854d-213">Optionally, click **Advanced** to set provider-specific properties for the report.</span></span>  
  
6.  <span data-ttu-id="d854d-214">按一下 **[測試連接]** 確認可以將報表當做資料摘要使用。</span><span class="sxs-lookup"><span data-stu-id="d854d-214">Click **Test Connection** to make sure the report is available as a data feed.</span></span> <span data-ttu-id="d854d-215">或者，您也可以按一下 **[進階]** 來確認 **[內嵌服務文件]** 屬性包含指定資料摘要連接的內嵌 XML。</span><span class="sxs-lookup"><span data-stu-id="d854d-215">Alternatively, you can also click **Advanced** to confirm that the **Inline Service Document** property contains embedded XML that specifies the data feed connection.</span></span>  
  
7.  <span data-ttu-id="d854d-216">按 **[下一步]** 繼續執行匯入作業。</span><span class="sxs-lookup"><span data-stu-id="d854d-216">Click **Next** to continue with the import.</span></span>  
  
8.  <span data-ttu-id="d854d-217">在 **[模擬資訊]** 頁面中，指定 Analysis Services 在重新整理資料時將用來連接資料來源的憑證，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-217">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="d854d-218">在精靈的 **[選取資料表和檢視表]** 頁面中，選取要匯入做為資料之報表組件旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d854d-218">In the **Select Tables and Views** page of the wizard, select the check box next to the report parts that you want to import as data.</span></span>  
  
     <span data-ttu-id="d854d-219">一些報表可能包含多個部分，包括資料表、清單或圖表。</span><span class="sxs-lookup"><span data-stu-id="d854d-219">Some reports can contain multiple parts, including tables, lists, or graphs.</span></span>  
  
10. <span data-ttu-id="d854d-220">在 **[易記名稱]** 方塊中，輸入您要在模型中儲存之資料摘要所在的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="d854d-220">In the **Friendly name** box, type the name of the table where you want the data feed to be saved in your model.</span></span>  
  
     <span data-ttu-id="d854d-221">如果沒有指派名稱，便會依預設使用 Reporting Service 控制項的名稱，例如 Tablix1、Tablix2。</span><span class="sxs-lookup"><span data-stu-id="d854d-221">The name of the Reporting Service control is used by default if no name has been assigned: for example, Tablix1, Tablix2.</span></span> <span data-ttu-id="d854d-222">建議您在匯入期間變更此名稱，這樣便能更輕易地識別匯入之資料摘要的來源。</span><span class="sxs-lookup"><span data-stu-id="d854d-222">We recommend that you change this name during import so that you can more easily identify the origin of the imported data feed.</span></span>  
  
11. <span data-ttu-id="d854d-223">按一下 **[預覽和篩選]** 來檢閱資料和變更資料行選取項目。</span><span class="sxs-lookup"><span data-stu-id="d854d-223">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="d854d-224">您不能限制匯入報表資料摘要中的資料列，但是可以藉由清除核取方塊移除資料行。</span><span class="sxs-lookup"><span data-stu-id="d854d-224">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="d854d-225">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d854d-225">Click **OK**.</span></span>  
  
12. <span data-ttu-id="d854d-226">在 **[選取資料表和檢視表]** 頁面中，按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="d854d-226">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d854d-227">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d854d-227">See Also</span></span>  
 <span data-ttu-id="d854d-228">[&#40;SSAS 表格式&#41;支援的資料來源](tabular-models/data-sources-supported-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="d854d-228">[Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md) </span></span>  
 <span data-ttu-id="d854d-229">[&#40;SSAS 表格式&#41;支援的資料類型](tabular-models/data-types-supported-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="d854d-229">[Data Types Supported &#40;SSAS Tabular&#41;](tabular-models/data-types-supported-ssas-tabular.md) </span></span>  
 <span data-ttu-id="d854d-230">[&#40;SSAS 表格式&#41;的模擬](tabular-models/impersonation-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="d854d-230">[Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md) </span></span>  
 <span data-ttu-id="d854d-231">[&#40;SSAS 表格式&#41;處理資料](process-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="d854d-231">[Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="d854d-232">匯入資料 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="d854d-232">Import Data &#40;SSAS Tabular&#41;</span></span>](import-data-ssas-tabular.md)  
  
  
