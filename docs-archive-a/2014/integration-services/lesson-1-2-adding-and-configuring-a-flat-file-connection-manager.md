---
title: 步驟 2：新增和設定一般檔案連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9a77dd32-d8c2-4961-ad37-2a971f9d6043
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3ba3adee2422af8b2df027f55ec84366b90ddd7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596147"
---
# <a name="step-2-adding-and-configuring-a-flat-file-connection-manager"></a><span data-ttu-id="dbe39-102">步驟 2:新增和設定一般檔案連線管理員</span><span class="sxs-lookup"><span data-stu-id="dbe39-102">Step 2: Adding and Configuring a Flat File Connection Manager</span></span>
  <span data-ttu-id="dbe39-103">在這項工作中，您將一般檔案連接管理員加入您剛才建立的封裝中。</span><span class="sxs-lookup"><span data-stu-id="dbe39-103">In this task, you add a Flat File connection manager to the package that you just created.</span></span> <span data-ttu-id="dbe39-104">一般檔案連接管理員可讓封裝從一般檔案擷取資料。</span><span class="sxs-lookup"><span data-stu-id="dbe39-104">A Flat File connection manager enables a package to extract data from a flat file.</span></span> <span data-ttu-id="dbe39-105">使用一般檔案連接管理員，您可以指定當封裝從一般檔案擷取資料時，要套用的檔案名稱和位置、地區設定和字碼頁及檔案格式 (包括資料行分隔符號)。</span><span class="sxs-lookup"><span data-stu-id="dbe39-105">Using the Flat File connection manager, you can specify the file name and location, the locale and code page, and the file format, including column delimiters, to apply when the package extracts data from the flat file.</span></span> <span data-ttu-id="dbe39-106">此外，您可以手動指定個別資料行的資料類型，或使用 [建議資料行類型]  對話方塊，將所擷取資料的資料行自動對應至 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="dbe39-106">In addition, you can manually specify the data type for the individual columns, or use the **Suggest Column Types** dialog box to automatically map the columns of extracted data to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] data types.</span></span>  
  
 <span data-ttu-id="dbe39-107">您必須為您要使用的每一個檔案格式建立新的一般檔案連接管理員。</span><span class="sxs-lookup"><span data-stu-id="dbe39-107">You must create a new Flat File connection manager for each file format that you work with.</span></span> <span data-ttu-id="dbe39-108">因為這個教學課程是從多個具有相同資料格式的一般檔案擷取資料，所以您只需要在封裝中加入和設定一個一般檔案連接管理員。</span><span class="sxs-lookup"><span data-stu-id="dbe39-108">Because this tutorial extracts data from multiple flat files that have exactly the same data format, you will need to add and configure only one Flat File connection manager for your package.</span></span>  
  
 <span data-ttu-id="dbe39-109">在此教學課程中，您將在一般檔案連接管理員中設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="dbe39-109">For this tutorial, you will configure the following properties in your Flat File connection manager:</span></span>  
  
-   <span data-ttu-id="dbe39-110">**資料行名稱** ：因為一般檔案沒有資料行名稱，所以一般檔案連接管理員會建立預設資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="dbe39-110">**Column names:** Because the flat file does not have column names, the Flat File connection manager creates default column names.</span></span> <span data-ttu-id="dbe39-111">這些預設名稱無助於識別每一個資料行所代表的內容。</span><span class="sxs-lookup"><span data-stu-id="dbe39-111">These default names are not useful for identifying what each column represents.</span></span> <span data-ttu-id="dbe39-112">若要使這些預設名稱有所幫助，您必須將預設名稱變更為符合一般檔案資料即將載入的事實資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="dbe39-112">To make these default names more useful, you need to change the default names to names that match the fact table into which the flat file data is to be loaded.</span></span>  
  
