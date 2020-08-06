---
title: SQL Server 2014 的離線檔
description: 瞭解如何安裝 SQL Server 2014 的離線檔。 使用 SQL Server Management Studio (SSMS) 來檢視離線內容。
ms.prod: sql
ms.technology: install
ms.topic: conceptual
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
author: markingmyname
ms.author: maghan
ms.reviewer: carlrab
ms.date: 07/19/2020
ms.openlocfilehash: bfd4adc658a203f8e2d22ef77ce0381084e36363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595374"
---
# <a name="install-sql-server-2014-offline-documentation"></a><span data-ttu-id="72a9a-104">安裝 SQL Server 2014 離線檔</span><span class="sxs-lookup"><span data-stu-id="72a9a-104">Install SQL Server 2014 offline documentation</span></span>

<span data-ttu-id="72a9a-105">本文說明如何下載和觀看離線 SQL Server 2014 內容。</span><span class="sxs-lookup"><span data-stu-id="72a9a-105">This article describes how to download and view offline SQL Server 2014 content.</span></span> <span data-ttu-id="72a9a-106">離線內容可讓您在沒有網際網路連線的情況下存取文件 (但是一開始需要網際網路連線來下載文件)。</span><span class="sxs-lookup"><span data-stu-id="72a9a-106">Offline content enables you to access the documentation without an internet connection (although an internet connection is initially required to download it).</span></span>

