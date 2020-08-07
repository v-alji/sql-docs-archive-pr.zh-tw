---
title: 將 Excel 檔案中的值匯入定義域 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.failingvalues.f1
- sql12.dqs.kb.importfailing.f1
- sql12.dqs.kb.importselect.f1
ms.assetid: 04cde693-2043-477f-8417-fcc463ca7195
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7726f7ad41dfe3609a52f1d09473cab748580778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598004"
---
# <a name="import-values-from-an-excel-file-into-a-domain"></a><span data-ttu-id="1a23f-102">將 Excel 檔案中的值匯入定義域中</span><span class="sxs-lookup"><span data-stu-id="1a23f-102">Import Values from an Excel File into a Domain</span></span>
  <span data-ttu-id="1a23f-103">本主題描述如何將 Excel 檔案中的值匯入 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 的定義域中。</span><span class="sxs-lookup"><span data-stu-id="1a23f-103">This topic describes how to import values from an Excel file into a domain in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="1a23f-104">使用 Excel 檔案將定義域值匯入 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 應用程式可簡化知識產生程序，進而節省時間與精力。</span><span class="sxs-lookup"><span data-stu-id="1a23f-104">Using an Excel file to import domain values into the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="1a23f-105">此程序可讓在 Excel 檔案或文字檔案中擁有有效資料值清單的人，將這些值匯入定義域中。</span><span class="sxs-lookup"><span data-stu-id="1a23f-105">It enables people who have a list of valid data values in an Excel file or a text file to import those values into a domain.</span></span> <span data-ttu-id="1a23f-106">透過 Excel 檔案，您可以將定義域值匯入定義域或將定義域匯入知識庫中</span><span class="sxs-lookup"><span data-stu-id="1a23f-106">From an Excel file you can import domain values into a domain or domains into a knowledge base.</span></span> <span data-ttu-id="1a23f-107"> (參閱[知識探索中的從 Excel 檔案匯入定義域](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md)，以取得將定義域匯入知識庫的詳細資訊。不支援匯出至 excel 檔案 ) 。</span><span class="sxs-lookup"><span data-stu-id="1a23f-107">(See [Import Domains from an Excel File in Knowledge Discovery](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md) for more information about importing domains into a knowledge base.) Exporting to an Excel file is not supported.</span></span>  
  
 <span data-ttu-id="1a23f-108">您可以用兩種方式匯入資料值：</span><span class="sxs-lookup"><span data-stu-id="1a23f-108">You can import data values in two ways:</span></span>  
  
-   <span data-ttu-id="1a23f-109">建立新的定義域，然後從 Excel 檔案將值匯入定義域中，此時所有值都會加入至定義域。</span><span class="sxs-lookup"><span data-stu-id="1a23f-109">Create a new domain and then import values into it from an Excel file, in which case all values are added to the domain.</span></span>  
  
