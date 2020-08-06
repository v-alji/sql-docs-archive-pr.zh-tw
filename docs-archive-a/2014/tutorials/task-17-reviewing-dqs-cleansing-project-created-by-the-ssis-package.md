---
title: 工作17：查看 SSIS 封裝所建立的 DQS 清理專案 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0876a0b727e810f8834fcf5445958bf9884a87f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686550"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a><span data-ttu-id="fbb72-102">工作 17：檢閱 SSIS 封裝所建立的 DQS 清理專案</span><span class="sxs-lookup"><span data-stu-id="fbb72-102">Task 17: Reviewing DQS Cleansing Project Created by the SSIS package</span></span>
  <span data-ttu-id="fbb72-103">在這項工作中，您會開啟 DQS 用戶端中的 SSIS 封裝所建立的 DQS 專案、檢閱清理程序的結果，並選擇性地執行互動式清理及匯出結果。</span><span class="sxs-lookup"><span data-stu-id="fbb72-103">In this task, you open the DQS project created by the SSIS package in DQS Client, review the results from the cleansing process, and optionally perform interactive cleansing and export the results.</span></span>  
  
1.  <span data-ttu-id="fbb72-104">啟動**Data Quality Client**。</span><span class="sxs-lookup"><span data-stu-id="fbb72-104">Launch **Data Quality Client**.</span></span>  
  
2.  <span data-ttu-id="fbb72-105">按一下 [系統**管理**] 窗格中的 [**活動監控**]。</span><span class="sxs-lookup"><span data-stu-id="fbb72-105">Click **Activity Monitoring** in the **Administration** pane.</span></span>  
  
3.  <span data-ttu-id="fbb72-106">依據 [**活動開始時間**] 排序清單，以查看最新的記錄。</span><span class="sxs-lookup"><span data-stu-id="fbb72-106">Sort the list based on **Activity Start Time** to see the latest record.</span></span>  
  
4.  <span data-ttu-id="fbb72-107">請注意，您會看到專案的名稱，格式如下： **cleanseandcurate.cleanse supplier data.guid。清理供應商資料. GUID**。</span><span class="sxs-lookup"><span data-stu-id="fbb72-107">Notice that you see a name of the project in the following format: **CleanseAndCurate.Cleanse Supplier Data.GUID**.</span></span>  
  
     <span data-ttu-id="fbb72-108">![SSIS 封裝建立的 DQS 清理專案](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "SSIS 封裝建立的 DQS 清理專案")</span><span class="sxs-lookup"><span data-stu-id="fbb72-108">![DQS Cleansing Project Created by SSIS Package](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "DQS Cleansing Project Created by SSIS Package")</span></span>  
  
5.  <span data-ttu-id="fbb72-109">請注意，[ **Is active** ] 欄位中的值為 [**作用中]。**</span><span class="sxs-lookup"><span data-stu-id="fbb72-109">Notice that the value in the **Is Active** field is **Active**.</span></span>  
  
6.  <span data-ttu-id="fbb72-110">按一下**底部**窗格中的 [分析工具] 索引標籤，以查看 SSIS 封裝執行之清理活動的 Profiler 統計資料。</span><span class="sxs-lookup"><span data-stu-id="fbb72-110">Click **Profiler** tab in the bottom pane to see profiler statistics for the Cleansing activity that the SSIS package performed.</span></span>  
  
7.  <span data-ttu-id="fbb72-111">按一下 [**關閉**] 以關閉 [**管理**] 畫面。</span><span class="sxs-lookup"><span data-stu-id="fbb72-111">Click **Close** to close the **Administration** screen.</span></span>  
  
8.  <span data-ttu-id="fbb72-112">在**DQS 用戶端**的主頁面中，按一下 [**資料品質**專案] 窗格中的 [**開啟資料品質專案**]。</span><span class="sxs-lookup"><span data-stu-id="fbb72-112">In the main page of **DQS Client**, click **Open Data Quality Project** in the **Data Quality Projects** pane.</span></span>  
  
9. <span data-ttu-id="fbb72-113">在專案清單中，選取 SSIS DQS 清理元件所建立的專案。</span><span class="sxs-lookup"><span data-stu-id="fbb72-113">In the list of projects, select the project created by SSIS DQS Cleansing component.</span></span> <span data-ttu-id="fbb72-114">專案的名稱應為格式： \*\*cleanseandcurate.cleanse supplier data.guid。清理供應商資料。 GUID (為紅色色彩) \*\*。</span><span class="sxs-lookup"><span data-stu-id="fbb72-114">The name of the project should be in format:  **CleanseAndCurate.Cleanse Supplier Data.GUID (in red color)**.</span></span> <span data-ttu-id="fbb72-115">您可能需要根據 [**建立日期] 資料**行來排序清單，並尋找最新的記錄。</span><span class="sxs-lookup"><span data-stu-id="fbb72-115">You may need to sort the list based on **Date Created** column and look for the latest record.</span></span>  
  
10. <span data-ttu-id="fbb72-116">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="fbb72-116">Click **Next**.</span></span>  
  
11. <span data-ttu-id="fbb72-117">從您稍早在本教學課程中進行的互動式清理，您應該不熟悉 [**管理] 和 [查看結果**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="fbb72-117">The **Manage and View Results** page should be familiar to you from the interactive cleansing you did earlier in this tutorial.</span></span>  
  
12. <span data-ttu-id="fbb72-118">檢閱清理結果。</span><span class="sxs-lookup"><span data-stu-id="fbb72-118">Review the cleansing results.</span></span> <span data-ttu-id="fbb72-119">您也可以執行互動式清理，並在下一頁將結果匯出到 Excel 檔案或資料庫。</span><span class="sxs-lookup"><span data-stu-id="fbb72-119">You can also perform interactive cleansing and export results to an Excel file or to a database in the next page.</span></span>  
  
13. <span data-ttu-id="fbb72-120">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="fbb72-120">Click **Next**.</span></span> <span data-ttu-id="fbb72-121">在此**匯出**頁面中，您可以將結果匯出至 excel 檔案、CSV 檔案或 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fbb72-121">In this **Export** page, you can export results to an excel file, CSV file, or to a SQL database.</span></span>  
  
14. <span data-ttu-id="fbb72-122">按一下 **[完成]** 以完成活動。</span><span class="sxs-lookup"><span data-stu-id="fbb72-122">Click **Finish** to finish the activity.</span></span>  
  
15. <span data-ttu-id="fbb72-123">在**DQS 用戶端**的主頁面中，按一下 [系統**管理**] 窗格中的 [**活動監控**]。</span><span class="sxs-lookup"><span data-stu-id="fbb72-123">In the main page of **DQS Client**, click **Activity Monitoring** in the **Administration** pane.</span></span>  
  
16. <span data-ttu-id="fbb72-124">請注意，專案的 [ **IsActive** ] 欄位的值現在已**結束**。</span><span class="sxs-lookup"><span data-stu-id="fbb72-124">Notice that the value of **IsActive** field for the project is **Ended** now.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="fbb72-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="fbb72-125">Next Step</span></span>  
 [<span data-ttu-id="fbb72-126">結論</span><span class="sxs-lookup"><span data-stu-id="fbb72-126">Conclusion</span></span>](../../2014/tutorials/conclusion.md)  
  
  
