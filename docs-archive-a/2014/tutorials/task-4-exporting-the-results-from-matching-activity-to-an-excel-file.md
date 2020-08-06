---
title: 工作4：將比對活動的結果匯出至 Excel 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 644454c4-3c5a-469a-90ec-e51dc7fb99fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b583e44f887fc0595fb904ec977f1de28c2fecd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704418"
---
# <a name="task-4-exporting-the-results-from-matching-activity-to-an-excel-file"></a><span data-ttu-id="7e4ff-102">工作 4：將比對活動的結果匯出到 Excel 檔案</span><span class="sxs-lookup"><span data-stu-id="7e4ff-102">Task 4: Exporting the Results from Matching Activity to an Excel File</span></span>
  <span data-ttu-id="7e4ff-103">在這項工作中，您會將比對活動的結果匯出到 Excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-103">In this task, you export the results from the matching activity to an Excel file.</span></span>

1.  <span data-ttu-id="7e4ff-104">在 [**匯出**] 頁面中，針對 [**目的地類型**] 選取 [ **Excel**檔案]。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-104">In the **Export** page, select **Excel File** for the **Destination Type**.</span></span>

2.  <span data-ttu-id="7e4ff-105">選取 [**生存結果**] 選項。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-105">Select **Survivorship Results** option.</span></span> <span data-ttu-id="7e4ff-106">在生存程式中，DQS 會根據您選取的**生存規則**，決定每個叢集的生存者記錄。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-106">In the survivorship process, DQS determines a survivor record for each cluster based on the **Survivorship Rule** you selected.</span></span>

3.  <span data-ttu-id="7e4ff-107">按一下 **[流覽]** ，並流覽至您要儲存輸出檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-107">Click **Browse** and navigate to the folder where you want to store the output file.</span></span>

4.  <span data-ttu-id="7e4ff-108">針對名稱輸入**清理和相符的 Suppliers.xls** ，然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-108">Type **Cleansed and Matched Suppliers.xls** for the name and click **Open**.</span></span>

5.  <span data-ttu-id="7e4ff-109">確認已選取 [**生存] 規則**的 [**樞紐分析表記錄**]。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-109">Confirm that **Pivot Record** is selected for the **Survivorship Rule**.</span></span> <span data-ttu-id="7e4ff-110">當您選取此選項時，便會針對叢集的輸出挑選每個叢集的樞紐記錄。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-110">When you select this option, the pivot record for each cluster is picked for the output from a cluster.</span></span> <span data-ttu-id="7e4ff-111">存活規則的其他選項包括：</span><span class="sxs-lookup"><span data-stu-id="7e4ff-111">The other options for the Survivorship Rule are:</span></span>

    1.  <span data-ttu-id="7e4ff-112">**最完整的記錄：** 生存者記錄是已填入最多欄位的記錄。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-112">**Most complete record:** Survivor record is the one with the largest number of populated fields.</span></span>

    2.  <span data-ttu-id="7e4ff-113">**最長的記錄：** 生存者記錄是來源欄位中具有最大詞彙數目的記錄。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-113">**Longest record:** Survivor record is the one with the largest number of terms in source fields.</span></span>

    3.  <span data-ttu-id="7e4ff-114">**最完整且最長的記錄：** 生存者記錄是已填入最多欄位數目，而且每個欄位中的詞彙數目最大值。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-114">**Most complete and longest record:** Survivor record is the one with the largest number of populated fields, and has the largest number of terms in each field.</span></span>

     <span data-ttu-id="7e4ff-115">![[匯出比對結果] 頁面](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "[匯出比對結果] 頁面")</span><span class="sxs-lookup"><span data-stu-id="7e4ff-115">![Export Results from Matching Page](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "Export Results from Matching Page")</span></span>

6.  <span data-ttu-id="7e4ff-116">按一下 [**匯出**]，將結果匯出至 Excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-116">Click **Export** to export the results to an Excel file.</span></span>

7.  <span data-ttu-id="7e4ff-117">按一下 [**關閉**] 以關閉 [比對**匯出**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-117">Click **Close** to close the **Matching Export** dialog box.</span></span>

8.  <span data-ttu-id="7e4ff-118">按一下 **[完成]** 完成比對活動。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-118">Click **Finish** to finish the matching activity.</span></span>

9. <span data-ttu-id="7e4ff-119">開啟**清理並**比對 Suppliers.xlsx檔案，並確認您沒有看到任何重複專案 (已) 的任何複本。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-119">Open the **Cleansed and Matched Suppliers.xlsx** file and confirm that you do not see any duplicates (SupplierID).</span></span>

 <span data-ttu-id="7e4ff-120">現在，您的供應商資料已經清理和比對，以移除重複項。</span><span class="sxs-lookup"><span data-stu-id="7e4ff-120">Now, you have supplier data that has been cleansed and matched to remove duplicates.</span></span>

## <a name="next-step"></a><span data-ttu-id="7e4ff-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7e4ff-121">Next Step</span></span>
 [<span data-ttu-id="7e4ff-122">第 4 課：在 MDS 中儲存供應商資料</span><span class="sxs-lookup"><span data-stu-id="7e4ff-122">Lesson 4: Storing Supplier Data in MDS</span></span>](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)