-   <span data-ttu-id="1a23f-110">將值匯入現有且已填入的定義域中，此時只會匯入新的值。</span><span class="sxs-lookup"><span data-stu-id="1a23f-110">Import values into an existing, populated domain, in which case only new values are imported.</span></span> <span data-ttu-id="1a23f-111">系統將不會匯入已經存在的所有值。</span><span class="sxs-lookup"><span data-stu-id="1a23f-111">All values that already exist will not be imported.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1a23f-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="1a23f-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="1a23f-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="1a23f-113">Prerequisites</span></span>  
 <span data-ttu-id="1a23f-114">若要從 Excel 檔案匯入定義域，安裝 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 應用程式的電腦上必須已安裝 Excel，才能匯入定義域值或完整定義域；您必須已經使用定義域值建立 Excel 檔案 (請參閱＜ [How the import works](#How)＞)；而且您必須已經建立及開啟要匯入定義域到其中的知識庫。</span><span class="sxs-lookup"><span data-stu-id="1a23f-114">To import domains from an Excel file, Excel must be installed on the computer that the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application is installed on in order to import domain values or a complete domain; you must have created an Excel file with domain values (see [How the import works](#How)); and you must have created and opened a knowledge base to import the domain into.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1a23f-115">Security</span><span class="sxs-lookup"><span data-stu-id="1a23f-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1a23f-116">權限</span><span class="sxs-lookup"><span data-stu-id="1a23f-116">Permissions</span></span>  
 <span data-ttu-id="1a23f-117">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 或 dqs_administrator 角色，才能從 Excel 檔案匯入定義域值。</span><span class="sxs-lookup"><span data-stu-id="1a23f-117">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import domains values from an Excel file.</span></span>  
  
##  <a name="import-values-from-an-excel-file-into-a-domain"></a><a name="Import"></a><span data-ttu-id="1a23f-118">將 Excel 檔案中的值匯入定義域中</span><span class="sxs-lookup"><span data-stu-id="1a23f-118">Import values from an Excel file into a domain</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="1a23f-119">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="1a23f-119">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="1a23f-120">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，於 [定義域管理] 活動中開啟知識庫。</span><span class="sxs-lookup"><span data-stu-id="1a23f-120">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="1a23f-121">如果您要將值加入至新的定義域，請使用 **[建立定義域]** 圖示來建立新的定義域，然後在定義域清單中選取新的定義域。</span><span class="sxs-lookup"><span data-stu-id="1a23f-121">If adding values to a new domain, create a new domain using the **Create a Domain** icon, and then select the new domain in the domain list.</span></span>  
  
4.  <span data-ttu-id="1a23f-122">如果您要將值加入至現有的定義域，請在定義域清單中選取定義域。</span><span class="sxs-lookup"><span data-stu-id="1a23f-122">If adding values to an existing domain, select the domain in the domain list.</span></span>  
  
5.  <span data-ttu-id="1a23f-123">按一下 **[定義域值]** 索引標籤、按一下圖示列中的 **[匯入值]** 圖示，然後按一下 **[從 Excel 匯入有效值]**。</span><span class="sxs-lookup"><span data-stu-id="1a23f-123">Click the **Domain Values** tab, click the **Import Values** icon in the icon bar, and then click **Import valid values from Excel**.</span></span>  
  
6.  <span data-ttu-id="1a23f-124">在 **[匯入定義域值]** 對話方塊中，按一下 **[瀏覽]**。</span><span class="sxs-lookup"><span data-stu-id="1a23f-124">In the **Import Domain Values** dialog box, click **Browse**.</span></span>  
  
7.  <span data-ttu-id="1a23f-125">在 **[選取檔案]** 對話方塊中，移至您想要匯入定義域值之來源 Excel 檔案所在的資料夾、選取此檔案 (副檔名為 .xlsx、.xls 或 .csv)，然後按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="1a23f-125">In the **Select file** dialog box, move to the folder that contains the Excel file that you want to import domain values from, select the file (with a .xlsx, .xls, or .csv extension), and then click **Open**.</span></span> <span data-ttu-id="1a23f-126">此檔案必須位於您從中執行 DQS 的用戶端上，或位於使用者擁有存取權的共用檔案中。</span><span class="sxs-lookup"><span data-stu-id="1a23f-126">The file must be either on the client that you run DQS from, or in a share file that the user has access to.</span></span>  
  
8.  <span data-ttu-id="1a23f-127">在 **[工作表]** 下拉式清單中，選取您要匯入的來源工作表。</span><span class="sxs-lookup"><span data-stu-id="1a23f-127">From the **Worksheet** drop-down list, select the worksheet that you are importing from.</span></span>  
  
9. <span data-ttu-id="1a23f-128">如果試算表中的第一個資料列代表定義域名稱，而且所有其他資料列都代表有效的定義域值，請選取 **[使用第一個資料列做為標頭]** 。</span><span class="sxs-lookup"><span data-stu-id="1a23f-128">Select **Use first row as header** if the first row in the spreadsheet represents the domain name, and all other rows represent valid domain values.</span></span>  
  
10. <span data-ttu-id="1a23f-129">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="1a23f-129">Click **OK**.</span></span> <span data-ttu-id="1a23f-130">此時，系統會顯示進度列，其中指出已經成功匯入的值數目、未匯入的數目，以及值的總數。</span><span class="sxs-lookup"><span data-stu-id="1a23f-130">A progress bar is displayed, with an indication of how many values have been imported successfully, how many were not imported, and the total number of values.</span></span> <span data-ttu-id="1a23f-131">按一下 **[取消]** 按鈕即可取消進度。</span><span class="sxs-lookup"><span data-stu-id="1a23f-131">Click the **Cancel** button to cancel the process.</span></span>  
  
11. <span data-ttu-id="1a23f-132">確認「匯入完成」已顯示在 [匯入定義域值]\*\*\*\* 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="1a23f-132">Verify that "Import complete" is displayed in the **Import Domain Values** dialog box.</span></span> <span data-ttu-id="1a23f-133">您可以在此對話方塊中查看已成功匯入的值，以及未匯入的值。</span><span class="sxs-lookup"><span data-stu-id="1a23f-133">See which values were successfully imported, and which were not, in this dialog box.</span></span> <span data-ttu-id="1a23f-134">它會指出檔案的名稱和檔案的路徑、作業的完成狀態、已經成功匯入的值數目、未匯入的值數目，以及已處理的值總數。</span><span class="sxs-lookup"><span data-stu-id="1a23f-134">It indicates the name of the file and the file's path, the completion status of the operation, how many values have been imported successfully, how many values were not imported, and the total number of values processed.</span></span>  
  
12. <span data-ttu-id="1a23f-135">對於未成功匯入的這些值，請按一下 [記錄檔]\*\*\*\* 顯示 [匯入定義域值 - 失敗值]\*\*\*\* 對話方塊，以便查看匯入作業失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="1a23f-135">For those values that were not successfully imported, click **Log** to display the **Import Domain Values - Failing Values** dialog box to see why the import operation failed.</span></span> <span data-ttu-id="1a23f-136">**[失敗值]** 資料行會顯示無法從 Excel 檔案匯入定義域的值，而 **[原因]** 資料行會說明匯入失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="1a23f-136">The **Failing Value** column shows the values that failed to be imported from an Excel file into a domain, and the **Reason** column explains why the import failed.</span></span> <span data-ttu-id="1a23f-137">您可以按一下 **[複製至剪貼簿]** ，將 **[失敗值]** 資料表複製到 [剪貼簿]，以便將該資料表複製到另一個程式，例如 Excel 試算表或 [記事本] 檔案。</span><span class="sxs-lookup"><span data-stu-id="1a23f-137">Click **Copy to clipboard** to copy the **Failing Value** table onto the clipboard, from which you can copy it into another program, such as an Excel spreadsheet or a Notepad file.</span></span> <span data-ttu-id="1a23f-138">按一下 **[確定]** 關閉 **[失敗值]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1a23f-138">Click **OK** to close the **Failing Values** dialog box.</span></span>  
  
13. <span data-ttu-id="1a23f-139">按一下 **[確定]** 完成匯入作業，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1a23f-139">Click **OK** to complete the import operation and close the dialog box.</span></span> <span data-ttu-id="1a23f-140">當匯入成功完成時， **[定義域值]** 頁面上的定義域值清單就會重新整理，而且將包含新匯入的值。</span><span class="sxs-lookup"><span data-stu-id="1a23f-140">When the import has completed successfully, the domain values list on the **Domain Values** page is refreshed and will include the new imported values.</span></span> <span data-ttu-id="1a23f-141">此時，篩選會變更為 **[所有值]** ，並且選取 **[只顯示新值]** 。</span><span class="sxs-lookup"><span data-stu-id="1a23f-141">The filter is changed to **All Values** and **Show Only New** is selected.</span></span> <span data-ttu-id="1a23f-142">在匯入作業之後選取 **[只顯示新值]** 時，就只會顯示從 Excel 檔案匯入的值。</span><span class="sxs-lookup"><span data-stu-id="1a23f-142">When **Show Only New** is selected after the import operation, only the values imported from the Excel file will be displayed.</span></span>  
  
14. <span data-ttu-id="1a23f-143">按一下 **[完成]** ，將值加入至知識庫。</span><span class="sxs-lookup"><span data-stu-id="1a23f-143">Click **Finish** to add the values to the knowledge base.</span></span>  
  
##  <a name="follow-up-after-importing-values-from-an-excel-file-into-a-domain"></a><a name="FollowUp"></a><span data-ttu-id="1a23f-144">後續操作：將 Excel 檔案中的值匯入定義域之後</span><span class="sxs-lookup"><span data-stu-id="1a23f-144">Follow Up: After Importing Values from an Excel File into a Domain</span></span>  
 <span data-ttu-id="1a23f-145">將值匯入定義域之後，您可以針對定義域執行其他定義域管理工作、執行知識探索以將知識加入至定義域，或者將比對原則加入至定義域。</span><span class="sxs-lookup"><span data-stu-id="1a23f-145">After you import values into a domain, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="1a23f-146">如需詳細資訊，請參閱[執行知識探索](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理定義域](../../2014/data-quality-services/managing-a-domain.md)或[建立比對原則](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="1a23f-146">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
##  <a name="importing-synonyms"></a><a name="Synonyms"></a><span data-ttu-id="1a23f-147">匯入同義字</span><span class="sxs-lookup"><span data-stu-id="1a23f-147">Importing Synonyms</span></span>  
 <span data-ttu-id="1a23f-148">同義字的匯入方式如下：</span><span class="sxs-lookup"><span data-stu-id="1a23f-148">Synonyms are imported as follows:</span></span>  
  
-   <span data-ttu-id="1a23f-149">首先，系統會匯入所有值，然後建立同義字連接。</span><span class="sxs-lookup"><span data-stu-id="1a23f-149">First, all values are imported, then the synonym connection is established.</span></span>  
  
-   <span data-ttu-id="1a23f-150">如果無法連接同義字值，記錄畫面就會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="1a23f-150">If it is impossible to connect synonym values, an error will appear in the log screen.</span></span> <span data-ttu-id="1a23f-151">檔案中的前置值和同義字可能將匯入定義域，但是不會設定為同義字。</span><span class="sxs-lookup"><span data-stu-id="1a23f-151">It is possible that the leading values and the synonyms in the file will be imported to the domain, but will not be set as synonyms.</span></span>  
  
 <span data-ttu-id="1a23f-152">下列規則適用於設定同義字連接的程序：</span><span class="sxs-lookup"><span data-stu-id="1a23f-152">The following apply to the process of setting synonym connections:</span></span>  
  
-   <span data-ttu-id="1a23f-153">如果 Excel 檔案中的前置值已經存在定義域中做為不同值的同義字，您就必須手動設定同義字 (例如，在 Excel 檔案中，我們想要讓 A 值成為 B 值的前置值，但是在定義域中，A 值顯示成 C 值的同義字)。</span><span class="sxs-lookup"><span data-stu-id="1a23f-153">If the leading value in the Excel file already exists in the domain as a synonym of a different value, you will have to set the synonyms manually (e.g., in the Excel file we want that value A will be the leading value for value B, but in the domain value A appears as a synonym of value C).</span></span> <span data-ttu-id="1a23f-154">除了在匯入完成之後手動設定同義字以外，您也可以取消連結目前是同義字的值 (例如，取消連結上述 A 和 C 值)，然後再匯入檔案。</span><span class="sxs-lookup"><span data-stu-id="1a23f-154">In addition to setting synonyms manually after the import completes, you can also unlink values that are at present synonyms (for example, unlink values A and C above), and then import the file.</span></span>  
  
-   <span data-ttu-id="1a23f-155">如果同義字已經連接到不同的前置值，您就必須手動設定同義字。</span><span class="sxs-lookup"><span data-stu-id="1a23f-155">If the synonym is already connected to a different leading value, you will have to set the synonyms manually.</span></span>  
  
-   <span data-ttu-id="1a23f-156">如果由於任何原因而無法在應用程式中手動連接值，表示該值可能不適用於匯入作業。</span><span class="sxs-lookup"><span data-stu-id="1a23f-156">If the values cannot be connected manually in the application for any reason, it will not be applicable through the import operation.</span></span>  
  
##  <a name="how-the-import-works"></a><a name="How"></a><span data-ttu-id="1a23f-157">匯入的運作方式</span><span class="sxs-lookup"><span data-stu-id="1a23f-157">How the import works</span></span>  
 <span data-ttu-id="1a23f-158">此作業將匯入下列值：</span><span class="sxs-lookup"><span data-stu-id="1a23f-158">The following values are imported by this operation:</span></span>  
  
 <span data-ttu-id="1a23f-159">在匯入作業中，DQS 會依照以下方式從 Excel 檔案匯入資料：</span><span class="sxs-lookup"><span data-stu-id="1a23f-159">In the import operation, DQS imports from an Excel file as follows:</span></span>  
  
-   <span data-ttu-id="1a23f-160">匯入正確的值和新值。</span><span class="sxs-lookup"><span data-stu-id="1a23f-160">Correct values and new values are imported.</span></span> <span data-ttu-id="1a23f-161">如果一個或多個匯入的定義域值已經存在，就不會匯入這些值。</span><span class="sxs-lookup"><span data-stu-id="1a23f-161">If one or more of the imported domain values already exists, the values will not be imported.</span></span>  
  
-   <span data-ttu-id="1a23f-162">與定義域規則衝突的值將匯入成無效的值。</span><span class="sxs-lookup"><span data-stu-id="1a23f-162">A value that contradicts a domain rule will be imported as an invalid value.</span></span>  
  
-   <span data-ttu-id="1a23f-163">如果某個值不屬於定義域的資料類型或為 Null，就不會從檔案匯入該值。</span><span class="sxs-lookup"><span data-stu-id="1a23f-163">A value will not be imported from the file if the value is not of the domain's data type or is null.</span></span>  
  
-   <span data-ttu-id="1a23f-164">系統會依照值出現在檔案中的順序匯入值。</span><span class="sxs-lookup"><span data-stu-id="1a23f-164">Values are imported in the order in which they appear in the file.</span></span>  
  
-   <span data-ttu-id="1a23f-165">每個資料列都代表一個定義域值。</span><span class="sxs-lookup"><span data-stu-id="1a23f-165">Each row represents a domain value.</span></span>  
  
-   <span data-ttu-id="1a23f-166">第一個資料列表示定義域名稱，或者為第一個資料值或記錄 (根據 **[使用第一個資料列做為標頭]** 核取方塊的設定而定)。</span><span class="sxs-lookup"><span data-stu-id="1a23f-166">The first row either represents domain names or is the first data value or record, depending upon the setting of the **Use First Row as header** checkbox.</span></span> <span data-ttu-id="1a23f-167">如果您在使用 .xslx 或 .xls 檔案時選取 **[使用第一個資料列做為標頭]** ，任何 Null 資料行名稱都將自動轉換成 F*n*，而且任何重複的資料行都會附加一個數字。</span><span class="sxs-lookup"><span data-stu-id="1a23f-167">If you select **Use First Row as header** when using an .xslx or .xls file, any column names that are null will be automatically converted into F*n*, and any columns that are duplicate will have a number appended to them.</span></span>  
  
-   <span data-ttu-id="1a23f-168">如果您在匯入作業完成之前加以取消，系統將回復此作業，而且不會匯入任何資料。</span><span class="sxs-lookup"><span data-stu-id="1a23f-168">If you cancel the import operation before it has completed, the operation will be rolled back and no data will be imported.</span></span>  
  
-   <span data-ttu-id="1a23f-169">第一個資料行中的值會匯入定義域中。</span><span class="sxs-lookup"><span data-stu-id="1a23f-169">The values in the first column are imported into the domain.</span></span> <span data-ttu-id="1a23f-170">如果除了第一個資料行以外，已填入一個或多個其他資料行，則這些資料行中的值將會加入成為同義字 (請參閱＜ [匯入同義字](#Synonyms)＞)。</span><span class="sxs-lookup"><span data-stu-id="1a23f-170">If in addition to the first column, one or more additional columns are populated, then the values in those columns will be added as synonyms (see [Importing Synonyms](#Synonyms)).</span></span>  
  
    -   <span data-ttu-id="1a23f-171">預期的格式如下：第一個資料行成為前置值，而第二個以上的資料行則成為同義字。</span><span class="sxs-lookup"><span data-stu-id="1a23f-171">The expected format is that the first column will be leading values and the second column and above will be synonyms.</span></span>  
  
    -   <span data-ttu-id="1a23f-172">您可以在相同的資料列或不同的資料列中匯入多個同義字。</span><span class="sxs-lookup"><span data-stu-id="1a23f-172">You can import multiple synonyms in the same row or in different rows.</span></span> <span data-ttu-id="1a23f-173">例如，如果您想要匯入 "NYC" 和 "New York City" 成為 "New York" 的同義字，可以匯入資料行 1 包含 "New York"、資料行 2 包含 "NYC" 而且資料行 3 包含 "New York City" 的單一資料列。或者，您也可以匯入資料行 1 包含 "New York" 而且資料行 2 包含 "NYC" 的一個資料列，以及資料行 1 包含 "New York" 而且資料行 2 包含 "New York City" 的另一個資料列。</span><span class="sxs-lookup"><span data-stu-id="1a23f-173">For example, if you want to import "NYC" and "New York City" as synonyms for "New York", you can import a single row with "New York" in column 1, "NYC" in column 2, and "New York City" in column 3; or you can import one row with "New York" in column 1 and "NYC" in column 2, and another row with "New York" in column 1 and "New York City" in column 2.</span></span> <span data-ttu-id="1a23f-174">請注意，如果 "New York" 值已經存在定義域中，系統就只會加入同義字，而且使用者不會在匯入程序期間收到錯誤，指出該值已經存在。</span><span class="sxs-lookup"><span data-stu-id="1a23f-174">Note that if the value "New York" already exists in the domain, only the synonyms will be added, and the user will not receive an error during the import process telling him that the value already exist.</span></span> <span data-ttu-id="1a23f-175">如果第一個值原本不存在，它就會加入至定義域。</span><span class="sxs-lookup"><span data-stu-id="1a23f-175">If the first value does not already exist, it will be added to the domain.</span></span>  
  
 <span data-ttu-id="1a23f-176">下列規則適用於針對匯入所使用的 Excel 檔案：</span><span class="sxs-lookup"><span data-stu-id="1a23f-176">The following rules apply to the Excel file being used for the import:</span></span>  
  
-   <span data-ttu-id="1a23f-177">Excel 檔案的副檔名可為 .xlsx、.xls 或 .csv。</span><span class="sxs-lookup"><span data-stu-id="1a23f-177">The Excel file can have the extension .xlsx, .xls, or .csv.</span></span> <span data-ttu-id="1a23f-178">安裝 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 應用程式電腦上必須安裝 Microsoft Excel，才能匯入定義域值或完整定義域。</span><span class="sxs-lookup"><span data-stu-id="1a23f-178">Microsoft Excel must be installed on the computer that the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application is installed on in order to import domain values or a complete domain.</span></span> <span data-ttu-id="1a23f-179">Excel 2003 及更新的版本都有受到支援。</span><span class="sxs-lookup"><span data-stu-id="1a23f-179">Excel versions 2003 and later are supported.</span></span> <span data-ttu-id="1a23f-180">如果使用 64 位元版本的 Excel，則僅支援 Excel 2003 檔案，不支援 Excel 2007 或 2010 檔案。</span><span class="sxs-lookup"><span data-stu-id="1a23f-180">If the 64-bit version of Excel is used, only Excel 2003 files are supported; Excel 2007 or 2010 files are not supported.</span></span>  
  
-   <span data-ttu-id="1a23f-181">Excel 64 位元安裝不支援 Excel 檔案類型 .xlsx。</span><span class="sxs-lookup"><span data-stu-id="1a23f-181">Excel files of type .xlsx are not supported for an Excel 64-bit installation.</span></span> <span data-ttu-id="1a23f-182">如果您要使用 64 位元 Excel，請將試算表檔案儲存成 .xls 檔案或 .csv 檔案，或是改為安裝 Excel 32 位元版本。</span><span class="sxs-lookup"><span data-stu-id="1a23f-182">If you are using 64-bit Excel, save the spreadsheet file as an .xls file or a .csv file, or install an Excel 32-bit installation instead.</span></span>  
  
-   <span data-ttu-id="1a23f-183">在 .xlsx 和 .xls 檔案中，資料行的資料類型是由前八個資料列所決定。</span><span class="sxs-lookup"><span data-stu-id="1a23f-183">In .xlsx and .xls files, the data type of the column is determined by the first eight rows.</span></span> <span data-ttu-id="1a23f-184">如果前八個資料列的資料行類型為混合式，資料行類型就是字串。</span><span class="sxs-lookup"><span data-stu-id="1a23f-184">If the column data type of the first eight rows is mixed, the column type will be string.</span></span> <span data-ttu-id="1a23f-185">如果資料列 9 以上的資料格不符合該資料類型，將會為它提供 Null 值。</span><span class="sxs-lookup"><span data-stu-id="1a23f-185">If a cell for row 9 and higher does not conform to that data type, it will be given a null value.</span></span>  
  
-   <span data-ttu-id="1a23f-186">在 .csv 檔案中，資料類型是由前八個資料列中最普遍的資料類型所決定。</span><span class="sxs-lookup"><span data-stu-id="1a23f-186">In .csv files, the data type is determined by the most prevalent data type in the first eight rows.</span></span>  
  
-   <span data-ttu-id="1a23f-187">如果 Excel 檔案的格式不正確或是已損毀，則匯入作業會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1a23f-187">If the Excel file is not in the right format or is corrupted, the import operation will result in an error.</span></span>  
  
  