-   <span data-ttu-id="dbe39-113">**資料對應** ：所有參考連接管理員的一般檔案資料來源元件，將使用您為一般檔案連接管理員指定的資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="dbe39-113">**Data mappings:** The data type mappings that you specify for the Flat File connection manager will be used by all flat file data source components that reference the connection manager.</span></span> <span data-ttu-id="dbe39-114">您可以使用一般檔案連接管理員來手動對應資料類型，或使用 [建議資料行類型]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="dbe39-114">You can either manually map the data types by using the Flat File connection manager, or you can use the **Suggest Column Types** dialog box.</span></span> <span data-ttu-id="dbe39-115">在此教學課程中，您將檢視在 [建議資料行類型]\*\*\*\* 對話方塊中建議的對應，然後在 [一般檔案連接管理員編輯器]\*\*\*\* 對話方塊中手動做一些必要的對應。</span><span class="sxs-lookup"><span data-stu-id="dbe39-115">In this tutorial, you will view the mappings suggested in the **Suggest Column Types** dialog box and then manually make the necessary mappings in the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="dbe39-116">一般檔案連接管理員提供有關資料檔的地區設定資訊。</span><span class="sxs-lookup"><span data-stu-id="dbe39-116">The Flat File connection manager provides locale information about the data file.</span></span> <span data-ttu-id="dbe39-117">如果您的電腦未設定為使用地區選項英文 (美國) ，您必須在 [一般檔案**連接管理員編輯器**] 對話方塊中設定其他屬性。</span><span class="sxs-lookup"><span data-stu-id="dbe39-117">If your computer is not configured to use the regional option English (United States), you must set additional properties in the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
### <a name="to-add-a-flat-file-connection-manager-to-the-ssis-package"></a><span data-ttu-id="dbe39-118">若要將一般檔案連接管理員加入至 SSIS 封裝</span><span class="sxs-lookup"><span data-stu-id="dbe39-118">To add a Flat File connection manager to the SSIS package</span></span>  
  