<span data-ttu-id="72a9a-107">這項技術牽涉到使用 SQL Server Management Studio (SSMS) **的 [說明**] 功能表，以存取說明檢視器公用程式 ( # A0) 。</span><span class="sxs-lookup"><span data-stu-id="72a9a-107">The technique involves using the **Help** menu of SQL Server Management Studio (SSMS), to access the Help Viewer utility (HlpViewer.exe).</span></span>

<span data-ttu-id="72a9a-108">離線檔適用于2012-2019 範圍內的 SQL Server，也可能是其他較新版本的版本。</span><span class="sxs-lookup"><span data-stu-id="72a9a-108">Offline documentation is available for versions of SQL Server in the range of 2012-2019, and perhaps for additional later versions too.</span></span> <span data-ttu-id="72a9a-109">雖然您可[線上檢視舊版內容](https://docs.microsoft.com/previous-versions/sql/)，但離線選項提供一種存取舊版內容的便利方式。</span><span class="sxs-lookup"><span data-stu-id="72a9a-109">Although you can view content for [previous versions online](https://docs.microsoft.com/previous-versions/sql/), an offline option provides a convenient way to access the older content.</span></span>

- [<span data-ttu-id="72a9a-110">SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="72a9a-110">SQL Server 2014</span></span>](#sql-server-2014-offline-content)
- [<span data-ttu-id="72a9a-111">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="72a9a-111">SQL Server 2012</span></span>](#sql-server-2012-offline-content)

<span data-ttu-id="72a9a-112">如 SQL Server 2016 和更新版本，請參閱其版本特定的檔，以瞭解這些版本如何處理其離線檔。</span><span class="sxs-lookup"><span data-stu-id="72a9a-112">For SQL Server 2016 and later versions, see their version-specific documentation to learn how those versions handle their offline documentation.</span></span>

## <a name="sql-server-2014-offline-content"></a><span data-ttu-id="72a9a-113">SQL Server 2014 離線內容</span><span class="sxs-lookup"><span data-stu-id="72a9a-113">SQL Server 2014 offline content</span></span>

> [!IMPORTANT]
> <span data-ttu-id="72a9a-114">SQL 2014 Transact-SQL 內容僅供離線使用。</span><span class="sxs-lookup"><span data-stu-id="72a9a-114">SQL 2014 Transact-SQL content is only available offline.</span></span>

<span data-ttu-id="72a9a-115">下列步驟說明如何載入 SQL Server 2014 的離線內容。</span><span class="sxs-lookup"><span data-stu-id="72a9a-115">The following steps explain how to load offline content for SQL Server 2014.</span></span>

1. <span data-ttu-id="72a9a-116">從下載中心下載 [Microsoft SQL Server 2014 的防火牆和 Proxy 受限環境產品文件](https://www.microsoft.com/download/details.aspx?id=42557) \(英文\) 內容，並將其儲存到資料夾。</span><span class="sxs-lookup"><span data-stu-id="72a9a-116">Download the [Product Documentation for Microsoft SQL Server 2014 for firewall and proxy restricted environments](https://www.microsoft.com/download/details.aspx?id=42557) content from the download center and save it to a folder.</span></span>

2. <span data-ttu-id="72a9a-117">解壓縮檔案以查看 *.msha*檔案。</span><span class="sxs-lookup"><span data-stu-id="72a9a-117">Unzip the file to view the *.msha* file.</span></span>

   ![SQL Server 2014 說明文件安裝檔](../sql-server/media/sql-server-offline-documentation/sql-2014-help-content-setup-msha.png)

3. <span data-ttu-id="72a9a-119">在 SSMS 中，選取 [說明] 功能表上的 [加入和移除說明內容]。</span><span class="sxs-lookup"><span data-stu-id="72a9a-119">In SSMS, select **Add and Remove Help Content** on the Help menu.</span></span>

   ![說明檢視器新增移除內容](../sql-server/media/sql-server-offline-documentation/add-remove-content.png)

   <span data-ttu-id="72a9a-121">說明檢視器會開啟至 [管理內容] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="72a9a-121">The Help Viewer opens to the Manage Content tab.</span></span>

4. <span data-ttu-id="72a9a-122">若要安裝最新說明內容，請選擇 [安裝來源] 底下的 [磁碟]，然後選擇省略符號 (...)。</span><span class="sxs-lookup"><span data-stu-id="72a9a-122">To install the latest help content, choose **Disk** under Installation source and then the ellipses (...).</span></span>

   ![說明檢視器管理內容磁碟來源](../sql-server/media/sql-server-offline-documentation/install-source-disk.png)

   > [!NOTE]
   > <span data-ttu-id="72a9a-124">[管理內容] 索引標籤上的 [本機存放區路徑] 會顯示內容在本機電腦上的所在位置。</span><span class="sxs-lookup"><span data-stu-id="72a9a-124">The Local store path on the Manage Content tab shows where on the local computer the content is located.</span></span> <span data-ttu-id="72a9a-125">若要變更位置，請選取 [移動]，並在 [到] 欄位中輸入不同資料夾路徑，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="72a9a-125">To change the location, select **Move**, enter a different folder path in the **To** field, and then select **OK**.</span></span>
   <span data-ttu-id="72a9a-126">如果變更本機存放區路徑後，說明安裝失敗，請關閉並重新開啟 Help Viewer。</span><span class="sxs-lookup"><span data-stu-id="72a9a-126">If the help installation fails after changing the Local store path, close and reopen the Help Viewer.</span></span> <span data-ttu-id="72a9a-127">請確定新的位置出現在本機存放區路徑中，然後再次嘗試安裝。</span><span class="sxs-lookup"><span data-stu-id="72a9a-127">Ensure the new location appears in the Local store path and then try the installation again.</span></span>

5. <span data-ttu-id="72a9a-128">尋找已解壓縮內容所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="72a9a-128">Locate the folder where you unzipped the content.</span></span> <span data-ttu-id="72a9a-129">選取資料夾中的 [HelpContentSetup.msha] 檔案，然後選取 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="72a9a-129">Select the **HelpContentSetup.msha** file in the folder then select **Open**.</span></span>

   ![開啟 SQL Server 2014 Help Content Setup.msha 檔案](../sql-server/media/sql-server-offline-documentation/sql-2014-open-msha.png)

6. <span data-ttu-id="72a9a-131">在搜尋列中輸入 *sql server 2014*。</span><span class="sxs-lookup"><span data-stu-id="72a9a-131">Type in *sql server 2014* in the search bar.</span></span> <span data-ttu-id="72a9a-132">當您看到有 2014 內容可供使用之後，選取您想要安裝至 [說明檢視器] 之每個內容套件 (書籍) 旁邊的 [新增]，然後選取 [更新]。</span><span class="sxs-lookup"><span data-stu-id="72a9a-132">Once you see the 2014 content available, select **Add** next to each content package (book) that you want to install to Help Viewer and then select **Update**.</span></span>

   ![[說明檢視器] 中的 SQL Server 2014 書籍搜尋](../sql-server/media/sql-server-offline-documentation/sql-2014-search.png)

   ![[說明檢視器] 中的 SQL Server 2014 書籍新增與更新](../sql-server/media/sql-server-offline-documentation/sql-2014-add-update.png)

    > [!NOTE]
    > <span data-ttu-id="72a9a-135">如果說明檢視器凍結 (在新增內容時停止回應) ，請將%LOCALAPPDATA%\Microsoft\HelpViewer2.x\ 中的快取 LastRefreshed = " \<mm/dd/yyyy> 00:00:00" 行 HlpViewer_SSMSx_en-us. settings 或 HlpViewer_VisualStudiox_en-us. 設定檔案變更為未來的某個日期。</span><span class="sxs-lookup"><span data-stu-id="72a9a-135">If the Help Viewer freezes (hangs) while adding content, change the Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" line in the %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings or HlpViewer_VisualStudiox_en-US.settings file to some date in the future.</span></span> <span data-ttu-id="72a9a-136">如需此問題的詳細資訊，請參閱 [Visual Studio 說明檢視器凍結在啟動顯示畫面上](/visualstudio/welcome-to-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="72a9a-136">For more information about this issue, see [Visual Studio Help Viewer freezes](/visualstudio/welcome-to-visual-studio).</span></span>

7. <span data-ttu-id="72a9a-137">您可以在左側內容窗格底下搜尋 *sql server 2014*，以確認是否已安裝 SQL Server 2014 內容。</span><span class="sxs-lookup"><span data-stu-id="72a9a-137">You can verify that the SQL Server 2014 content installed by searching under the content pane on the left for *sql server 2014*.</span></span>

   ![SQL Server 2014 書籍已自動更新](../sql-server/media/sql-server-offline-documentation/sql-2014-content.png)

## <a name="sql-server-2012-offline-content"></a><span data-ttu-id="72a9a-139">SQL Server 2012 離線內容</span><span class="sxs-lookup"><span data-stu-id="72a9a-139">SQL Server 2012 offline content</span></span>

<span data-ttu-id="72a9a-140">下列步驟說明如何載入 SQL Server 2012 的離線內容</span><span class="sxs-lookup"><span data-stu-id="72a9a-140">The following steps explain how to load offline content for SQL Server 2012</span></span>

1. <span data-ttu-id="72a9a-141">從下載中心下載 [Microsoft SQL Server 2012 的防火牆和 Proxy 受限環境產品文件](https://www.microsoft.com/download/details.aspx?id=35750) \(英文\) 內容，並將其儲存到資料夾。</span><span class="sxs-lookup"><span data-stu-id="72a9a-141">Download the [Product Documentation for Microsoft SQL Server 2012 for firewall and proxy restricted environments](https://www.microsoft.com/download/details.aspx?id=35750) content from the download center and save it to a folder.</span></span>

2. <span data-ttu-id="72a9a-142">解壓縮檔案以查看 *.msha*檔案。</span><span class="sxs-lookup"><span data-stu-id="72a9a-142">Unzip the file to view the *.msha* file.</span></span>

   ![SQL Server 2012 說明內容安裝程式檔案](../sql-server/media/sql-server-offline-documentation/sql-2012-help-content-setup-msha.png)

3. <span data-ttu-id="72a9a-144">在 SSMS 中，選取 [說明] 功能表上的 [加入和移除說明內容]。</span><span class="sxs-lookup"><span data-stu-id="72a9a-144">In SSMS, select **Add and Remove Help Content** on the Help menu.</span></span>

   ![說明檢視器新增移除內容](../sql-server/media/sql-server-offline-documentation/add-remove-content.png)

   <span data-ttu-id="72a9a-146">說明檢視器會開啟至 [管理內容] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="72a9a-146">The Help Viewer opens to the Manage Content tab.</span></span>

4. <span data-ttu-id="72a9a-147">若要安裝最新說明內容，請選擇 [安裝來源] 底下的 [磁碟]，然後選擇省略符號 (...)。</span><span class="sxs-lookup"><span data-stu-id="72a9a-147">To install the latest help content, choose **Disk** under Installation source and then the ellipses (...).</span></span>

   ![說明檢視器管理內容磁碟來源](../sql-server/media/sql-server-offline-documentation/install-source-disk.png)

   > [!NOTE]
   > <span data-ttu-id="72a9a-149">[管理內容] 索引標籤上的 [本機存放區路徑] 會顯示內容在本機電腦上的所在位置。</span><span class="sxs-lookup"><span data-stu-id="72a9a-149">The Local store path on the Manage Content tab shows where on the local computer the content is located.</span></span> <span data-ttu-id="72a9a-150">若要變更位置，請選取 [移動]，並在 [到] 欄位中輸入不同資料夾路徑，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="72a9a-150">To change the location, select **Move**, enter a different folder path in the **To** field, and then select **OK**.</span></span>
   <span data-ttu-id="72a9a-151">如果變更本機存放區路徑後，說明安裝失敗，請關閉並重新開啟 Help Viewer。</span><span class="sxs-lookup"><span data-stu-id="72a9a-151">If the help installation fails after changing the Local store path, close and reopen the Help Viewer.</span></span> <span data-ttu-id="72a9a-152">請確定新的位置出現在本機存放區路徑中，然後再次嘗試安裝。</span><span class="sxs-lookup"><span data-stu-id="72a9a-152">Ensure the new location appears in the Local store path and then try the installation again.</span></span>

5. <span data-ttu-id="72a9a-153">尋找已解壓縮內容所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="72a9a-153">Locate the folder where you unzipped the content.</span></span> <span data-ttu-id="72a9a-154">選取資料夾中的 [HelpContentSetup.msha] 檔案，然後選取 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="72a9a-154">Select the **HelpContentSetup.msha** file in the folder then select **Open**.</span></span>

   ![開啟 SQL Server 2012 Help Content Setup.msha 檔案](../sql-server/media/sql-server-offline-documentation/sql-2012-open-msha.png)

6. <span data-ttu-id="72a9a-156">在搜尋列中輸入 *sql server 2012*。</span><span class="sxs-lookup"><span data-stu-id="72a9a-156">Type in *sql server 2012* in the search bar.</span></span> <span data-ttu-id="72a9a-157">當您看到有 2012 內容可供使用之後，選取您想要安裝至 [說明檢視器] 之每個內容套件 (書籍) 旁邊的 [新增]，然後選取 [更新]。</span><span class="sxs-lookup"><span data-stu-id="72a9a-157">Once you see the 2012 content available, select **Add** next to each content package (book) that you want to install to Help Viewer and then select **Update**.</span></span>

   ![[說明檢視器] 中的 SQL Server 2012 書籍搜尋](../sql-server/media/sql-server-offline-documentation/sql-2012-search.png)

   ![[說明檢視器] 中的 SQL Server 2012 書籍新增與更新](../sql-server/media/sql-server-offline-documentation/sql-2012-add-update.png)

    > [!NOTE]
    > <span data-ttu-id="72a9a-160">如果說明檢視器凍結 (在新增內容時停止回應) ，請將%LOCALAPPDATA%\Microsoft\HelpViewer2.x\ 中的快取 LastRefreshed = " \<mm/dd/yyyy> 00:00:00" 行 HlpViewer_SSMSx_en-us. settings 或 HlpViewer_VisualStudiox_en-us. 設定檔案變更為未來的某個日期。</span><span class="sxs-lookup"><span data-stu-id="72a9a-160">If the Help Viewer freezes (hangs) while adding content, change the Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" line in the %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings or HlpViewer_VisualStudiox_en-US.settings file to some date in the future.</span></span> <span data-ttu-id="72a9a-161">如需此問題的詳細資訊，請參閱 [Visual Studio 說明檢視器凍結在啟動顯示畫面上](/visualstudio/welcome-to-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="72a9a-161">For more information about this issue, see [Visual Studio Help Viewer freezes](/visualstudio/welcome-to-visual-studio).</span></span>

7. <span data-ttu-id="72a9a-162">您可以在左側內容窗格底下搜尋 *sql server 2012*，以確認是否已載入 SQL Server 2012 內容。</span><span class="sxs-lookup"><span data-stu-id="72a9a-162">You can verify that the SQL Server 2012 content is loaded by searching under the content pane on the left for *sql server 2012*.</span></span>

   ![SQL Server 2012 文件已自動更新](../sql-server/media/sql-server-offline-documentation/sql-2012-content.png)

## <a name="view-offline-documentation"></a><span data-ttu-id="72a9a-164">檢視離線文件</span><span class="sxs-lookup"><span data-stu-id="72a9a-164">View offline documentation</span></span>

<span data-ttu-id="72a9a-165">您可以使用最新版 SQL Server Management Studio (SSMS) 中**的 [說明] 功能表來觀看**SQL Server 說明內容。</span><span class="sxs-lookup"><span data-stu-id="72a9a-165">You can view SQL Server help content using the **HELP** menu in the latest version of SQL Server Management Studio (SSMS).</span></span>

### <a name="view-offline-help-content-in-ssms"></a><span data-ttu-id="72a9a-166">在 SSMS 中檢視離線說明內容</span><span class="sxs-lookup"><span data-stu-id="72a9a-166">View offline help content in SSMS</span></span>

<span data-ttu-id="72a9a-167">若要在 SSMS 中檢視已安裝的說明，請從 [說明] 功能表中選取 [在說明檢視器中啟動]，以啟動 [說明檢視器]。</span><span class="sxs-lookup"><span data-stu-id="72a9a-167">To view the installed help in SSMS, select **Launch in Help Viewer** from the Help menu, to launch the Help Viewer.</span></span>

   ![在說明檢視器中啟動](../sql-server/media/sql-server-offline-documentation/helpviewer-view-offline.png)  

<span data-ttu-id="72a9a-169">[說明檢視器] 會開啟至 [管理內容] 索引標籤，並在左窗格中顯示已安裝的說明目錄。</span><span class="sxs-lookup"><span data-stu-id="72a9a-169">Help Viewer opens to the Manage Content tab, with the installed help table of contents in the left pane.</span></span> <span data-ttu-id="72a9a-170">選取目錄中的文章以在右方窗格中顯示該文章。</span><span class="sxs-lookup"><span data-stu-id="72a9a-170">select articles in the table of contents to display them in the right pane.</span></span>

> [!Important]
> <span data-ttu-id="72a9a-171">如果看不到內容窗格，請選取左邊界上的 [內容]。</span><span class="sxs-lookup"><span data-stu-id="72a9a-171">If the contents pane is not visible, select Contents on the left margin.</span></span> <span data-ttu-id="72a9a-172">選取圖釘圖示以將內容窗格保持開啟。</span><span class="sxs-lookup"><span data-stu-id="72a9a-172">select the pushpin icon to keep the contents pane open.</span></span>  

   ![含內容的 [說明檢視器]](../sql-server/media/sql-server-offline-documentation/view-offline-all.png)
