---
title: 第 1 課：建立報表伺服器專案 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 675671ca-e6c9-48a2-82e9-386778f3a49f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a708e5114344e87edd620ef58bc50594a9b9ef8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710274"
---
# <a name="lesson-1-creating-a-report-server-project-reporting-services"></a><span data-ttu-id="0c950-102">第 1 課：建立報表伺服器專案 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="0c950-102">Lesson 1: Creating a Report Server Project (Reporting Services)</span></span>
  <span data-ttu-id="0c950-103">若要在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中建立報表，必須先建立報表伺服器專案，您將在其中儲存報表定義 (.rdl) 檔案以及報表所需的任何其他資源檔案。</span><span class="sxs-lookup"><span data-stu-id="0c950-103">To create a report in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you must first create a report server project where you will save your report definition (.rdl) file and any other resource files that you need for your report.</span></span> <span data-ttu-id="0c950-104">然後，您將建立實際的報表定義檔案、定義報表的資料來源、定義資料集，以及定義報表配置。</span><span class="sxs-lookup"><span data-stu-id="0c950-104">Then you will create the actual report definition file, define a data source for your report, define a dataset, and define the report layout.</span></span> <span data-ttu-id="0c950-105">當您執行報表時，會擷取實際資料並與配置結合，然後轉譯在您的螢幕上，再從螢幕上匯出、列印或儲存資料。</span><span class="sxs-lookup"><span data-stu-id="0c950-105">When you run the report, the actual data is retrieved and combined with the layout, and then rendered on your screen, from where you can export it, print it, or save it.</span></span>  
  
 <span data-ttu-id="0c950-106">在這一課，您將學習如何在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中建立報表伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="0c950-106">In this lesson, you will learn how to create a report server project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="0c950-107">報表伺服器專案用於建立在報表伺服器上執行的報表。</span><span class="sxs-lookup"><span data-stu-id="0c950-107">A report server project is used to create reports that run on a report server.</span></span>  
  
### <a name="to-create-a-report-server-project"></a><span data-ttu-id="0c950-108">建立報表伺服器專案</span><span class="sxs-lookup"><span data-stu-id="0c950-108">To create a report server project</span></span>  
  
