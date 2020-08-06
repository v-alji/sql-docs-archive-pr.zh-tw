---
title: 步驟 2：新增和設定記錄 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 56105f3f-e500-4669-8c8e-acf434527727
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0f2cdce6f34a19e22830d357d20f5d99cff8c14f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700012"
---
# <a name="step-2-adding-and-configuring-logging"></a><span data-ttu-id="9e91f-102">步驟 2:新增和設定記錄</span><span class="sxs-lookup"><span data-stu-id="9e91f-102">Step 2: Adding and Configuring Logging</span></span>
  <span data-ttu-id="9e91f-103">在這項工作中，您將針對 Lesson 3.dtsx 封裝的資料流程啟用記錄。</span><span class="sxs-lookup"><span data-stu-id="9e91f-103">In this task, you will enable logging for the data flow in the Lesson 3.dtsx package.</span></span> <span data-ttu-id="9e91f-104">然後，您會設定文字檔案記錄提供者來記錄 PipelineExecutionPlan 和 PipelineExecuteTrees 事件。</span><span class="sxs-lookup"><span data-stu-id="9e91f-104">Then, you will configure a Text File log provider to log the PipelineExecutionPlan and PipelineExecuteTrees events.</span></span> <span data-ttu-id="9e91f-105">文字檔案記錄提供者會建立容易檢視及容易傳輸的記錄。</span><span class="sxs-lookup"><span data-stu-id="9e91f-105">The Text Files log provider creates logs that are easy to view and easily transportable.</span></span> <span data-ttu-id="9e91f-106">這些記錄檔的簡單性，使它們在封裝的基本測試階段特別有用。</span><span class="sxs-lookup"><span data-stu-id="9e91f-106">The simplicity of these log files makes these files especially useful during the basic testing phase of a package.</span></span> <span data-ttu-id="9e91f-107">您也可以在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師的 [記錄事件] 視窗中檢視記錄項目。</span><span class="sxs-lookup"><span data-stu-id="9e91f-107">You can also view the log entries in the Log Events window of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
### <a name="to-add-logging-to-the-package"></a><span data-ttu-id="9e91f-108">若要將記錄加入封裝中</span><span class="sxs-lookup"><span data-stu-id="9e91f-108">To add logging to the package</span></span>  
  
1.  <span data-ttu-id="9e91f-109">在 **[SSIS]** 功能表上，按一下 **[記錄]** 。</span><span class="sxs-lookup"><span data-stu-id="9e91f-109">On the **SSIS** menu, click **Logging**.</span></span>  
  
2.  <span data-ttu-id="9e91f-110">在 **[設定 SSIS 記錄]** 對話方塊的 **[容器]** 窗格中，確定有選取代表第 3 課封裝的最上層物件。</span><span class="sxs-lookup"><span data-stu-id="9e91f-110">In the **Configure SSIS Logs** dialog box, in the **Containers** pane, make sure that the topmost object, which represents the Lesson 3 package, is selected.</span></span>  
  
3.  <span data-ttu-id="9e91f-111">在 **[提供者與記錄]** 索引標籤的 **[提供者類型]** 方塊中，選取 **[文字檔的 SSIS 記錄提供者]**，然後按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="9e91f-111">On the **Providers and Logs** tab, in the **Provider type** box, select **SSIS log provider for Text files**, and then click **Add**.</span></span>  
  
     <span data-ttu-id="9e91f-112">Integration Services 會將新的文字檔記錄提供者新增至封裝，並具有文字檔的預設名稱**SSIS 記錄提供者**。</span><span class="sxs-lookup"><span data-stu-id="9e91f-112">Integration Services adds a new Text File log provider to the package with the default name **SSIS log provider for text files**.</span></span> <span data-ttu-id="9e91f-113">現在您可以設定新的記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="9e91f-113">You can now configure the new log provider.</span></span>  
  
4.  <span data-ttu-id="9e91f-114">在 [**名稱**] 資料行中，輸入 `Lesson 3 Log File` 。</span><span class="sxs-lookup"><span data-stu-id="9e91f-114">In the **Name** column, type `Lesson 3 Log File`.</span></span>  
  
5.  <span data-ttu-id="9e91f-115">可選擇性地修改 **[描述]** 。</span><span class="sxs-lookup"><span data-stu-id="9e91f-115">Optionally, modify the **Description**.</span></span>  
  
