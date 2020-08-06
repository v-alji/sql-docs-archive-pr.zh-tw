---
title: 使用 SSIS 從 Excel 匯入或匯出至 Excel | Microsoft Docs
description: 了解如何使用 SQL Server Integration Services (SSIS) 匯入或匯出 Excel 資料，以及必要條件、已知問題和限制。
ms.date: 04/10/2018
ms.prod: sql-server-2014
ms.prod_service: integration-services
ms.reviewer: ''
ms.custom: ''
ms.technology: integration-services
ms.topic: conceptual
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58b0165925e73d0eb72b118113bc354338741a0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596109"
---
# <a name="import-data-from-excel-or-export-data-to-excel-with-sql-server-integration-services-ssis"></a><span data-ttu-id="cd130-103">使用 SQL Server Integration Services (SSIS) 從 Excel 匯入資料，或將資料匯出至 Excel</span><span class="sxs-lookup"><span data-stu-id="cd130-103">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>

<span data-ttu-id="cd130-104">本文描述如何使用 SQL Server Integration Services (SSIS) 從 Excel 匯入資料，或將資料匯出至 Excel。</span><span class="sxs-lookup"><span data-stu-id="cd130-104">This article describes how to import data from Excel or export data to Excel with SQL Server Integration Services (SSIS).</span></span> <span data-ttu-id="cd130-105">本文也描述必要條件、限制和已知問題。</span><span class="sxs-lookup"><span data-stu-id="cd130-105">The article also describes prerequisites, limitations, and known issues.</span></span>

<span data-ttu-id="cd130-106">您可以藉由建立 SSIS 套件，並使用 Excel 連線管理員和 Excel 來源或 Excel 目的地，從 Excel 匯入資料，或將資料匯出至 Excel。</span><span class="sxs-lookup"><span data-stu-id="cd130-106">You can import data from Excel or export data to Excel by creating an SSIS package and using the Excel Connection Manager and the Excel Source or the Excel Destination.</span></span> <span data-ttu-id="cd130-107">您也可以使用建立在 SSIS 上的 [SQL Server 匯入和匯出精靈]。</span><span class="sxs-lookup"><span data-stu-id="cd130-107">You can also use the SQL Server Import and Export Wizard, which is built on SSIS.</span></span>

