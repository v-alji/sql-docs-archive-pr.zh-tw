---
title: 步驟 1：建立工作資料夾與環境變數 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 45091ba2-ea3d-4399-9814-489d812b42cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 63308d406e230538e5ca8b90dbb55bb802759bd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596149"
---
# <a name="step-1-creating-working-folders-and-environment-variables"></a><span data-ttu-id="c12c5-102">步驟 1:建立工作資料夾和環境變數</span><span class="sxs-lookup"><span data-stu-id="c12c5-102">Step 1: Creating Working Folders and Environment Variables</span></span>
  <span data-ttu-id="c12c5-103">在這項工作中，您將建立工作資料夾 (C:\DeploymentTutorial) 和新的系統環境變數 (`DataTransfer` 與 `LoadXMLData`)，並稍後在教學課程工作中使用。</span><span class="sxs-lookup"><span data-stu-id="c12c5-103">In this task, you will create the working folder (C:\DeploymentTutorial) and the new system environment variables (`DataTransfer` and `LoadXMLData`) that you will use in later tutorial tasks.</span></span>  
  
 <span data-ttu-id="c12c5-104">工作資料夾位於 C 磁碟的根目錄。</span><span class="sxs-lookup"><span data-stu-id="c12c5-104">The working folder is at the root of the C drive.</span></span> <span data-ttu-id="c12c5-105">如果必須使用其他磁碟或位置，這是可行的。</span><span class="sxs-lookup"><span data-stu-id="c12c5-105">If you must use a different drive or location, you can do that.</span></span> <span data-ttu-id="c12c5-106">不過必須記下這個位置，只要教學課程提到 DeploymentTutorial 工作資料夾時就會用到這個位置。</span><span class="sxs-lookup"><span data-stu-id="c12c5-106">However, you need to note this location and then use it wherever the tutorial refers to the location of the DeploymentTutorial working folder.</span></span>  
  
 <span data-ttu-id="c12c5-107">在後面的課程中，您會將儲存在檔案系統中的套件部署到 msdb[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫中的 sysssispackages 資料表。</span><span class="sxs-lookup"><span data-stu-id="c12c5-107">In a later lesson, you will deploy packages that are saved to the file system to the sysssispackages table in the msdb[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="c12c5-108">理想的狀況是將 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝部署到其他電腦。</span><span class="sxs-lookup"><span data-stu-id="c12c5-108">Ideally you will deploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to a different computer.</span></span> <span data-ttu-id="c12c5-109">如果不可行，但透過將封裝部署到本機電腦上 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體，您仍可從進行本課中學到許多知識。</span><span class="sxs-lookup"><span data-stu-id="c12c5-109">If that is not possible, you can still learn a lot from doing this tutorial by deploying the packages to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that is on the local computer.</span></span> <span data-ttu-id="c12c5-110">本機電腦和目的電腦中使用的環境變數有著相同的名稱，但儲存在變數中的值則不同。</span><span class="sxs-lookup"><span data-stu-id="c12c5-110">The environment variables that are used on the local and destination computers have the same variable names, but different values are stored in the variables.</span></span> <span data-ttu-id="c12c5-111">例如，本機電腦上環境變數 `DataTransfer` 的值會參考 C:\DeploymentTutorial 資料夾，而目標電腦上環境變數 `DataTransfer` 卻會參考 C:\DeploymentTutorialInstall 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c12c5-111">For example, on the local computer, the value of the environment variable `DataTransfer` references the C:\DeploymentTutorial folder, whereas on the target computer the environment variable `DataTransfer` references the C:\DeploymentTutorialInstall folder.</span></span>  
  
 <span data-ttu-id="c12c5-112">如果您打算部署到本機電腦，必須只建立一組環境變數，但在進行本機部署之前必須先將環境變數的值更新為適合的值。</span><span class="sxs-lookup"><span data-stu-id="c12c5-112">If you plan to deploy to the local computer, you need to create only one set of environment variables; however, you will need to update the value of the environment variables to an appropriate value before you do the local deployment.</span></span>  
  
 <span data-ttu-id="c12c5-113">如果您打算將封裝部署到其他電腦，必須建立兩組環境變數：一組用於本機電腦，另一組用於目的電腦。</span><span class="sxs-lookup"><span data-stu-id="c12c5-113">If you plan to deploy the packages to a different computer, you must create two sets of environment variables: one set for the local computer, and one set for the destination computer.</span></span> <span data-ttu-id="c12c5-114">您現在就可以先為來源電腦建立一個變數，而稍後再為目的電腦建立變數，但必須在目的電腦上有可用的資料夾和環境變數，才能安裝封裝。</span><span class="sxs-lookup"><span data-stu-id="c12c5-114">You can create only the variables for the source computer now, and create the variables for the destination computer later, but you must have both the folder and environment variables available on the destination computer before you can install the packages on that computer.</span></span>  
  
### <a name="to-create-the-local-working-folder"></a><span data-ttu-id="c12c5-115">建立本機工作資料夾</span><span class="sxs-lookup"><span data-stu-id="c12c5-115">To create the local working folder</span></span>  
  
1.  <span data-ttu-id="c12c5-116">以滑鼠右鍵按一下 [開始] 功能表，然後按一下 [檔案總管]。</span><span class="sxs-lookup"><span data-stu-id="c12c5-116">Right-click the Start menu, and click Explore.</span></span>  
  
2.  <span data-ttu-id="c12c5-117">按一下 [本機磁碟 (C:)]  。</span><span class="sxs-lookup"><span data-stu-id="c12c5-117">Click **Local Disk (C:)**.</span></span>  
  
3.  <span data-ttu-id="c12c5-118">在 [檔案]  功能表上，指向 [新增]  ，然後按一下 [資料夾]  。</span><span class="sxs-lookup"><span data-stu-id="c12c5-118">On the **File** menu, point to **New**, and then click **Folder**.</span></span>  
  
4.  <span data-ttu-id="c12c5-119">將新資料夾重新命名為 `DeploymentTutorial` 。</span><span class="sxs-lookup"><span data-stu-id="c12c5-119">Rename New Folder to `DeploymentTutorial`.</span></span>  
  
### <a name="to-create-local-environment-variables"></a><span data-ttu-id="c12c5-120">建立基本環境變數</span><span class="sxs-lookup"><span data-stu-id="c12c5-120">To create local environment variables</span></span>  
  
1.  <span data-ttu-id="c12c5-121">在 **[開始]** 功能表上，按一下 **[控制台]** 。</span><span class="sxs-lookup"><span data-stu-id="c12c5-121">On the **Start** menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="c12c5-122">在 [控制台] 中，按兩下 [系統]  。</span><span class="sxs-lookup"><span data-stu-id="c12c5-122">In Control Panel, double-click **System**.</span></span>  
  
3.  <span data-ttu-id="c12c5-123">在 [系統內容]  對話方塊中，按一下 [進階]  索引標籤，然後按一下 [環境變數]  。</span><span class="sxs-lookup"><span data-stu-id="c12c5-123">In the **System Properties** dialog box, click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="c12c5-124">在 [環境變數]  對話方塊的 [系統變數]  框架中，按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="c12c5-124">In the **Environment Variables** dialog box, in the **System variables** frame, click **New**.</span></span>  
  
5.  <span data-ttu-id="c12c5-125">在 [**新增系統變數**] 對話方塊中，于 [變數 `DataTransfer` **名稱**] 方塊和 `C:\DeploymentTutorial\datatransferconfig.dtsconfig` [**變數值**] 方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="c12c5-125">In the **New System Variable** dialog box, type `DataTransfer` in the **Variable name** box, and `C:\DeploymentTutorial\datatransferconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
6.  <span data-ttu-id="c12c5-126">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="c12c5-126">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="c12c5-127">再次按一下 [**新增**]，然後在 `LoadXMLData` [變數**名稱**] 方塊和 `C:\DeploymentTutorial\loadxmldataconfig.dtsconfig` [**變數值**] 方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="c12c5-127">Click **New** again, and type `LoadXMLData` in the **Variable name** box, and `C:\DeploymentTutorial\loadxmldataconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
8.  <span data-ttu-id="c12c5-128">按一下 [確定]  ，結束 [環境變數]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c12c5-128">Click **OK** to exit the **Environment Variables** dialog box.</span></span>  
  
9. <span data-ttu-id="c12c5-129">按一下 [確定]  ，結束 [系統內容]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c12c5-129">Click **OK** to exit the **System Properties** dialog box.\</span></span>  
  
10. <span data-ttu-id="c12c5-130">選擇性重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="c12c5-130">Optionally, restart your computer.</span></span> <span data-ttu-id="c12c5-131">如果不重新啟動電腦，新的變數名稱不會在「封裝組態精靈」中顯示，但您仍然可以使用這個名稱。</span><span class="sxs-lookup"><span data-stu-id="c12c5-131">If you do not restart the computer, the name of the new variable will not be displayed in the Package Configuration Wizard, but you can still use it.</span></span>  
  
### <a name="to-create-destination-environment-variables"></a><span data-ttu-id="c12c5-132">建立目的環境變數</span><span class="sxs-lookup"><span data-stu-id="c12c5-132">To create destination environment variables</span></span>  
  
1.  <span data-ttu-id="c12c5-133">在 **[開始]** 功能表上，按一下 **[控制台]** 。</span><span class="sxs-lookup"><span data-stu-id="c12c5-133">On the **Start** menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="c12c5-134">在 [控制台] 中，按兩下 [系統]  。</span><span class="sxs-lookup"><span data-stu-id="c12c5-134">In Control Panel, double-click **System**.</span></span>  
  
3.  <span data-ttu-id="c12c5-135">在 [系統內容]  對話方塊中，按一下 [進階]  索引標籤，然後按一下 [環境變數]  。</span><span class="sxs-lookup"><span data-stu-id="c12c5-135">In the **System Properties** dialog box, click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="c12c5-136">在 [環境變數]  對話方塊的 [系統變數]  框架中，按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="c12c5-136">In the **Environment Variables** dialog box, in **System variables** frame, click **New**.</span></span>  
  
5.  <span data-ttu-id="c12c5-137">在 [**新增系統變數**] 對話方塊中，于 [變數 `DataTransfer` **名稱**] 方塊和 `C:\DeploymentTutorialInstall\datatransferconfig.dtsconfig` [**變數值**] 方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="c12c5-137">In the **New System Variables** dialog box, type `DataTransfer` in the **Variable name** box, and `C:\DeploymentTutorialInstall\datatransferconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
6.  <span data-ttu-id="c12c5-138">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="c12c5-138">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="c12c5-139">再次按一下 [**新增**]，然後在 `LoadXMLData` [變數**名稱**] 方塊和 `C:\DeploymentTutorialInstall\loadxmldataconfig.dtsconfig` [**變數值**] 方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="c12c5-139">Click **New** again, and type `LoadXMLData` in the **Variable name** box, and `C:\DeploymentTutorialInstall\loadxmldataconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
8.  <span data-ttu-id="c12c5-140">按一下 [確定]  ，結束 [環境變數]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c12c5-140">Click **OK** to exit the **Environment Variables** dialog box.</span></span>  
  
9. <span data-ttu-id="c12c5-141">按一下 [確定]  ，結束 [系統內容]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c12c5-141">Click **OK** to exit the **System Properties** dialog box.\</span></span>  
  
10. <span data-ttu-id="c12c5-142">選擇性重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="c12c5-142">Optionally, restart your computer.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c12c5-143">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="c12c5-143">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c12c5-144">步驟 2：建立部署專案</span><span class="sxs-lookup"><span data-stu-id="c12c5-144">Step 2: Creating the Deployment Project</span></span>](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
<span data-ttu-id="c12c5-145">![Integration Services 圖示 (小型) ](media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="c12c5-145">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c12c5-146">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="c12c5-146">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c12c5-147">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="c12c5-147">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c12c5-148">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="c12c5-148">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
