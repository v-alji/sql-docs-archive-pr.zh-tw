---
title: 步驟 3：加入封裝和其他檔案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a7e6ec9c-d31d-4613-9525-8947a7b358f7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d5ddcb6315576558161119a8774bccbd63fa5844
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596143"
---
# <a name="step-3-adding-packages-and-other-files"></a><span data-ttu-id="a8a00-102">步驟 3：新增封裝和其他檔案</span><span class="sxs-lookup"><span data-stu-id="a8a00-102">Step 3: Adding Packages and Other Files</span></span>
  <span data-ttu-id="a8a00-103">在這項工作中，您會將現有的封裝、支援個別封裝的輔助檔案以及讀我檔案，加入至前一項工作所建立的「部署教學課程」專案中。</span><span class="sxs-lookup"><span data-stu-id="a8a00-103">In this task, you will add existing packages, ancillary files that support individual packages, and a Readme to the Deployment Tutorial project that you created in the previous task.</span></span> <span data-ttu-id="a8a00-104">例如，您將會加入包含封裝資料的 XML 資料檔，還會加入一個文字檔，以提供有關專案中所有封裝的讀我資訊。</span><span class="sxs-lookup"><span data-stu-id="a8a00-104">For example, you will add an XML data file that contains the data for a package and a text file that provides Readme information about all the packages in the project.</span></span>  
  
 <span data-ttu-id="a8a00-105">當您將封裝部署到測試或實際執行環境時，通常不會將資料檔包含在部署中，而是利用組態來更新資料來源的路徑，以存取資料檔或資料庫的測試版本或實際執行版本。</span><span class="sxs-lookup"><span data-stu-id="a8a00-105">When you deploy packages to a test or production environment, you typically do not include the data files in the deployment, but instead use configurations to update the paths of the data sources to access test or production versions of the data files or databases.</span></span> <span data-ttu-id="a8a00-106">為了教學上的目的，這個教學課程會將資料檔包含在封裝部署中。</span><span class="sxs-lookup"><span data-stu-id="a8a00-106">For instructional purposes, this tutorial includes data files in the package deployment.</span></span>  
  
 <span data-ttu-id="a8a00-107">當您安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 範例時，會一併安裝封裝和封裝所使用的範例資料。</span><span class="sxs-lookup"><span data-stu-id="a8a00-107">The packages and the sample data that the packages use are installed when you install the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] samples.</span></span> <span data-ttu-id="a8a00-108">您將會在「部署教學課程」專案中加入下列封裝：</span><span class="sxs-lookup"><span data-stu-id="a8a00-108">You will add the following packages to the Deployment Tutorial project:</span></span>  
  
-   <span data-ttu-id="a8a00-109">**DataTransfer：**</span><span class="sxs-lookup"><span data-stu-id="a8a00-109">**DataTransfer.**</span></span> <span data-ttu-id="a8a00-110">這是基本套件，它會從一般檔案中擷取資料、評估資料行的值以便有條件地保留資料集中的資料列，以及將資料載入至 AdventureWorks 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="a8a00-110">Basic package that extracts data from a flat file, evaluates column values to conditionally keep rows in the dataset, and loads data into a table in the AdventureWorks database.</span></span>  
  
-   <span data-ttu-id="a8a00-111">**LoadXMLData：**</span><span class="sxs-lookup"><span data-stu-id="a8a00-111">**LoadXMLData.**</span></span> <span data-ttu-id="a8a00-112">這是資料傳輸套件，它會從 XML 資料檔中擷取資料、評估和彙總資料行的值，以及將資料載入至 AdventureWorks 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="a8a00-112">Data-transfer package that extracts data from an XML data file, evaluates and aggregates column values, and loads data into a table in the AdventureWorks database.</span></span>  
  
 <span data-ttu-id="a8a00-113">若要支援這些封裝的部署，您需要將下列輔助檔案加入至「部署教學課程」專案中：</span><span class="sxs-lookup"><span data-stu-id="a8a00-113">To support the deployment of these packages, you will add the following ancillary files to the Deployment Tutorial project.</span></span>  
  
