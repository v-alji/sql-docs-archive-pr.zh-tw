---
title: OLE DB 連線類型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d00cb13b-e1c2-4300-a195-3da1430a2df1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 66d4074d6bf90a23814b13da8836fd0594e8cf1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710226"
---
# <a name="ole-db-connection-type-ssrs"></a><span data-ttu-id="abc01-102">OLE DB 連接類型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="abc01-102">OLE DB Connection Type (SSRS)</span></span>
  <span data-ttu-id="abc01-103">若要加入來自 OLE DB 資料提供者的資料，您必須具有以 OLE DB 類型之報表資料來源為基礎的資料集。</span><span class="sxs-lookup"><span data-stu-id="abc01-103">To include data from an OLE DB data provider, you must have a dataset that is based on a report data source of type OLE DB.</span></span> <span data-ttu-id="abc01-104">這個內建的資料來源類型是以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] OLE DB 資料處理延伸模組為基礎。</span><span class="sxs-lookup"><span data-stu-id="abc01-104">This built-in data source type is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] OLE DB data processing extension.</span></span>  
  
 <span data-ttu-id="abc01-105">OLE DB 是一項資料存取技術，可讓用戶端連接至各種不同的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="abc01-105">OLE DB is a data access technology that enables clients to connect to a variety of data providers.</span></span> <span data-ttu-id="abc01-106">在您選取 OLE DB 資料來源類型之後，必須選取特定的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="abc01-106">After you select the data source type OLE DB, you must select a specific data provider.</span></span> <span data-ttu-id="abc01-107">例如參數和認證這類功能的支援，是依據您選取的資料提供者而定。</span><span class="sxs-lookup"><span data-stu-id="abc01-107">Support for features such as parameters and credentials are dependent on the data provider that you select.</span></span>  
  
 <span data-ttu-id="abc01-108">您可以使用本主題中的資訊來建置資料來源。</span><span class="sxs-lookup"><span data-stu-id="abc01-108">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="abc01-109">如需逐步指示，請參閱 [加入及驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="abc01-109">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="abc01-110">連接字串</span><span class="sxs-lookup"><span data-stu-id="abc01-110">Connection String</span></span>  
 <span data-ttu-id="abc01-111">OLE DB 資料處理延伸模組的連接字串會視您所要的資料提供者而定。</span><span class="sxs-lookup"><span data-stu-id="abc01-111">The connection string for the OLE DB data processing extension depends on the data provider that you want.</span></span> <span data-ttu-id="abc01-112">一般連接字串包含資料提供者支援的名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="abc01-112">A typical connection string contains name/value pairs that are supported by the data provider.</span></span> <span data-ttu-id="abc01-113">例如，下列連接字串便指 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 和 AdventureWorks 資料庫的 OLE DB 提供者：</span><span class="sxs-lookup"><span data-stu-id="abc01-113">For example, the following connection string specifies the OLE DB provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and the AdventureWorks database:</span></span>  
  
```  
Provider=SQLNCLI10.1;Data Source=server; Initial Catalog=AdventureWorks  
```  
  
 <span data-ttu-id="abc01-114">您使用的連接字串是依據您要連接的外部資料來源而定。</span><span class="sxs-lookup"><span data-stu-id="abc01-114">The connection string that you use depends on the external data source that you are connecting to.</span></span> <span data-ttu-id="abc01-115">若要設定資料提供者所特有的連接字串屬性，請在 **[資料來源屬性]** 對話方塊的 **[一般]** 頁面上，按一下 **[建立]** 按鈕，以便開啟 **[連接屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="abc01-115">To set connection string properties specific to a data provider, from the **General** page of the **Data Source Properties** dialog box, click the **Build** button to open the **Connection Properties** dialog box.</span></span> <span data-ttu-id="abc01-116">透過 **[資料連結屬性]** 對話方塊，設定延伸資料來源屬性。</span><span class="sxs-lookup"><span data-stu-id="abc01-116">Set extended data source properties through the **Data Link Properties** dialog box.</span></span>  
  
 <span data-ttu-id="abc01-117">如需更多連接字串的範例，請參閱 [報表產生器中的資料連接、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="abc01-117">For examples of connection strings, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="abc01-118">認證</span><span class="sxs-lookup"><span data-stu-id="abc01-118">Credentials</span></span>  
 <span data-ttu-id="abc01-119">需要有認證才能夠執行報表、於本機預覽報表並且從報表伺服器預覽報表。</span><span class="sxs-lookup"><span data-stu-id="abc01-119">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="abc01-120">發行報表之後，您可能需要變更資料來源的認證，如此當報表在報表伺服器上執行時，擷取資料的權限就會是有效的。</span><span class="sxs-lookup"><span data-stu-id="abc01-120">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="abc01-121">如需詳細資訊，請參閱 [Reporting Services 中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) ，或 [在 Report Builder 中指定認證](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="abc01-121">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
###### <a name="special-characters-in-a-password"></a><span data-ttu-id="abc01-122">密碼中的特殊字元</span><span class="sxs-lookup"><span data-stu-id="abc01-122">Special Characters in a Password</span></span>  
 <span data-ttu-id="abc01-123">如果您設定 OLE DB 資料來源來提示輸入密碼或是將密碼包含在連接字串中，則當使用者輸入含有特殊字元 (如標點符號) 的密碼時，某些基礎資料來源驅動程式將無法驗證這些特殊字元。</span><span class="sxs-lookup"><span data-stu-id="abc01-123">If you configure the OLE DB data source to prompt for a password or to include the password in the connection string, and a user enters the password with special characters such as punctuation marks, some underlying data source drivers cannot validate the special characters.</span></span> <span data-ttu-id="abc01-124">當您處理報表時，訊息「不是有效密碼」可能會指出此問題。</span><span class="sxs-lookup"><span data-stu-id="abc01-124">When you process the report, the message "Not a valid password" may indicate this problem.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="abc01-125">建議您不要在連接字串中加入登入資訊，例如密碼。</span><span class="sxs-lookup"><span data-stu-id="abc01-125">It is recommended that you do not add login information such as passwords to the connection string.</span></span> <span data-ttu-id="abc01-126">報表產生器會在 **[資料來源]** 對話方塊中提供另一個索引標籤，您可以使用此索引標籤來輸入認證。</span><span class="sxs-lookup"><span data-stu-id="abc01-126">Report Builder provides a separate tab on the **Data Source** dialog box that you can use to enter credentials.</span></span>  
  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="abc01-127">參數</span><span class="sxs-lookup"><span data-stu-id="abc01-127">Parameters</span></span>  
 <span data-ttu-id="abc01-128">有些 OLE DB 提供者支援未具名參數，而不支援具名參數。</span><span class="sxs-lookup"><span data-stu-id="abc01-128">Some OLE DB providers support unnamed parameters and not named parameters.</span></span> <span data-ttu-id="abc01-129">參數是使用查詢中的預留位置依據位置傳遞。</span><span class="sxs-lookup"><span data-stu-id="abc01-129">Parameters are passed by position by using a placeholder in the query.</span></span> <span data-ttu-id="abc01-130">預留位置字元是由資料提供者支援的語法決定。</span><span class="sxs-lookup"><span data-stu-id="abc01-130">The placeholder character is determined by the syntax that is supported by the data provider.</span></span>  
  
 
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="abc01-131">備註</span><span class="sxs-lookup"><span data-stu-id="abc01-131">Remarks</span></span>  
 <span data-ttu-id="abc01-132">OLEDB 是一項原生技術，用於建立特定資料來源的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="abc01-132">OLEDB is a native technology for building data providers for specific data sources.</span></span> <span data-ttu-id="abc01-133">OLEDB 是以 COM (元件物件模型) 介面為基礎。</span><span class="sxs-lookup"><span data-stu-id="abc01-133">OLEDB is based on COM (Component Object Model) interfaces.</span></span> <span data-ttu-id="abc01-134">OLEDB 是比 ODBC 更新的技術，但是比 ADO.NET 資料提供者更早出現。</span><span class="sxs-lookup"><span data-stu-id="abc01-134">OLEDB is a later technology than ODBC and earlier than ADO.NET data providers.</span></span> <span data-ttu-id="abc01-135">OLEDB 資料提供者會在作業系統中註冊，就像其他 COM 元件一般。</span><span class="sxs-lookup"><span data-stu-id="abc01-135">OLEDB data providers are registered with the operating system like any other COM component.</span></span> <span data-ttu-id="abc01-136">OLEDB 資料提供者可從 Microsoft 和協力廠商取得。</span><span class="sxs-lookup"><span data-stu-id="abc01-136">OLEDB data providers are available from Microsoft and third party vendors.</span></span> <span data-ttu-id="abc01-137">Microsoft 同時提供 MSDASQL，這是橋接與 ODBC 驅動程式之通訊的 OLEDB 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="abc01-137">Microsoft also provides MSDASQL, an OLEDB data provider that bridges communication to ODBC drivers.</span></span> <span data-ttu-id="abc01-138">如需詳細資訊，請參閱 [ODBC 連線類型 &#40;SSRS&#41;](odbc-connection-type-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="abc01-138">For more information, see [ODBC Connection Type &#40;SSRS&#41;](odbc-connection-type-ssrs.md).</span></span>  
  
 <span data-ttu-id="abc01-139">若要成功擷取您想要的資料，您必須提供資料提供者支援的查詢語法。</span><span class="sxs-lookup"><span data-stu-id="abc01-139">To successfully retrieve the data that you want, you must provide query syntax that is supported by the data provider.</span></span> <span data-ttu-id="abc01-140">參數支援會因資料提供者而異。</span><span class="sxs-lookup"><span data-stu-id="abc01-140">Parameter support varies by data provider.</span></span> <span data-ttu-id="abc01-141">如需詳細資訊，請參閱所選取資料提供者的特定主題。</span><span class="sxs-lookup"><span data-stu-id="abc01-141">For more information, see topics that are specific to the data provider that you select.</span></span> <span data-ttu-id="abc01-142">例如：</span><span class="sxs-lookup"><span data-stu-id="abc01-142">For example:</span></span>  
  
-   [<span data-ttu-id="abc01-143">Analysis Services OLE DB 提供者 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="abc01-143">Analysis Services OLE DB Provider &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../analysis-services/dev-guide/analysis-services-ole-db-provider-analysis-services-multidimensional-data.md)  
  
-   [<span data-ttu-id="abc01-144">使用 .NET Framework Data Provider for Oracle</span><span class="sxs-lookup"><span data-stu-id="abc01-144">Using the .NET Framework Data Provider for Oracle</span></span>](https://go.microsoft.com/fwlink/?LinkId=112314)  
  
-   [<span data-ttu-id="abc01-145">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="abc01-145">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
 <span data-ttu-id="abc01-146">如需特定 OLE DB 資料提供者的詳細資訊，請參閱[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [線上叢書](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件的 [Reporting Services &#40;SSRS&#41; 支援的資料來源](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="abc01-146">For more information about specific OLE DB data providers, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="abc01-147">如何主題</span><span class="sxs-lookup"><span data-stu-id="abc01-147">How-To Topics</span></span>  
 <span data-ttu-id="abc01-148">本節包含使用資料連接、資料來源與資料集的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="abc01-148">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="abc01-149">新增及驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="abc01-149">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="abc01-150">建立共用資料集或內嵌資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="abc01-150">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="abc01-151">將篩選加入資料集中 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="abc01-151">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="abc01-152">相關章節</span><span class="sxs-lookup"><span data-stu-id="abc01-152">Related Sections</span></span>  
 <span data-ttu-id="abc01-153">本文件集的這些章節會提供報表資料的深入概念性資訊，以及如何定義、自訂和使用與報表資料相關組件的程序資訊。</span><span class="sxs-lookup"><span data-stu-id="abc01-153">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="abc01-154">將資料加入至報表 &#40;Report Builder 和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="abc01-154">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="abc01-155">提供存取報表資料的概觀。</span><span class="sxs-lookup"><span data-stu-id="abc01-155">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="abc01-156">報表產生器中的資料連接、資料來源及連接字串</span><span class="sxs-lookup"><span data-stu-id="abc01-156">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="abc01-157">提供資料連接與資料來源的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="abc01-157">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="abc01-158">報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="abc01-158">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="abc01-159">提供內嵌與共用資料集的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="abc01-159">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="abc01-160">資料集欄位集合 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="abc01-160">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="abc01-161">提供查詢所產生之資料集欄位集合的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="abc01-161">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="abc01-162">《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [線上叢書》](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件的 [Reporting Services 支援的資料來源 &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="abc01-162">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="abc01-163">提供支援每一個資料延伸模組之平台與版本的深入資訊。</span><span class="sxs-lookup"><span data-stu-id="abc01-163">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="abc01-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abc01-164">See Also</span></span>  
 <span data-ttu-id="abc01-165">[報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="abc01-165">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="abc01-166">[篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="abc01-166">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="abc01-167">運算式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="abc01-167">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
