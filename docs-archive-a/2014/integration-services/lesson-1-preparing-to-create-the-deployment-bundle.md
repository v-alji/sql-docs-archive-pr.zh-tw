---
title: 第 1 課：準備建立部署配套 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6fe283c-9856-4ba1-a497-e3912424fd18
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0deda2a81ddd86d4e40c1c546232b8056264508a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596120"
---
# <a name="lesson-1-preparing-to-create-the-deployment-bundle"></a><span data-ttu-id="d8c8e-102">第 1 課：準備建立部署配套</span><span class="sxs-lookup"><span data-stu-id="d8c8e-102">Lesson 1: Preparing to Create the Deployment Bundle</span></span>
  <span data-ttu-id="d8c8e-103">在這一課中，您會建立支援教學課程的工作資料夾和環境變數、建立 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案、在專案中加入數個封裝及其支援檔案，以及在封裝中實作組態。</span><span class="sxs-lookup"><span data-stu-id="d8c8e-103">In this lesson, you will create the working folders and environment variables that support the tutorial, create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, add several packages and their supporting files to the project, and implement configurations in packages.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="d8c8e-104">會依照個別專案部署套件，因此，在建立部署配套的第一個步驟中，您必須將所有的套件和套件相依性全部收集到一個 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案中。</span><span class="sxs-lookup"><span data-stu-id="d8c8e-104">deploys packages on a project basis; therefore, as the first step in creating the deployment bundle, you must collect all the packages and package dependencies into one [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="d8c8e-105">在部署的封裝中納入其他資訊，通常會很有用，例如，您也可以在專案中加入讀我檔案，以提供此封裝群組的基本文件集。</span><span class="sxs-lookup"><span data-stu-id="d8c8e-105">Frequently it is useful to include other information with the deployed packages: for example you will also add to the project a Readme file that provides basic documentation for this group of packages.</span></span>  
  
 <span data-ttu-id="d8c8e-106">在加入封裝和檔案之後，您還會在尚未使用組態的封裝中加入組態。</span><span class="sxs-lookup"><span data-stu-id="d8c8e-106">After you have added the packages and files, you will add configurations to packages that do not already use configurations.</span></span> <span data-ttu-id="d8c8e-107">組態會在執行階段更新封裝和封裝物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="d8c8e-107">The configurations update properties of packages and package objects at run time.</span></span> <span data-ttu-id="d8c8e-108">在稍後的課程中，您將會在封裝部署期間修改這些組態的值，以便在部署的目標環境中支援封裝。</span><span class="sxs-lookup"><span data-stu-id="d8c8e-108">In a later lesson, you will modify the values of these configurations during package deployment to support the packages in the deployed-to environment.</span></span>  
  
 <span data-ttu-id="d8c8e-109">在加入組態之後，您應該在 [ [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] (用來建立 ETL 封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 圖形化工具) 中開啟封裝，並且檢查封裝和封裝元素的屬性以及封裝組態，以便能更加了解部署所需解決的問題。</span><span class="sxs-lookup"><span data-stu-id="d8c8e-109">After you have added the configurations, you should open the packages in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] graphical tool for building ETL packages, and examine the properties of packages and package elements as well as the package configurations to better understand the issues that the deployment needs to address.</span></span> <span data-ttu-id="d8c8e-110">例如，由於其中一個封裝會從文字檔擷取資料，因此您必須先更新資料檔的位置，部署的封裝才能順利執行。</span><span class="sxs-lookup"><span data-stu-id="d8c8e-110">For example, one of the packages extracts data from text files, so the location of the data files must be updated before the deployed packages will run successfully.</span></span>  
  
 <span data-ttu-id="d8c8e-111">**完成本課程的估計時間** ：1 小時</span><span class="sxs-lookup"><span data-stu-id="d8c8e-111">**Estimated time to complete this lesson:** 1 hour</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="d8c8e-112">課程工作</span><span class="sxs-lookup"><span data-stu-id="d8c8e-112">Lesson Tasks</span></span>  
 <span data-ttu-id="d8c8e-113">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="d8c8e-113">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="d8c8e-114">步驟 1：建立工作資料夾和環境變數</span><span class="sxs-lookup"><span data-stu-id="d8c8e-114">Step 1: Creating Working Folders and Environment Variables</span></span>](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
-   [<span data-ttu-id="d8c8e-115">步驟 2：建立部署專案</span><span class="sxs-lookup"><span data-stu-id="d8c8e-115">Step 2: Creating the Deployment Project</span></span>](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
-   [<span data-ttu-id="d8c8e-116">步驟 3：新增套件和其他檔案</span><span class="sxs-lookup"><span data-stu-id="d8c8e-116">Step 3: Adding Packages and Other Files</span></span>](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
-   [<span data-ttu-id="d8c8e-117">步驟 4：新增套件設定</span><span class="sxs-lookup"><span data-stu-id="d8c8e-117">Step 4: Adding Package Configurations</span></span>](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
-   [<span data-ttu-id="d8c8e-118">步驟 5：測試更新的套件</span><span class="sxs-lookup"><span data-stu-id="d8c8e-118">Step 5: Testing the Updated Packages</span></span>](../integration-services/lesson-1-5-testing-the-updated-packages.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="d8c8e-119">開始課程</span><span class="sxs-lookup"><span data-stu-id="d8c8e-119">Start the Lesson</span></span>  
 [<span data-ttu-id="d8c8e-120">步驟 1：建立工作資料夾和環境變數</span><span class="sxs-lookup"><span data-stu-id="d8c8e-120">Step 1: Creating Working Folders and Environment Variables</span></span>](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
<span data-ttu-id="d8c8e-121">![Integration Services 圖示 (小型) ](media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="d8c8e-121">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d8c8e-122">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="d8c8e-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d8c8e-123">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="d8c8e-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d8c8e-124">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="d8c8e-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