|<span data-ttu-id="a8a00-114">Package</span><span class="sxs-lookup"><span data-stu-id="a8a00-114">Package</span></span>|<span data-ttu-id="a8a00-115">檔案</span><span class="sxs-lookup"><span data-stu-id="a8a00-115">File</span></span>|  
|-------------|----------|  
|<span data-ttu-id="a8a00-116">DataTransfer</span><span class="sxs-lookup"><span data-stu-id="a8a00-116">DataTransfer</span></span>|<span data-ttu-id="a8a00-117">NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="a8a00-117">NewCustomers.txt</span></span>|  
|<span data-ttu-id="a8a00-118">LoadXMLData</span><span class="sxs-lookup"><span data-stu-id="a8a00-118">LoadXMLData</span></span>|<span data-ttu-id="a8a00-119">orders.xml 和 orders.xsd</span><span class="sxs-lookup"><span data-stu-id="a8a00-119">orders.xml and orders.xsd</span></span>|  
  
 <span data-ttu-id="a8a00-120">您還需要加入讀我檔案，這是一個文字檔，會提供有關「部署教學課程」專案的資訊。</span><span class="sxs-lookup"><span data-stu-id="a8a00-120">You will also add a Readme, which is a text file that provides information about the Deployment Tutorial project.</span></span>  
  
 <span data-ttu-id="a8a00-121">下列程序中所使用的路徑是假設 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 範例已安裝在預設位置 [!INCLUDE[ssSampPathIS](../includes/sssamppathis-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a8a00-121">The paths used in the following procedures assume that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] samples were installed in the default location, [!INCLUDE[ssSampPathIS](../includes/sssamppathis-md.md)].</span></span> <span data-ttu-id="a8a00-122">如果您將範例安裝在不同的位置，則請在程序中改用該位置。</span><span class="sxs-lookup"><span data-stu-id="a8a00-122">If you installed the samples to a different location, you should use that location instead in the procedures.</span></span>  
  
 <span data-ttu-id="a8a00-123">在下一項工作中，您會將組態加入至 DataTransfer 和 LoadXMLData 封裝中。</span><span class="sxs-lookup"><span data-stu-id="a8a00-123">In the next task, you will add configurations to the DataTransfer and LoadXMLData packages.</span></span> <span data-ttu-id="a8a00-124">所有組態都是儲存在 XML 檔案中，您必須使用系統環境變數來指定檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="a8a00-124">All configurations are stored in XML files, and you will use a system environment variable to specify the location of the files.</span></span> <span data-ttu-id="a8a00-125">在您建立組態檔之後，請將檔案加入至專案中。</span><span class="sxs-lookup"><span data-stu-id="a8a00-125">After you create the configuration files, you will add them to the project.</span></span>  
  
### <a name="to-add-packages-to-the-deployment-tutorial-project"></a><span data-ttu-id="a8a00-126">若要將封裝加入至部署教學課程專案中</span><span class="sxs-lookup"><span data-stu-id="a8a00-126">To add packages to the Deployment Tutorial project</span></span>  
  
1.  <span data-ttu-id="a8a00-127">如果 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 尚未開啟，請按一下 [開始]  ，依序指向 [所有程式]  和 [Microsoft SQL Server]  ，然後按一下 [SQL Server Data Tools]  。</span><span class="sxs-lookup"><span data-stu-id="a8a00-127">If [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="a8a00-128">在 [檔案]  功能表上，依序按一下 [開啟]  、[專案/方案]  和 [部署教學課程]  資料夾，然後按一下 [開啟]  ，再按兩下 [Deployment Tutorial.sln]  。</span><span class="sxs-lookup"><span data-stu-id="a8a00-128">On the **File** menu, click **Open**, click **Project/Solution**, click the **Deployment Tutorial** folder and click **Open**, and then double-click **Deployment Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="a8a00-129">在方案總管中，以滑鼠右鍵按一下 [部署教學課程]，按一下 [加入]  ，然後按一下 [現有的封裝]  。</span><span class="sxs-lookup"><span data-stu-id="a8a00-129">In Solution Explorer, right-click Deployment Tutorial, click **Add**, and then click **Existing Package**.</span></span>  
  
4.  <span data-ttu-id="a8a00-130">在 [加入現有封裝的複本]  對話方塊的 [封裝位置]  中，選取 [檔案系統]  。</span><span class="sxs-lookup"><span data-stu-id="a8a00-130">In the **Add Copy of Existing Package** dialog box, in **Package location**, select **File System**.</span></span>  
  
5.  <span data-ttu-id="a8a00-131">按一下瀏覽 **(…)** 按鈕，巡覽至 C:\Program Files\Microsoft SQL Server\100\Samples\Integration ServicesTutorial\Deploying Packages\Completed Packages，選取 [DataTransfer.dtsx]  ，然後按一下 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="a8a00-131">Click the browse **(...)** button, navigate to C:\Program Files\Microsoft SQL Server\100\Samples\Integration ServicesTutorial\Deploying Packages\Completed Packages, select **DataTransfer.dtsx**, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="a8a00-132">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="a8a00-132">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="a8a00-133">重複步驟 3 到 6，這次請加入 LoadXMLData.dtsx，您可以在 C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages 中找到此檔案。</span><span class="sxs-lookup"><span data-stu-id="a8a00-133">Repeat steps 3 - 6, and this time add LoadXMLData.dtsx, which is found in C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages.</span></span>  
  
### <a name="to-add-ancillary-files-to-the-deployment-tutorial-project"></a><span data-ttu-id="a8a00-134">若要將輔助檔案加入至部署教學課程專案中</span><span class="sxs-lookup"><span data-stu-id="a8a00-134">To add ancillary files to the Deployment Tutorial project</span></span>  
  
1.  <span data-ttu-id="a8a00-135">在方案總管中，以滑鼠右鍵按一下 [部署教學課程]，按一下 [加入]  ，然後按一下 [現有項目]  。</span><span class="sxs-lookup"><span data-stu-id="a8a00-135">In Solution Explorer, right-click Deployment Tutorial, click **Add**, and then click **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="a8a00-136">在 [加入現有項目 - 部署教學課程]  對話方塊中，巡覽至 C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\Sample Data，選取 orders.xml、orders.xsd 和 NewCustomers.txt，然後按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="a8a00-136">In the **Add Existing Item - Deployment Tutorial** dialog box, navigate to C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\Sample Data, select orders.xml, orders.xsd, and NewCustomers.txt, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="a8a00-137">在 [加入現有項目 - 部署教學課程]  對話方塊中，巡覽至 C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\\，選取 Readme.txt，然後按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="a8a00-137">In the **Add Existing Item - Deployment Tutorial** dialog box, navigate to C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\\, select Readme.txt and click **Add**.</span></span>  
  
4.  <span data-ttu-id="a8a00-138">按一下 [檔案] 功能表上的 [全部儲存]  。</span><span class="sxs-lookup"><span data-stu-id="a8a00-138">On the File menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a8a00-139">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="a8a00-139">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a8a00-140">步驟 4：新增套件設定</span><span class="sxs-lookup"><span data-stu-id="a8a00-140">Step 4: Adding Package Configurations</span></span>](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
<span data-ttu-id="a8a00-141">![Integration Services 圖示 (小型) ](media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="a8a00-141">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a8a00-142">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="a8a00-142">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a8a00-143">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="a8a00-143">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a8a00-144">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="a8a00-144">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
