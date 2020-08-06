---
title: 解決 Excel 資料列限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a4c8700b-bef5-4440-a99c-bba5dcc46bfd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 128f65cf09833d23234da10bf7744c6ce30065ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593314"
---
# <a name="work-around-the-excel-row-limitation"></a><span data-ttu-id="406e2-102">解決 Excel 資料列限制</span><span class="sxs-lookup"><span data-stu-id="406e2-102">Work Around the Excel Row Limitation</span></span>
  <span data-ttu-id="406e2-103">本主題說明如何在您將報表匯出至 Excel 時解決 Excel 2003 的資料列限制。</span><span class="sxs-lookup"><span data-stu-id="406e2-103">This topic explains how to work around the Excel 2003 row limitation when you export reports to Excel.</span></span> <span data-ttu-id="406e2-104">此因應措施適用於只包含資料表的報表。</span><span class="sxs-lookup"><span data-stu-id="406e2-104">The workaround is for a report that contains only a table.</span></span>  
  
 <span data-ttu-id="406e2-105">Excel 2003 在每張工作表中所支援的資料列上限為 65,536 列。</span><span class="sxs-lookup"><span data-stu-id="406e2-105">Excel 2003 supports a maximum of 65,536 rows per worksheet.</span></span> <span data-ttu-id="406e2-106">您可以在特定資料列數目之後強制使用明確分頁符號來避開這個限制。</span><span class="sxs-lookup"><span data-stu-id="406e2-106">You can work around this limitation by forcing an explicit page break after a certain number of rows.</span></span> <span data-ttu-id="406e2-107">Excel 轉譯器會針對每一個明確分頁符號建立新的工作表。</span><span class="sxs-lookup"><span data-stu-id="406e2-107">The Excel renderer creates a new worksheet for each explicit page break.</span></span>  
  
### <a name="to-create-an-explicit-page-break"></a><span data-ttu-id="406e2-108">若要建立明確分頁符號</span><span class="sxs-lookup"><span data-stu-id="406e2-108">To create an explicit page break</span></span>  
  
1.  <span data-ttu-id="406e2-109">在 [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] 或報表管理員中開啟報表。</span><span class="sxs-lookup"><span data-stu-id="406e2-109">Open the report in [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] or Report Manager.</span></span>  
  
2.  <span data-ttu-id="406e2-110">以滑鼠右鍵按一下資料表中的資料列，然後按一下 [**加入群組**] [  >  **父群組**] 來加入外部資料表群組。</span><span class="sxs-lookup"><span data-stu-id="406e2-110">Right click the Data row in the table, and then click **Add Group** > **Parent Group** to add an outer table group.</span></span>  
  
     <span data-ttu-id="406e2-111">![選取父群組](../media/datarow-selectparentgroup.png "選取父群組")</span><span class="sxs-lookup"><span data-stu-id="406e2-111">![Select the Parent Group](../media/datarow-selectparentgroup.png "Select the Parent Group")</span></span>  
  
3.  <span data-ttu-id="406e2-112">在 [群組依據]\*\*\*\* 運算式方塊中輸入下列公式，然後按一下 [確定]\*\*\*\* 來加入父群組。</span><span class="sxs-lookup"><span data-stu-id="406e2-112">Enter the following formula in the **Group by** expression box, and then click **OK** to add the parent group.</span></span>  
  
     <span data-ttu-id="406e2-113">=Int((RowNumber(Nothing)-1)/65000)</span><span class="sxs-lookup"><span data-stu-id="406e2-113">=Int((RowNumber(Nothing)-1)/65000)</span></span>  
  
     <span data-ttu-id="406e2-114">此公式會針對資料集中的每一組 65000 個資料列指派一個數字。</span><span class="sxs-lookup"><span data-stu-id="406e2-114">The formula assigns a number to each set of 65000 rows in the dataset.</span></span> <span data-ttu-id="406e2-115">為群組定義分頁符號時，這個運算式每隔 65000 個資料列就會產生一個分頁符號。</span><span class="sxs-lookup"><span data-stu-id="406e2-115">When a page break is defined for the group, the expression results in a page break every 65000 rows.</span></span>  
  
     <span data-ttu-id="406e2-116">加入外部資料表群組會將群組資料行加入至報表中。</span><span class="sxs-lookup"><span data-stu-id="406e2-116">Adding the outer table group adds a group column to the report.</span></span>  
  
4.  <span data-ttu-id="406e2-117">以滑鼠右鍵按一下群組資料行標頭來刪除群組資料行，再按一下 [刪除資料行]\*\*\*\*，並選取 [只刪除資料行]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="406e2-117">Delete the group column by right-clicking on the column header, clicking **Delete Columns**, selecting **Delete columns only**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="406e2-118">![刪除群組資料行](../media/groupcolumn-delete-updated.png "刪除群組資料行")</span><span class="sxs-lookup"><span data-stu-id="406e2-118">![Delete a group column](../media/groupcolumn-delete-updated.png "Delete a group column")</span></span>  
  
5.  <span data-ttu-id="406e2-119">以滑鼠右鍵按一下 [資料列群組]\*\*\*\* 區段中的 [群組 1]\*\*\*\*，然後按一下 [群組屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="406e2-119">Right click **Group 1** in the **Row Groups** section, and then click **Group Properties**.</span></span>  
  
     <span data-ttu-id="406e2-120">![檢視群組屬性](../media/groupproperties-updated.png "檢視群組屬性")</span><span class="sxs-lookup"><span data-stu-id="406e2-120">![View group properties](../media/groupproperties-updated.png "View group properties")</span></span>  
  
6.  <span data-ttu-id="406e2-121">在 [群組屬性]\*\*\*\* 對話方塊的 [排序]\*\*\*\* 頁面上，選取預設排序選項，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="406e2-121">On the **Sorting** page of the **Group Properties** dialog box, select the default sorting option and click **Delete**.</span></span>  
  
     <span data-ttu-id="406e2-122">![刪除預設排序](../media/groupproperties-sorting-updated.png "刪除預設排序")</span><span class="sxs-lookup"><span data-stu-id="406e2-122">![Delete default sorting](../media/groupproperties-sorting-updated.png "Delete default sorting")</span></span>  
  
7.  <span data-ttu-id="406e2-123">在 [分頁符號]\*\*\*\* 頁面上，按一下 [在群組的每個執行個體之間]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="406e2-123">On the **Page Breaks** page, click **Between each instance of a group** and then click **OK**.</span></span>  
  
     <span data-ttu-id="406e2-124">![設定分頁符號](../media/groupproperties-pagebreaks-updated.png "設定分頁符號")</span><span class="sxs-lookup"><span data-stu-id="406e2-124">![Set page breaks](../media/groupproperties-pagebreaks-updated.png "Set page breaks")</span></span>  
  
8.  <span data-ttu-id="406e2-125">儲存報表。</span><span class="sxs-lookup"><span data-stu-id="406e2-125">Save the report.</span></span> <span data-ttu-id="406e2-126">當您將它匯出至 Excel 時，它會匯出到多個工作表，而且每個工作表最多包含 65000 個資料列。</span><span class="sxs-lookup"><span data-stu-id="406e2-126">When you export it to Excel, it exports to multiple worksheets and each worksheet contains a maximum of 65000 rows.</span></span>  
  
  
