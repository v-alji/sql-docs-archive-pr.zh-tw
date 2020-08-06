---
title: 在 Excel 或 Reporting Services 中使用 BI 語義模型連接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 486195ca-530f-49e8-b40d-0f817db159ee
author: minewiskan
ms.author: owend
ms.openlocfilehash: a48ebfc515b97327655e34409bf80ce0c749e04e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705530"
---
# <a name="use-a-bi-semantic-model-connection-in-excel-or-reporting-services"></a><span data-ttu-id="a3ef1-102">在 Excel 或 Reporting Services 使用 BI 語意模型連接</span><span class="sxs-lookup"><span data-stu-id="a3ef1-102">Use a BI Semantic Model Connection in Excel or Reporting Services</span></span>
  <span data-ttu-id="a3ef1-103">本主題說明如何使用透過其他主題的指示所建立的 BI 語意模型連接。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-103">This topic explains how to use the BI semantic model connections you created using instructions in other topics.</span></span> <span data-ttu-id="a3ef1-104">如果您尚未建立 BI 語義模型，請參閱[建立與 PowerPivot 活頁簿的 Bi 語義模型連接](create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md)和[建立與表格式模型資料庫的 Bi 語義模型連接](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-104">If you have not yet created a BI semantic model, see [Create a BI Semantic Model Connection to a PowerPivot Workbook](create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md) and [Create a BI Semantic Model Connection to a Tabular Model Database](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md).</span></span>  
  
##  <a name="connect-from-excel"></a><a name="bkmk_connect"></a> <span data-ttu-id="a3ef1-105">從 Excel 連接</span><span class="sxs-lookup"><span data-stu-id="a3ef1-105">Connect from Excel</span></span>  
 <span data-ttu-id="a3ef1-106">您可以在 Excel 或是使用 Analysis Services 表格式模型資料的其他任何商務應用程式中，指定 BI 語意模型連接當做資料來源。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-106">You can specify a BI semantic model connection as a data source in Excel or any other business application that uses Analysis Services tabular model data.</span></span> <span data-ttu-id="a3ef1-107">本節說明使用 Excel 連接到 BI 語意模型資料的兩種方法。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-107">This section explains the two approaches for connecting to BI semantic model data using Excel.</span></span>  
  
 <span data-ttu-id="a3ef1-108">來自 Excel 的 BI 語意模型連接要求在工作站上安裝 Excel 2010 和 MSOLAP.5 OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-108">BI semantic model connections from Excel require that you have Excel 2010 and the MSOLAP.5 OLE DB provider installed on your workstation.</span></span> <span data-ttu-id="a3ef1-109">本節會進一步提供有關連接需求的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-109">Additional information about connection requirements is provided further on in this section.</span></span>  
  
 <span data-ttu-id="a3ef1-110">**從 SharePoint 啟動**</span><span class="sxs-lookup"><span data-stu-id="a3ef1-110">**Starting from SharePoint**</span></span>  
  
-   <span data-ttu-id="a3ef1-111">以滑鼠右鍵按一下文件庫中的 BI 語意模型連接，然後選取 [啟動 Excel]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-111">Right-click a BI semantic model connection in a library and select **Launch Excel**.</span></span>  
  
 <span data-ttu-id="a3ef1-112">![BISM 快速啟動命令的螢幕擷取畫面](../media/ssas-bism-quicklaunch.gif "BISM 快速啟動命令的螢幕擷取畫面")</span><span class="sxs-lookup"><span data-stu-id="a3ef1-112">![Screenshot of BISM quick launch command](../media/ssas-bism-quicklaunch.gif "Screenshot of BISM quick launch command")</span></span>  
  
 <span data-ttu-id="a3ef1-113">當系統提示您啟用資料連接時，按一下 **[啟用]** 。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-113">Click **Enable** when prompted to enable data connections.</span></span> <span data-ttu-id="a3ef1-114">Excel 會開啟活頁簿，其中包含填入了基礎資料來源中之欄位的樞紐分析表欄位清單。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-114">Excel opens a workbook that contains a PivotTable field list populated with fields from the underlying data source.</span></span>  
  
 <span data-ttu-id="a3ef1-115">**從 Excel 啟動**</span><span class="sxs-lookup"><span data-stu-id="a3ef1-115">**Starting from Excel**</span></span>  
  
1.  <span data-ttu-id="a3ef1-116">啟動 Excel 並開啟活頁簿。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-116">Start Excel and open a workbook.</span></span> <span data-ttu-id="a3ef1-117">在 [資料] 索引標籤上，按一下 [取得外部資料] 中的 **[從其他來源]**。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-117">On the Data tab, in Get External Data, click **From Other Sources**.</span></span>  
  
2.  <span data-ttu-id="a3ef1-118">按一下 **[從 Analysis Services]** ，然後使用 [資料連線精靈] 匯入資料。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-118">Click **From Analysis Services** and use the Data Connection Wizard to import the data.</span></span>  
  
