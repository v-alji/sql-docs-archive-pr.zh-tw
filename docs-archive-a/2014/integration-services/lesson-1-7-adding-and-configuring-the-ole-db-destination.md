---
title: 步驟 7：新增及設定 OLE DB 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 442c841d-d528-4bf0-8724-7156f909ee50
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da917ccc4ca756c2442e70477976b5a71f7eb56e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596127"
---
# <a name="step-7-adding-and-configuring-the-ole-db-destination"></a><span data-ttu-id="b1c0a-102">步驟 7：新增和設定 OLE DB 目的地</span><span class="sxs-lookup"><span data-stu-id="b1c0a-102">Step 7: Adding and Configuring the OLE DB Destination</span></span>
  <span data-ttu-id="b1c0a-103">現在，封裝可以從一般檔案來源中擷取資料，再將資料轉換成與目的地相容的格式。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-103">Your package now can extract data from the flat file source and transform that data into a format that is compatible with the destination.</span></span> <span data-ttu-id="b1c0a-104">下一項工作是要把已轉換的資料實際載入到目的地。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-104">The next task is to actually load the transformed data into the destination.</span></span> <span data-ttu-id="b1c0a-105">若要載入資料，您必須將 OLE DB 目的地加入資料流程中。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-105">To load the data, you must add an OLE DB destination to the data flow.</span></span> <span data-ttu-id="b1c0a-106">OLE DB 目的地可使用資料庫資料表、檢視或 SQL 命令，將資料載入到各種 OLE DB 相容資料庫中。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-106">The OLE DB destination can use a database table, view, or an SQL command to load data into a variety of OLE DB-compliant databases.</span></span>  
  
 <span data-ttu-id="b1c0a-107">在這個程序中，您加入和設定 OLE DB 目的地來使用您先前建立的 OLE DB 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-107">In this procedure, you add and configure an OLE DB destination to use the OLE DB connection manager that you previously created.</span></span>  
  
### <a name="to-add-and-configure-the-sample-ole-db-destination"></a><span data-ttu-id="b1c0a-108">若要加入和設定範例 OLE DB 目的地</span><span class="sxs-lookup"><span data-stu-id="b1c0a-108">To add and configure the sample OLE DB destination</span></span>  
  
1.  <span data-ttu-id="b1c0a-109">在 [ **SSIS 工具箱**] 中，展開 [**其他目的地**]，然後將 [ **OLE DB 目的地**] 拖曳至 **[資料流程]** 索引標籤的設計介面上。將 OLE DB 目的地直接放在 [**查閱日期索引鍵**] 轉換底下。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-109">In the **SSIS Toolbox**, expand **Other Destinations**, and drag **OLE DB Destination** onto the design surface of the **Data Flow** tab. Place the OLE DB destination directly below the **Lookup Date Key** transformation.</span></span>  
  
2.  <span data-ttu-id="b1c0a-110">按一下 [查閱日期索引鍵]\*\*\*\* 轉換，將綠色箭頭拖曳至新加入的 [OLE DB 目的地]\*\*\*\*，來連接這兩個元件。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-110">Click the **Lookup Date Key** transformation and drag the green arrow over to the newly added **OLE DB Destination** to connect the two components together.</span></span>  
  
3.  <span data-ttu-id="b1c0a-111">在 [輸入輸出選擇]\*\*\*\* 對話方塊的 [輸出]\*\*\*\* 清單方塊中，按一下 [查閱比對輸出]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-111">In the **Input Output Selection** dialog box, in the **Output** list box, click **Lookup Match Output**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="b1c0a-112">在 [資料流程]\*\*\*\* 設計介面上，於新加入的 [OLE DB 目的地]\*\*\*\* 元件中按一下 [OLE DB 目的地]\*\*\*\*，將名稱變更為**範例 OLE DB 目的地**。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-112">On the **Data Flow** design surface, click **OLE DB Destination** in the newly added **OLE DB Destination** component, and change the name to **Sample OLE DB Destination**.</span></span>  
  