1.  <span data-ttu-id="0c950-109">按一下 [**開始**]，指向 [**所有程式**]，指向 [] [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] ，然後按一下 [ **SQL Server Data Tools**]。</span><span class="sxs-lookup"><span data-stu-id="0c950-109">Click **Start**, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], and then click **SQL Server Data Tools**.</span></span> <span data-ttu-id="0c950-110">如果這是您第一次開啟 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] ，請按一下 [**商業智慧設定**] 做為預設環境設定。</span><span class="sxs-lookup"><span data-stu-id="0c950-110">If this is the first time you have opened [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Business Intelligence Settings** for the default environment settings.</span></span>  
  
2.  <span data-ttu-id="0c950-111">在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="0c950-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="0c950-112">在 [已安裝的範本]\*\*\*\* 清單中，按一下 [商業智慧]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c950-112">In the **Installed Templates** list, click **Business Intelligence**.</span></span>  
  
4.  <span data-ttu-id="0c950-113">按一下 [**報表伺服器專案**]。</span><span class="sxs-lookup"><span data-stu-id="0c950-113">Click **Report Server Project**.</span></span>  
  
5.  <span data-ttu-id="0c950-114">在 [名稱] \*\*\*\* 中，輸入 **Tutorial**。</span><span class="sxs-lookup"><span data-stu-id="0c950-114">In **Name**, type **Tutorial**.</span></span>  
  
6.  <span data-ttu-id="0c950-115">按一下 [確定]  以建立專案。</span><span class="sxs-lookup"><span data-stu-id="0c950-115">Click **OK** to create the project.</span></span>  
  
     <span data-ttu-id="0c950-116">Tutorial 專案隨即顯示在 [方案總管] 中。</span><span class="sxs-lookup"><span data-stu-id="0c950-116">The Tutorial project is displayed in Solution Explorer.</span></span>  
  
### <a name="to-create-a-new-report-definition-file"></a><span data-ttu-id="0c950-117">建立新的報表定義檔案</span><span class="sxs-lookup"><span data-stu-id="0c950-117">To create a new report definition file</span></span>  
  
1.  <span data-ttu-id="0c950-118">在方案總管中，以滑鼠右鍵按一下 [**報表**]，指向 [**加入**]，然後按一下 [**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="0c950-118">In Solution Explorer, right-click **Reports**, point to **Add**, and click **New Item**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0c950-119">如果看不到方案總管\*\*\*\* 視窗，請在 [檢視]\*\*\*\* 功能表上按一下方案總管\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c950-119">If the **Solution Explorer** window is not visible, from the **View** menu, click **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="0c950-120">在 [**加入新專案**] 對話方塊的 [**範本**] 底下，按一下 [**報表**]。</span><span class="sxs-lookup"><span data-stu-id="0c950-120">In the **Add New Item** dialog box, under **Templates**, click **Report**.</span></span>  
  
3.  <span data-ttu-id="0c950-121">在 [名稱] \*\*\*\* 中，輸入 **Sales Orders.rdl** ，然後按一下 [新增] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c950-121">In **Name**, type **Sales Orders.rdl** and then click **Add**.</span></span>  
  
     <span data-ttu-id="0c950-122">報表設計師會在 [設計] 檢視中開啟並顯示新的 .rdl 檔案。</span><span class="sxs-lookup"><span data-stu-id="0c950-122">Report Designer opens and displays the new .rdl file in Design view.</span></span>  
  
 <span data-ttu-id="0c950-123">報表設計師是一個在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中執行的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]元件。</span><span class="sxs-lookup"><span data-stu-id="0c950-123">Report Designer is a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] component that runs in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="0c950-124">它有兩個檢視：[設計] \*\*\*\* 和 [預覽] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c950-124">It has two views: **Design** and **Preview**.</span></span> <span data-ttu-id="0c950-125">按一下各個索引標籤，即可變更檢視。</span><span class="sxs-lookup"><span data-stu-id="0c950-125">Click each tab to change views.</span></span>  
  
 <span data-ttu-id="0c950-126">您會在 [報表資料] \*\*\*\* 窗格中定義資料，</span><span class="sxs-lookup"><span data-stu-id="0c950-126">You define your data in the **Report Data** pane.</span></span> <span data-ttu-id="0c950-127">並在 [設計] \*\*\*\* 檢視中定義報表配置。</span><span class="sxs-lookup"><span data-stu-id="0c950-127">You define your report layout in **Design** view.</span></span> <span data-ttu-id="0c950-128">您可以執行報表，然後在 [預覽] \*\*\*\* 檢視中查看外觀。</span><span class="sxs-lookup"><span data-stu-id="0c950-128">You can run the report and see what it looks like in **Preview** view.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="0c950-129">下一項工作</span><span class="sxs-lookup"><span data-stu-id="0c950-129">Next Task</span></span>  
 <span data-ttu-id="0c950-130">您已順利建立稱為 "Tutorial" 的報表專案，並將報表定義 (.rdl) 檔案加入至報表專案。</span><span class="sxs-lookup"><span data-stu-id="0c950-130">You have successfully created a report project called "Tutorial" and added a report definition (.rdl) file to the report project.</span></span> <span data-ttu-id="0c950-131">下一步，您將指定報表要用的資料來源。</span><span class="sxs-lookup"><span data-stu-id="0c950-131">Next, you will specify a data source to use for the report.</span></span> <span data-ttu-id="0c950-132">請參閱[第 2 課：指定連線資訊 &#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0c950-132">See [Lesson 2: Specifying Connection Information &#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c950-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c950-133">See Also</span></span>  
 [<span data-ttu-id="0c950-134">建立基本資料表報表 &#40;SSRS 教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="0c950-134">Create a Basic Table Report &#40;SSRS Tutorial&#41;</span></span>](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