<span data-ttu-id="cd130-108">本文包含成功從 SSIS 使用 Excel，或要了解及針對常見問題進行疑難排解所需的三組資訊：</span><span class="sxs-lookup"><span data-stu-id="cd130-108">This article contains the three sets of information you need to use Excel successfully from SSIS or to understand and troubleshoot common problems:</span></span>
1.  <span data-ttu-id="cd130-109">[您需要的](#files-you-need)檔案。</span><span class="sxs-lookup"><span data-stu-id="cd130-109">[The files you need](#files-you-need).</span></span>
2.  <span data-ttu-id="cd130-110">當您使用 Excel 載入或取出資料時，您必須提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="cd130-110">The information you have to provide when you load data from or to Excel.</span></span>
    -   <span data-ttu-id="cd130-111">[指定 Excel](#specify-excel) 作為資料來源。</span><span class="sxs-lookup"><span data-stu-id="cd130-111">[Specify Excel](#specify-excel) as your data source.</span></span>
    -   <span data-ttu-id="cd130-112">提供 [Excel 檔案名稱和路徑](#excel-file)。</span><span class="sxs-lookup"><span data-stu-id="cd130-112">Provide the [Excel file name and path](#excel-file).</span></span>
    -   <span data-ttu-id="cd130-113">選取 [Excel 版本](#excel-version)。</span><span class="sxs-lookup"><span data-stu-id="cd130-113">Select the [Excel version](#excel-version).</span></span>
    -   <span data-ttu-id="cd130-114">指定是否在[第一個資料列包含資料行名稱](#first-row)。</span><span class="sxs-lookup"><span data-stu-id="cd130-114">Specify whether the [first row contains column names](#first-row).</span></span>
    -   <span data-ttu-id="cd130-115">提供[包含資料的工作表或範圍](#sheets-ranges)。</span><span class="sxs-lookup"><span data-stu-id="cd130-115">Provide the [worksheet or range that contains the data](#sheets-ranges).</span></span>
3.  <span data-ttu-id="cd130-116">已知問題和限制。</span><span class="sxs-lookup"><span data-stu-id="cd130-116">Known issues and limitations.</span></span>
    -   <span data-ttu-id="cd130-117">[資料類型](#issues-types)的問題。</span><span class="sxs-lookup"><span data-stu-id="cd130-117">Issues with [data types](#issues-types).</span></span>
    -   <span data-ttu-id="cd130-118">[匯入](#issues-importing)的問題。</span><span class="sxs-lookup"><span data-stu-id="cd130-118">Issues with [importing](#issues-importing).</span></span>
    -   <span data-ttu-id="cd130-119">[匯出](#issues-exporting)的問題。</span><span class="sxs-lookup"><span data-stu-id="cd130-119">Issues with [exporting](#issues-exporting).</span></span>

## <a name="get-the-files-you-need-to-connect-to-excel"></a><a name="files-you-need"></a> <span data-ttu-id="cd130-120">取得連線至 Excel 所需的檔案</span><span class="sxs-lookup"><span data-stu-id="cd130-120">Get the files you need to connect to Excel</span></span>

<span data-ttu-id="cd130-121">您可能必須下載適用於 Excel 的連線元件，如果它們尚未安裝的話，然後才能從 Excel 匯入資料，或將資料匯出至 Excel。</span><span class="sxs-lookup"><span data-stu-id="cd130-121">Before you can import data from Excel or export data to Excel, you may have to download the connectivity components for Excel if they're not already installed.</span></span> <span data-ttu-id="cd130-122">預設不會安裝適用於 Excel 的連線元件。</span><span class="sxs-lookup"><span data-stu-id="cd130-122">The connectivity components for Excel are not installed by default.</span></span>

<span data-ttu-id="cd130-123">在這裡下載適用於 Excel 的連線元件最新版本：[Microsoft Access Database Engine 2016 可轉散發套件](https://www.microsoft.com/download/details.aspx?id=54920)。</span><span class="sxs-lookup"><span data-stu-id="cd130-123">Download the latest version of the connectivity components for Excel here: [Microsoft Access Database Engine 2016 Redistributable](https://www.microsoft.com/download/details.aspx?id=54920).</span></span>
  
<span data-ttu-id="cd130-124">最新版的元件可以開啟舊版 Excel 所建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd130-124">The latest version of the components can open files created by earlier versions of Excel.</span></span>

<span data-ttu-id="cd130-125">請確定下載 Access Database Engine 2016「可轉散發套件」  ，而非 Microsoft Access 2016 *Runtime*。</span><span class="sxs-lookup"><span data-stu-id="cd130-125">Make sure that you download the Access Database Engine 2016 *Redistributable* and not the Microsoft Access 2016 *Runtime*.</span></span>

<span data-ttu-id="cd130-126">如果電腦已有 32 位元版的 Office，您就必須安裝 32 位元版的元件。</span><span class="sxs-lookup"><span data-stu-id="cd130-126">If the computer already has a 32-bit version of Office, then you have to install the 32-bit version of the components.</span></span> <span data-ttu-id="cd130-127">您也必須確定您在 32 位元模式中執行 SSIS 套件，或執行 [匯入和匯出精靈] 的 32 位元版本。</span><span class="sxs-lookup"><span data-stu-id="cd130-127">You also have to ensure that you run the SSIS package in 32-bit mode, or run the 32-bit version of the Import and Export Wizard.</span></span>

<span data-ttu-id="cd130-128">如果您有 Office 365 訂閱，可能會在執行安裝程式時看到一則錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="cd130-128">If you have an Office 365 subscription, you may see an error message when you run the installer.</span></span> <span data-ttu-id="cd130-129">錯誤訊息指出您無法使用 Office 隨選即用元件並存安裝下載。</span><span class="sxs-lookup"><span data-stu-id="cd130-129">The error indicates that you can't install the download side by side with Office click-to-run components.</span></span> <span data-ttu-id="cd130-130">若要略過此錯誤訊息，請開啟 [命令提示字元] 視窗並執行使用 `/quiet` 參數所下載的 .EXE 檔案，以無訊息模式執行安裝。</span><span class="sxs-lookup"><span data-stu-id="cd130-130">To bypass this error message, run the installation in quiet mode by opening a Command Prompt window and running the .EXE file that you downloaded with the `/quiet` switch.</span></span> <span data-ttu-id="cd130-131">例如：</span><span class="sxs-lookup"><span data-stu-id="cd130-131">For example:</span></span>

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

<span data-ttu-id="cd130-132">如果您無法安裝 2016 可轉散發套件，請改為從這裡安裝 2010 可轉散發套件：[Microsoft Access Database Engine 2010 Redistributable](https://www.microsoft.com/download/details.aspx?id=13255) (Microsoft Access 資料庫引擎 2010 可轉散發套件)。</span><span class="sxs-lookup"><span data-stu-id="cd130-132">If you have trouble installing the 2016 redistributable, install the 2010 redistributable instead from here: [Microsoft Access Database Engine 2010 Redistributable](https://www.microsoft.com/download/details.aspx?id=13255).</span></span> <span data-ttu-id="cd130-133">(沒有任何適用於 Excel 2013 的可轉散發套件。)</span><span class="sxs-lookup"><span data-stu-id="cd130-133">(There is no redistributable for Excel 2013.)</span></span>

## <a name="specify-excel"></a><a name="specify-excel"></a> <span data-ttu-id="cd130-134">指定 Excel</span><span class="sxs-lookup"><span data-stu-id="cd130-134">Specify Excel</span></span>

<span data-ttu-id="cd130-135">第一個步驟是指出您想要連接至 Excel。</span><span class="sxs-lookup"><span data-stu-id="cd130-135">The first step is to indicate that you want to connect to Excel.</span></span>

### <a name="in-ssis"></a><span data-ttu-id="cd130-136">在 SSIS 中</span><span class="sxs-lookup"><span data-stu-id="cd130-136">In SSIS</span></span>
<span data-ttu-id="cd130-137">在 SSIS 中建立 Excel 連線管理員以連接至 Excel 來源或目的地檔案。</span><span class="sxs-lookup"><span data-stu-id="cd130-137">In SSIS, create an Excel Connection Manager to connect to the Excel source or destination file.</span></span> <span data-ttu-id="cd130-138">有數種方式可建立連線管理員：</span><span class="sxs-lookup"><span data-stu-id="cd130-138">There are several ways to create the connection manager:</span></span>

-   <span data-ttu-id="cd130-139">在 [連線管理員]  區域，以滑鼠右鍵按一下然後選取 [新增連線]  。</span><span class="sxs-lookup"><span data-stu-id="cd130-139">In the **Connection Managers** area, right-click and select **New connection**.</span></span> <span data-ttu-id="cd130-140">在 [新增 SSIS 連線管理員]  對話方塊中，依序選取 [EXCEL]  和 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="cd130-140">In the **Add SSIS Connection Manager** dialog box, select **EXCEL** and then **Add**.</span></span>
 
-   <span data-ttu-id="cd130-141">在 [SSIS]  功能表上，選取 [新增連線]  。</span><span class="sxs-lookup"><span data-stu-id="cd130-141">On the **SSIS** menu, select **New connection**.</span></span> <span data-ttu-id="cd130-142">在 [新增 SSIS 連線管理員]  對話方塊中，依序選取 [EXCEL]  和 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="cd130-142">In the **Add SSIS Connection Manager** dialog box, select **EXCEL** and then **Add**.</span></span>

-   <span data-ttu-id="cd130-143">當您在 [Excel 來源編輯器]或 [Excel 目的地編輯器] 的 [連線管理員] 頁面設定 [Excel 來源] 或 [Excel 目的地] 的同時建立連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cd130-143">Create the connection manager at the same time that you configure the **Excel Source** or the **Excel Destination** on the **Connection manager** page of the **Excel Source Editor** or of the **Excel Destination Editor**.</span></span>

### <a name="in-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="cd130-144">在 [SQL Server 匯入和匯出精靈] 中</span><span class="sxs-lookup"><span data-stu-id="cd130-144">In the SQL Server Import and Export Wizard</span></span>
<span data-ttu-id="cd130-145">在 [匯入和匯出精靈] 的 [選擇資料來源] 或 [選擇目的地] 頁面上，選取 [資料來源] 清單中的 **Microsoft Excel**。</span><span class="sxs-lookup"><span data-stu-id="cd130-145">In the Import and Export Wizard, on the **Choose a Data Source** or **Choose a Destination** page, select **Microsoft Excel** in the **Data source** list.</span></span>

<span data-ttu-id="cd130-146">如果您在資料來源清單中看不到 Excel，請確定是否執行 32 位元精靈。</span><span class="sxs-lookup"><span data-stu-id="cd130-146">If you don't see Excel in the list of data sources, make sure you're running the 32-bit wizard.</span></span> <span data-ttu-id="cd130-147">Excel 連線元件均通常是 32 位元檔案，在 64 位元精靈中不會顯示。</span><span class="sxs-lookup"><span data-stu-id="cd130-147">The Excel connectivity components are typically 32-bit files and aren't visible in the 64-bit wizard.</span></span>

## <a name="excel-file-and-file-path"></a><a name="excel-file"></a> <span data-ttu-id="cd130-148">Excel 檔案和檔案路徑</span><span class="sxs-lookup"><span data-stu-id="cd130-148">Excel file and file path</span></span>

<span data-ttu-id="cd130-149">要提供資訊的第一項資訊是 Excel 檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="cd130-149">The first piece of info to provide is the path and file name for the Excel file.</span></span> <span data-ttu-id="cd130-150">提供此資訊的方式是使用 [Excel 連線管理員編輯器]  中的 SSIS 套件，或在 [匯入和匯出精靈] 的 [選擇資料來源]  或 [選擇目的地]  頁面。</span><span class="sxs-lookup"><span data-stu-id="cd130-150">You provide this info in the **Excel Connection Manager Editor** in an SSIS package, or on the **Choose a Data Source** or **Choose a Destination** page of the Import and Export Wizard.</span></span>

<span data-ttu-id="cd130-151">以下列格式輸入路徑和檔案名稱：</span><span class="sxs-lookup"><span data-stu-id="cd130-151">Enter the path and file name in the following format:</span></span>

-   <span data-ttu-id="cd130-152">本機電腦上的檔案為 **C:\\TestData.xlsx**。</span><span class="sxs-lookup"><span data-stu-id="cd130-152">For a file on the local computer, **C:\\TestData.xlsx**.</span></span>

-   <span data-ttu-id="cd130-153">網路共用上的檔案為 **\\\\Sales\\Data\\TestData.xlsx**。</span><span class="sxs-lookup"><span data-stu-id="cd130-153">For a file on a network share, **\\\\Sales\\Data\\TestData.xlsx**.</span></span>

<span data-ttu-id="cd130-154">或者，按一下 [瀏覽] 以使用 [開啟] 對話方塊找出試算表。</span><span class="sxs-lookup"><span data-stu-id="cd130-154">Or, click **Browse** to locate the spreadsheet by using the **Open** dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cd130-155">您不能連接至受密碼保護的 Excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="cd130-155">You can't connect to a password-protected Excel file.</span></span>

## <a name="excel-version"></a><a name="excel-version"></a> <span data-ttu-id="cd130-156">Excel 版本</span><span class="sxs-lookup"><span data-stu-id="cd130-156">Excel version</span></span>

<span data-ttu-id="cd130-157">要提供的第二項資訊是 Excel 檔案的版本。</span><span class="sxs-lookup"><span data-stu-id="cd130-157">The second piece of info to provide is the version of the Excel file.</span></span> <span data-ttu-id="cd130-158">提供此資訊的方式是使用 [Excel 連線管理員編輯器]  中的 SSIS 套件，或在 [匯入和匯出精靈] 的 [選擇資料來源]  或 [選擇目的地]  頁面。</span><span class="sxs-lookup"><span data-stu-id="cd130-158">You provide this info in the **Excel Connection Manager Editor** in an SSIS package, or on the **Choose a Data Source** or **Choose a Destination** page of the Import and Export Wizard.</span></span>

<span data-ttu-id="cd130-159">選取用於建立檔案的 Microsoft Excel 版本，或另一個相容版本。</span><span class="sxs-lookup"><span data-stu-id="cd130-159">Select the version of Microsoft Excel that was used to create the file, or another compatible version.</span></span> <span data-ttu-id="cd130-160">例如，如果您無法安裝 2016 連線元件，您可以安裝 2010 元件並選取此清單中的 [Microsoft Excel 2007-2010]  。</span><span class="sxs-lookup"><span data-stu-id="cd130-160">For example, if you had trouble installing the 2016 connectivity components, you can install the 2010 components and select **Microsoft Excel 2007-2010** in this list.</span></span>

<span data-ttu-id="cd130-161">如果您只安裝了較舊版本的連線元件，可能無法選取清單中的較新 Excel 版本。</span><span class="sxs-lookup"><span data-stu-id="cd130-161">You may not be able to select newer Excel versions in the list if you only have older versions of the connectivity components installed.</span></span> <span data-ttu-id="cd130-162">**Excel 版本**清單包含 SSIS 支援的所有 Excel 版本。</span><span class="sxs-lookup"><span data-stu-id="cd130-162">The **Excel version** list includes all the versions of Excel supported by SSIS.</span></span> <span data-ttu-id="cd130-163">這份清單中的項目存在並不表示已安裝必要的連線元件。</span><span class="sxs-lookup"><span data-stu-id="cd130-163">The presence of items in this list does not indicate that the required connectivity components are installed.</span></span> <span data-ttu-id="cd130-164">例如，即使您尚未安裝 2016 連線元件，**Microsoft Excel 2016** 也會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="cd130-164">For example, **Microsoft Excel 2016** appears in the list even if you have not installed the 2016 connectivity components.</span></span>

## <a name="first-row-has-column-names"></a><a name="first-row"></a> <span data-ttu-id="cd130-165">第一個資料列具有資料行名稱</span><span class="sxs-lookup"><span data-stu-id="cd130-165">First row has column names</span></span>

<span data-ttu-id="cd130-166">如果您從 Excel 匯入資料，下一個步驟就是指出資料的第一個資料列是否包含資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="cd130-166">If you're importing data from Excel, the next step is to indicate whether the first row of the data contains column names.</span></span> <span data-ttu-id="cd130-167">提供此資訊的方式是使用 [Excel 連線管理員編輯器]  中的 SSIS 套件，或在 [匯入和匯出精靈] 的 [選擇資料來源]  頁面上。</span><span class="sxs-lookup"><span data-stu-id="cd130-167">You provide this info in the **Excel Connection Manager Editor** in an SSIS package, or on the **Choose a Data Source** page of the Import and Export Wizard.</span></span>

-   <span data-ttu-id="cd130-168">如果因為來源資料未包含資料行名稱而停用此選項，精靈會使用 F1、F2 等作為資料行標題。</span><span class="sxs-lookup"><span data-stu-id="cd130-168">If you disable this option because the source data doesn't contain column names, the wizard uses F1, F2, and so forth, as column headings.</span></span>
-   <span data-ttu-id="cd130-169">如果資料包含資料行名稱，但您停用了此選項，則精靈會將資料行名稱匯入為資料的第一列。</span><span class="sxs-lookup"><span data-stu-id="cd130-169">If the data contains column names, but you disable this option, the wizard imports the column names as the first row of data.</span></span>
-   <span data-ttu-id="cd130-170">如果資料不包含資料行名稱，但您啟用了此選項，則精靈會將來源資料的第一列用來作為資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="cd130-170">If the data does not contain column names, but you enable this option, the wizard uses the first row of source data as the column names.</span></span> <span data-ttu-id="cd130-171">在此情況下，來源資料的第一列已不再包含在資料本身。</span><span class="sxs-lookup"><span data-stu-id="cd130-171">In this case, the first row of source data is no longer included in the data itself.</span></span>

<span data-ttu-id="cd130-172">如果您要從 Excel 匯出資料，且啟用了此選項，則匯出資料的第一列會包含資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="cd130-172">If you're exporting data from Excel, and you enable this option, the first row of exported data includes the column names.</span></span>

## <a name="worksheets-and-ranges"></a><a name="sheets-ranges"></a> <span data-ttu-id="cd130-173">工作表和範圍</span><span class="sxs-lookup"><span data-stu-id="cd130-173">Worksheets and ranges</span></span>

<span data-ttu-id="cd130-174">有三種 Excel 物件可以作為資料的來源或目的地：工作表、您指定位址的資料格具名範圍或未具名範圍。</span><span class="sxs-lookup"><span data-stu-id="cd130-174">There are three types of Excel objects that you can use as the source or destination for your data: a worksheet, a named range, or an unnamed range of cells that you specify with its address.</span></span>

-   <span data-ttu-id="cd130-175">**工作表。**</span><span class="sxs-lookup"><span data-stu-id="cd130-175">**Worksheet.**</span></span> <span data-ttu-id="cd130-176">若要指定工作表，請在工作表名稱結尾加上 `$` 字元，並以分隔符號括住字串，例如 **[Sheet1$]** 。</span><span class="sxs-lookup"><span data-stu-id="cd130-176">To specify a worksheet, append the `$` character to the end of the sheet name and add delimiters around the string - for example, **[Sheet1$]**.</span></span> <span data-ttu-id="cd130-177">或者，在現有資料表和檢視的清單中，尋找結尾為 `$` 字元的名稱。</span><span class="sxs-lookup"><span data-stu-id="cd130-177">Or, look for a name that ends with the `$` character in the list of existing tables and views.</span></span>

-   <span data-ttu-id="cd130-178">**命名範圍。**</span><span class="sxs-lookup"><span data-stu-id="cd130-178">**Named range.**</span></span> <span data-ttu-id="cd130-179">若要指定命名範圍，請提供範圍名稱，例如 **MyDataRange**。</span><span class="sxs-lookup"><span data-stu-id="cd130-179">To specify a named range, provide the range name - for example, **MyDataRange**.</span></span> <span data-ttu-id="cd130-180">或者，在現有資料表和檢視的清單中，尋找結尾不是 `$` 字元的名稱。</span><span class="sxs-lookup"><span data-stu-id="cd130-180">Or, look for a name that does not end with the `$` character in the list of existing tables and views.</span></span>
    
-   <span data-ttu-id="cd130-181">**未命名範圍。**</span><span class="sxs-lookup"><span data-stu-id="cd130-181">**Unnamed range.**</span></span> <span data-ttu-id="cd130-182">若要指定尚未命名的儲存格範圍，請在工作表名稱結尾加上 $ 字元、指定範圍，再以分隔符號括住字串，例如 **[Sheet1$A1:B4]** 。</span><span class="sxs-lookup"><span data-stu-id="cd130-182">To specify a range of cells that you haven't named, append the $ character to the end of the sheet name, add the range specification, and add delimiters around the string - for example, **[Sheet1$A1:B4]**.</span></span>

<span data-ttu-id="cd130-183">若要選取或指定您想要用作資料來源或目的地的 Excel 物件類型，請執行下列事項之一：</span><span class="sxs-lookup"><span data-stu-id="cd130-183">To select or specify the type of Excel object that you want to use as the source or destination for your data, do one of the following things:</span></span>

### <a name="in-ssis"></a><span data-ttu-id="cd130-184">在 SSIS 中</span><span class="sxs-lookup"><span data-stu-id="cd130-184">In SSIS</span></span>

<span data-ttu-id="cd130-185">在 SSIS 中，在 [Excel 來源編輯器] 或 [Excel 目的地編輯器] 的 [連線管理員] 頁面上，執行下列事項之一：</span><span class="sxs-lookup"><span data-stu-id="cd130-185">In SSIS, on the **Connection manager** page of the **Excel Source Editor** or of the **Excel Destination Editor**, do one of the following things:</span></span>

-   <span data-ttu-id="cd130-186">若要使用**工作表**或**具名範圍**，請選取 [資料表或檢視]  作為 [資料存取模式]  。</span><span class="sxs-lookup"><span data-stu-id="cd130-186">To use a **worksheet** or a **named range**, select **Table or view** as the **Data access mode**.</span></span> <span data-ttu-id="cd130-187">然後，在 [Excel 工作表的名稱]  清單中，選取工作表或具名範圍。</span><span class="sxs-lookup"><span data-stu-id="cd130-187">Then, in the **Name of the Excel sheet** list, select the worksheet or named range.</span></span>

-   <span data-ttu-id="cd130-188">若要使用您指定位址的**未具名範圍**，請選取 [SQL 命令]  作為 [資料存取模式]  。</span><span class="sxs-lookup"><span data-stu-id="cd130-188">To use an **unnamed range** that you specify with its address, select **SQL command** as the **Data access mode**.</span></span> <span data-ttu-id="cd130-189">然後，在 [SQL 命令文字]  欄位中，輸入類似下列範例的查詢：</span><span class="sxs-lookup"><span data-stu-id="cd130-189">Then, in the **SQL command text** field, enter a query like the following example:</span></span>

    ```sql
    SELECT * FROM [Sheet1$A1:B5]
    ```

### <a name="in-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="cd130-190">在 [SQL Server 匯入和匯出精靈] 中</span><span class="sxs-lookup"><span data-stu-id="cd130-190">In the SQL Server Import and Export Wizard</span></span>
<span data-ttu-id="cd130-191">在 [匯入和匯出精靈] 中，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="cd130-191">In the Import and Export Wizard, do one of the following things:</span></span>

-   <span data-ttu-id="cd130-192">當您從 Excel **匯入**時，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="cd130-192">When you're **importing** from Excel, do one of the following things:</span></span>

    -   <span data-ttu-id="cd130-193">若要使用 **工作表** 或 **具名範圍**，請在 [Specify table copy or query] \(指定資料表複製或查詢)  畫面，選取 [Copy data from one or more tables or views] \(從一或多個資料表或檢視複製資料)  。</span><span class="sxs-lookup"><span data-stu-id="cd130-193">To use a **worksheet** or a **named range**, on the **Specify table copy or query** page, select **Copy data from one or more tables or views**.</span></span> <span data-ttu-id="cd130-194">然後，在 [Select Source Tables and Views] 選取來源資料表和檢視)  頁面上，於 [來源]  資料行中，選取來源工作表及具名範圍。</span><span class="sxs-lookup"><span data-stu-id="cd130-194">Then, on the **Select Source Tables and Views** page, in the **Source** column, select the source worksheets and named ranges.</span></span>

    -   <span data-ttu-id="cd130-195">若要您使用指定位址的 **未具名範圍** ，請在 [Specify table copy or query] \(指定資料表複製或查詢)  頁面上，選取 [Write a query to specify the data to transfer] \(撰寫查詢來指定要傳送的資料)  。</span><span class="sxs-lookup"><span data-stu-id="cd130-195">To use an **unnamed range** that you specify with its address, on the **Specify table copy or query** page, select **Write a query to specify the data to transfer**.</span></span> <span data-ttu-id="cd130-196">然後，在 [Provide a Source Query] \(提供來源查詢)  頁面上，提供類似於下列範例的查詢：</span><span class="sxs-lookup"><span data-stu-id="cd130-196">Then, on the **Provide a Source Query** page, provide a query similar to the following example:</span></span>

        ```sql
        SELECT * FROM [Sheet1$A1:B5]
        ```

-   <span data-ttu-id="cd130-197">當您 **匯出** Excel 時，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="cd130-197">When you're **exporting** to Excel, do one of the following things:</span></span>

    -   <span data-ttu-id="cd130-198">若要使用 **工作表** 或 **具名範圍**，請在 [Select Source Tables and Views] \(選取來源資料表和檢視)  頁面上的 [目的地]  資料行中，選取目的地工作表與具名範圍。</span><span class="sxs-lookup"><span data-stu-id="cd130-198">To use a **worksheet** or a **named range**, on the **Select Source Tables and Views** page, in the **Destination** column, select the destination worksheets and named ranges.</span></span>

    -   <span data-ttu-id="cd130-199">若要使用指定位址的 **未具名範圍** ，請在 [Select Source Tables and Views] \(選取來源資料表和檢視)  頁面的 [目的地]  資料行中，以不含分隔符號的下列格式輸入範圍： `Sheet1$A1:B5` 。</span><span class="sxs-lookup"><span data-stu-id="cd130-199">To use an **unnamed range** that you specify with its address, on the **Select Source Tables and Views** page, in the **Destination** column, enter the range in the following format without delimiters: `Sheet1$A1:B5`.</span></span> <span data-ttu-id="cd130-200">精靈會新增分隔符號。</span><span class="sxs-lookup"><span data-stu-id="cd130-200">The wizard adds the delimiters.</span></span>

<span data-ttu-id="cd130-201">選取或輸入要匯入或匯出的 Excel 物件之後，您也可以在精靈的 [Select Source Tables and Views] \(選取來源資料表和檢視)  頁面上執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cd130-201">After you select or enter the Excel objects to import or export, you can also do the following things on the **Select Source Tables and Views** page of the wizard:</span></span>

-   <span data-ttu-id="cd130-202">選取 [編譯對應]  來檢閱來源與目的地之間的資料行對應。</span><span class="sxs-lookup"><span data-stu-id="cd130-202">Review column mappings between source and destination by selecting **Edit Mappings**.</span></span>

-   <span data-ttu-id="cd130-203">預覽範例資料，選取 [預覽]  以確定它如您的預期。</span><span class="sxs-lookup"><span data-stu-id="cd130-203">Preview sample data to make sure it's what you expect by selecting **Preview**.</span></span>

## <a name="issues-with-data-types"></a><a name="issues-types"></a> <span data-ttu-id="cd130-204">資料類型的問題</span><span class="sxs-lookup"><span data-stu-id="cd130-204">Issues with data types</span></span>

### <a name="data-types"></a><span data-ttu-id="cd130-205">資料類型</span><span class="sxs-lookup"><span data-stu-id="cd130-205">Data types</span></span>

<span data-ttu-id="cd130-206">Excel 驅動程式只能辨識有限的一組資料類型。</span><span class="sxs-lookup"><span data-stu-id="cd130-206">The Excel driver recognizes only a limited set of data types.</span></span> <span data-ttu-id="cd130-207">例如，所有的數值資料行都會被解譯為倍整數 (DT_R8)，而所有的字串資料行 (備忘錄資料行除外) 全都會被解譯成 255 個字元的 Unicode 字串 (DT_WSTR)。</span><span class="sxs-lookup"><span data-stu-id="cd130-207">For example, all numeric columns are interpreted as doubles (DT_R8), and all string columns (other than memo columns) are interpreted as 255-character Unicode strings (DT_WSTR).</span></span> <span data-ttu-id="cd130-208">SSIS 對應 Excel 資料類型的情況如下：</span><span class="sxs-lookup"><span data-stu-id="cd130-208">SSIS maps the Excel data types as follows:</span></span>

-   <span data-ttu-id="cd130-209">數值 - 雙精確度浮點數 (DT_R8)</span><span class="sxs-lookup"><span data-stu-id="cd130-209">Numeric - double-precision float (DT_R8)</span></span>

-   <span data-ttu-id="cd130-210">貨幣 - 貨幣 (DT_CY)</span><span class="sxs-lookup"><span data-stu-id="cd130-210">Currency - currency (DT_CY)</span></span>

-   <span data-ttu-id="cd130-211">布林值 - 布林值 (DT_BOOL)</span><span class="sxs-lookup"><span data-stu-id="cd130-211">Boolean - Boolean (DT_BOOL)</span></span>

-   <span data-ttu-id="cd130-212">日期/時間 - datetime (DT_DATE)</span><span class="sxs-lookup"><span data-stu-id="cd130-212">Date/time - datetime (DT_DATE)</span></span>

-   <span data-ttu-id="cd130-213">字串 - Unicode 字串，長度 255 (DT_WSTR)</span><span class="sxs-lookup"><span data-stu-id="cd130-213">String - Unicode string, length 255 (DT_WSTR)</span></span>

-   <span data-ttu-id="cd130-214">備忘錄 - Unicode 文字資料流 (DT_NTEXT)</span><span class="sxs-lookup"><span data-stu-id="cd130-214">Memo - Unicode text stream (DT_NTEXT)</span></span>

### <a name="data-type-and-length-conversions"></a><span data-ttu-id="cd130-215">資料類型和長度轉換</span><span class="sxs-lookup"><span data-stu-id="cd130-215">Data type and length conversions</span></span>

<span data-ttu-id="cd130-216">SSIS 不會隱含地轉換資料類型。</span><span class="sxs-lookup"><span data-stu-id="cd130-216">SSIS does not implicitly convert data types.</span></span> <span data-ttu-id="cd130-217">因此，您可能必須使用衍生的資料行轉換或資料轉換，在將 Excel 資料載入至非 Excel 目的地之前明確轉換 Excel 資料，或是在將資料載入至 Excel 目的地之前，轉換來自非 Excel 來源的資料。</span><span class="sxs-lookup"><span data-stu-id="cd130-217">As a result, you may have to use Derived Column or Data Conversion transformations to convert Excel data explicitly before loading it into a destination other than Excel, or to convert data from a source other than Excel before loading it into an Excel destination.</span></span>

<span data-ttu-id="cd130-218">以下是一些可能需要的轉換範例：</span><span class="sxs-lookup"><span data-stu-id="cd130-218">Here are some examples of the conversions that may be required:</span></span>  
  
-   <span data-ttu-id="cd130-219">Unicode Excel 字串資料行與具有特定字碼頁之非 Unicode 字串資料行之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="cd130-219">Conversion between Unicode Excel string columns and non-Unicode string columns with specific codepage.</span></span>
  
-   <span data-ttu-id="cd130-220">255 個字元之 Excel 字串資料行與不同長度之字串資料行之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="cd130-220">Conversion between 255-character Excel string columns and string columns of different lengths.</span></span>
  
-   <span data-ttu-id="cd130-221">雙精確度 Excel 數值資料行與其他類型之數值資料行之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="cd130-221">Conversion between double-precision Excel numeric columns and numeric columns of other types.</span></span>

> [!TIP]
> <span data-ttu-id="cd130-222">如果您使用 [匯入和匯出精靈]，且您的資料需要這其中的某些轉換，精靈會為您設定所需的轉換。</span><span class="sxs-lookup"><span data-stu-id="cd130-222">If you're using the Import and Export Wizard, and your data requires some of these conversions, the wizard configures the necessary conversions for you.</span></span> <span data-ttu-id="cd130-223">因此，即使是您想要使用 SSIS 套件時，使用 [匯入和匯出精靈] 來建立初始套件可能會很實用。</span><span class="sxs-lookup"><span data-stu-id="cd130-223">As a result, even when you want to use an SSIS package, it may be useful to create the initial package by using the Import and Export Wizard.</span></span> <span data-ttu-id="cd130-224">讓精靈為您建立並設定連線管理員、來源、轉換和目的地。</span><span class="sxs-lookup"><span data-stu-id="cd130-224">Let the wizard create and configure connection managers, sources, transformations, and destinations for you.</span></span>

## <a name="issues-with-importing"></a><a name="issues-importing"></a> <span data-ttu-id="cd130-225">匯入的問題</span><span class="sxs-lookup"><span data-stu-id="cd130-225">Issues with importing</span></span>

### <a name="empty-rows"></a><span data-ttu-id="cd130-226">空的資料列</span><span class="sxs-lookup"><span data-stu-id="cd130-226">Empty rows</span></span>

<span data-ttu-id="cd130-227">當您指定工作表或具名範圍為來源時，驅動程式會讀取「連續的」  資料格區塊，從工作表或範圍左上角的第一個非空白資料格開始。</span><span class="sxs-lookup"><span data-stu-id="cd130-227">When you specify a worksheet or a named range as the source, the driver reads the *contiguous* block of cells starting with the first non-empty cell in the upper-left corner of the worksheet or range.</span></span> <span data-ttu-id="cd130-228">因此，您的資料不需要從資料列 1 開始，但您的來源資料中不能有空的資料列。</span><span class="sxs-lookup"><span data-stu-id="cd130-228">As a result, your data doesn't have to start in row 1, but you can't have empty rows in the source data.</span></span> <span data-ttu-id="cd130-229">例如，您不能在資料行標題與資料列之間有空的資料列，或是標題後面接著在工作表頂端有空的資料列。</span><span class="sxs-lookup"><span data-stu-id="cd130-229">For example, you can't have an empty row between the column headers and the data rows, or a title followed by empty rows at the top of the worksheet.</span></span>

<span data-ttu-id="cd130-230">如果資料上方有空的資料列，便無法作為工作表來查詢資料。</span><span class="sxs-lookup"><span data-stu-id="cd130-230">If there are empty rows above your data, you can't query the data as a worksheet.</span></span> <span data-ttu-id="cd130-231">在 Excel 中，您必須選取資料範圍並將名稱指派給該範圍，然後查詢具名範圍，而不是工作表。</span><span class="sxs-lookup"><span data-stu-id="cd130-231">In Excel, you have to select your range of data and assign a name to the range, and then query the named range instead of the worksheet.</span></span>

### <a name="missing-values"></a><span data-ttu-id="cd130-232">遺漏值</span><span class="sxs-lookup"><span data-stu-id="cd130-232">Missing values</span></span>

<span data-ttu-id="cd130-233">Excel 驅動程式會在指定來源中讀取特定資料列數目 (依預設為八個資料列)，以猜測各資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="cd130-233">The Excel driver reads a certain number of rows (by default, eight rows) in the specified source to guess at the data type of each column.</span></span> <span data-ttu-id="cd130-234">當資料行可能包含混合資料類型，尤其是數值資料與文字資料混合時，驅動程式會做出有利於大部分資料類型的決定，並於包含其他類型資料的資料格中傳回 Null 值。</span><span class="sxs-lookup"><span data-stu-id="cd130-234">When a column appears to contain mixed data types, especially numeric data mixed with text data, the driver decides in favor of the majority data type, and returns null values for cells that contain data of the other type.</span></span> <span data-ttu-id="cd130-235">(在繫結中，以數值類型優先)。Excel 工作表中大部分的資料格格式化選項，似乎都不會影響這項資料類型決定。</span><span class="sxs-lookup"><span data-stu-id="cd130-235">(In a tie, the numeric type wins.) Most cell formatting options in the Excel worksheet do not seem to affect this data type determination.</span></span>

<span data-ttu-id="cd130-236">您可以藉由指定「匯入模式」將所有值當作文字匯入，來修改 Excel 驅動程式的這項行為。</span><span class="sxs-lookup"><span data-stu-id="cd130-236">You can modify this behavior of the Excel driver by specifying Import Mode to import all values as text.</span></span> <span data-ttu-id="cd130-237">若要指定「匯入模式」，請在 [屬性] 視窗中將 `IMEX=1` 新增到 Excel 連線管理員之連接字串中的 [擴充屬性]  值。</span><span class="sxs-lookup"><span data-stu-id="cd130-237">To specify Import Mode, add `IMEX=1` to the value of **Extended Properties** in the connection string of the Excel connection manager in the Properties window.</span></span> 

### <a name="truncated-text"></a><span data-ttu-id="cd130-238">截斷的文字</span><span class="sxs-lookup"><span data-stu-id="cd130-238">Truncated text</span></span>

<span data-ttu-id="cd130-239">當驅動程式判斷出某個 Excel 資料行包含文字資料時，驅動程式將會根據其取樣的最長值來選取資料類型 (字串或備忘錄)。</span><span class="sxs-lookup"><span data-stu-id="cd130-239">When the driver determines that an Excel column contains text data, the driver selects the data type (string or memo) based on the longest value that it samples.</span></span> <span data-ttu-id="cd130-240">如果驅動程式未在其取樣的資料列中發現任何長度超過 255 個字元的值，則會將該資料行視為 255 個字元字串資料行而非備忘錄資料行</span><span class="sxs-lookup"><span data-stu-id="cd130-240">If the driver does not discover any values longer than 255 characters in the rows that it samples, it treats the column as a 255-character string column instead of a memo column.</span></span> <span data-ttu-id="cd130-241">因此，長度超過 255 個字元的值可能會被截斷。</span><span class="sxs-lookup"><span data-stu-id="cd130-241">Therefore, values longer than 255 characters may be truncated.</span></span>

<span data-ttu-id="cd130-242">若要從備忘資料行匯入資料而不截斷，您有兩個選項：</span><span class="sxs-lookup"><span data-stu-id="cd130-242">To import data from a memo column without truncation, you have two options:</span></span>

-   <span data-ttu-id="cd130-243">確定至少一個取樣的資料列中的備忘錄資料行，包含長度超過 255 個字元的值</span><span class="sxs-lookup"><span data-stu-id="cd130-243">Make sure that the memo column in at least one of the sampled rows contains a value longer than 255 characters</span></span>

-   <span data-ttu-id="cd130-244">增加驅動程式取樣的資料列數目，以包含這類資料列。</span><span class="sxs-lookup"><span data-stu-id="cd130-244">Increase the number of rows sampled by the driver to include such a row.</span></span> <span data-ttu-id="cd130-245">您可以提高下列登錄機碼下的 **TypeGuessRows** 值，藉以增加取樣的資料列數目：</span><span class="sxs-lookup"><span data-stu-id="cd130-245">You can increase the number of rows sampled by increasing the value of **TypeGuessRows** under the following registry key:</span></span>

| <span data-ttu-id="cd130-246">可轉散發套件的元件版本</span><span class="sxs-lookup"><span data-stu-id="cd130-246">Redistributable components version</span></span> | <span data-ttu-id="cd130-247">登錄機碼</span><span class="sxs-lookup"><span data-stu-id="cd130-247">Registry key</span></span> |
|---|---|
| <span data-ttu-id="cd130-248">Excel 2016</span><span class="sxs-lookup"><span data-stu-id="cd130-248">Excel 2016</span></span> | <span data-ttu-id="cd130-249">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel</span><span class="sxs-lookup"><span data-stu-id="cd130-249">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel</span></span> |
| <span data-ttu-id="cd130-250">Excel 2010</span><span class="sxs-lookup"><span data-stu-id="cd130-250">Excel 2010</span></span> | <span data-ttu-id="cd130-251">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\14.0\Access Connectivity Engine\Engines\Excel</span><span class="sxs-lookup"><span data-stu-id="cd130-251">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\14.0\Access Connectivity Engine\Engines\Excel</span></span> |
| | |

## <a name="issues-with-exporting"></a><a name="issues-exporting"></a> <span data-ttu-id="cd130-252">匯出的問題</span><span class="sxs-lookup"><span data-stu-id="cd130-252">Issues with exporting</span></span>

### <a name="create-a-new-destination-file"></a><span data-ttu-id="cd130-253">建立新的目的地檔案</span><span class="sxs-lookup"><span data-stu-id="cd130-253">Create a new destination file</span></span>

#### <a name="in-ssis"></a><span data-ttu-id="cd130-254">在 SSIS 中</span><span class="sxs-lookup"><span data-stu-id="cd130-254">In SSIS</span></span>

<span data-ttu-id="cd130-255">建立 Excel 連線管理員，並使用您想要建立的新 Excel 檔案路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="cd130-255">Create an Excel Connection Manager with the path and file name of the new Excel file that you want to create.</span></span> <span data-ttu-id="cd130-256">然後，在 [Excel 目的地編輯器]  中，針對 [Excel 工作表名稱]  選取 [新增]  建立目的地工作表。</span><span class="sxs-lookup"><span data-stu-id="cd130-256">Then, in the **Excel Destination Editor**, for **Name of the Excel sheet**, select **New** to create the destination worksheet.</span></span> <span data-ttu-id="cd130-257">此時，SSIS 會使用指定的工作表，建立新的 Excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="cd130-257">At this point, SSIS creates the new Excel file with the specified worksheet.</span></span>

#### <a name="in-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="cd130-258">在 [SQL Server 匯入和匯出精靈] 中</span><span class="sxs-lookup"><span data-stu-id="cd130-258">In the SQL Server Import and Export Wizard</span></span>

<span data-ttu-id="cd130-259">在 [選擇目的地]  頁面上，選取 [瀏覽]  。</span><span class="sxs-lookup"><span data-stu-id="cd130-259">On the **Choose a Destination** page, select **Browse**.</span></span> <span data-ttu-id="cd130-260">在 [開啟]  對話方塊方塊中，覽至您想要用來建立新 Excel 檔案的資料夾、提供新檔案的名稱，然後選取 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="cd130-260">In the **Open** dialog box, navigate to the folder where you want the new Excel file to be created, provide a name for the new file, and then select **Open**.</span></span>

### <a name="export-to-a-large-enough-range"></a><span data-ttu-id="cd130-261">匯出到夠大的範圍</span><span class="sxs-lookup"><span data-stu-id="cd130-261">Export to a large enough range</span></span>

<span data-ttu-id="cd130-262">當您將範圍指定為目的地時，如果範圍的「資料行」  數目比來源資料還要少，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd130-262">When you specify a range as the destination, an error occurs if the range has fewer *columns* than the source data.</span></span> <span data-ttu-id="cd130-263">不過，如果您所指定範圍的「資料列」  數目比來源資料還要少，則精靈會繼續寫入資料列而不會有錯誤，並且會延伸範圍定義，以符合新的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="cd130-263">However, if the range that you specify has fewer *rows* than the source data, the wizard continues writing rows without error and extends the range definition to match the new number of rows.</span></span>

### <a name="export-long-text-values"></a><span data-ttu-id="cd130-264">匯出長文字值</span><span class="sxs-lookup"><span data-stu-id="cd130-264">Export long text values</span></span>

<span data-ttu-id="cd130-265">在 Excel 資料行中成功儲存長於 255 個字元的字串之前，驅動程式必須能將目的地資料行的資料類型辨識為 **備忘** ，而不是 **字串**。</span><span class="sxs-lookup"><span data-stu-id="cd130-265">Before you can successfully save strings longer than 255 characters to an Excel column, the driver must recognize the data type of the destination column as **memo** and not **string**.</span></span>

-   <span data-ttu-id="cd130-266">如果現有目的地資料表已包含資料列，則驅動程式所取樣的前幾個資料列必須在備忘資料行中至少包含一個值長於 255 個字元的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd130-266">If an existing destination table already contains rows of data, then the first few rows that are sampled by the driver must contain at least one instance of a value longer than 255 characters in the memo column.</span></span>

-   <span data-ttu-id="cd130-267">如果在套件設計期間或在執行階段或由 [匯入和匯出精靈] 建立新的目的地資料表，則 `CREATE TABLE` 陳述式必須使用 LONGTEXT (或其同義字之一) 作為目的地備忘資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="cd130-267">If a new destination table is created during package design or at run time or by the Import and Export Wizard, then the `CREATE TABLE` statement must use LONGTEXT (or one of its synonyms) as the data type of the destination memo column.</span></span> <span data-ttu-id="cd130-268">在精靈中，按一下 [資料行對應]\*\*\*\* 頁面的 [建立目的地資料表]\*\*\*\* 選項旁邊的 [編輯 SQL]\*\*\*\*，檢查 `CREATE TABLE` 陳述式並做必要的修訂。</span><span class="sxs-lookup"><span data-stu-id="cd130-268">In the wizard, check the `CREATE TABLE` statement and revise it, if necessary, by clicking **Edit SQL** next to the **Create destination table** option on the **Column Mappings** page.</span></span>

## <a name="related-content"></a><span data-ttu-id="cd130-269">相關內容</span><span class="sxs-lookup"><span data-stu-id="cd130-269">Related content</span></span>

<span data-ttu-id="cd130-270">如需本文中所述的元件和程序的詳細資訊，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="cd130-270">For more information about the components and procedures described in this article, see the following articles:</span></span>

### <a name="about-ssis"></a><span data-ttu-id="cd130-271">關於 SSIS</span><span class="sxs-lookup"><span data-stu-id="cd130-271">About SSIS</span></span>
[<span data-ttu-id="cd130-272">Excel 連線管理員</span><span class="sxs-lookup"><span data-stu-id="cd130-272">Excel Connection Manager</span></span>](connection-manager/excel-connection-manager.md)  
[<span data-ttu-id="cd130-273">Excel 來源</span><span class="sxs-lookup"><span data-stu-id="cd130-273">Excel Source</span></span>](data-flow/excel-source.md)  
[<span data-ttu-id="cd130-274">Excel 目的地</span><span class="sxs-lookup"><span data-stu-id="cd130-274">Excel Destination</span></span>](data-flow/excel-destination.md)  
[<span data-ttu-id="cd130-275">使用 Foreach 迴圈容器來執行 Excel 檔案和資料表迴圈</span><span class="sxs-lookup"><span data-stu-id="cd130-275">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
[<span data-ttu-id="cd130-276">以指令碼工作處理 Excel 檔案</span><span class="sxs-lookup"><span data-stu-id="cd130-276">Working with Excel Files with the Script Task</span></span>](extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)

### <a name="about-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="cd130-277">關於 SQL Server 匯入和匯出精靈</span><span class="sxs-lookup"><span data-stu-id="cd130-277">About the SQL Server Import and Export Wizard</span></span>
[<span data-ttu-id="cd130-278">連接至 Excel 資料來源</span><span class="sxs-lookup"><span data-stu-id="cd130-278">Connect to an Excel Data Source</span></span>](/sql/integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard)  
[<span data-ttu-id="cd130-279">透過匯入和匯出精靈的簡單範例開始使用</span><span class="sxs-lookup"><span data-stu-id="cd130-279">Get started with this simple example of the Import and Export Wizard</span></span>](/sql/integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard)

### <a name="other-articles"></a><span data-ttu-id="cd130-280">其他文章</span><span class="sxs-lookup"><span data-stu-id="cd130-280">Other articles</span></span>
[<span data-ttu-id="cd130-281">將 Excel 中的資料匯入 SQL Server 或 Azure SQL Database</span><span class="sxs-lookup"><span data-stu-id="cd130-281">Import data from Excel to SQL Server or Azure SQL Database</span></span>](/sql/relational-databases/import-export/import-data-from-excel-to-sql)  