1.  <span data-ttu-id="dbe39-119">以滑鼠右鍵按一下 [連接管理員]\*\*\*\* 區域的任何位置，然後按一下 [新增一般檔案連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbe39-119">Right-click anywhere in the **Connection Managers** area, and then click **New Flat File Connection**.</span></span>  
  
2.  <span data-ttu-id="dbe39-120">在 [一般檔案連接管理員編輯器]\*\*\*\* 對話方塊中，對 [連接管理員名稱]\*\*\*\* 輸入 [範例一般檔案來源資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbe39-120">In the **Flat File Connection Manager Editor** dialog box, for **Connection manager name**, type **Sample Flat File Source Data**.</span></span>  
  
3.  <span data-ttu-id="dbe39-121">按一下 **[瀏覽]** 。</span><span class="sxs-lookup"><span data-stu-id="dbe39-121">Click **Browse**.</span></span>  
  
4.  <span data-ttu-id="dbe39-122">在 [開啟]\*\*\*\* 對話方塊中，尋找電腦上的 SampleCurrencyData.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="dbe39-122">In the **Open** dialog box, locate the SampleCurrencyData.txt file on your machine.</span></span>  
  
     <span data-ttu-id="dbe39-123">範例資料隨附在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 課程封裝中。</span><span class="sxs-lookup"><span data-stu-id="dbe39-123">The sample data is included with the [!INCLUDE[ssIS](../includes/ssis-md.md)] lesson packages.</span></span> <span data-ttu-id="dbe39-124">若要下載範例資料和課程封裝，請執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="dbe39-124">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="dbe39-125">導覽至 [Integration Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=275027)</span><span class="sxs-lookup"><span data-stu-id="dbe39-125">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="dbe39-126">按一下 [**下載**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="dbe39-126">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="dbe39-127">按一下 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="dbe39-127">Click the  SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="dbe39-128">清除第一個資料列核取方塊中的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="dbe39-128">Clear the Column names in the first data row checkbox.</span></span>  
  
### <a name="to-set-locale-sensitive-properties"></a><span data-ttu-id="dbe39-129">若要設定區分地區設定屬性</span><span class="sxs-lookup"><span data-stu-id="dbe39-129">To set locale sensitive properties</span></span>  
  
1.  <span data-ttu-id="dbe39-130">在 [一般檔案連接管理員編輯器]\*\*\*\* 對話方塊中，按一下 [一般]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbe39-130">In the **Flat File Connection Manager Editor** dialog box, click **General**.</span></span>  
  
2.  <span data-ttu-id="dbe39-131">將 [**地區**設定] ([美國) ] 和 [**字碼頁**] 設為1252。</span><span class="sxs-lookup"><span data-stu-id="dbe39-131">Set **Locale** to English (United States) and **Code page** to 1252.</span></span>  
  
### <a name="to-rename-columns-in-the-flat-file-connection-manager"></a><span data-ttu-id="dbe39-132">若要重新命名一般檔案連接管理員中的資料行</span><span class="sxs-lookup"><span data-stu-id="dbe39-132">To rename columns in the Flat File connection manager</span></span>  
  
1.  <span data-ttu-id="dbe39-133">在 [一般檔案連接管理員編輯器]\*\*\*\* 對話方塊中，按一下 [進階]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbe39-133">In the **Flat File Connection Manager Editor** dialog box, click **Advanced**.</span></span>  
  
2.  <span data-ttu-id="dbe39-134">在屬性窗格中，進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="dbe39-134">In the property pane, make the following changes:</span></span>  
  
    -   <span data-ttu-id="dbe39-135">將 [資料**行 0** ] 名稱屬性變更為 `AverageRate` 。</span><span class="sxs-lookup"><span data-stu-id="dbe39-135">Change the **Column 0** name property to `AverageRate`.</span></span>  
  
    -   <span data-ttu-id="dbe39-136">將 [資料**行 1** ] 名稱屬性變更為 `CurrencyID` 。</span><span class="sxs-lookup"><span data-stu-id="dbe39-136">Change the **Column 1** name property to `CurrencyID`.</span></span>  
  
    -   <span data-ttu-id="dbe39-137">將 [資料**行 2** ] 名稱屬性變更為 `CurrencyDate` 。</span><span class="sxs-lookup"><span data-stu-id="dbe39-137">Change the **Column 2** name property to `CurrencyDate`.</span></span>  
  
    -   <span data-ttu-id="dbe39-138">將 [資料**行 3** ] 名稱屬性變更為 `EndOfDayRate` 。</span><span class="sxs-lookup"><span data-stu-id="dbe39-138">Change the **Column 3** name property to `EndOfDayRate`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dbe39-139">依預設，所有 4 個資料行一開始是設為字串資料類型 [DT_STR]，且 `OutputColumnWidth` 為 50。</span><span class="sxs-lookup"><span data-stu-id="dbe39-139">By default, all four of the columns are initially set to a string data type [DT_STR] with an `OutputColumnWidth` of 50.</span></span>  
  
### <a name="to-remap-column-data-types"></a><span data-ttu-id="dbe39-140">若要重新對應資料行資料類型</span><span class="sxs-lookup"><span data-stu-id="dbe39-140">To remap column data types</span></span>  
  
1.  <span data-ttu-id="dbe39-141">在 [一般檔案連接管理員編輯器]\*\*\*\* 對話方塊中，按一下 [建議類型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbe39-141">In the **Flat File Connection Manager Editor** dialog box, click **Suggest Types**.</span></span>  
  
     [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="dbe39-142">會依據最前面的 200 個資料列，自動建議最適合的資料類型。</span><span class="sxs-lookup"><span data-stu-id="dbe39-142">automatically suggests the most appropriate data types based on the first 200 rows of data.</span></span> <span data-ttu-id="dbe39-143">您也可以變更這些建議選項，以增加或減少取樣資料、指定整數或布林資料的預設資料類型，或是加入空格以填補字串資料行。</span><span class="sxs-lookup"><span data-stu-id="dbe39-143">You can also change these suggestion options to sample more or less data, to specify the default data type for integer or Boolean data, or to add spaces as padding to string columns.</span></span>  
  
     <span data-ttu-id="dbe39-144">目前請暫時不要對 [建議資料行類型]\*\*\*\* 對話方塊中的選項做任何變更，並按一下 [確定]\*\*\*\*，由 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 建議適合資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="dbe39-144">For now, make no changes to the options in the **Suggest Column Types** dialog box, and click **OK** to have [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] suggest data types for columns.</span></span> <span data-ttu-id="dbe39-145">這時會回到 [一般檔案連接管理員編輯器]\*\*\*\* 對話方塊的 [進階]\*\*\*\* 窗格，您可以在此檢視 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 建議的資料行資料類型。</span><span class="sxs-lookup"><span data-stu-id="dbe39-145">This returns you to the **Advanced** pane of the **Flat File Connection Manager Editor** dialog box, where you can view the column data types suggested by [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="dbe39-146">(如果按一下 [取消]\*\*\*\*，則不會對資料行中繼資料做出任何建議，而是使用預設的字串 (DT_STR) 資料類型)。</span><span class="sxs-lookup"><span data-stu-id="dbe39-146">(If you click **Cancel**, no suggestions are made to column metadata and the default string (DT_STR) data type is used.)</span></span>  
  
     <span data-ttu-id="dbe39-147">在這個教學課程中， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 會對 SampleCurrencyData.txt 檔案的資料建議下列資料表中第二個資料行所顯示的資料類型。</span><span class="sxs-lookup"><span data-stu-id="dbe39-147">In this tutorial, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] suggests the data types shown in the second column of the following table for the data from the SampleCurrencyData.txt file.</span></span> <span data-ttu-id="dbe39-148">不過，目的地的資料行所需要的資料類型 (將在後面的步驟中定義) 將顯示在下表的最後一個資料行。</span><span class="sxs-lookup"><span data-stu-id="dbe39-148">However, the data types that are required for the columns in the destination, which will be defined in a later step, are shown in the last column of the following table.</span></span>  
  
    |<span data-ttu-id="dbe39-149">一般檔案資料行</span><span class="sxs-lookup"><span data-stu-id="dbe39-149">Flat File Column</span></span>|<span data-ttu-id="dbe39-150">建議類型</span><span class="sxs-lookup"><span data-stu-id="dbe39-150">Suggested Type</span></span>|<span data-ttu-id="dbe39-151">目的地資料行</span><span class="sxs-lookup"><span data-stu-id="dbe39-151">Destination Column</span></span>|<span data-ttu-id="dbe39-152">目的地類型</span><span class="sxs-lookup"><span data-stu-id="dbe39-152">Destination Type</span></span>|  
    |----------------------|--------------------|------------------------|----------------------|  
    |<span data-ttu-id="dbe39-153">AverageRate</span><span class="sxs-lookup"><span data-stu-id="dbe39-153">AverageRate</span></span>|<span data-ttu-id="dbe39-154">float [DT_R4]</span><span class="sxs-lookup"><span data-stu-id="dbe39-154">float [DT_R4]</span></span>|<span data-ttu-id="dbe39-155">FactCurrency.AverageRate</span><span class="sxs-lookup"><span data-stu-id="dbe39-155">FactCurrency.AverageRate</span></span>|<span data-ttu-id="dbe39-156">FLOAT</span><span class="sxs-lookup"><span data-stu-id="dbe39-156">float</span></span>|  
    |<span data-ttu-id="dbe39-157">CurrencyID</span><span class="sxs-lookup"><span data-stu-id="dbe39-157">CurrencyID</span></span>|<span data-ttu-id="dbe39-158">string [DT_STR]</span><span class="sxs-lookup"><span data-stu-id="dbe39-158">string [DT_STR]</span></span>|<span data-ttu-id="dbe39-159">DimCurrency.CurrencyAlternateKey</span><span class="sxs-lookup"><span data-stu-id="dbe39-159">DimCurrency.CurrencyAlternateKey</span></span>|<span data-ttu-id="dbe39-160">nchar(3)</span><span class="sxs-lookup"><span data-stu-id="dbe39-160">nchar(3)</span></span>|  
    |<span data-ttu-id="dbe39-161">CurrencyDate</span><span class="sxs-lookup"><span data-stu-id="dbe39-161">CurrencyDate</span></span>|<span data-ttu-id="dbe39-162">date [DT_DATE]</span><span class="sxs-lookup"><span data-stu-id="dbe39-162">date [DT_DATE]</span></span>|<span data-ttu-id="dbe39-163">DimDate.FullDateAlternateKey</span><span class="sxs-lookup"><span data-stu-id="dbe39-163">DimDate.FullDateAlternateKey</span></span>|<span data-ttu-id="dbe39-164">date</span><span class="sxs-lookup"><span data-stu-id="dbe39-164">date</span></span>|  
    |<span data-ttu-id="dbe39-165">EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="dbe39-165">EndOfDayRate</span></span>|<span data-ttu-id="dbe39-166">float [DT_R4]</span><span class="sxs-lookup"><span data-stu-id="dbe39-166">float [DT_R4]</span></span>|<span data-ttu-id="dbe39-167">FactCurrency.EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="dbe39-167">FactCurrency.EndOfDayRate</span></span>|<span data-ttu-id="dbe39-168">FLOAT</span><span class="sxs-lookup"><span data-stu-id="dbe39-168">float</span></span>|  
  
     <span data-ttu-id="dbe39-169">為數據行建議的資料類型 `CurrencyID` 與目的地資料表中的欄位資料類型不相容。</span><span class="sxs-lookup"><span data-stu-id="dbe39-169">The data type suggested for the `CurrencyID` column is incompatible with the data type of the field in the destination table.</span></span> <span data-ttu-id="dbe39-170">因為的資料類型 `DimCurrency.CurrencyAlternateKey` 是 Nchar (3) ，所以 `CurrencyID` 必須從 string [DT_STR] 變更為 string [DT_WSTR]。</span><span class="sxs-lookup"><span data-stu-id="dbe39-170">Because the data type of `DimCurrency.CurrencyAlternateKey` is nchar (3), `CurrencyID` must be changed from string [DT_STR] to string [DT_WSTR].</span></span> <span data-ttu-id="dbe39-171">此外，此欄位 `DimDate.FullDateAlternateKey` 會定義為日期資料類型; 因此，必須 `CurrencyDate` 從 date [DT_Date] 變更為資料庫日期 [DT_DBDATE]。</span><span class="sxs-lookup"><span data-stu-id="dbe39-171">Additionally, the field `DimDate.FullDateAlternateKey` is defined as a date data type; therefore, `CurrencyDate` needs to be changed from date [DT_Date] to database date [DT_DBDATE].</span></span>  
  
2.  <span data-ttu-id="dbe39-172">在清單中選取 [CurrencyID] 資料行，然後在 [屬性] 窗格中，將資料行的資料類型 `CurrencyID` 從 string [DT_STR] 變更為 Unicode string [DT_WSTR]。</span><span class="sxs-lookup"><span data-stu-id="dbe39-172">In the list, select the CurrencyID column and in the property pane, change the Data Type of column `CurrencyID` from string [DT_STR] to Unicode string [DT_WSTR].</span></span>  
  
3.  <span data-ttu-id="dbe39-173">在 [屬性] 窗格中，將 [date [DT_DATE] 資料行的資料類型變更 `CurrencyDate` 為 [資料庫日期 [DT_DBDATE]]。</span><span class="sxs-lookup"><span data-stu-id="dbe39-173">In the property pane, change the data type of column `CurrencyDate` from date [DT_DATE] to database date [DT_DBDATE].</span></span>  
  
4.  <span data-ttu-id="dbe39-174">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="dbe39-174">Click **OK**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="dbe39-175">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="dbe39-175">Next Task in Lesson</span></span>  
 [<span data-ttu-id="dbe39-176">步驟 3：新增和設定 OLE DB 連線管理員</span><span class="sxs-lookup"><span data-stu-id="dbe39-176">Step 3: Adding and Configuring an OLE DB Connection Manager</span></span>](lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
## <a name="see-also"></a><span data-ttu-id="dbe39-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbe39-177">See Also</span></span>  
 <span data-ttu-id="dbe39-178">[一般檔案連線管理員](connection-manager/file-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="dbe39-178">[Flat File Connection Manager](connection-manager/file-connection-manager.md) </span></span>  
 [<span data-ttu-id="dbe39-179">Integration Services 資料類型</span><span class="sxs-lookup"><span data-stu-id="dbe39-179">Integration Services Data Types</span></span>](data-flow/integration-services-data-types.md)  
  
  
