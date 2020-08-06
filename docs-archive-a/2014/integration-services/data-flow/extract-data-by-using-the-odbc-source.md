---
title: 使用 ODBC 來源擷取資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 10f25703-49a2-4d45-abab-6b4da2a57ba5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c05efe2b0479047280fc093ee555e037c77d82e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709793"
---
# <a name="extract-data-by-using-the-odbc-source"></a><span data-ttu-id="1ce10-102">使用 ODBC 來源來擷取資料</span><span class="sxs-lookup"><span data-stu-id="1ce10-102">Extract Data by Using the ODBC Source</span></span>
  <span data-ttu-id="1ce10-103">此程序描述如何使用 ODBC 來源擷取資料。</span><span class="sxs-lookup"><span data-stu-id="1ce10-103">This procedure describes how to extract data by using an ODBC source.</span></span> <span data-ttu-id="1ce10-104">若要加入和設定 ODBC 來源，封裝必須至少含有一個「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="1ce10-104">To add and configure an ODBC source, the package must already include at least one Data Flow task.</span></span>  
  
### <a name="to-extract-data-using-an-odbc-source"></a><span data-ttu-id="1ce10-105">使用 ODBC 來源擷取資料</span><span class="sxs-lookup"><span data-stu-id="1ce10-105">To extract data using an ODBC source</span></span>  
  
1.  <span data-ttu-id="1ce10-106">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，開啟所要的 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="1ce10-106">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] package you want.</span></span>  
  
2.  <span data-ttu-id="1ce10-107">按一下 **[資料流程]** 索引標籤，然後將 ODBC 來源從 **[工具箱]** 拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="1ce10-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the ODBC source to the design surface.</span></span>  
  
3.  <span data-ttu-id="1ce10-108">按兩下 ODBC 來源。</span><span class="sxs-lookup"><span data-stu-id="1ce10-108">Double-click the ODBC source.</span></span>  
  
4.  <span data-ttu-id="1ce10-109">在 **[ODBC 來源編輯器]** 對話方塊中的 **[連接管理員]** 頁面上，選取現有的 ODBC 連接管理員，或按一下 **[新增]** 以建立新的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="1ce10-109">In the **ODBC Source Editor** dialog box, on the **Connection Manager** page, select an existing ODBC connection manager or click **New** to create a new connection manager.</span></span>  
  
5.  <span data-ttu-id="1ce10-110">選取資料存取方法。</span><span class="sxs-lookup"><span data-stu-id="1ce10-110">Select the data access method.</span></span>  
  
    -   <span data-ttu-id="1ce10-111">**資料表名稱**：選取 ODBC 連接管理員連接之資料庫中的資料表或檢視，或輸入規則運算式以識別資料表。</span><span class="sxs-lookup"><span data-stu-id="1ce10-111">**Table Name**: Select a table or view in the database or type a regular expression to identify the table to which the ODBC connection manager connects.</span></span>  
  
         <span data-ttu-id="1ce10-112">此清單只包含前 1000 個資料表。</span><span class="sxs-lookup"><span data-stu-id="1ce10-112">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="1ce10-113">如果您的資料庫包含超過 1000 個資料表，您可以輸入資料表名稱的開頭或使用 (\*) 萬用字元來輸入名稱的任何部分，以便顯示您想要使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="1ce10-113">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>  
  
    -   <span data-ttu-id="1ce10-114">**SQL 命令**：輸入 SQL 命令，或按一下 **[瀏覽]** 從文字檔載入 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="1ce10-114">**SQL Command**: Type an SQL Command or click **Browse** to load the SQL query from a text file.</span></span>  
  
6.  <span data-ttu-id="1ce10-115">您可以按一下 **[預覽]** ，以檢視 ODBC 來源擷取的最多 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="1ce10-115">You can click **Preview** to view up to 200 rows of the data extracted by the ODBC source.</span></span>  
  
7.  <span data-ttu-id="1ce10-116">若要更新外部及輸出資料行之間的對應，請按一下 **[資料行]** ，並在 **[外部資料行]** 清單中選取不同的資料行。</span><span class="sxs-lookup"><span data-stu-id="1ce10-116">To update the mapping between external and output columns, click **Columns** and select different columns in the **External Column** list.</span></span>  
  
8.  <span data-ttu-id="1ce10-117">如有需要，藉由編輯 **[輸出資料行]** 清單中的值，更新輸出資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="1ce10-117">If necessary, update the names of output columns by editing values in the **Output Column** list.</span></span>  
  
9. <span data-ttu-id="1ce10-118">若要設定錯誤輸出，請按一下 **[錯誤輸出]** 。</span><span class="sxs-lookup"><span data-stu-id="1ce10-118">To configure the error output, click **Error Output**.</span></span>  
  
10. <span data-ttu-id="1ce10-119">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="1ce10-119">Click **OK**.</span></span>  
  
11. <span data-ttu-id="1ce10-120">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="1ce10-120">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce10-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ce10-121">See Also</span></span>  
 <span data-ttu-id="1ce10-122">[ODBC 來源編輯器 &#40;連線管理員頁面&#41;](../odbc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="1ce10-122">[ODBC Source Editor &#40;Connection Manager Page&#41;](../odbc-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="1ce10-123">[ODBC 來源編輯器 &#40;資料行頁面&#41;](../odbc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="1ce10-123">[ODBC Source Editor &#40;Columns Page&#41;](../odbc-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="1ce10-124">ODBC 來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="1ce10-124">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../odbc-source-editor-error-output-page.md)  
  
  
