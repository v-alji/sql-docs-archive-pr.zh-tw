---
title: 在 Data Quality Client 中開啟 Integration Services 專案 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a8bad2f1-8fb0-4d14-a978-11a5720e62d6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fd29bbba274535d6489eb8d188aa4f0150ed7c4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594191"
---
# <a name="open-integration-services-projects-in-data-quality-client"></a><span data-ttu-id="403f5-102">在 Data Quality Client 中開啟 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="403f5-102">Open Integration Services Projects in Data Quality Client</span></span>
  <span data-ttu-id="403f5-103">[!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)] 可讓您以批次模式執行清理專案。</span><span class="sxs-lookup"><span data-stu-id="403f5-103">The [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)] enables you to run a cleansing project in batch mode.</span></span> <span data-ttu-id="403f5-104">但是，有時您可能會想要在 Integration Services 封裝中檢閱清理結果，類似於在 DQS 中，於資料品質專案中清理活動內的 **[管理和檢視結果]** 索引標籤中檢閱清理結果。</span><span class="sxs-lookup"><span data-stu-id="403f5-104">However, at times you might want to review the cleansing results in an Integration Services package similar to how you can review the cleansing results in the **Manage and View Results** tab of a cleansing activity in a data quality project in DQS.</span></span> <span data-ttu-id="403f5-105">DQS 可讓您在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 中開啟 Integration Services 專案，就像從 **[開啟專案]** 畫面開啟其他任何資料品質專案，並讓您擁有在 Integration Services 專案中清理結果的互動式清理體驗。</span><span class="sxs-lookup"><span data-stu-id="403f5-105">DQS enables you to open Integration Services projects in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] just like any other data quality project from the **Open project** screen, and have an interactive cleansing experience of the cleansing results in an Integration Services project.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="403f5-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="403f5-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="403f5-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="403f5-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="403f5-108">**中的** [開啟專案] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]畫面上只會提供完成的 Integration Services 專案。</span><span class="sxs-lookup"><span data-stu-id="403f5-108">Only completed Integration Services projects are available in the **Open project** screen in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="403f5-109">**[開啟專案]** 畫面上不會提供失敗或執行中的專案。</span><span class="sxs-lookup"><span data-stu-id="403f5-109">Failed or running projects are not available in the **Open project** screen.</span></span>  
  
-   <span data-ttu-id="403f5-110">Integration Services 專案會在**中的互動式清理階段開啟 (** [管理和檢視結果] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]索引標籤)。</span><span class="sxs-lookup"><span data-stu-id="403f5-110">Integration Services projects open at the interactive cleansing stage (**Manage View and Results** tab) in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="403f5-111">您不能移至 **[清理]** 或 **[對應]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="403f5-111">You cannot go to the **Cleanse** or **Map** tabs.</span></span> <span data-ttu-id="403f5-112">您只能按 **[下一步]** 移至 **[匯出]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="403f5-112">You can only go to the **Export** tab by clicking **Next**.</span></span>  
  
-   <span data-ttu-id="403f5-113">您無法從 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]刪除鎖定的 Integration Services 專案。</span><span class="sxs-lookup"><span data-stu-id="403f5-113">You cannot delete a locked Integration Services project from [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="403f5-114">您必須先解除鎖定，然後才能刪除。</span><span class="sxs-lookup"><span data-stu-id="403f5-114">You must first unlock it to delete.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="403f5-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="403f5-115">Prerequisites</span></span>  
 <span data-ttu-id="403f5-116">您必須已經順利執行完 Integration Services 專案 (其中包含的封裝具有 DQS 清理元件)，才能在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]中加以查看及開啟。</span><span class="sxs-lookup"><span data-stu-id="403f5-116">You must have successfully completed running an Integration Services project containing a package with a DQS Cleansing component to see and open it in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="403f5-117">Security</span><span class="sxs-lookup"><span data-stu-id="403f5-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="403f5-118">權限</span><span class="sxs-lookup"><span data-stu-id="403f5-118">Permissions</span></span>  
 <span data-ttu-id="403f5-119">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 或 dqs_kb_operator 角色，才能開啟 Integration Services 專案。</span><span class="sxs-lookup"><span data-stu-id="403f5-119">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to open an Integration Services project.</span></span>  
  