3.  <span data-ttu-id="a3ef1-119">輸入 BI 語義模型連接檔案的 SharePoint URL， (例如\*\* http://mysharepoint/shared Documents/myData. bism\*\*) 。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-119">Enter the SharePoint URL of the BI semantic model connection file (for example, **http://mysharepoint/shared documents/myData.bism**).</span></span> <span data-ttu-id="a3ef1-120">接受認證選項 **[使用 Windows 驗證]** 上的預設記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-120">Accept the default log on credentials option, **Use Windows Authentication**.</span></span> <span data-ttu-id="a3ef1-121">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-121">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="a3ef1-122">在下一個頁面上，再按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-122">On the next page, click **Next** again.</span></span> <span data-ttu-id="a3ef1-123">雖然系統會提示您選取資料庫，但是您只能使用在 BI 語意模型連接中指定的資料庫。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-123">Although you are prompted to select a database, you can only use the one database that is specified in the BI semantic model connection.</span></span>  
  
5.  <span data-ttu-id="a3ef1-124">在最後一個頁面上，您可以提供易記名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-124">On the last page, you can provide a friendly name and description.</span></span> <span data-ttu-id="a3ef1-125">按一下 **[完成]**，然後按一下 [匯入資料] 對話方塊上的 **[確定]** 來匯入資料。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-125">Click **Finish**, and then click **OK** on the Import Data dialog box to import the data.</span></span>  
  
 <span data-ttu-id="a3ef1-126">若要讓連接成功，您必須將 Excel 2010 和 MSOLAP.5.dll 安裝在用戶端電腦上。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-126">For connections to succeed you must have Excel 2010 and the MSOLAP.5.dll installed on the client computer.</span></span> <span data-ttu-id="a3ef1-127">您可以藉由安裝這個版本的最新版本 PowerPivot for Excel 來取得提供者，或者您可以從[功能套件下載頁面](https://go.microsoft.com/fwlink/?linkid=214066)僅下載 Analysis Services OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-127">You can get the provider by installing the version of PowerPivot for Excel that is current for this release or you can download just the Analysis Services OLE DB provider from the [Feature Pack download page](https://go.microsoft.com/fwlink/?linkid=214066).</span></span>  
  
 <span data-ttu-id="a3ef1-128">若要確認 MSOLAP.5.dll 是最新的版本，請檢查登錄中的 `HKEY_CLASSES_ROOT\MSOLAP`。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-128">To confirm that MSOLAP.5.dll is the current version, check `HKEY_CLASSES_ROOT\MSOLAP` in the registry.</span></span> <span data-ttu-id="a3ef1-129">`CurVer` 應該設定為 MSOLAP.5。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-129">`CurVer` should be set to MSOLAP.5.</span></span>  
  
 <span data-ttu-id="a3ef1-130">在 SharePoint 中，您也必須擁有 BI 語意模型檔案的「讀取」權限。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-130">You must also have Read permissions on the BI semantic model file in SharePoint.</span></span> <span data-ttu-id="a3ef1-131">「讀取」權限包含下載權限。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-131">Read permissions include download rights.</span></span> <span data-ttu-id="a3ef1-132">Excel 會從 SharePoint 下載 BI 語意模型連接資訊，然後透過 `HTTP Get` 開啟與資料庫的直接連接。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-132">Excel downloads the BI semantic model connection information from SharePoint and opens a direct connection to the database via `HTTP Get`.</span></span> <span data-ttu-id="a3ef1-133">一旦 BI 語意模型連接資訊在本機上儲存，連接要求就不會流經 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-133">Connection requests do not flow through SharePoint once BI semantic model connection information is stored locally.</span></span>  
  
 <span data-ttu-id="a3ef1-134">如果您要連接至 Analysis Services 伺服器上執行的表格式模型資料庫，則 SharePoint 權限還不夠。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-134">If you are connecting to a tabular model database that runs on an Analysis Services server, SharePoint permissions are not sufficient.</span></span> <span data-ttu-id="a3ef1-135">您也必須擁有伺服器的資料庫讀取權限。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-135">You must also have database read permissions on the server.</span></span> <span data-ttu-id="a3ef1-136">當您建立 BI 語意模型連接時，應該已經執行這個步驟。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-136">This step should have been performed when you created the BI semantic model connection.</span></span> <span data-ttu-id="a3ef1-137">如需詳細資訊，請參閱 [建立與表格式模型資料庫的 BI 語意模型連接](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-137">For more information, see [Create a BI Semantic Model Connection to a Tabular Model Database](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md).</span></span>  
  
##  <a name="connect-from-reporting-services-in-sharepoint"></a><a name="bkmk_use"></a> <span data-ttu-id="a3ef1-138">在 SharePoint 中從 Reporting Services 連接</span><span class="sxs-lookup"><span data-stu-id="a3ef1-138">Connect from Reporting Services in SharePoint</span></span>  
 <span data-ttu-id="a3ef1-139">您可以利用您使用多數資料來源的相同方式來使用 BI 語意模型連接，方法是在使用資料的文件或工具中，將檔案指定為資料來源。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-139">You can use a BI semantic model connection the same way you use most data sources, by specifying the file as a data source in the document or tool that uses the data.</span></span> <span data-ttu-id="a3ef1-140">雖然 BI 語意模型連接會指向其他伺服器上的實體資料庫，但是您要將該連接檔案本身當做資料來源使用。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-140">Although a BI semantic model connection points to a physical database on another server, you use the connection file as if it were the data source.</span></span> <span data-ttu-id="a3ef1-141">BI 語意模型連接的 SharePoint URL 對於使用 BI 語意模型資料的 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 報表而言是有效的資料來源位置。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-141">The SharePoint URL of the BI semantic model connection is a valid data source location for [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports that use BI semantic model data.</span></span>  
  
 <span data-ttu-id="a3ef1-142">針對 SharePoint 中的隨選報表設計，建立報表的使用者必須擁有 BI 語意模型連接 (.bism) 檔案和商業智慧語意模型資料庫的 SharePoint 權限。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-142">For ad hoc report design in SharePoint, the user who creates the report must have SharePoint permissions on the BI semantic model connection (.bism) file and on the business intelligence semantic model database.</span></span> <span data-ttu-id="a3ef1-143">連接的安全性內容是正在建立報表的互動式使用者。</span><span class="sxs-lookup"><span data-stu-id="a3ef1-143">The security context of the connection is the interactive user who is creating the report.</span></span>  
  
  