5.  <span data-ttu-id="b1c0a-113">按兩下 [範例 OLE DB 目的地]  。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-113">Double-click **Sample OLE DB Destination**.</span></span>  
  
6.  <span data-ttu-id="b1c0a-114">在 [OLE DB 目的地編輯器]\*\*\*\* 對話方塊中，確定已在 [OLE DB 連線管理員]\*\*\*\* 方塊中選取 [localhost.AdventureWorksDW2012]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-114">In the **OLE DB Destination Editor** dialog box, ensure that **localhost.AdventureWorksDW2012** is selected in the **OLE DB Connection manager** box.</span></span>  
  
7.  <span data-ttu-id="b1c0a-115">在 [資料表或檢視的名稱]\*\*\*\* 方塊中，輸入或選取 **[dbo].[FactCurrencyRate]**。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-115">In the **Name of the table or the view** box, type or select **[dbo].[FactCurrencyRate]**.</span></span>  
  
8.  <span data-ttu-id="b1c0a-116">按一下 [新增]\*\*\*\* 按鈕，建立新的資料表。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-116">Click the **New** button to create a new table.</span></span>  <span data-ttu-id="b1c0a-117">在指令碼中變更資料表的名稱，使其成為 **NewFactCurrencyRate**。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-117">Change the name of the table in the script to read **NewFactCurrencyRate**.</span></span>  <span data-ttu-id="b1c0a-118">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-118">Click **OK**.</span></span>  
  
9. <span data-ttu-id="b1c0a-119">按一下 [確定]\*\*\*\* 後，此對話方塊將會關閉，而且 [資料表或檢視表的名稱]\*\*\*\* 將會自動變更為 [NewFactCurrencyRate]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-119">Upon clicking **OK**, the dialog will close and the **Name of the table or the view** will automatically change to **NewFactCurrencyRate**.</span></span>  
  
10. <span data-ttu-id="b1c0a-120">按一下 [對應]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-120">Click **Mappings**.</span></span>  
  
11. <span data-ttu-id="b1c0a-121">確認 [AverageRate]  、[CurrencyKey]  、[EndOfDayRate]  和 [DateKey]  輸入資料行都正確對應到目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-121">Verify that the **AverageRate**, **CurrencyKey**, **EndOfDayRate**, and **DateKey** input columns are mapped correctly to the destination columns.</span></span> <span data-ttu-id="b1c0a-122">如果對應到同名資料行，則表示對應是正確的。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-122">If same-named columns are mapped, the mapping is correct.</span></span>  
  
12. <span data-ttu-id="b1c0a-123">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-123">Click **OK**.</span></span>  
  
13. <span data-ttu-id="b1c0a-124">以滑鼠右鍵按一下 [範例 OLE DB 目的地]\*\*\*\* 目的地，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-124">Right-click the **Sample OLE DB Destination** destination and click **Properties**.</span></span>  
  
14. <span data-ttu-id="b1c0a-125">在 [屬性視窗中，確認 `LocaleID` 屬性已設為 [**英文] ([美國]) **而且 `DefaultCodePage` 屬性設定為**1252**。</span><span class="sxs-lookup"><span data-stu-id="b1c0a-125">In the Properties window, verify that the `LocaleID` property is set to **English (United States)** and the`DefaultCodePage` property is set to **1252**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="b1c0a-126">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="b1c0a-126">Next Task in Lesson</span></span>  
 [<span data-ttu-id="b1c0a-127">步驟 8：使第 1 課的封裝更容易了解</span><span class="sxs-lookup"><span data-stu-id="b1c0a-127">Step 8: Making the Lesson 1 Package Easier to Understand</span></span>](lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
## <a name="see-also"></a><span data-ttu-id="b1c0a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1c0a-128">See Also</span></span>  
 [<span data-ttu-id="b1c0a-129">OLE DB 目的地</span><span class="sxs-lookup"><span data-stu-id="b1c0a-129">OLE DB Destination</span></span>](data-flow/ole-db-destination.md)  
  
  
