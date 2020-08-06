---
title: 第2課：建立部署配套 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab17289d-c3d4-4a5e-b7f5-4fea8ae21707
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 927bcd393e4b54e92971c197d93dcc1e2804dcd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597906"
---
# <a name="lesson-2-creating-the-deployment-bundle"></a><span data-ttu-id="15cf1-102">第 2 課：建立部署套件組合</span><span class="sxs-lookup"><span data-stu-id="15cf1-102">Lesson 2: Creating the Deployment Bundle</span></span>
  <span data-ttu-id="15cf1-103">在 [第 1 課：準備建立部署配套](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)中，您建立了名稱為「部署教學課程」的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案、在專案中加入了套件和支援檔案，並且已在套件中實作組態。</span><span class="sxs-lookup"><span data-stu-id="15cf1-103">In [Lesson 1: Preparing to Create the Deployment Bundle](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md), you created the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project named Deployment Tutorial, added the packages and supporting files to the project, and implemented configurations in packages.</span></span>  
  
 <span data-ttu-id="15cf1-104">在這一課中，您會建立部署配套，這是一個資料夾，其中包含您必須在其他電腦上安裝封裝的項目。</span><span class="sxs-lookup"><span data-stu-id="15cf1-104">In this lesson, you will create the deployment bundle, which is a folder that contains the items that you need to install packages on another computer.</span></span> <span data-ttu-id="15cf1-105">部署配套將會包含「部署教學課程」專案中的部署資訊清單、封裝的副本，以及支援檔案的副本。</span><span class="sxs-lookup"><span data-stu-id="15cf1-105">The deployment bundle will include a deployment manifest, copies of the packages, and copies of the supporting files from the Deployment Tutorial project.</span></span> <span data-ttu-id="15cf1-106">部署資訊清單會列出部署配套中的封裝、其他檔案和組態。</span><span class="sxs-lookup"><span data-stu-id="15cf1-106">The deployment manifest lists the packages, miscellaneous files, and configurations in the deployment bundle.</span></span>  
  
 <span data-ttu-id="15cf1-107">此外，您還會確認部署配套中的檔案清單，並檢查資訊清單的內容。</span><span class="sxs-lookup"><span data-stu-id="15cf1-107">You will also verify the file list in the deployment bundle and examine the contents of the manifest.</span></span>  
  
 <span data-ttu-id="15cf1-108">**完成本課程的估計時間** ：30 分鐘</span><span class="sxs-lookup"><span data-stu-id="15cf1-108">**Estimated time to complete this lesson:** 30 minutes</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="15cf1-109">課程工作</span><span class="sxs-lookup"><span data-stu-id="15cf1-109">Lesson Tasks</span></span>  
 <span data-ttu-id="15cf1-110">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="15cf1-110">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="15cf1-111">步驟 1：建置部署公用程式</span><span class="sxs-lookup"><span data-stu-id="15cf1-111">Step 1: Building the Deployment Utility</span></span>](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
-   [<span data-ttu-id="15cf1-112">步驟 2：確認部署配套</span><span class="sxs-lookup"><span data-stu-id="15cf1-112">Step 2: Verifying the Deployment Bundle</span></span>](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="15cf1-113">開始課程</span><span class="sxs-lookup"><span data-stu-id="15cf1-113">Start the Lesson</span></span>  
 [<span data-ttu-id="15cf1-114">步驟 1：建置部署公用程式</span><span class="sxs-lookup"><span data-stu-id="15cf1-114">Step 1: Building the Deployment Utility</span></span>](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
<span data-ttu-id="15cf1-115">![Integration Services 圖示 (小型) ](media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="15cf1-115">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="15cf1-116">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="15cf1-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="15cf1-117">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="15cf1-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="15cf1-118">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="15cf1-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
