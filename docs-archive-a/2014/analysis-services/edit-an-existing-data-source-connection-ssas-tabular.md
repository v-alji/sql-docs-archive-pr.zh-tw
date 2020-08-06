---
title: 編輯現有的資料來源連接 (SSAS 表格式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.selexistconn.f1
ms.assetid: 97e63f18-a01d-4c91-a411-e7e6d40a0647
author: minewiskan
ms.author: owend
ms.openlocfilehash: 675a0d1119e25a92231d3e74a79739cb2e96b6d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599244"
---
# <a name="edit-an-existing-data-source-connection-ssas-tabular"></a><span data-ttu-id="96ebb-102">編輯現有的資料來源連接 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="96ebb-102">Edit an Existing Data Source Connection (SSAS Tabular)</span></span>
  <span data-ttu-id="96ebb-103">本主題描述如何編輯表格式模型中現有資料來源連接的屬性。</span><span class="sxs-lookup"><span data-stu-id="96ebb-103">This topic describes how to edit the properties of an existing data source connection in a tabular model.</span></span>  
  
 <span data-ttu-id="96ebb-104">當您建立與外部資料來源的連接之後，就可以依照下列方法來修改該連接：</span><span class="sxs-lookup"><span data-stu-id="96ebb-104">After you have created a connection to an external data source, you can later modify that connection in these ways:</span></span>  
  
-   <span data-ttu-id="96ebb-105">您可以變更連接資訊，包括當做來源使用的檔案、摘要或資料庫、連接的屬性，或是其他提供者特有的連接選項。</span><span class="sxs-lookup"><span data-stu-id="96ebb-105">You can change the connection information, including the file, feed, or database used as a source, its properties, or other provider-specific connection options.</span></span>  
  
-   <span data-ttu-id="96ebb-106">您可以變更資料表和資料行對應，並移除已不再使用的資料行參考。</span><span class="sxs-lookup"><span data-stu-id="96ebb-106">You can change table and column mappings, and remove references to columns that are no longer used.</span></span>  
  
-   <span data-ttu-id="96ebb-107">您可以變更從外部資料來源取得的資料表、檢視表或資料行。</span><span class="sxs-lookup"><span data-stu-id="96ebb-107">You can change the tables, views, or columns that you get from the external data source.</span></span>  
  
## <a name="modify-a-connection"></a><span data-ttu-id="96ebb-108">修改連接</span><span class="sxs-lookup"><span data-stu-id="96ebb-108">Modify a Connection</span></span>  
 <span data-ttu-id="96ebb-109">此程序描述如何修改資料庫資料來源連接。</span><span class="sxs-lookup"><span data-stu-id="96ebb-109">This procedure describes how to modify a database data source connection.</span></span> <span data-ttu-id="96ebb-110">使用資料來源的某些選項會因資料來源類型而異，但是您應該能夠輕鬆識別這些差異。</span><span class="sxs-lookup"><span data-stu-id="96ebb-110">Some options for working with data sources differ depending on the data source type; however, you should be able to easily identify those differences.</span></span>  
  
#### <a name="to-change-the-external-data-source-used-by-a-current-connection"></a><span data-ttu-id="96ebb-111">若要變更目前連接所使用的外部資料來源</span><span class="sxs-lookup"><span data-stu-id="96ebb-111">To change the external data source used by a current connection</span></span>  
  
1.  <span data-ttu-id="96ebb-112">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，按一下 **[模型]** 功能表，然後再按一下 **[現有連接]**。</span><span class="sxs-lookup"><span data-stu-id="96ebb-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Existing Connections**.</span></span>  
  
2.  <span data-ttu-id="96ebb-113">選取您要修改的資料來源連接，然後按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="96ebb-113">Select the data source connection you want to modify, and then click **Edit**.</span></span>  
  
3.  <span data-ttu-id="96ebb-114">在 **[編輯連接]** 對話方塊中，按一下 **[瀏覽]** ，找出另一個類型相同，但名稱或位置不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="96ebb-114">In the **Edit Connection** dialog box, click **Browse** to locate another database of the same type but with a different name or location.</span></span>  
  
     <span data-ttu-id="96ebb-115">您一變更資料庫檔案之後，就會出現一則訊息，指出您需要儲存及重新整理資料表，才能看到新的資料。</span><span class="sxs-lookup"><span data-stu-id="96ebb-115">As soon as you change the database file, a message appears indicating that you need to save and refresh the tables in order to see the new data.</span></span>  
  
4.  <span data-ttu-id="96ebb-116">按一下 **[儲存]**，然後按一下 **[關閉]**。</span><span class="sxs-lookup"><span data-stu-id="96ebb-116">Click **Save**, and then click **Close**.</span></span>  
  
5.  <span data-ttu-id="96ebb-117">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，依序按一下 **[模型]**、 **[處理]** 及 **[處理全部]**。</span><span class="sxs-lookup"><span data-stu-id="96ebb-117">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model**, click **Process**, and then click **Process All**.</span></span>  
  
     <span data-ttu-id="96ebb-118">資料表隨即以新的資料來源重新處理，但是會採用原始資料選擇。</span><span class="sxs-lookup"><span data-stu-id="96ebb-118">The tables are re-processed using the new data source, but with the original data selections.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="96ebb-119">如果新的資料來源包含了原本不在原始資料來源中的其他任何資料表，您必須重新開啟已變更的連接並加入資料表。</span><span class="sxs-lookup"><span data-stu-id="96ebb-119">If the new data source contains any additional tables that were not present in the original data source, you must re-open the changed connection and add the tables.</span></span>  
  
## <a name="edit-table-and-column-mappings-bindings"></a><span data-ttu-id="96ebb-120">編輯資料表和資料行對應 (繫結)</span><span class="sxs-lookup"><span data-stu-id="96ebb-120">Edit Table and Column Mappings (Bindings)</span></span>  
 <span data-ttu-id="96ebb-121">本程序描述如何在變更資料來源之後編輯對應。</span><span class="sxs-lookup"><span data-stu-id="96ebb-121">This procedure describes how to edit the mappings after you change a data source.</span></span>  
  
#### <a name="to-edit-column-mappings-when-a-data-source-changes"></a><span data-ttu-id="96ebb-122">在資料來源變更時編輯資料行對應</span><span class="sxs-lookup"><span data-stu-id="96ebb-122">To edit column mappings when a data source changes</span></span>  
  
1.  <span data-ttu-id="96ebb-123">在模型設計師中，選取一個資料表。</span><span class="sxs-lookup"><span data-stu-id="96ebb-123">In the model designer, select a table.</span></span>  
  
2.  <span data-ttu-id="96ebb-124">按一下 **[資料表]** 功能表，然後再按一下 **[資料表屬性]**。</span><span class="sxs-lookup"><span data-stu-id="96ebb-124">Click on the **Table** menu, and then click **Table Properties**.</span></span>  
  
     <span data-ttu-id="96ebb-125">所選資料表的名稱會顯示在 **[資料表名稱]** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="96ebb-125">The name of the selected table is displayed in the **Table Name** box.</span></span> <span data-ttu-id="96ebb-126">**[來源名稱]** 方塊會包含此資料表在外部資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="96ebb-126">The **Source Name** box contains the name of the table in the external data source.</span></span> <span data-ttu-id="96ebb-127">如果資料行在來源和模型中的名稱不同，您可以在兩組資料行名稱之間切換，其方式是選取 **[來源]** 或 **[模型]** 選項。</span><span class="sxs-lookup"><span data-stu-id="96ebb-127">If columns are named differently in the source and in the model, you can toggle between the two sets of column names by selecting the options **Source** or **Model**.</span></span>  
  
3.  <span data-ttu-id="96ebb-128">若要變更當做資料來源使用的資料表，請針對 **[來源名稱]** 選取與目前資料表不同的資料表。</span><span class="sxs-lookup"><span data-stu-id="96ebb-128">To change the table that is used as a data source, for **Source Name**, select a different table than the current one.</span></span>  
  
4.  <span data-ttu-id="96ebb-129">視需要變更資料行對應：</span><span class="sxs-lookup"><span data-stu-id="96ebb-129">Change column mappings if needed:</span></span>  
  
    1.  <span data-ttu-id="96ebb-130">若要加入在來源中但是不在模型中的資料行，請選取資料行名稱旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="96ebb-130">To add columns that are present in the source but not in the model, select the checkbox beside the column name.</span></span>  
  
         <span data-ttu-id="96ebb-131">下一次當您重新整理時，實際的資料將會載入模型。</span><span class="sxs-lookup"><span data-stu-id="96ebb-131">The actual data will be loaded into the model the next time you refresh.</span></span>  
  
    2.  <span data-ttu-id="96ebb-132">如果目前的資料來源不再提供模型中的某些資料行，通知區域會出現一則訊息，列出無效的資料行。</span><span class="sxs-lookup"><span data-stu-id="96ebb-132">If some columns in the model are no longer available in the current data source, a message appears in the notification area that lists the invalid columns.</span></span> <span data-ttu-id="96ebb-133">您不需要進行其他任何處理。</span><span class="sxs-lookup"><span data-stu-id="96ebb-133">You do not need to do anything else.</span></span>  
  
5.  <span data-ttu-id="96ebb-134">按一下 **[儲存]** ，將變更套用到模型。</span><span class="sxs-lookup"><span data-stu-id="96ebb-134">Click **Save** to apply the changes to your model.</span></span>  
  
     <span data-ttu-id="96ebb-135">當您儲存目前的資料表屬性集時，可能會出現一則訊息，指出您需要處理資料表。</span><span class="sxs-lookup"><span data-stu-id="96ebb-135">When you save the current set of table properties, a message may appear indicating that you need to process the tables.</span></span> <span data-ttu-id="96ebb-136">按一下 **[處理]** ，將更新的資料載入模型中。</span><span class="sxs-lookup"><span data-stu-id="96ebb-136">Click **Process** to load updated data into your model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ebb-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96ebb-137">See Also</span></span>  
 <span data-ttu-id="96ebb-138">[&#40;SSAS 表格式&#41;處理資料](process-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="96ebb-138">[Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="96ebb-139">支援的資料來源 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="96ebb-139">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
