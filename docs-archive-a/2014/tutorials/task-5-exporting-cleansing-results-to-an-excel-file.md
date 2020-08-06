---
title: 工作5：將清理結果匯出至 Excel 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0dbdc1bef348e03e211e4933132985ea2c089b97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598697"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a><span data-ttu-id="6cd10-102">工作 5：將清理結果匯出到 Excel 檔案</span><span class="sxs-lookup"><span data-stu-id="6cd10-102">Task 5: Exporting Cleansing Results to an Excel File</span></span>
  <span data-ttu-id="6cd10-103">在這項工作中，您會將清理活動的結果匯出到 Excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="6cd10-103">In this task, you export results from the cleansing activity to an Excel file.</span></span> <span data-ttu-id="6cd10-104">如需詳細資訊，請參閱[匯出階段](https://msdn.microsoft.com/library/hh213061.aspx#Export)主題。</span><span class="sxs-lookup"><span data-stu-id="6cd10-104">See [Export Stage](https://msdn.microsoft.com/library/hh213061.aspx#Export) topic for more details.</span></span>  
  
1.  <span data-ttu-id="6cd10-105">在右窗格中，選取 [ **Excel** ] 作為 [**目的地類型**]。</span><span class="sxs-lookup"><span data-stu-id="6cd10-105">In the right pane, select **Excel** for the **Destination Type**.</span></span>  
  
2.  <span data-ttu-id="6cd10-106">按一下 **[流覽]**，將輸出檔案名指定為**清理供應商 List.xls**，然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="6cd10-106">Click **Browse**, specify the output file name as **Cleansed Supplier List.xls**, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="6cd10-107">僅針對**輸出**格式選取 [**資料**]，只匯出清理的資料。</span><span class="sxs-lookup"><span data-stu-id="6cd10-107">Select **Data Only** for the **Output** format to export just the cleansed data.</span></span> <span data-ttu-id="6cd10-108">第二個選項 [**資料和清理資訊**] 可讓您連同清理資料一起匯出清理活動詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="6cd10-108">The second option, **Data and Cleansing Info**, lets you export cleansing activity details along with the cleansed data.</span></span> <span data-ttu-id="6cd10-109">[**標準化格式**] 選項可讓您將在網域上定義的任何輸出格式套用至該定義域的值。</span><span class="sxs-lookup"><span data-stu-id="6cd10-109">The **Standardize Format** option lets you apply any output formats you define on a domain to the values of that domain.</span></span> <span data-ttu-id="6cd10-110">在本教學課程中，您尚未在任何定義域定義輸出格式。</span><span class="sxs-lookup"><span data-stu-id="6cd10-110">You have not defined an output format on any domain in the tutorial.</span></span>  
  
     <span data-ttu-id="6cd10-111">![[匯出清理結果] 頁面](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "[匯出清理結果] 頁面")</span><span class="sxs-lookup"><span data-stu-id="6cd10-111">![Export Cleansing Results Page](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "Export Cleansing Results Page")</span></span>  
  
4.  <span data-ttu-id="6cd10-112">按一下 [**匯出**] 匯出資料。</span><span class="sxs-lookup"><span data-stu-id="6cd10-112">Click **Export** to export the data.</span></span> <span data-ttu-id="6cd10-113">請不要按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="6cd10-113">Do not click **Finish** yet.</span></span>  
  
5.  <span data-ttu-id="6cd10-114">在 [**正在匯出**] 對話方塊上，按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="6cd10-114">Click **Close** on the **Exporting** dialog box.</span></span>  
  
6.  <span data-ttu-id="6cd10-115">按一下 **[完成]** 以完成活動。</span><span class="sxs-lookup"><span data-stu-id="6cd10-115">Click **Finish** to finish the activity.</span></span> <span data-ttu-id="6cd10-116">如果您在按一下 **[完成]** 之前忘記匯出結果，請在**DQS 用戶端**的主頁面中，按一下 [**開啟資料品質專案**]，從專案清單中選取 [**清理供應商清單**]，然後按一下畫面底部的 **[下一步]** ，再次進入清理程式的 [**匯出**] 階段。</span><span class="sxs-lookup"><span data-stu-id="6cd10-116">If you forgot to export results before clicking **Finish**, click **Open Data Quality Project** in the main page of **DQS Client**, select **Cleanse Supplier List** from the list of projects, and click **Next** at the bottom of the screen to get to the **Export** stage of cleansing process again.</span></span> <span data-ttu-id="6cd10-117">您也可以按一下 [**上一步**] 按鈕，切換到 [**管理和查看結果**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6cd10-117">You can also switch to **Manage and View Results** tab by clicking **Back** button.</span></span>  
  
7.  <span data-ttu-id="6cd10-118">開啟**清理供應商 List.xls** ，然後執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6cd10-118">Open the **Cleansed Supplier List.xls** and do the following:</span></span>  
  
    1.  <span data-ttu-id="6cd10-119">藉由在工作表中搜尋 adventure-work.com，確保沒有以 adventure-work.com (結尾的電子郵件地址沒有字元的 ' ) 。</span><span class="sxs-lookup"><span data-stu-id="6cd10-119">Ensure that there are no email addresses that end with adventure-work.com (without character 's') by searching for adventure-work.com in the worksheet.</span></span>  
  
    2.  <span data-ttu-id="6cd10-120">查看 [**國家/地區**] 資料行中沒有任何**美國**值。</span><span class="sxs-lookup"><span data-stu-id="6cd10-120">See that there is no **USA** value in the **Country** column.</span></span>  
  
    3.  <span data-ttu-id="6cd10-121">搜尋洛杉磯 **，並查看\*\*\*\*狀態**設定為 [ **CA**]。</span><span class="sxs-lookup"><span data-stu-id="6cd10-121">Search for **Los Angeles** and see that the **State** is set to **CA**.</span></span>  
  
    4.  <span data-ttu-id="6cd10-122">確認沒有任何「 **Co**」、「 **Corp**」和「 **inc.**」的條款。</span><span class="sxs-lookup"><span data-stu-id="6cd10-122">Confirm that there are no terms **Co.**, **Corp.**, and **Inc.**.</span></span>  
  
    5.  <span data-ttu-id="6cd10-123">從試算表刪除 [**位址驗證**] 資料行，並儲存 excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="6cd10-123">Delete the **Address Validation** column from the spreadsheet and save the excel file.</span></span> <span data-ttu-id="6cd10-124">此額外資料行對應至「地址驗證」複合定義域。</span><span class="sxs-lookup"><span data-stu-id="6cd10-124">This additional column corresponds to the Address Validation composite domain.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="6cd10-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6cd10-125">Next Step</span></span>  
 [<span data-ttu-id="6cd10-126">工作 6：從清理供應商清單專案匯入值</span><span class="sxs-lookup"><span data-stu-id="6cd10-126">Task 6: Importing Values from the Cleanse Supplier List Project</span></span>](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  
