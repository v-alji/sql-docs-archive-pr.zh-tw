---
title: 步驟 6：加入及設定查閱轉換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5c59f723-9707-4407-80ae-f05f483cf65f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 96b0a848508c19eb24cf1538244a39fcec57361a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596128"
---
# <a name="step-6-adding-and-configuring-the-lookup-transformations"></a><span data-ttu-id="6da15-102">步驟 6：新增和設定查閱轉換</span><span class="sxs-lookup"><span data-stu-id="6da15-102">Step 6: Adding and Configuring the Lookup Transformations</span></span>
  <span data-ttu-id="6da15-103">在設定一般檔案來源從來源檔擷取資料之後，下一項工作是要定義所需要的查閱轉換來取得 **CurrencyKey** 和 **DateKey**的值。</span><span class="sxs-lookup"><span data-stu-id="6da15-103">After you have configured the Flat File source to extract data from the source file, the next task is to define the Lookup transformations needed to obtain the values for the **CurrencyKey** and **DateKey**.</span></span> <span data-ttu-id="6da15-104">查閱轉換是藉由聯結指定輸入資料行中的資料與參考資料集內的資料行來執行查閱。</span><span class="sxs-lookup"><span data-stu-id="6da15-104">A Lookup transformation performs a lookup by joining data in the specified input column to a column in a reference dataset.</span></span> <span data-ttu-id="6da15-105">參考資料集可以是現有的資料表或檢視、新資料表，或 SQL 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="6da15-105">The reference dataset can be an existing table or view, a new table, or the result of an SQL statement.</span></span> <span data-ttu-id="6da15-106">在此教學課程中，查閱轉換使用 OLE DB 連接管理員來連接到資料庫，該資料庫包含的資料就是參考資料集的來源。</span><span class="sxs-lookup"><span data-stu-id="6da15-106">In this tutorial, the Lookup transformation uses an OLE DB connection manager to connect to the database that contains the data that is the source of the reference dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6da15-107">您也可以將查閱轉換設定為連接到包含參考資料集的快取。</span><span class="sxs-lookup"><span data-stu-id="6da15-107">You can also configure the Lookup transformation to connect to a cache that contains the reference dataset.</span></span> <span data-ttu-id="6da15-108">如需相關資訊，請參閱 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="6da15-108">For more information, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="6da15-109">在此教學課程中，您會在封裝中加入和設定下列兩個查閱轉換元件：</span><span class="sxs-lookup"><span data-stu-id="6da15-109">For this tutorial, you will add and configure the following two Lookup transformation components to the package:</span></span>  
  
-   <span data-ttu-id="6da15-110">一個轉換是基於一般檔案中相符的 **CurrencyID** 資料行值，來查閱 **DimCurrency** 維度資料表之 **CurrencyKey** 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="6da15-110">One transformation to perform a lookup of values from the **CurrencyKey** column of the **DimCurrency** dimension table based on matching **CurrencyID** column values from the flat file.</span></span>  
  
-   <span data-ttu-id="6da15-111">一個轉換是基於一般檔案中相符的 **CurrencyDate** 資料行值，來查閱 **DimDate** 維度資料表之 **DateKey** 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="6da15-111">One transformation to perform a lookup of values from the **DateKey** column of the **DimDate** dimension table based on matching **CurrencyDate** column values from the flat file.</span></span>  
  
 <span data-ttu-id="6da15-112">在這兩種案例中，查閱轉換將利用您先前建立的 OLE DB 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="6da15-112">In both cases, the Lookup transformation will utilize the OLE DB connection manager that you previously created.</span></span>  
  
### <a name="to-add-and-configure-the-lookup-currency-key-transformation"></a><span data-ttu-id="6da15-113">若要加入及設定查閱貨幣索引鍵轉換</span><span class="sxs-lookup"><span data-stu-id="6da15-113">To add and configure the Lookup Currency Key transformation</span></span>  
  
