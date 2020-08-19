---
title: ODBC 連線類型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 24163866-f37a-4c38-982e-c3d79bf64d4c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b2bf5ee6f3eeaa38796e4fa41f3cc0634fd128cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592456"
---
# <a name="odbc-connection-type-ssrs"></a><span data-ttu-id="578ba-102">ODBC 連接類型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="578ba-102">ODBC Connection Type (SSRS)</span></span>
  <span data-ttu-id="578ba-103">若要加入來自 ODBC 資料提供者的資料，您必須具有以 ODBC 類型之報表資料來源為基礎的資料集。</span><span class="sxs-lookup"><span data-stu-id="578ba-103">To include data from an ODBC data provider, you must have a dataset that is based on a report data source of type ODBC.</span></span> <span data-ttu-id="578ba-104">這個內建資料來源類型是以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ODBC 資料處理延伸模組為基礎。</span><span class="sxs-lookup"><span data-stu-id="578ba-104">This built-in data source type is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ODBC data processing extension.</span></span>  
  
 <span data-ttu-id="578ba-105">您可以使用本主題中的資訊來建置資料來源。</span><span class="sxs-lookup"><span data-stu-id="578ba-105">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="578ba-106">如需逐步指示，請參閱 [加入及驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="578ba-106">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="578ba-107">連接字串</span><span class="sxs-lookup"><span data-stu-id="578ba-107">Connection String</span></span>  
 <span data-ttu-id="578ba-108">ODBC 資料處理延伸模組的連接字串會視您所要的 ODBC 驅動程式而定。</span><span class="sxs-lookup"><span data-stu-id="578ba-108">The connection string for the ODBC data processing extension depends on the ODBC driver that you want.</span></span> <span data-ttu-id="578ba-109">一般連接字串包含驅動程式支援的名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="578ba-109">A typical connection string contains name/value pairs that are supported by the driver.</span></span> <span data-ttu-id="578ba-110">例如，下列連接字串便指 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 和 AdventureWorks 資料庫的 ODBC 驅動程式：</span><span class="sxs-lookup"><span data-stu-id="578ba-110">For example, the following connection string specifies the ODBC driver for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and the AdventureWorks database:</span></span>  
  
```  
Driver={SQL Server Native Client 10.0};Server=server;Database=AdventureWorks;Trusted_Connection=yes;  
```  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="578ba-111">認證</span><span class="sxs-lookup"><span data-stu-id="578ba-111">Credentials</span></span>  
 <span data-ttu-id="578ba-112">需要有認證才能夠執行報表、於本機預覽報表並且從報表伺服器預覽報表。</span><span class="sxs-lookup"><span data-stu-id="578ba-112">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="578ba-113">發行報表之後，您可能需要變更資料來源的認證，如此當報表在報表伺服器上執行時，擷取資料的權限就會是有效的。</span><span class="sxs-lookup"><span data-stu-id="578ba-113">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="578ba-114">如果您設定 ODBC 資料來源以提示密碼或將密碼包含在連接字串中，則當使用者輸入含有特殊字元 (例如標點符號) 的密碼時，某些基礎資料來源驅動程式無法驗證這些特殊字元。</span><span class="sxs-lookup"><span data-stu-id="578ba-114">If you configure your ODBC data source to prompt for a password or to include the password in the connection string, and a user enters the password with special characters such as punctuation marks, some underlying data source drivers cannot validate the special characters.</span></span> <span data-ttu-id="578ba-115">當您處理報表時，訊息「不是有效密碼」可能會指出此問題。</span><span class="sxs-lookup"><span data-stu-id="578ba-115">When you process the report, the message "Not a valid password" might indicate this problem.</span></span> <span data-ttu-id="578ba-116">如果無法變更此密碼，您可以和資料庫管理員一起合作，將適當的認證儲存在報表伺服器上，當做系統 ODBC 資料來源名稱 (DSN) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="578ba-116">If changing the password is impractical, you can work with your database administrator to store the appropriate credentials on the report server as part of a system ODBC data source name (DSN).</span></span> <span data-ttu-id="578ba-117">如需詳細資訊，請參閱 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文件集中的＜OdbcConnection.ConnectionString＞。</span><span class="sxs-lookup"><span data-stu-id="578ba-117">For more information, see "OdbcConnection.ConnectionString" in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="578ba-118">建議您不要在連接字串中加入登入資訊，例如密碼。</span><span class="sxs-lookup"><span data-stu-id="578ba-118">It is recommended that you do not add login information such as passwords to the connection string.</span></span> <span data-ttu-id="578ba-119">報表產生器會在 **[資料來源]** 對話方塊中提供另一個索引標籤，您可以使用此索引標籤來輸入認證。</span><span class="sxs-lookup"><span data-stu-id="578ba-119">Report Builder provides a separate tab on the **Data Source** dialog box that you can use to enter credentials.</span></span>  
  
 <span data-ttu-id="578ba-120">如需詳細資訊，請參閱 [Reporting Services 中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) ，或 [在 Report Builder 中指定認證](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="578ba-120">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="578ba-121">備註</span><span class="sxs-lookup"><span data-stu-id="578ba-121">Remarks</span></span>  
 <span data-ttu-id="578ba-122">ODBC 是在 OLEDB 之前的早期資料存取技術。</span><span class="sxs-lookup"><span data-stu-id="578ba-122">ODBC is an early data access technology that preceded OLEDB.</span></span> <span data-ttu-id="578ba-123">ODBC 只能支援關聯式資料來源。</span><span class="sxs-lookup"><span data-stu-id="578ba-123">ODBC supports only relational data sources.</span></span> <span data-ttu-id="578ba-124">ODBC 資料提供者稱為 *「驅動程式」* (Driver)。</span><span class="sxs-lookup"><span data-stu-id="578ba-124">ODBC data providers are called *drivers*.</span></span> <span data-ttu-id="578ba-125">ODBC 驅動程式由 Microsoft 和協力廠商提供。</span><span class="sxs-lookup"><span data-stu-id="578ba-125">ODBC drivers are provided by Microsoft and third party vendors.</span></span> <span data-ttu-id="578ba-126">例如，Microsoft Office 會安裝連接至 Office 檔案格式的 ODBC 驅動程式。</span><span class="sxs-lookup"><span data-stu-id="578ba-126">For example, Microsoft Office installs ODBC drivers that connect to Office file formats.</span></span>  
  
 <span data-ttu-id="578ba-127">在建立 ODBC 連接字串之前，您必須已安裝 ODBC 驅動程式並建立機器或系統資料來源名稱 (DSN)。</span><span class="sxs-lookup"><span data-stu-id="578ba-127">Before you can build an ODBC connection string, you must have ODBC drivers installed and build a machine or system DSN.</span></span> <span data-ttu-id="578ba-128">若要成功擷取您想要的資料，您必須提供驅動程式支援的查詢語法。</span><span class="sxs-lookup"><span data-stu-id="578ba-128">To successfully retrieve the data that you want, you must provide query syntax that is supported by the driver.</span></span> <span data-ttu-id="578ba-129">參數支援會因驅動程式而異。</span><span class="sxs-lookup"><span data-stu-id="578ba-129">Parameter support varies by driver.</span></span> <span data-ttu-id="578ba-130">如需詳細資訊，請參閱所選驅動程式的特定主題，例如 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="578ba-130">For more information, see topics that are specific to the driver that you select, for example, [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md).</span></span>  
  
###### <a name="platform-and-version-information"></a><span data-ttu-id="578ba-131">平台和版本資訊</span><span class="sxs-lookup"><span data-stu-id="578ba-131">Platform and Version Information</span></span>  
 <span data-ttu-id="578ba-132">如需特定 ODBC 資料提供者的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [ 線上叢書](https://go.microsoft.com/fwlink/?linkid=121312)》中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件的 [Reporting Services &#40;SSRS&#41; 支援的資料來源](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="578ba-132">For more information about specific ODBC data providers, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="578ba-133">如何主題</span><span class="sxs-lookup"><span data-stu-id="578ba-133">How-To Topics</span></span>  
 <span data-ttu-id="578ba-134">本節包含使用資料連接、資料來源與資料集的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="578ba-134">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="578ba-135">新增及驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="578ba-135">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="578ba-136">建立共用資料集或內嵌資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="578ba-136">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="578ba-137">將篩選加入資料集中 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="578ba-137">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="578ba-138">相關章節</span><span class="sxs-lookup"><span data-stu-id="578ba-138">Related Sections</span></span>  
 <span data-ttu-id="578ba-139">本文件集的這些章節會提供報表資料的深入概念性資訊，以及如何定義、自訂和使用與報表資料相關組件的程序資訊。</span><span class="sxs-lookup"><span data-stu-id="578ba-139">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="578ba-140">將資料加入至報表 &#40;Report Builder 和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="578ba-140">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="578ba-141">提供存取報表資料的概觀。</span><span class="sxs-lookup"><span data-stu-id="578ba-141">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="578ba-142">報表產生器中的資料連接、資料來源及連接字串</span><span class="sxs-lookup"><span data-stu-id="578ba-142">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="578ba-143">提供資料連接與資料來源的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="578ba-143">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="578ba-144">報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="578ba-144">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="578ba-145">提供內嵌與共用資料集的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="578ba-145">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="578ba-146">資料集欄位集合 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="578ba-146">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="578ba-147">提供查詢所產生之資料集欄位集合的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="578ba-147">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="578ba-148">《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [線上叢書》](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件的 [Reporting Services 支援的資料來源 &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="578ba-148">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="578ba-149">提供支援每一個資料延伸模組之平台與版本的深入資訊。</span><span class="sxs-lookup"><span data-stu-id="578ba-149">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="578ba-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="578ba-150">See Also</span></span>  
 <span data-ttu-id="578ba-151">[報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="578ba-151">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="578ba-152">[篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="578ba-152">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="578ba-153">運算式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="578ba-153">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
