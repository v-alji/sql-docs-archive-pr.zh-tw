---
title: 工作6：將 Excel 來源加入至資料流程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 0209055e-cb6b-4a07-909e-836596727a2c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ae183dee04619a407655026a49b189f7bb3ac6fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598692"
---
# <a name="task-6-adding-excel-source-to-the-data-flow"></a><span data-ttu-id="2737f-102">工作 6：將 Excel 來源新增至資料流程</span><span class="sxs-lookup"><span data-stu-id="2737f-102">Task 6: Adding Excel Source to the Data Flow</span></span>
  <span data-ttu-id="2737f-103">在這項工作中，您會將 Excel 來源加入至資料流程，以便從來源 Excel 檔案讀取供應商資料。</span><span class="sxs-lookup"><span data-stu-id="2737f-103">In this task, you add an Excel Source to the data flow to read supplier data from the source Excel file.</span></span> <span data-ttu-id="2737f-104">Excel 來源會從 Microsoft Excel 活頁簿中的工作表或範圍擷取資料。</span><span class="sxs-lookup"><span data-stu-id="2737f-104">The Excel Source extracts data from worksheets or ranges in Microsoft Excel workbooks.</span></span> <span data-ttu-id="2737f-105">如需詳細資訊，請參閱[Excel 來源](../integration-services/data-flow/excel-source.md)主題。</span><span class="sxs-lookup"><span data-stu-id="2737f-105">See [Excel Source](../integration-services/data-flow/excel-source.md) topic for more details.</span></span>

1.  <span data-ttu-id="2737f-106">從 [ **SSIS 工具箱**] 中的 [**其他來源**] 將 [ **Excel 來源**] 拖放至 [**資料流程**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2737f-106">Drag-drop **Excel Source** from **Other Sources** in **SSIS Toolbox** to the **Data Flow** tab.</span></span>

2.  <span data-ttu-id="2737f-107">以滑鼠右鍵**按一下 [資料流程**] 索引標籤中的 [ **Excel 來源**]，然後按一下 [**重新命名**]。</span><span class="sxs-lookup"><span data-stu-id="2737f-107">Right-click on **Excel Source** in the **Data Flow** tab, and click **Rename**.</span></span>

3.  <span data-ttu-id="2737f-108">輸入**從 Excel 檔案讀取供應商資料**，然後按**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="2737f-108">Type **Read Supplier Data from Excel File** and press **ENTER**.</span></span>

4.  <span data-ttu-id="2737f-109">按兩下 [**從 excel 檔案讀取供應商資料**]，啟動 [ **excel 來源編輯器**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2737f-109">Double-click **Read Supplier Data from Excel File** to launch the **Excel Source Editor** dialog box.</span></span>

5.  <span data-ttu-id="2737f-110">在 [ **Excel 來源編輯器**] 對話方塊中，按一下 [**新增**] 以建立 Excel 連接。</span><span class="sxs-lookup"><span data-stu-id="2737f-110">In the **Excel Source Editor** dialog box, click **New** to create an Excel connection.</span></span>

6.  <span data-ttu-id="2737f-111">在 [ **Excel 連接管理員**] 對話方塊中，按一下 [**流覽]**，然後選取 [ **EIM 教學**課程] 資料夾中的**Suppliers.xls**檔案。</span><span class="sxs-lookup"><span data-stu-id="2737f-111">In the **Excel Connection Manager** dialog box, click **Browse**, and then select the **Suppliers.xls** file in the **EIM Tutorial** folder.</span></span> <span data-ttu-id="2737f-112">確認已在 [ **Excel 版本**] 方塊中選取 [ **Microsoft Excel 97-2003** ]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2737f-112">Confirm that **Microsoft Excel 97-2003** is selected in the **Excel Version** box and then click **OK**.</span></span>

     <span data-ttu-id="2737f-113">![Excel 連接管理員對話方塊](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "Excel 連接管理員對話方塊")</span><span class="sxs-lookup"><span data-stu-id="2737f-113">![Excel Connection Manager Dialog Box](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "Excel Connection Manager Dialog Box")</span></span>

7.  <span data-ttu-id="2737f-114">在 [ **Excel 來源編輯器**] 對話方塊中，于 [ **excel 工作表的名稱**] 清單方塊中選取 [ **IncomingSuppliers $** ]。</span><span class="sxs-lookup"><span data-stu-id="2737f-114">In the **Excel Source Editor** dialog box, select **IncomingSuppliers$** in the **Name of the Excel sheet** list box.</span></span>

     <span data-ttu-id="2737f-115">![Excel 工作表名稱 - 進貨供應商$](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "Excel 工作表名稱 - 進貨供應商$")</span><span class="sxs-lookup"><span data-stu-id="2737f-115">![Name of Excel Sheet - Incoming Suppliers$](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "Name of Excel Sheet - Incoming Suppliers$")</span></span>

8.  <span data-ttu-id="2737f-116">按一下 [**預覽**] 以預覽 Excel 檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="2737f-116">Click **Preview** to preview the data in Excel file.</span></span>

9. <span data-ttu-id="2737f-117">按一下 **[確定]** ，關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2737f-117">Click **OK** to close the dialog box.</span></span>

10. <span data-ttu-id="2737f-118">在 [ **SSIS 工具箱**] 的**其他轉換**中，將**DQS 清理**轉換拖放至 [**從 Excel 檔案讀取供應商資料**] 底下的 [**資料流程**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2737f-118">Drag-drop **DQS Cleansing** transform in **Other Transforms** on the **SSIS Toolbox** to the **Data Flow** tab under **Read Supplier Data from Excel File**.</span></span> <span data-ttu-id="2737f-119">DQS 清理轉換會使用 Data Quality Services (DQS)，藉由套用知識庫中核准的規則來更正資料。</span><span class="sxs-lookup"><span data-stu-id="2737f-119">The DQS Cleansing transformation uses Data Quality Services (DQS) to correct data by applying approved rules in the knowledge base.</span></span> <span data-ttu-id="2737f-120">這項轉換在執行階段會在 DQS 伺服器上建立 DQS 清理專案。</span><span class="sxs-lookup"><span data-stu-id="2737f-120">This transform, at runtime, creates a DQS cleansing project on the DQS server.</span></span> <span data-ttu-id="2737f-121">如需詳細資訊，請參閱[DQS 清理轉換](https://msdn.microsoft.com/library/ee677619.aspx)主題。</span><span class="sxs-lookup"><span data-stu-id="2737f-121">See [DQS Cleansing Transformation](https://msdn.microsoft.com/library/ee677619.aspx) topic for more details.</span></span>

## <a name="next-step"></a><span data-ttu-id="2737f-122">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2737f-122">Next Step</span></span>

[<span data-ttu-id="2737f-123">工作 7：將 DQS 清理轉換新增至資料流程</span><span class="sxs-lookup"><span data-stu-id="2737f-123">Task 7: Adding DQS Cleansing Transform to the Data Flow</span></span>](task-7-adding-dqs-cleansing-transform-to-the-data-flow.md)

### <a name="see-also"></a><span data-ttu-id="2737f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2737f-124">See Also</span></span>

[<span data-ttu-id="2737f-125">資料流程</span><span class="sxs-lookup"><span data-stu-id="2737f-125">Data Flow</span></span>](../integration-services/data-flow/data-flow.md)
