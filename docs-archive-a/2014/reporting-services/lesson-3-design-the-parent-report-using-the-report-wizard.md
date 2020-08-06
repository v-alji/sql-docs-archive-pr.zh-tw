---
title: 第 3 課：使用報表精靈設計父報表 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3cb6a0972a2bb63e82e80c02b3ce90912ba01c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592521"
---
# <a name="lesson-3-design-the-parent-report-using-the-report-wizard"></a><span data-ttu-id="37c93-102">第 3 課：使用報表精靈設計父報表</span><span class="sxs-lookup"><span data-stu-id="37c93-102">Lesson 3: Design the Parent Report using the Report Wizard</span></span>
  <span data-ttu-id="37c93-103">在您建立父報表的資料連接和資料表之後，下一步是要使用報表設計師中的 [報表精靈] 設計父報表。</span><span class="sxs-lookup"><span data-stu-id="37c93-103">After you create a data connection and a data table for the parent report, your next step is to design the parent report using the Report Wizard in Report Designer.</span></span> <span data-ttu-id="37c93-104">如需報表設計師的詳細資訊，請參閱[使用報表設計師設計報表 &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="37c93-104">For more information about Report Designer, see [Design Reports with Report Designer &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).</span></span>  
  
### <a name="to-design-the-parent-report-using-the-report-wizard"></a><span data-ttu-id="37c93-105">若要使用報表精靈設計父報表</span><span class="sxs-lookup"><span data-stu-id="37c93-105">To design the parent report using the Report Wizard</span></span>  
  
1.  <span data-ttu-id="37c93-106">請確認已在 **方案總管**中選取頂層網站。</span><span class="sxs-lookup"><span data-stu-id="37c93-106">Make sure that the top-level website is selected in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="37c93-107">以滑鼠右鍵按一下網站，然後選取 [新增項目]  。</span><span class="sxs-lookup"><span data-stu-id="37c93-107">Right-click on the website and select **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="37c93-108">在 [**加入新專案**] 對話方塊中，選取 [**報表 Wizard]**，輸入報表檔案的名稱，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="37c93-108">In the **Add New Item** dialog box, select **Report Wizard**, enter a name for the report file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="37c93-109">這樣會啟動 [報表精靈]。</span><span class="sxs-lookup"><span data-stu-id="37c93-109">This launches the Report Wizard.</span></span>  
  
4.  <span data-ttu-id="37c93-110">在 [資料集屬性] 頁面的 [資料來源] 方塊中，選取您在[第 2 課：定義父報表的資料連線和資料表](lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)中建立的 [DataSet1]。</span><span class="sxs-lookup"><span data-stu-id="37c93-110">On the **Dataset Properties** page, in the **Data source** box, select the **DataSet1** you created in [Lesson 2: Define a Data Connection and Data Table for Parent Report](lesson-2-define-a-data-connection-and-data-table-for-parent-report.md).</span></span>  
    <span data-ttu-id="37c93-111">[可用資料集]  方塊會自動更新為您如上所建立的 **DataTable**。</span><span class="sxs-lookup"><span data-stu-id="37c93-111">The **Available datasets** box is automatically updated with the **DataTable** you created above.</span></span>  
  
5.  <span data-ttu-id="37c93-112">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="37c93-112">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="37c93-113">在 [排列欄位]  頁面中執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="37c93-113">In the **Arrange Fields** page do the following:</span></span>  
  
    1.  <span data-ttu-id="37c93-114">從 [可用欄位] 將 **ProductID**、**Name**、**ProductNumber**、**SafetyStockLevel** 和 **ReorderLevel** 拖曳至 [值] 方塊。</span><span class="sxs-lookup"><span data-stu-id="37c93-114">Drag **ProductID**, **Name**, **ProductNumber**, **SafetyStockLevel**, and **ReorderLevel** from **Available fields** to the **Values** box.</span></span>  
  
    2.  <span data-ttu-id="37c93-115">按一下 [ \*\*sum] (ProductID) \*\*， \*\*sum (SafetyStockLevel) \*\*，sum \*\* (ReorderLevel) \*\* ] 旁的箭號，然後清除 [ **sum** ] 選取專案。</span><span class="sxs-lookup"><span data-stu-id="37c93-115">Click the arrow next to **Sum(ProductID)**, **Sum(SafetyStockLevel)**, **Sum(ReorderLevel)** and clear the **Sum** selection.</span></span>  
  
7.  <span data-ttu-id="37c93-116">按兩次 **[下一步**]，然後按一下 **[完成**] 以關閉**報表精靈**。</span><span class="sxs-lookup"><span data-stu-id="37c93-116">Click **Next** twice, then click **Finish** to close the **Report Wizard**.</span></span>  
  
     <span data-ttu-id="37c93-117">現在您已建立 .rdlc 檔。</span><span class="sxs-lookup"><span data-stu-id="37c93-117">You've now created the .rdlc file.</span></span> <span data-ttu-id="37c93-118">此檔案會在報表設計師中開啟。</span><span class="sxs-lookup"><span data-stu-id="37c93-118">The file opens in Report Designer.</span></span> <span data-ttu-id="37c93-119">您設計的 Tablix 現在會顯示於設計介面中。</span><span class="sxs-lookup"><span data-stu-id="37c93-119">The tablix you designed is now displayed in the design surface.</span></span>  
  
8.  <span data-ttu-id="37c93-120">儲存 .rdlc 檔。</span><span class="sxs-lookup"><span data-stu-id="37c93-120">Save the .rdlc file.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="37c93-121">下一項工作</span><span class="sxs-lookup"><span data-stu-id="37c93-121">Next Task</span></span>  
 <span data-ttu-id="37c93-122">您已使用 [報表精靈] 成功設計父報表。</span><span class="sxs-lookup"><span data-stu-id="37c93-122">You have successfully designed the parent report using the Report Wizard.</span></span> <span data-ttu-id="37c93-123">接下來您將建立子報表的資料連接和資料表。</span><span class="sxs-lookup"><span data-stu-id="37c93-123">Next, you will create a data connection and a data table for the child report.</span></span>  
  
  
