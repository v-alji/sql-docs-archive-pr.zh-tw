---
title: 工作3：建立及執行資料品質專案以進行比對 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6260e911-ea8b-4c69-a39d-d1bccd565a32
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 221d6d583c61ee035c20fcb63f0ed5278f2b8678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592394"
---
# <a name="task-3-creating-and-running-a-data-quality-project-for-matching"></a><span data-ttu-id="bcb0a-102">工作 3：建立及執行資料品質專案以進行比對</span><span class="sxs-lookup"><span data-stu-id="bcb0a-102">Task 3: Creating and Running a Data Quality Project for Matching</span></span>
  <span data-ttu-id="bcb0a-103">在這項工作中，您會針對比對活動建立資料品質專案，並針對已清理的供應商資料執行比對程序，以移除資料中的任何重複項。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-103">In this task, you create a Data Quality Project for the matching activity and run the matching process on cleansed supplier data to remove any duplicates in the data.</span></span>

1.  <span data-ttu-id="bcb0a-104">在**DQS 用戶端**的主頁面上，按一下 [**新增資料品質專案**]。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-104">On the main page of **DQS Client**, click **New Data Quality Project**.</span></span>

2.  <span data-ttu-id="bcb0a-105">輸入從**專案名稱**中**移除供應商重複**。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-105">Type **Remove Supplier Duplicates** from the **Name of the project**.</span></span>

3.  <span data-ttu-id="bcb0a-106">從 [**使用知識庫**] 欄位的 kb 清單中選取 [**供應商**]。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-106">Select **Suppliers** from the list of KBs for the **Use Knowledge Base** field.</span></span> <span data-ttu-id="bcb0a-107">在上一課，您已經在此知識庫中建立比對原則。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-107">You have created a matching policy in this knowledge base in the previous lesson.</span></span>

4.  <span data-ttu-id="bcb0a-108">從右下方的 [**活動] 清單**中選取 [比對]。 **Matching**</span><span class="sxs-lookup"><span data-stu-id="bcb0a-108">Select **Matching** from the **list of activities** from the bottom-right pane.</span></span>

     <span data-ttu-id="bcb0a-109">![新增資料品質專案 - 已選取 [比對]](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "新增資料品質專案 - 已選取 [比對]")</span><span class="sxs-lookup"><span data-stu-id="bcb0a-109">![New Data Quality Project - Matching Selected](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "New Data Quality Project - Matching Selected")</span></span>

5.  <span data-ttu-id="bcb0a-110">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-110">Click **Next**.</span></span>

6.  <span data-ttu-id="bcb0a-111">在 [對應] \*\*\*\* 頁面上，針對 [資料來源] \*\*\*\* 選取 [Excel 檔案] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-111">In the **Map** page, select **Excel File** for **Data Source**.</span></span>

7.  <span data-ttu-id="bcb0a-112">按一下 **[流覽]** 並選取 [**清理供應商 List.xls**]，這是 [清理] 活動中的輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-112">Click **Browse** and select **Cleansed Supplier List.xls**, which is the output file from the cleansing activity.</span></span>

8.  <span data-ttu-id="bcb0a-113">將 [供應商**識別碼**] 欄位、[**供應商名稱**] 資料**行對應至**供應商**名稱**網域，並將 [ **ContactEmailAddress** ] 資料行對應至 [**連絡人電子郵件**網域]</span><span class="sxs-lookup"><span data-stu-id="bcb0a-113">Map **SupplierID** source column to the **Supplier ID** domain, **Supplier Name** column to **Supplier Name** domain, and **ContactEmailAddress** column to **Contact Email** domain.</span></span>

9. <span data-ttu-id="bcb0a-114">按 **[下一步]** 切換至 [**對應**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-114">Click **Next** to switch to the **Matching** page.</span></span>

10. <span data-ttu-id="bcb0a-115">按一下 [**啟動**] 開始比對程式。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-115">Click **Start** to start the matching process.</span></span> <span data-ttu-id="bcb0a-116">您應該會看到與上一個工作類似的結果，因為您使用了相同的輸入檔來定義比對原則。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-116">You should see results similar to those from the previous task because you used the same input file for defining the matching policy.</span></span>

11. <span data-ttu-id="bcb0a-117">請在清單方塊中檢閱所有相符記錄及其比對分數。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-117">Review all the matched records and their matching score in the list box.</span></span> <span data-ttu-id="bcb0a-118">結果應該與您在上一個工作看到的結果相同。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-118">The results should be same as the ones you saw in the previous task.</span></span> <span data-ttu-id="bcb0a-119">請參閱上一個工作的步驟，以分析這個比對活動的結果。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-119">See the steps in the previous task to analyze the results from this matching activity.</span></span>

12. <span data-ttu-id="bcb0a-120">按 **[下一步]** 切換至 [**匯出**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="bcb0a-120">Click **Next** to switch to the **Export** page.</span></span>

## <a name="next-step"></a><span data-ttu-id="bcb0a-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="bcb0a-121">Next Step</span></span>
 [<span data-ttu-id="bcb0a-122">工作 4：將比對活動的結果匯出到 Excel 檔案</span><span class="sxs-lookup"><span data-stu-id="bcb0a-122">Task 4: Exporting the Results from Matching Activity to an Excel File</span></span>](../../2014/tutorials/task-4-exporting-the-results-from-matching-activity-to-an-excel-file.md)