##  <a name="open-an-integration-services-project"></a><a name="Open"></a> <span data-ttu-id="403f5-120">開啟 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="403f5-120">Open an Integration Services Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="403f5-121">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="403f5-121">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="403f5-122">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，按一下 [**開啟資料品質專案**]。</span><span class="sxs-lookup"><span data-stu-id="403f5-122">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open Data Quality Project**.</span></span> <span data-ttu-id="403f5-123">**[開啟專案]** 畫面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="403f5-123">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="403f5-124">在 **[開啟專案]** 畫面上，您可以依照以下其中一種方式來識別 Integration Services 專案：</span><span class="sxs-lookup"><span data-stu-id="403f5-124">In the **Open project** screen, you can identify an Integration Services project in either of the following ways:</span></span>  
  
    1.  <span data-ttu-id="403f5-125">**專案名稱**： Integration Services 專案會使用下列命名詞彙列出： "PACKAGE. DQS Cleansing_ *\<DATE>\*\*\<TIME>* _ {GUID}"。</span><span class="sxs-lookup"><span data-stu-id="403f5-125">**Project Name**: Integration Services projects are listed using the following naming terminology: "Package.DQS Cleansing_*\<DATE>\*\*\<TIME>*_{GUID}."</span></span> <span data-ttu-id="403f5-126">每次在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中成功執行相同的封裝時，新的專案會列在 [開啟專案] \*\*\*\* 畫面中。</span><span class="sxs-lookup"><span data-stu-id="403f5-126">Every time you successfully run the same package in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], a new project is listed in the **Open project** screen.</span></span>  
  
    2.  <span data-ttu-id="403f5-127">**專案類型**：Integration Services 專案在 **[開啟專案]** 畫面上擁有 **[SSIS]** 專案類型。</span><span class="sxs-lookup"><span data-stu-id="403f5-127">**Project Type**: Integration Services projects have **SSIS** as the project type in the **Open project** screen.</span></span>  
  
     <span data-ttu-id="403f5-128">選取專案，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="403f5-128">Select a project, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="403f5-129">Integration Services 專案會在互動式清理階段開啟 (**[管理和檢視結果]** 索引標籤)。</span><span class="sxs-lookup"><span data-stu-id="403f5-129">The Integration Services project opens at the interactive cleansing stage (**Manage View and Results** tab).</span></span> <span data-ttu-id="403f5-130">您可以針對 Integration Services 專案中的資料執行互動式清理。</span><span class="sxs-lookup"><span data-stu-id="403f5-130">You can perform an interactive cleansing on the data in the Integration Services project.</span></span> <span data-ttu-id="403f5-131">如需 [管理和檢視結果]\*\*\*\* 索引標籤的詳細資訊，請參閱[使用 DQS &#40;內部&#41; 知識清理資料](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)中的[互動式清理階段](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive)。</span><span class="sxs-lookup"><span data-stu-id="403f5-131">For detailed information about the **Manage and View Results** tab, see [Interactive Cleansing Stage](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive) in [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).</span></span>  
  
5.  <span data-ttu-id="403f5-132">按 **[下一步]** 移至 **[匯出]** 索引標籤，您可以在這裡將處理過的資料匯出到以下任何項目：SQL Server 資料庫中的新資料表、.csv 檔案或 Excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="403f5-132">Click **Next** to go to the **Export** tab where you can export the processed data to any of the following: a new table in the SQL Server database, a .csv file, or an Excel file.</span></span> <span data-ttu-id="403f5-133">如需 [匯出]\*\*\*\* 索引標籤的詳細資訊，請參閱[使用 DQS &#40;內部&#41; 知識清理資料](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)中的[匯出階段](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export)。</span><span class="sxs-lookup"><span data-stu-id="403f5-133">For detailed information about the **Export** tab, see [Export Stage](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export) in [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)</span></span>  
  
6.  <span data-ttu-id="403f5-134">在匯出資料之後，按一下 **[完成]** ，關閉 Integration Services 專案。</span><span class="sxs-lookup"><span data-stu-id="403f5-134">After exporting the data, click **Finish** to close the Integration Services project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="403f5-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="403f5-135">See Also</span></span>  
 <span data-ttu-id="403f5-136">[DQS 清理轉換](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="403f5-136">[DQS Cleansing Transformation](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) </span></span>  
 [<span data-ttu-id="403f5-137">Integration Services &#40;SSIS&#41; 專案</span><span class="sxs-lookup"><span data-stu-id="403f5-137">Integration Services &#40;SSIS&#41; Projects</span></span>](../integration-services/integration-services-ssis-projects-and-solutions.md)  
