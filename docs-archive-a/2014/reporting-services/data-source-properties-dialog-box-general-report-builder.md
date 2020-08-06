---
title: 資料來源屬性對話方塊、一般 (報表產生器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10018"
ms.assetid: b956f43a-8426-4679-acc1-00f405d5ff5b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dcfba8346a3519817a36c21b24be1a91a613e098
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585148"
---
# <a name="data-source-properties-dialog-box-general-report-builder"></a><span data-ttu-id="948e6-102">資料來源屬性對話方塊、一般 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="948e6-102">Data Source Properties Dialog Box, General (Report Builder)</span></span>
  <span data-ttu-id="948e6-103">選取 **[資料來源屬性]** 對話方塊上的 **[一般]** ，即可從報表伺服器中選取共用資料來源，或針對報表中內嵌的資料來源建立或修改連接資訊。</span><span class="sxs-lookup"><span data-stu-id="948e6-103">Select **General** on the **Data Source Properties** dialog box to select a shared data source from a report server or to create or modify connection information for a data source embedded in the report.</span></span>  
  
 <span data-ttu-id="948e6-104">用來連接資料來源的認證類型是在資料來源屬性中指定。</span><span class="sxs-lookup"><span data-stu-id="948e6-104">The type of credentials used to connect to a data source is specified in the data source properties.</span></span> <span data-ttu-id="948e6-105">當您開啟報表伺服器中的報表時，在資料來源屬性中指定的執行階段認證可能不適用於設計階段工作，例如建立查詢和預覽報表。</span><span class="sxs-lookup"><span data-stu-id="948e6-105">When you open a report from the report server, the run-time credentials, specified in the data source properties, might not work for design time tasks such as creating queries and previewing reports.</span></span> <span data-ttu-id="948e6-106">例如，資料來源可能會使用 Windows 認證 (而非您的認證)，或您不知道的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="948e6-106">For example, the data source might use Windows credentials other than yours or a user name and password that are unknown to you.</span></span>  
  
 <span data-ttu-id="948e6-107">當報表產生器無法使用資料來源屬性中提供的認證連線至資料來源時，會開啟 **[輸入資料來源認證]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="948e6-107">Report Builder opens the **Enter Data Source Credentials** dialog box when it is unable to connect to the data source using the credentials provided in the data source properties.</span></span> <span data-ttu-id="948e6-108">這通常是在以下情況時發生：</span><span class="sxs-lookup"><span data-stu-id="948e6-108">Typically this happens when:</span></span>  
  
-   <span data-ttu-id="948e6-109">資料來源設定為提示認證。</span><span class="sxs-lookup"><span data-stu-id="948e6-109">The data source is configured to prompt for credentials.</span></span>  
  
-   <span data-ttu-id="948e6-110">資料來源設定為使用預存認證。</span><span class="sxs-lookup"><span data-stu-id="948e6-110">The data source is configured to use stored credentials.</span></span>  <span data-ttu-id="948e6-111">為了盡量降低潛在的安全性威脅，報表產生器已設計成不會擷取伺服器上儲存的認證。</span><span class="sxs-lookup"><span data-stu-id="948e6-111">To minimize potential security threats, Report Builder is designed to not retrieve credentials stored on the server.</span></span>  
  
 <span data-ttu-id="948e6-112">您可以使用 **[輸入資料來源認證]** 對話方塊來變更報表產生器在設計階段所使用的認證，以當做目前的 Windows 使用者連線至資料來源或提供使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="948e6-112">You can use the **Enter Data Source Credentials** dialog box to change the credentials used by Report Builder at design time to connect to the data source as the current Windows user or provide a user name and password.</span></span> <span data-ttu-id="948e6-113">如果您提供使用者名稱和密碼，則可以指出是否將使用者名稱和密碼當做 Windows 認證使用。</span><span class="sxs-lookup"><span data-stu-id="948e6-113">If you provide a user name and password you can indicate whether they are used as Windows credentials.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="948e6-114">雖然查詢設計工具可讓您指定用於設計階段認證的其他認證類型，但是報表預覽僅能讓您針對資料來源中指定的現有認證選項，輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="948e6-114">Although the query designers allow you to specify other another credentials type for design-time credentials, report preview only allows you to enter the user name and password for the existing credentials options specified in the data source.</span></span>  
  
 <span data-ttu-id="948e6-115">當您按一下 **[測試連接]** 時，系統會使用資料來源屬性認證頁面中所指定的認證測試資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="948e6-115">When you click **Test Connection**, the connection to the data source is tested using the credentials specified in the data source properties credentials page.</span></span> <span data-ttu-id="948e6-116">您可以測試內嵌和共用資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="948e6-116">You can test connections to embedded and shared data sources.</span></span>  
  
 <span data-ttu-id="948e6-117">如果指定的認證不完整 (例如，需要密碼)，報表產生器會在需要連接資料來源時，再次提示您輸入執行階段認證。</span><span class="sxs-lookup"><span data-stu-id="948e6-117">If the credentials specified are incomplete (for example, a password is required), Report Builder prompts you again for run-time credentials when it needs to connect the data source.</span></span> <span data-ttu-id="948e6-118">系統會儲存設計階段認證，因此不會再次提示。</span><span class="sxs-lookup"><span data-stu-id="948e6-118">The design-time credentials are stored and you are not prompted again.</span></span>  
  
## <a name="options"></a><span data-ttu-id="948e6-119">選項。</span><span class="sxs-lookup"><span data-stu-id="948e6-119">Options</span></span>  
 <span data-ttu-id="948e6-120">**名稱**</span><span class="sxs-lookup"><span data-stu-id="948e6-120">**Name**</span></span>  
 <span data-ttu-id="948e6-121">輸入資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="948e6-121">Type the name of the data source.</span></span> <span data-ttu-id="948e6-122">資料來源名稱在報表內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="948e6-122">The data source name must be unique within the report.</span></span> <span data-ttu-id="948e6-123">根據預設，系統會將一般名稱 (例如，DataSource1 或 DataSource2) 指派給資料來源。</span><span class="sxs-lookup"><span data-stu-id="948e6-123">By default, a general name, such as DataSource1 or DataSource2, is assigned to the data source.</span></span>  
  
 <span data-ttu-id="948e6-124">**使用共用連接**</span><span class="sxs-lookup"><span data-stu-id="948e6-124">**Use a shared connection**</span></span>  
 <span data-ttu-id="948e6-125">選取此選項，即可瀏覽至已經發行到報表伺服器的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="948e6-125">Select this option to browse to a shared data source that has been published to a report server.</span></span>  
  
 <span data-ttu-id="948e6-126">在您從報表伺服器中選取資料來源之後，報表產生器就會維持這個報表伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="948e6-126">After you select a data source from a report server, Report Builder maintains a connection to this report server.</span></span>  
  
 <span data-ttu-id="948e6-127">**使用內嵌於我的報表的連接**</span><span class="sxs-lookup"><span data-stu-id="948e6-127">**Use a connection embedded in my report**</span></span>  
 <span data-ttu-id="948e6-128">選取此選項，即可建立僅供這份報表使用的資料來源。</span><span class="sxs-lookup"><span data-stu-id="948e6-128">Select this option to create a data source that is used only by this report.</span></span>  
  
 <span data-ttu-id="948e6-129">**型別**</span><span class="sxs-lookup"><span data-stu-id="948e6-129">**Type**</span></span>  
 <span data-ttu-id="948e6-130">選取資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="948e6-130">Select a data processing extension.</span></span> <span data-ttu-id="948e6-131">此清單會顯示所有已註冊的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="948e6-131">The list displays all registered extensions.</span></span>  
  
 <span data-ttu-id="948e6-132">**連接字串**</span><span class="sxs-lookup"><span data-stu-id="948e6-132">**Connection string**</span></span>  
 <span data-ttu-id="948e6-133">輸入資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="948e6-133">Enter a connection string for the data source.</span></span> <span data-ttu-id="948e6-134">按一下 **[建立]** ，即可使用 **[連接屬性]** 對話方塊來建立連接字串。</span><span class="sxs-lookup"><span data-stu-id="948e6-134">Click **Build** to build the connection string using the **Connection Properties** dialog box.</span></span> <span data-ttu-id="948e6-135">請按一下 [運算式]\*\*\*\* (*fx*) 按鈕來編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="948e6-135">Click the **Expressions** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="948e6-136">**處理查詢時使用單一交易**</span><span class="sxs-lookup"><span data-stu-id="948e6-136">**Use a single transaction when processing the queries**</span></span>  
 <span data-ttu-id="948e6-137">選取此選項，指出使用此資料來源的資料集會在單一交易中針對資料庫執行。</span><span class="sxs-lookup"><span data-stu-id="948e6-137">Select this option to indicate that datasets that use this data source are run in a single transaction against the database.</span></span> <span data-ttu-id="948e6-138">若要包含使用相同資料來源之子報表的交易，請選取子報表，然後在 [屬性] 窗格中，將 **[MergeTransactions]** 設定為 **[True]**。</span><span class="sxs-lookup"><span data-stu-id="948e6-138">To include transactions for subreports that use the same data source, select the subreport, and in the Properties pane, set **MergeTransactions** to **True**.</span></span>  
  
 <span data-ttu-id="948e6-139">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="948e6-139">**Test Connection**</span></span>  
 <span data-ttu-id="948e6-140">按一下以使用指定的認證確認資料來源連接能夠運作。</span><span class="sxs-lookup"><span data-stu-id="948e6-140">Click to verify that the data source connection works by using the specified credentials.</span></span> <span data-ttu-id="948e6-141">如果無法建立連接，您需要確認認證和伺服器可用性。</span><span class="sxs-lookup"><span data-stu-id="948e6-141">If the connection cannot be made, you need to verify your credentials and the server availability.</span></span> <span data-ttu-id="948e6-142">可以測試內嵌和共用資料來源的資料來源連接。</span><span class="sxs-lookup"><span data-stu-id="948e6-142">You can test data source connections for embedded and shared data sources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="948e6-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="948e6-143">See Also</span></span>  
 <span data-ttu-id="948e6-144">[將資料加入報表 &#40;報表產生器和 SSRS&#41;](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="948e6-144">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="948e6-145">[加入及驗證資料連線或資料來源 &#40;報表產生器和 SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="948e6-145">[Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="948e6-146">[報表產生器中的資料連線、資料來源及連接字串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="948e6-146">[Data Connections, Data Sources, and Connection Strings in Report Builder](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) </span></span>  
 <span data-ttu-id="948e6-147">[資料來源屬性對話方塊、認證 &#40;報表產生器&#41;](../../2014/reporting-services/data-source-properties-dialog-box-credentials-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="948e6-147">[Data Source Properties Dialog Box, Credentials &#40;Report Builder&#41;](../../2014/reporting-services/data-source-properties-dialog-box-credentials-report-builder.md) </span></span>  
 [<span data-ttu-id="948e6-148">對話方塊、窗格和精靈的報表產生器說明</span><span class="sxs-lookup"><span data-stu-id="948e6-148">Report Builder Help for Dialog Boxes, Panes, and Wizards</span></span>](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)  
  
  