6.  <span data-ttu-id="9e91f-116">在 [組態]\*\*\*\* 資料行中，按一下 [\<New Connection>]\*\*\*\* 來指定記錄資訊寫入的目的地。</span><span class="sxs-lookup"><span data-stu-id="9e91f-116">In the **Configuration** column, click **\<New Connection>** to specify the destination to which the log information is written.</span></span>  
  
     <span data-ttu-id="9e91f-117">在 **[檔案連接管理員編輯器]** 對話方塊中，對於 **[使用類型]** 選取 **[建立檔案]**，然後按一下 **[瀏覽]**。</span><span class="sxs-lookup"><span data-stu-id="9e91f-117">In the **File Connection Manager Editor** dialog box, for **Usage type**, select **Create file**, and then click **Browse**.</span></span> <span data-ttu-id="9e91f-118">依預設， **[選取檔案]** 對話方塊會開啟專案資料夾，但您可以將記錄資訊儲存至任何位置。</span><span class="sxs-lookup"><span data-stu-id="9e91f-118">By default, the **Select File** dialog box opens the project folder, but you can save log information to any location.</span></span>  
  
7.  <span data-ttu-id="9e91f-119">在 [**選取**檔案] 對話方塊的 [**檔案名**] 方塊中，輸入 `TutorialLog.log` ，然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="9e91f-119">In the **Select File** dialog box, in the **File name** box type `TutorialLog.log`, and click **Open**.</span></span>  
  
8.  <span data-ttu-id="9e91f-120">按一下 **[確定]** 來關閉 **[檔案連接管理員編輯器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9e91f-120">Click **OK** to close the **File Connection Manager Editor** dialog box.</span></span>  
  
9. <span data-ttu-id="9e91f-121">在 **[容器]** 窗格中，展開封裝容器階層的所有節點，然後清除所有核取方塊，包括 **[擷取範例貨幣資料]** 核取方塊在內。</span><span class="sxs-lookup"><span data-stu-id="9e91f-121">In the **Containers** pane, expand all nodes of the package container hierarchy, and then clear all check boxes, including the **Extract Sample Currency Data** check box.</span></span> <span data-ttu-id="9e91f-122">現在，請選取 **[擷取範例貨幣資料]** 來取得只有此節點的事件。</span><span class="sxs-lookup"><span data-stu-id="9e91f-122">Now select the check box for **Extract Sample Currency Data** to get only the events for this node.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9e91f-123"> 如果 **[擷取範例貨幣資料]** 核取方塊呈現暗灰色而不是被選取，此工作將使用父容器的記錄設定，且您不能啟用此工作特定的記錄事件。</span><span class="sxs-lookup"><span data-stu-id="9e91f-123">If the state of the **Extract Sample Currency Data** check box is dimmed instead of selected, the task uses the log settings of the parent container and you cannot enable the log events that are specific to the task.</span></span>  
  
10. <span data-ttu-id="9e91f-124">在 **[詳細資料]** 索引標籤的 **[事件]** 資料行中，選取 **[PipelineExecutionPlan]** 和 **[PipelineExecutionTrees]** 事件。</span><span class="sxs-lookup"><span data-stu-id="9e91f-124">On the **Details** tab, in the **Events** column, select the **PipelineExecutionPlan** and **PipelineExecutionTrees** events.</span></span>  
  
11. <span data-ttu-id="9e91f-125">按一下 **[進階]** 來檢閱記錄提供者將針對每一個事件寫入記錄檔的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9e91f-125">Click **Advanced** to review the details that the log provider will write to the log for each event.</span></span> <span data-ttu-id="9e91f-126">依預設，對於您指定的事件，會自動選取所有資訊類別目錄。</span><span class="sxs-lookup"><span data-stu-id="9e91f-126">By default, all information categories are automatically selected for the events you specify.</span></span>  
  
12. <span data-ttu-id="9e91f-127">按一下 **[基本]** 來隱藏資訊類別目錄。</span><span class="sxs-lookup"><span data-stu-id="9e91f-127">Click **Basic** to hide the information categories.</span></span>  
  
13. <span data-ttu-id="9e91f-128">在 [**提供者和記錄**檔] 索引標籤的 [**名稱**] 欄中，選取 [] `Lesson 3 Log File` 。</span><span class="sxs-lookup"><span data-stu-id="9e91f-128">On the **Provider and Logs** tab, in the **Name** column, select `Lesson 3 Log File`.</span></span> <span data-ttu-id="9e91f-129">建立封裝的記錄提供者之後，您就可以選擇性地取消選取它，來暫時關閉記錄，而不必刪除再重新建立記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="9e91f-129">Once you have created a log provider for your package, you can optionally deselect it to temporarily turn off logging, without having to delete and re-create a log provider.</span></span>  
  
14. <span data-ttu-id="9e91f-130">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="9e91f-130">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9e91f-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9e91f-131">Next Steps</span></span>  
 [<span data-ttu-id="9e91f-132">步驟 3：測試第 3 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="9e91f-132">Step 3: Testing the Lesson 3 Tutorial Package</span></span>](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
  
