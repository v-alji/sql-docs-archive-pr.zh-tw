---
title: 使用 ODBC 目的地來載入資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 339ec0a8-922e-48c0-97b3-fc5ee34f95e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e8bf0b30619c2886df6ddb28858cf98bad858421
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700096"
---
# <a name="load-data-by-using-the-odbc-destination"></a><span data-ttu-id="dddc9-102">使用 ODBC 目的地來載入資料</span><span class="sxs-lookup"><span data-stu-id="dddc9-102">Load Data by Using the ODBC Destination</span></span>
  <span data-ttu-id="dddc9-103">此程序說明如何透過使用 ODBC 目的地載入資料。</span><span class="sxs-lookup"><span data-stu-id="dddc9-103">This procedure shows how to load data by using the ODBC destination.</span></span> <span data-ttu-id="dddc9-104">若要加入及設定 ODBC 目的地，封裝必須已包括至少一個「資料流程」工作與來源。</span><span class="sxs-lookup"><span data-stu-id="dddc9-104">To add and configure an ODBC destination, the package must already include at least one Data Flow task and source.</span></span>  
  
### <a name="to-load-data-using-an-odbc-destination"></a><span data-ttu-id="dddc9-105">使用 ODBC 目的地載入資料</span><span class="sxs-lookup"><span data-stu-id="dddc9-105">To load data using an ODBC destination</span></span>  
  
1.  <span data-ttu-id="dddc9-106">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，開啟所要的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="dddc9-106">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package you want.</span></span>  
  
2.  <span data-ttu-id="dddc9-107">按一下 **[資料流程]** 索引標籤，然後將 ODBC 目的地從 **[工具箱]** 拖曳到設計介面。</span><span class="sxs-lookup"><span data-stu-id="dddc9-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the ODBC destination to the design surface.</span></span>  
  
3.  <span data-ttu-id="dddc9-108">將某個資料流程元件的可用輸出拖曳到 ODBC 目的地的輸入。</span><span class="sxs-lookup"><span data-stu-id="dddc9-108">Drag an available output of a data flow component to the input of the ODBC destination.</span></span>  
  
4.  <span data-ttu-id="dddc9-109">按兩下 ODBC 目的地。</span><span class="sxs-lookup"><span data-stu-id="dddc9-109">Double-click the ODBC destination.</span></span>  
  
5.  <span data-ttu-id="dddc9-110">在 **[ODBC 目的地編輯器]** 對話方塊中的 **[連接管理員]** 頁面上，選取現有的 ODBC 連接管理員，或按一下 **[新增]** 以建立新的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="dddc9-110">In the **ODBC Destination Editor** dialog box, on the **Connection Manager** page, select an existing ODBC connection manager or click **New** to create a new connection manager.</span></span>  
  
6.  <span data-ttu-id="dddc9-111">選取資料存取方法。</span><span class="sxs-lookup"><span data-stu-id="dddc9-111">Select the data access method.</span></span>  
  
    -   <span data-ttu-id="dddc9-112">**資料表名稱 - 批次**：若要將 ODBC 目的地設定成以批次模式運作，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="dddc9-112">**Table Name - Batch**: Select this option to configure the ODBC destination to work in batch mode.</span></span> <span data-ttu-id="dddc9-113">當您選取此選項時，可以設定 **[批次大小]** 。</span><span class="sxs-lookup"><span data-stu-id="dddc9-113">When you select this option, you can set the **Batch size**.</span></span>  
  
    -   <span data-ttu-id="dddc9-114">**資料表名稱 - 逐列**：若要將 ODBC 目的地設定成插入每個資料列至目的地資料表 (一次一個)，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="dddc9-114">**Table Name - Row by Row**: Select this option to configure the ODBC destination to insert each of the rows into the destination table one at a time.</span></span> <span data-ttu-id="dddc9-115">當您選取此選項時，資料會以一次一個資料列的方式載入到資料表。</span><span class="sxs-lookup"><span data-stu-id="dddc9-115">When you select this option, the data is loaded into the table one row at a time.</span></span>  
  
7.  <span data-ttu-id="dddc9-116">在 **[資料表或檢視表的名稱]** 欄位中，從清單中選取資料庫中可用的資料表或檢視表，或是輸入可識別資料表的規則運算式。此清單只包含前 1000 個資料表。</span><span class="sxs-lookup"><span data-stu-id="dddc9-116">In the **Name of the table or the view** field, select an available table or view from the database from the list or type in a regular expression to identify the table.This list contains the first 1000 tables only.</span></span> <span data-ttu-id="dddc9-117">如果您的資料庫包含超過 1000 個資料表，您可以輸入資料表名稱的開頭或使用 (\*) 萬用字元來輸入名稱的任何部分，以便顯示您想要使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="dddc9-117">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>  
  
8.  <span data-ttu-id="dddc9-118">您可以按一下 **[預覽]** ，最多可檢視從 ODBC 目的地中選取之資料表的 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="dddc9-118">You can click **Preview** to view up to 200 rows of the data from the table selected in the ODBC destination.</span></span>  
  
9. <span data-ttu-id="dddc9-119">按一下 **[對應]** ，然後將資料行從一個清單拖曳至另一個清單，使 **[可用的輸入資料行]** 清單中的資料行對應至 **[可用的目的地資料行]** 清單中的資料行。</span><span class="sxs-lookup"><span data-stu-id="dddc9-119">Click **Mappings** and then map columns from the **Available Input Columns** list to columns in the **Available Destination Columns** list by dragging columns from one list to another.</span></span>  
  
10. <span data-ttu-id="dddc9-120">若要設定錯誤輸出，請按一下 **[錯誤輸出]** 。</span><span class="sxs-lookup"><span data-stu-id="dddc9-120">To configure the error output, click **Error Output**.</span></span>  
  
11. <span data-ttu-id="dddc9-121">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="dddc9-121">Click **OK**.</span></span>  
  
12. <span data-ttu-id="dddc9-122">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="dddc9-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dddc9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dddc9-123">See Also</span></span>  
 <span data-ttu-id="dddc9-124">[ODBC 目的地編輯器 &#40;連線管理員頁面&#41;](../odbc-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="dddc9-124">[ODBC Destination Editor &#40;Connection Manager Page&#41;](../odbc-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="dddc9-125">[ODBC 目的地編輯器 &#40;對應頁面&#41;](../odbc-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="dddc9-125">[ODBC Destination Editor &#40;Mappings Page&#41;](../odbc-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="dddc9-126">ODBC 來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="dddc9-126">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../odbc-source-editor-error-output-page.md)  
  
  
