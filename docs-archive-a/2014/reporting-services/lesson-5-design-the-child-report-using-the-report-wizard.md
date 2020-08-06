---
title: 第 5 課：使用報表精靈設計子報表 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 19a3f927-ea97-4f40-a5f8-cd5f2598e4da
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f188a914fc2a2bb8370843191a31474a54c02aa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592515"
---
# <a name="lesson-5-design-the-child-report-using-the-report-wizard"></a><span data-ttu-id="dfa35-102">第 5 課：使用報表精靈設計子報表</span><span class="sxs-lookup"><span data-stu-id="dfa35-102">Lesson 5: Design the Child Report using the Report Wizard</span></span>
  <span data-ttu-id="dfa35-103">在您建立子報表的資料連接和資料表之後，下一步是要使用報表設計師中的 [報表精靈] 設計子報表。</span><span class="sxs-lookup"><span data-stu-id="dfa35-103">After you create a data connection and data table for the child report, your next step is to design the child report using the Report Wizard in Report Designer.</span></span> <span data-ttu-id="dfa35-104">如需報表設計師的詳細資訊，請參閱[使用報表設計師設計報表 &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="dfa35-104">For more information about Report Designer, see [Design Reports with Report Designer &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).</span></span>  
  
### <a name="to-design-the-child-report-using-the-report-wizard"></a><span data-ttu-id="dfa35-105">若要使用報表精靈設計子報表</span><span class="sxs-lookup"><span data-stu-id="dfa35-105">To design the child report using the Report Wizard</span></span>  
  
1.  <span data-ttu-id="dfa35-106">請確認已在 **方案總管**中選取頂層網站。</span><span class="sxs-lookup"><span data-stu-id="dfa35-106">Make sure that the top-level website is selected in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="dfa35-107">以滑鼠右鍵按一下網站，然後選取 [新增項目]  。</span><span class="sxs-lookup"><span data-stu-id="dfa35-107">Right-click on the website and select **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="dfa35-108">在 [**加入新專案**] 對話方塊中，按一下 [**報表 Wizard]**，輸入報表檔案的名稱，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="dfa35-108">In the **Add New Item** dialog box, click **Report Wizard**, enter a name for the report file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="dfa35-109">這樣會啟動 [報表精靈]。</span><span class="sxs-lookup"><span data-stu-id="dfa35-109">This launches the Report Wizard.</span></span>  
  
4.  <span data-ttu-id="dfa35-110">在 [資料**集屬性**] 頁面的 [**資料來源**] 方塊中，按一下 [ **DataSet2**]。</span><span class="sxs-lookup"><span data-stu-id="dfa35-110">In the **Dataset Properties** page, in the **Data source** box, click **DataSet2**.</span></span>  
  
     <span data-ttu-id="dfa35-111">[可用資料集]  方塊會自動更新為您所建立的 DataTable。</span><span class="sxs-lookup"><span data-stu-id="dfa35-111">The **Available datasets** box is automatically updated with the DataTable you created.</span></span>  
  
5.  <span data-ttu-id="dfa35-112">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="dfa35-112">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="dfa35-113">在 [排列欄位]  頁面中執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="dfa35-113">In the **Arrange Fields** page do the following:</span></span>  
  
    1.  <span data-ttu-id="dfa35-114">將 **ProductID**、**PurchaseOrderID**、**PurchaseOrderDetailID**、**OrderQty**、**ReceivedQty**、**RejectedQty** 和 **StockedQty** 從 [可用欄位]  拖曳至 [值]  方塊。</span><span class="sxs-lookup"><span data-stu-id="dfa35-114">Drag **ProductID**, **PurchaseOrderID**, **PurchaseOrderDetailID**, **OrderQty**, **ReceivedQty**, **RejectedQty**, and **StockedQty** from **Available Fields** to the **Values** box.</span></span>  
  
    2.  <span data-ttu-id="dfa35-115">按一下\*\*sum (ProductID) \*\*、 \*\*sum (PurchaseOrderID) \*\*、sum \*\* (PurchaseOrderDetailID) \*\*、 \*\*Sum (OrderQty) \*\*、 \*\*sum (ReceivedQty) \*\*、 \*\*Sum (RejectedQty) **和 sum \*\* (StockedQty) **並清除**總和**選取專案。</span><span class="sxs-lookup"><span data-stu-id="dfa35-115">Click the arrow next to **Sum(ProductID)**, **Sum(PurchaseOrderID)**, **Sum(PurchaseOrderDetailID)**, **Sum(OrderQty)**, **Sum(ReceivedQty)**, **Sum(RejectedQty)**, and **Sum(StockedQty)** and clear the **Sum** selection.</span></span>  
  
7.  <span data-ttu-id="dfa35-116">按兩次 **[下一步**]，然後按一下 **[完成**] 以關閉**報表精靈**。</span><span class="sxs-lookup"><span data-stu-id="dfa35-116">Click **Next** twice, then click **Finish** to close the **Report Wizard**.</span></span>  
  
     <span data-ttu-id="dfa35-117">現在您已建立 .rdlc 檔。</span><span class="sxs-lookup"><span data-stu-id="dfa35-117">You've now created the .rdlc file.</span></span> <span data-ttu-id="dfa35-118">此檔案會在報表設計師中開啟。</span><span class="sxs-lookup"><span data-stu-id="dfa35-118">The file opens in Report Designer.</span></span> <span data-ttu-id="dfa35-119">您設計的 Tablix 現在會顯示於設計介面中。</span><span class="sxs-lookup"><span data-stu-id="dfa35-119">The tablix you designed is now displayed in the design surface.</span></span>  
  
8.  <span data-ttu-id="dfa35-120">在 .rdlc 檔開啟的情況下，執行下列操作加入參數：</span><span class="sxs-lookup"><span data-stu-id="dfa35-120">With the .rdlc file open, add a parameter by doing the following:</span></span>  
  
    1.  <span data-ttu-id="dfa35-121">按一下 [**報表資料**] 窗格中的 [**參數**]，然後按一下 [**加入參數**]。</span><span class="sxs-lookup"><span data-stu-id="dfa35-121">Click **Parameters** in the **Report Data** pane, and then click **Add Parameters**.</span></span>  
  
    2.  <span data-ttu-id="dfa35-122">在 [名稱] 方塊中，輸入 **productid**。</span><span class="sxs-lookup"><span data-stu-id="dfa35-122">Enter **productid** in the **Name** box.</span></span>  
  
    3.  <span data-ttu-id="dfa35-123">確認已在 [資料類型] 清單方塊中，選取 [整數]。</span><span class="sxs-lookup"><span data-stu-id="dfa35-123">Confirm that **Integer** is selected in the **Data Type** list box.</span></span>  
  
    4.  <span data-ttu-id="dfa35-124">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="dfa35-124">Click **OK**.</span></span>  
  
9. <span data-ttu-id="dfa35-125">儲存 .rdlc 檔。</span><span class="sxs-lookup"><span data-stu-id="dfa35-125">Save the .rdlc file.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="dfa35-126">下一項工作</span><span class="sxs-lookup"><span data-stu-id="dfa35-126">Next Task</span></span>  
 <span data-ttu-id="dfa35-127">您已使用 [報表精靈] 成功設計子報表。</span><span class="sxs-lookup"><span data-stu-id="dfa35-127">You have successfully designed the child report by using the Report Wizard.</span></span> <span data-ttu-id="dfa35-128">接下來您要將 ReportViewer 控制項加入至網站應用程式。</span><span class="sxs-lookup"><span data-stu-id="dfa35-128">Next, you will add a ReportViewer control to the website application.</span></span>  
  
  
