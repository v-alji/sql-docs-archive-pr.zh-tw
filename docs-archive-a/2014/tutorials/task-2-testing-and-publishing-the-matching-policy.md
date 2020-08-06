---
title: 工作2：測試和發行比對原則 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: e1ffb6d7-fbc5-4695-b538-cc2302d1a17d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 88bed2e91ca1fee3eab6136fb94df0d13328dc80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598699"
---
# <a name="task-2-testing-and-publishing-the-matching-policy"></a><span data-ttu-id="fc4cf-102">工作 2：測試和發行比對原則</span><span class="sxs-lookup"><span data-stu-id="fc4cf-102">Task 2: Testing and Publishing the Matching Policy</span></span>
  <span data-ttu-id="fc4cf-103">在這項工作中，您會測試併發布**移除重複的供應商**比對原則。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-103">In this task, you test and publish the **Remove Duplicate Suppliers** matching policy.</span></span>  
  
1.  <span data-ttu-id="fc4cf-104">在 [比對**結果**] 頁面中，按一下 [**開始**] 測試整個原則。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-104">In the **Matching Results** page, click **Start** to test the entire policy.</span></span> <span data-ttu-id="fc4cf-105">在您的案例中，此原則只有一個規則，所以測試規則和原則的結果應該相同。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-105">In your case, you have only rule in the policy, so the results from testing the rule and the policy should be the same.</span></span>  
  
2.  <span data-ttu-id="fc4cf-106">請在清單方塊中檢閱所有相符記錄及其比對分數。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-106">Review all the matched records and their matching score in the list box.</span></span> <span data-ttu-id="fc4cf-107">具有相關聯**綠色**圖示的記錄，是其前面的樞紐分析表記錄的重複項。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-107">A record that has a **Green** icon associated with it is a duplicate of the pivot record that precedes it.</span></span> <span data-ttu-id="fc4cf-108">以下是幾個範例：</span><span class="sxs-lookup"><span data-stu-id="fc4cf-108">Here are couple of examples:</span></span>  
  
    1.  <span data-ttu-id="fc4cf-109">**記錄識別碼為 1000005**的記錄與記錄**識別碼： 1000004** （具有**分數： 100%** ）的記錄相符，因為這兩筆記錄都有相同的\*\* (必要條件) **、**供應商名稱**和 ContactEmailAddress 資料**行\*\*的值。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-109">The record with **Record ID: 1000005** is a match of the record with **Record Id: 1000004** with **Score: 100%** because both the records have the same values for **SupplierID (prerequisite)**, **Supplier Name**, and **ContactEmailAddress columns**.</span></span> <span data-ttu-id="fc4cf-110">DQS 會隨機挑選記錄當做叢集的樞紐記錄。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-110">DQS randomly picks a record as the pivot record for a cluster.</span></span>  
  
    2.  <span data-ttu-id="fc4cf-111">記錄**1000023**符合符合分數的記錄**1000022** ：93%，因為這兩筆記錄的\*\* (必要條件) **和**供應商名稱**資料行的相同值，但**ContactEmailAddress\*\*資料行的值不同。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-111">The record **1000023** is a match of the record **1000022** with the matching score: 93% because the two records have the same values for **SupplierID (prerequisite)** and **Supplier Name** columns, but different values for the **ContactEmailAddress** column.</span></span>  
  
    3.  <span data-ttu-id="fc4cf-112">請滾動到清單底部，以查看具有記錄識別碼的兩筆記錄： **1000051**和**1000052**。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-112">Scroll to the bottom of the list to see two records with records IDs: **1000051** and **1000052**.</span></span> <span data-ttu-id="fc4cf-113">記錄**1000052**會視為符合分數**91%** 的相符項，因為這兩筆記錄的 [供貨**商**] 和 [ **ContactEmailAddress** ] 資料行具有相同的值，但 [**供應商名稱**] 資料行的值不同。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-113">Record **1000052** is considered a match with matching score **91%** because the two records have the same values for the **SupplierID** and **ContactEmailAddress** columns, but different values for the **Supplier Name** column.</span></span>  
  
     <span data-ttu-id="fc4cf-114">![原則定義 - 原則結果](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-01.jpg "原則定義 - 原則結果")</span><span class="sxs-lookup"><span data-stu-id="fc4cf-114">![Policy Definition - Policy Results](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-01.jpg "Policy Definition - Policy Results")</span></span>  
  
