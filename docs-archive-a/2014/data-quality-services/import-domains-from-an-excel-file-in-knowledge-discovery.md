---
title: 將 Excel 檔案中的定義域匯入知識探索 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 4d3a3940-6c2a-4dc4-90eb-86f26012c165
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 332045466b95088523acda97a931168b0bb5c1ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598005"
---
# <a name="import-domains-from-an-excel-file-in-knowledge-discovery"></a><span data-ttu-id="d2955-102">在知識探索中匯入 Excel 檔案中的定義域</span><span class="sxs-lookup"><span data-stu-id="d2955-102">Import Domains from an Excel File in Knowledge Discovery</span></span>
  <span data-ttu-id="d2955-103">此主題描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 知識探索活動中匯入 Excel 檔案中的一個或多個定義域。</span><span class="sxs-lookup"><span data-stu-id="d2955-103">This topic describes how to import one or more domains from an Excel file in the [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) knowledge discovery activity.</span></span> <span data-ttu-id="d2955-104">此匯入程序會簡化知識產生程序，以節省時間和精力。</span><span class="sxs-lookup"><span data-stu-id="d2955-104">The import process simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="d2955-105">此程序可讓擁有 Excel 檔案或文字檔資料的人建立包含該資料的知識庫</span><span class="sxs-lookup"><span data-stu-id="d2955-105">It enables people who have data in an Excel file or a text file to create a knowledge base with that data.</span></span> <span data-ttu-id="d2955-106"> (參閱將[Excel 檔案中的值匯入定義域](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md)中，以取得將值匯入現有知識庫定義域的詳細資訊。不支援匯出至 Excel 檔案 ) 。</span><span class="sxs-lookup"><span data-stu-id="d2955-106">(See [Import Values from an Excel File into a Domain](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md) for more information about importing values into a domain of an existing knowledge base.) Exporting to an Excel file is not supported.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d2955-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="d2955-107">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="d2955-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="d2955-108">Prerequisites</span></span>  
 <span data-ttu-id="d2955-109">若要從 Excel 檔案匯入定義域，安裝 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 的電腦上必須已安裝 Excel；您必須已經使用定義域值建立 Excel 檔案 (請參閱 [How the import works](#How))；而且您必須已經建立及開啟要匯入定義域到其中的知識庫。</span><span class="sxs-lookup"><span data-stu-id="d2955-109">To import domains from an Excel file, Excel must be installed on the computer that the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] is installed on; you must have created an Excel file with domain values (see [How the import works](#How)); and you must have created and opened a knowledge base to import the domain into.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d2955-110">Security</span><span class="sxs-lookup"><span data-stu-id="d2955-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d2955-111">權限</span><span class="sxs-lookup"><span data-stu-id="d2955-111">Permissions</span></span>  
 <span data-ttu-id="d2955-112">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 角色或 dqs_administrator 角色，才能從 Excel 檔案匯入定義域。</span><span class="sxs-lookup"><span data-stu-id="d2955-112">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import domains from an Excel file.</span></span>  
  
##  <a name="import-domains-from-an-excel-file-into-a-knowledge-base"></a><a name="Import"></a> <span data-ttu-id="d2955-113">將 Excel 檔案中的定義域匯入知識庫</span><span class="sxs-lookup"><span data-stu-id="d2955-113">Import domains from an Excel file into a knowledge base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="d2955-114">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="d2955-114">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="d2955-115">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，執行下列其中一項作業：</span><span class="sxs-lookup"><span data-stu-id="d2955-115">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, do one of the following:</span></span>  
  
    -   <span data-ttu-id="d2955-116">若要建立新的知識庫，以便將資料匯入其中，請按一下 **[新增知識庫]**、輸入知識庫的名稱、為 **[建立知識庫來源]** 選取 **[無]**、選取 **[知識探索]** 活動，然後按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="d2955-116">Create a new knowledge base to import into by clicking **New knowledge base**, entering a name for the knowledge base, selecting **None** for **Create knowledge base from**, selecting the **Knowledge Discovery** activity, and then clicking **Create**.</span></span>  
  
    -   <span data-ttu-id="d2955-117">若要開啟現有知識庫，以便將資料匯入其中，請按一下 **[開啟知識庫]**、選取知識庫、選取 **[知識探索]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d2955-117">Open an existing knowledge base to import into by clicking **Open knowledge base**, selecting the knowledge base, selecting **Knowledge Discovery**, and then clicking **Next**.</span></span>  
  
3.  <span data-ttu-id="d2955-118">在 [對應] \*\*\*\* 頁面上，針對 [資料來源] \*\*\*\* 選取 [Excel 檔案] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d2955-118">In the **Map** page, select **Excel File** for **Data Source**.</span></span>  
  
4.  <span data-ttu-id="d2955-119">在 **[Excel 檔案]** 行上按一下 **[瀏覽]** 。</span><span class="sxs-lookup"><span data-stu-id="d2955-119">Click **Browse** on the **Excel File** line.</span></span>  
  
5.  <span data-ttu-id="d2955-120">在 **[選取 Excel 檔案]** 對話方塊中，移至您想要匯入之來源 Excel 檔案所在的資料夾，並選取此 Excel 檔案，然後按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="d2955-120">In the **Select an Excel File** dialog box, move to the folder that contains the Excel file that you want to import from, select the Excel file, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="d2955-121">從 **[工作表]** 下拉式清單中，選取您想要匯入之來源 Excel 檔案中的工作表。</span><span class="sxs-lookup"><span data-stu-id="d2955-121">From the **Worksheet** drop-down list, select the worksheet in the Excel file that you want to import from.</span></span>  
  
7.  <span data-ttu-id="d2955-122">如果您希望第一個資料列被視為資料標頭，而且您希望第一個資料列中的值當做資料行名稱使用，請選取 **[使用第一個資料列做為標頭]** 。</span><span class="sxs-lookup"><span data-stu-id="d2955-122">Select **Use First Row as header** if you want the first row to be considered a data header, and if you want the values in the first row to be used as column names.</span></span> <span data-ttu-id="d2955-123">如果您希望第一個資料列被視為資料值，此時 DQS 會將 Excel 標頭名稱 (英文字母) 用於資料行，請取消選取 **[使用第一個資料列做為標頭]** 。</span><span class="sxs-lookup"><span data-stu-id="d2955-123">Deselect **Use First Row as header** if you want the first row to be considered a data value, in which case DQS will use the Excel header names (alphabetical letters) for the column.</span></span>  
  
8.  <span data-ttu-id="d2955-124">選取資料行，然後將現有的定義域對應至此資料行，或是建立新的定義域，方法是按一下 **[建立定義域]** 圖示、在 **[建立定義域]** 對話方塊中建立定義域，然後將此定義域對應至此資料行。</span><span class="sxs-lookup"><span data-stu-id="d2955-124">Select a column, and then either map an existing domain to the column, or create a new domain by clicking the **Create a Domain** icon, creating a domain in the **Create a domain** dialog box, and then mapping the domain to the column.</span></span> <span data-ttu-id="d2955-125">此定義域的資料類型必須符合此資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d2955-125">The data type of the domain must match the data type of the column.</span></span> <span data-ttu-id="d2955-126">針對試算表的所有資料行重複上述步驟。</span><span class="sxs-lookup"><span data-stu-id="d2955-126">Repeat for all columns of the spreadsheet.</span></span>  
  
9. <span data-ttu-id="d2955-127">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="d2955-127">Click **Next**.</span></span>  
  
10. <span data-ttu-id="d2955-128">在 **[探索]** 頁面上，按一下 **[開始]** ，分析 Excel 試算表中的資料。</span><span class="sxs-lookup"><span data-stu-id="d2955-128">In the **Discover** page, click **Start** to analyze the data in the Excel spreadsheet.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d2955-129">如果您在資料上傳完畢之前離開頁面，檔案上傳程序將會終止。</span><span class="sxs-lookup"><span data-stu-id="d2955-129">If you leave the page before the data has been uploaded, the file upload process will be terminated.</span></span>  
  
11. <span data-ttu-id="d2955-130">確認分析已順利完成，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d2955-130">Verify that the analysis completed successfully, and then click **Next**.</span></span>  
  
12. <span data-ttu-id="d2955-131">在 **[管理定義域值]** 頁面中，確認正確的定義域已列在 **[定義域]** 清單中，而且值已輸入定義域資料表中。</span><span class="sxs-lookup"><span data-stu-id="d2955-131">In the **Manage Domain Values** page, verify that the correct domains are listed in the **Domains** list and that values are entered in the domain table.</span></span>  
  
13. <span data-ttu-id="d2955-132">按一下 **[完成]**，然後按一下 **[發行]** 發行知識庫，或是按一下 **[否]** ，不發行。</span><span class="sxs-lookup"><span data-stu-id="d2955-132">Click **Finish**, and then click **Publish** to publish the knowledge base, or **No** not to publish.</span></span>  
  
14. <span data-ttu-id="d2955-133">確認知識庫已發行，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d2955-133">Verify that the knowledge base was published, and then click **OK**.</span></span>  
  
##  <a name="follow-up-after-importing-domains-from-an-excel-file"></a><a name="FollowUp"></a><span data-ttu-id="d2955-134">後續操作：從 Excel 檔案匯入定義域之後</span><span class="sxs-lookup"><span data-stu-id="d2955-134">Follow Up: After Importing Domains from an Excel File</span></span>  
 <span data-ttu-id="d2955-135">當您從 Excel 檔案匯入定義域之後，您可以將知識加入至定義域，或是在清理或比對專案時使用定義域 (根據定義域的內容而定)。</span><span class="sxs-lookup"><span data-stu-id="d2955-135">After you import domains from an Excel file, you can add knowledge to the domains or use the domains in a cleansing or matching project, depending on the contents of the domains.</span></span> <span data-ttu-id="d2955-136">如需詳細資訊，請參閱[執行知識探索](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理定義域](../../2014/data-quality-services/managing-a-domain.md)、[管理複合定義域](../../2014/data-quality-services/managing-a-composite-domain.md)、[建立比對原則](../../2014/data-quality-services/create-a-matching-policy.md)、[資料清理](../../2014/data-quality-services/data-cleansing.md)或[資料比對](../../2014/data-quality-services/data-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="d2955-136">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md), [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md), [Data Cleansing](../../2014/data-quality-services/data-cleansing.md), or [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
##  <a name="how-the-import-works"></a><a name="How"></a><span data-ttu-id="d2955-137">匯入的運作方式</span><span class="sxs-lookup"><span data-stu-id="d2955-137">How the import works</span></span>  
 <span data-ttu-id="d2955-138">在匯入作業中，DQS 會依照以下方式解譯 Excel 檔案：</span><span class="sxs-lookup"><span data-stu-id="d2955-138">In the import operation, DQS interprets an Excel file as follows:</span></span>  
  
-   <span data-ttu-id="d2955-139">資料行表示定義域</span><span class="sxs-lookup"><span data-stu-id="d2955-139">A column represents a domain</span></span>  
  
-   <span data-ttu-id="d2955-140">資料列表示資料記錄</span><span class="sxs-lookup"><span data-stu-id="d2955-140">A row represents a data record</span></span>  
  
-   <span data-ttu-id="d2955-141">第一個資料列表示定義域名稱，或者為第一個資料值或記錄 (根據 **[使用第一個資料列做為標頭]** 核取方塊的設定而定)。</span><span class="sxs-lookup"><span data-stu-id="d2955-141">The first row either represents domain names or is the first data value or record, depending upon the setting of the **Use First Row as header** checkbox.</span></span>  
  
 <span data-ttu-id="d2955-142">下列規則適用於匯入作業：</span><span class="sxs-lookup"><span data-stu-id="d2955-142">The following rules apply to the import operation:</span></span>  
  
-   <span data-ttu-id="d2955-143">這個作業會將定義域值匯入知識庫中，</span><span class="sxs-lookup"><span data-stu-id="d2955-143">This operation imports domain values into a knowledge base.</span></span> <span data-ttu-id="d2955-144">而不會匯入定義域規則或比對原則。</span><span class="sxs-lookup"><span data-stu-id="d2955-144">It does not import domain rules or a matching policy.</span></span>  
  
-   <span data-ttu-id="d2955-145">Excel 檔案的副檔名可為 .xlsx、.xls 或 .csv。</span><span class="sxs-lookup"><span data-stu-id="d2955-145">The Excel file can have the extension .xlsx, .xls, or .csv.</span></span> <span data-ttu-id="d2955-146">要匯入定義域值或完整定義域的 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 電腦上必須安裝 Microsoft Excel。</span><span class="sxs-lookup"><span data-stu-id="d2955-146">Microsoft Excel must be installed on the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] computer to import domain values or a complete domain.</span></span> <span data-ttu-id="d2955-147">Excel 2003 及更新的版本都有受到支援。</span><span class="sxs-lookup"><span data-stu-id="d2955-147">Excel versions 2003 and later are supported.</span></span> <span data-ttu-id="d2955-148">如果使用 64 位元版本的 Excel，則僅支援 Excel 2003 檔案；Excel 2007 或 2010 檔案將不受支援。</span><span class="sxs-lookup"><span data-stu-id="d2955-148">If the 64-bit version of Excel is used, only Excel 2003 files will be supported; Excel 2007 or 2010 files will not be supported.</span></span>  
  
-   <span data-ttu-id="d2955-149">Excel 64 位元安裝不支援 Excel 檔案類型 .xlsx。</span><span class="sxs-lookup"><span data-stu-id="d2955-149">Excel files of type .xlsx are not supported for an Excel 64-bit installation.</span></span> <span data-ttu-id="d2955-150">如果您使用 64 位元 Excel，請將試算表檔案儲存為 .xls 檔案。</span><span class="sxs-lookup"><span data-stu-id="d2955-150">If you are using 64-bit Excel, save the spreadsheet file as an .xls file.</span></span>  
  
-   <span data-ttu-id="d2955-151">在 .xlsx 和 .xls 檔案中，資料行的資料類型是由前八個資料列中最普遍的資料類型所決定。</span><span class="sxs-lookup"><span data-stu-id="d2955-151">In .xlsx and .xls files, the data type of the column is determined by the most prevalent data type in the first eight rows.</span></span> <span data-ttu-id="d2955-152">如果資料格不符合該資料類型，將會為它提供 null 值。</span><span class="sxs-lookup"><span data-stu-id="d2955-152">If a cell does not conform to that data type, it will be given a null value.</span></span>  
  
-   <span data-ttu-id="d2955-153">在 .csv 檔案中，資料類型是由前八個資料列中最普遍的資料類型所決定。</span><span class="sxs-lookup"><span data-stu-id="d2955-153">In .csv files, the data type is determined by the most prevalent data type in the first eight rows.</span></span>  
  
-   <span data-ttu-id="d2955-154">如果 Excel 試算表中的值不符合定義域規則，則會將它匯入為無效的值。</span><span class="sxs-lookup"><span data-stu-id="d2955-154">A value in an Excel spreadsheet that does not conform to a domain rule will be imported as an invalid value.</span></span>  
  
-   <span data-ttu-id="d2955-155">如果 Excel 檔案的格式不正確或是已損毀，則匯入作業會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="d2955-155">If the Excel file is not in the right format or is corrupted, the import operation will result in an error.</span></span>  
  
  
