---
title: 第3課：安裝套件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 87bc4d82-39d8-424f-886f-98cf1e4bb07a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f8b58cee7bd8e16cd0ca2e726dc8e5eff2cfec5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595180"
---
# <a name="lesson-3-installing-packages"></a><span data-ttu-id="cc24f-102">第 3 課：安裝套件</span><span class="sxs-lookup"><span data-stu-id="cc24f-102">Lesson 3: Installing Packages</span></span>
  <span data-ttu-id="cc24f-103">在[第2課：建立部署](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)配套中，您建立了部署公用程式，並建立了部署配套，其中包含您必須在另一部電腦上安裝套件的專案。</span><span class="sxs-lookup"><span data-stu-id="cc24f-103">In [Lesson 2: Creating the Deployment Bundle](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md), you built a deployment utility and created the deployment bundle that contains the items that you must install packages on another computer.</span></span> <span data-ttu-id="cc24f-104">此外，您也確認了部署配套中的檔案清單，並且檢查了建立部署公用程式時所建立的資訊清單檔內容。</span><span class="sxs-lookup"><span data-stu-id="cc24f-104">You also verified the file list in the deployment bundle and examined the contents of the manifest file that was created when you built the deployment utility.</span></span>  
  
 <span data-ttu-id="cc24f-105">在這一課中，您會將部署配套複製到目的地電腦，然後執行「封裝安裝精靈」，將封裝、封裝相依性及輔助檔案安裝到該部電腦上。</span><span class="sxs-lookup"><span data-stu-id="cc24f-105">In this lesson, you will copy the deployment bundle to the destination computer and then run the Package Installation Wizard to install the packages, package dependencies, and ancillary files on that computer.</span></span> <span data-ttu-id="cc24f-106">封裝將會安裝在**msdb** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫中，而其他專案則會安裝在檔案系統中。</span><span class="sxs-lookup"><span data-stu-id="cc24f-106">The packages will be installed in the **msdb**[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database and the other items will be installed in the file system.</span></span> <span data-ttu-id="cc24f-107">完成封裝安裝之後，將會使用「執行封裝公用程式」從 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 執行封裝，以測試部署。</span><span class="sxs-lookup"><span data-stu-id="cc24f-107">After you complete the package installation, you will test the deployment by running the packages from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] using the Execute Package Utility.</span></span>  
  
 <span data-ttu-id="cc24f-108">**完成本課程的估計時間：** 30 分鐘</span><span class="sxs-lookup"><span data-stu-id="cc24f-108">**Estimated time to complete this lesson:** 30 minutes</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="cc24f-109">課程工作</span><span class="sxs-lookup"><span data-stu-id="cc24f-109">Lesson Tasks</span></span>  
 <span data-ttu-id="cc24f-110">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="cc24f-110">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="cc24f-111">步驟 1:複製部署套件組合</span><span class="sxs-lookup"><span data-stu-id="cc24f-111">Step 1: Copying the Deployment Bundle</span></span>](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
-   [<span data-ttu-id="cc24f-112">步驟 2:執行封裝安裝精靈</span><span class="sxs-lookup"><span data-stu-id="cc24f-112">Step 2: Running the Package Installation Wizard</span></span>](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
-   [<span data-ttu-id="cc24f-113">步驟 3：測試部署的封裝</span><span class="sxs-lookup"><span data-stu-id="cc24f-113">Step 3: Testing the Deployed Packages</span></span>](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="cc24f-114">開始課程</span><span class="sxs-lookup"><span data-stu-id="cc24f-114">Start the Lesson</span></span>  
 [<span data-ttu-id="cc24f-115">步驟 1:複製部署套件組合</span><span class="sxs-lookup"><span data-stu-id="cc24f-115">Step 1: Copying the Deployment Bundle</span></span>](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
<span data-ttu-id="cc24f-116">![Integration Services 圖示 (小型) ](media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="cc24f-116">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="cc24f-117">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="cc24f-117">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="cc24f-118">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="cc24f-118">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="cc24f-119">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="cc24f-119">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