1.  <span data-ttu-id="6da15-114">在 [ **SSIS 工具箱**] 中，展開 [**一般**]，然後將 [**查閱**] 拖曳至 **[資料流程]** 索引標籤的設計介面上。將 [查閱] 直接放在 [**解壓縮範例貨幣] 資料**源之下。</span><span class="sxs-lookup"><span data-stu-id="6da15-114">In the **SSIS Toolbox**, expand **Common**, and then drag **Lookup** onto the design surface of the **Data Flow** tab. Place Lookup directly below the **Extract Sample Currency Data** source.</span></span>  
  
2.  <span data-ttu-id="6da15-115">按一下 [Extract Sample Currency Data (擷取範例貨幣資料)]\*\*\*\* 一般檔案來源，將綠色箭頭拖曳至新增的 [查閱]\*\*\*\* 轉換來連接兩個元件。</span><span class="sxs-lookup"><span data-stu-id="6da15-115">Click the **Extract Sample Currency Data** flat file source and drag the green arrow onto the newly added **Lookup** transformation to connect the two components.</span></span>  
  
3.  <span data-ttu-id="6da15-116">在 [資料流程]\*\*\*\* 設計介面中，按一下 [查閱]\*\*\*\* 轉換中的 [查閱]\*\*\*\*，將名稱變更為 [Lookup Currency Key (查閱貨幣索引鍵)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6da15-116">On the **Data Flow** design surface, click **Lookup** in the **Lookup** transformation, and change the name to **Lookup Currency Key**.</span></span>  
  
4.  <span data-ttu-id="6da15-117">按兩下 [Lookup Currency Key (查閱貨幣索引鍵)]\*\*\*\* 轉換，即可顯示「查閱轉換編輯器」。</span><span class="sxs-lookup"><span data-stu-id="6da15-117">Double-click the **Lookup CurrencyKey** transformation to display the Lookup Transformation Editor.</span></span>  
  
5.  <span data-ttu-id="6da15-118">在 [一般]  頁面上，進行下列選擇：</span><span class="sxs-lookup"><span data-stu-id="6da15-118">On the **General** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="6da15-119">選取 [完整快取]  。</span><span class="sxs-lookup"><span data-stu-id="6da15-119">Select **Full cache**.</span></span>  
  
    2.  <span data-ttu-id="6da15-120">在 **[連接類型]** 區域中，選取 **[OLE DB 連接管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="6da15-120">In the **Connection type** area, select **OLE DB connection manager**.</span></span>  
  
6.  <span data-ttu-id="6da15-121">在 [連接]  頁面上，進行下列選擇：</span><span class="sxs-lookup"><span data-stu-id="6da15-121">On the **Connection** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="6da15-122">在 [OLE DB 連接管理員]  對話方塊中，確定 [localhost.AdventureWorksDW2012]  已顯示。</span><span class="sxs-lookup"><span data-stu-id="6da15-122">In the **OLE DB connection manager** dialog box, ensure that **localhost.AdventureWorksDW2012** is displayed.</span></span>  
  
    2.  <span data-ttu-id="6da15-123">選取 [使用 SQL 查詢的結果]\*\*\*\*，然後輸入或複製下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="6da15-123">Select **Use results of an SQL query**, and then type or copy the following SQL statement:</span></span>  
  
        ```  
        select * from (select * from [dbo].[DimCurrency]) as refTable  
        where [refTable].[CurrencyAlternateKey] = 'ARS'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'AUD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'BRL'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'CAD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'CNY'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'DEM'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'EUR'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'FRF'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'GBP'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'JPY'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'MXN'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'SAR'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'USD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'VEB'  
        ```  
  
7.  <span data-ttu-id="6da15-124">在 [資料行]\*\*\*\* 頁面上，進行下列選擇：</span><span class="sxs-lookup"><span data-stu-id="6da15-124">On the **Columns** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="6da15-125">在 [可用的輸入資料行]\*\*\*\* 面板中，將 [CurrencyID]\*\*\*\* 拖曳至 [可用的查閱資料行]\*\*\*\* 面板，並將它放在 [CurrencyAlternateKey]\*\*\*\* 中。</span><span class="sxs-lookup"><span data-stu-id="6da15-125">In the **Available Input Columns** panel, drag **CurrencyID** to the **Available Lookup Columns** panel and drop it on **CurrencyAlternateKey**.</span></span>  
  
    2.  <span data-ttu-id="6da15-126">在 [可用的查閱資料行]\*\*\*\* 清單中，選取 [CurrencyKey]\*\*\*\* 左邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6da15-126">In the **Available Lookup Columns** list, select the check box to the left of **CurrencyKey**.</span></span>  
  
8.  <span data-ttu-id="6da15-127">按一下 [確定]\*\*\*\*，回到 [資料流程]\*\*\*\* 設計介面。</span><span class="sxs-lookup"><span data-stu-id="6da15-127">Click **OK** to return to the **Data Flow** design surface.</span></span>  
  
9. <span data-ttu-id="6da15-128">以滑鼠右鍵按一下 [Lookup Currency Key (查閱貨幣索引鍵)] 轉換，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6da15-128">Right-click the Lookup Currency Key transformation, click **Properties**.</span></span>  
  
10. <span data-ttu-id="6da15-129">在 [屬性視窗中，確認 `LocaleID` 屬性是設為 [**英文] ([美國]) **而且 [ **DefaultCodePage** ] 屬性設定為**1252**。</span><span class="sxs-lookup"><span data-stu-id="6da15-129">In the Properties window, verify that the `LocaleID` property is set to **English (United States)** and the **DefaultCodePage** property is set to **1252**.</span></span>  
  
### <a name="to-add-and-configure-the--lookup-datekey-transformation"></a><span data-ttu-id="6da15-130">若要加入和設定查閱日期索引鍵轉換</span><span class="sxs-lookup"><span data-stu-id="6da15-130">To add and configure the  Lookup DateKey transformation</span></span>  
  
1.  <span data-ttu-id="6da15-131">在 [SSIS 工具箱]\*\*\*\* 中，將 [查閱]\*\*\*\* 拖曳至 [資料流程]\*\*\*\* 設計介面中。</span><span class="sxs-lookup"><span data-stu-id="6da15-131">In the **SSIS Toolbox**, drag **Lookup** onto the **Data Flow** design surface.</span></span> <span data-ttu-id="6da15-132">將 [查閱] 直接放在 [Lookup Currency Key (查閱貨幣索引鍵)]\*\*\*\* 轉換下面。</span><span class="sxs-lookup"><span data-stu-id="6da15-132">Place Lookup directly below the **Lookup Currency Key** transformation.</span></span>  
  
2.  <span data-ttu-id="6da15-133">按一下 [Lookup Currency Key (查閱貨幣索引鍵)]\*\*\*\* 轉換，將綠色箭頭拖曳至新增的 [查閱]\*\*\*\* 轉換來連接兩個元件。</span><span class="sxs-lookup"><span data-stu-id="6da15-133">Click the **Lookup Currency Key** transformation and drag the green arrow onto the newly added **Lookup** transformation to connect the two components.</span></span>  
  
3.  <span data-ttu-id="6da15-134">在 [輸入輸出選擇]\*\*\*\* 對話方塊的 [輸出]\*\*\*\* 清單方塊中，按一下 [查閱比對輸出]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6da15-134">In the **Input Output Selection** dialog box, click **Lookup Match Output** in the **Output** list box, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="6da15-135">在 [資料流程]\*\*\*\* 設計介面中，於新增的 [查閱]\*\*\*\* 轉換中按一下 [查閱]\*\*\*\*，將名稱變更為 [Lookup Date Key (查閱日期索引鍵)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6da15-135">On the **Data Flow** design surface, click **Lookup** in the newly added **Lookup** transformation, and change the name to **Lookup Date Key**.</span></span>  
  
5.  <span data-ttu-id="6da15-136">按兩下 [Lookup Date Key (查閱日期索引鍵)]\*\*\*\* 轉換。</span><span class="sxs-lookup"><span data-stu-id="6da15-136">Double-click the **Lookup Date Key** transformation.</span></span>  
  
6.  <span data-ttu-id="6da15-137">在 [一般]\*\*\*\* 頁面上，選取 [部分快取]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6da15-137">On the **General** page, select **Partial cache**.</span></span>  
  
7.  <span data-ttu-id="6da15-138">在 [連接]\*\*\*\* 頁面上，進行下列選擇：</span><span class="sxs-lookup"><span data-stu-id="6da15-138">On the **Connection** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="6da15-139">在 [OLE DB 連接管理員]\*\*\*\* 對話方塊中，確定 [localhost.AdventureWorksDW2012]\*\*\*\* 已顯示。</span><span class="sxs-lookup"><span data-stu-id="6da15-139">In the **OLEDB connection manager** dialog box, ensure that **localhost.AdventureWorksDW2012** is displayed.</span></span>  
  
    2.  <span data-ttu-id="6da15-140">在 [使用資料表或檢視]\*\*\*\* 方塊中，輸入或選取 **[dbo].[DimDate]**。</span><span class="sxs-lookup"><span data-stu-id="6da15-140">In the **Use a table or view** box, type or select **[dbo].[DimDate]**.</span></span>  
  
8.  <span data-ttu-id="6da15-141">在 [資料行]\*\*\*\* 頁面上，進行下列選擇：</span><span class="sxs-lookup"><span data-stu-id="6da15-141">On the **Columns** page, make the following selections:</span></span>  
  
    1.  <span data-ttu-id="6da15-142">在 [可用的輸入資料行]\*\*\*\* 面板中，將 [CurrencyDate]\*\*\*\* 拖曳至 [可用的查閱資料行]\*\*\*\* 面板，並將它放在 [FullDateAlternateKey]\*\*\*\* 中。</span><span class="sxs-lookup"><span data-stu-id="6da15-142">In the **Available Input Columns** panel, drag **CurrencyDate** to the **Available Lookup Columns** panel and drop it on **FullDateAlternateKey**.</span></span>  
  
    2.  <span data-ttu-id="6da15-143">在 [可用的查閱資料行]\*\*\*\* 清單中，選取 [DateKey]\*\*\*\* 左邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6da15-143">In the **Available Lookup Columns** list, select the check box to the left of **DateKey**.</span></span>  
  
9. <span data-ttu-id="6da15-144">在 [進階]\*\*\*\* 頁面上，檢閱快取選項。</span><span class="sxs-lookup"><span data-stu-id="6da15-144">On the **Advanced** page, review the caching options.</span></span>  
  
10. <span data-ttu-id="6da15-145">按一下 [確定]\*\*\*\*，回到 [資料流程]\*\*\*\* 設計介面。</span><span class="sxs-lookup"><span data-stu-id="6da15-145">Click **OK** to return to the **Data Flow** design surface.</span></span>  
  
11. <span data-ttu-id="6da15-146">以滑鼠右鍵按一下 [Lookup Date Key (查閱日期索引鍵)] 轉換，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6da15-146">Right-click the Lookup Date Key transformation and click **Properties.**</span></span>  
  
12. <span data-ttu-id="6da15-147">在 [屬性視窗中，確認 `LocaleID` 屬性是設為 [**英文] ([美國]) **而且 [ **DefaultCodePage** ] 屬性設定為**1252**。</span><span class="sxs-lookup"><span data-stu-id="6da15-147">In the Properties window, verify that the `LocaleID` property is set to **English (United States)** and the **DefaultCodePage** property is set to **1252**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6da15-148">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="6da15-148">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6da15-149">步驟 7：新增和設定 OLE DB 目的地</span><span class="sxs-lookup"><span data-stu-id="6da15-149">Step 7: Adding and Configuring the OLE DB Destination</span></span>](lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
## <a name="see-also"></a><span data-ttu-id="6da15-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6da15-150">See Also</span></span>  
 [<span data-ttu-id="6da15-151">查閱轉換</span><span class="sxs-lookup"><span data-stu-id="6da15-151">Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