3.  <span data-ttu-id="fc4cf-115">以滑鼠右鍵按一下任何相符的記錄 (綠色圖示) 然後按一下 [**查看詳細資料**]，以查看比對的詳細資料，例如每個欄位分數占整體符合分數的比重。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-115">Right-click on any matched record (with green icon) and click **View Details** to see more details about the matching such as contribution of each field score to the overall matching score.</span></span>  
  
     <span data-ttu-id="fc4cf-116">![[符合分數詳細資料] 對話方塊](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-02.jpg "[符合分數詳細資料] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="fc4cf-116">![Matching Score Details Dialog Box](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-02.jpg "Matching Score Details Dialog Box")</span></span>  
  
4.  <span data-ttu-id="fc4cf-117">按一下 [**關閉**] 以關閉 [**符合分數詳細資料**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-117">Click **Close** to close the **Matching Score Details** dialog box.</span></span>  
  
5.  <span data-ttu-id="fc4cf-118">按一下頁面底部的 [比對**結果**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-118">Click **Matching Results** tab at the bottom of the page.</span></span> <span data-ttu-id="fc4cf-119">此索引標籤會提供詳細資料，例如相符記錄的數目、不相符記錄的數目、具有相符記錄的叢集數目、平均叢集大小、最小叢集大小和最大叢集大小。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-119">This tab gives you detail such as number of matched records, number of unmatched records, number of clusters with matched records, the average cluster size, minimum cluster size, and maximum cluster size.</span></span> <span data-ttu-id="fc4cf-120">如需詳細資訊，請參閱建立比對[原則](https://msdn.microsoft.com/library/hh270290.aspx)。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-120">See [Create a Matching Policy](https://msdn.microsoft.com/library/hh270290.aspx) for more details.</span></span> <span data-ttu-id="fc4cf-121">您無法從這個活動匯出結果。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-121">You cannot export results from this activity.</span></span> <span data-ttu-id="fc4cf-122">您只會定義比對原則，方式是使用取樣資料來針對取樣資料測試規則和原則。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-122">You are just defining a matching policy by using the sample data to test rules and the policy against the sample data.</span></span>  
  
     <span data-ttu-id="fc4cf-123">![比對結果索引標籤](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-03.jpg "比對結果索引標籤")</span><span class="sxs-lookup"><span data-stu-id="fc4cf-123">![Matching Results Tab](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-03.jpg "Matching Results Tab")</span></span>  
  
6.  <span data-ttu-id="fc4cf-124">按一下 **[完成]** 完成比對原則的建立。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-124">Click **Finish** to finish creating the matching policy.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc4cf-125">您已經在這裡定義比對原則，因此無法將結果匯出到輸出檔。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-125">You have defined the matching policy here; therefore you cannot export results to an output file.</span></span> <span data-ttu-id="fc4cf-126">您基本上已經使用範例輸入檔、建立規則，並針對取樣資料測試規則和原則 (目標是要定義原則)。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-126">You basically used a sample input file, created rules, and tested the rules and policy against the sample data with the goal of defining the policy.</span></span>  
  
7.  <span data-ttu-id="fc4cf-127">在 [SQL Server Data Quality Services] 對話方塊中，按一下 [**發佈**]，然後按一下訊息方塊上的 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-127">In the SQL Server Data Quality Services dialog box, click **Publish** and click **OK** on the message box.</span></span> <span data-ttu-id="fc4cf-128">現在，您所定義的比對原則會發佈到**供應商**知識庫。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-128">Now, the matching policy you defined is published into the **Suppliers** Knowledge Base.</span></span> <span data-ttu-id="fc4cf-129">您可以使用此知識庫，針對輸入檔執行比對程序，以識別並移除重複項。</span><span class="sxs-lookup"><span data-stu-id="fc4cf-129">You can use the knowledge base to run the matching process against an input file to identify and remove duplicates.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="fc4cf-130">後續步驟</span><span class="sxs-lookup"><span data-stu-id="fc4cf-130">Next Step</span></span>  
 [<span data-ttu-id="fc4cf-131">工作 3：建立及執行資料品質專案以進行比對</span><span class="sxs-lookup"><span data-stu-id="fc4cf-131">Task 3: Creating and Running a Data Quality Project for Matching</span></span>](../../2014/tutorials/task-3-creating-and-running-a-data-quality-project-for-matching.md)  
  
  
