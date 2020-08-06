---
title: 步驟 1：複製部署配套 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6ef1e56-d278-4a24-afd3-68d8e0595cbb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 326a85a4d04fc22382457b4e2e919f81096ce989
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606419"
---
# <a name="step-1-copying-the-deployment-bundle"></a><span data-ttu-id="1897a-102">步驟 1:複製部署套件組合</span><span class="sxs-lookup"><span data-stu-id="1897a-102">Step 1: Copying the Deployment Bundle</span></span>
  <span data-ttu-id="1897a-103">在這項工作中，您會將部署配套複製到目的地電腦。</span><span class="sxs-lookup"><span data-stu-id="1897a-103">In this task, you will copy the deployment bundle to the destination computer.</span></span>  
  
 <span data-ttu-id="1897a-104">要將部署配套複製到目的地電腦，最簡單的方式就是先在目的地電腦上建立一個公用共用區，再將磁碟機對應至此公用共用區，然後將部署配套複製到此共用區。</span><span class="sxs-lookup"><span data-stu-id="1897a-104">The easiest way to copy the deployment bundle to the destination computer is to first create a public share on the destination computer, map a drive to the public share, and then copy the deployment bundle to the share.</span></span> <span data-ttu-id="1897a-105">如果不知道如何建立和設定公用資料夾或對應磁碟機，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="1897a-105">If you do not know how to create and configure public folders or map drives, see the Windows documentation.</span></span>  
  
### <a name="to-copy-the-deployment-bundle"></a><span data-ttu-id="1897a-106">若要複製部署配套</span><span class="sxs-lookup"><span data-stu-id="1897a-106">To copy the deployment bundle</span></span>  
  
1.  <span data-ttu-id="1897a-107">在電腦上找到部署配套。</span><span class="sxs-lookup"><span data-stu-id="1897a-107">Locate the deployment bundle on your computer.</span></span>  
  
     <span data-ttu-id="1897a-108">如果使用的是預設位置，則部署配套就是 [部署教學課程] 資料夾內的 Bin\Deployment 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1897a-108">If you used the default location, the deployment bundle is the Bin\Deployment folder within the Deployment Tutorial folder.</span></span>  
  
2.  <span data-ttu-id="1897a-109">以滑鼠右鍵按一下 [Deployment] 資料夾，然後按一下 [複製]  。</span><span class="sxs-lookup"><span data-stu-id="1897a-109">Right-click the Deployment folder and click **Copy**.</span></span>  
  
3.  <span data-ttu-id="1897a-110">在目標電腦上找到您要複製此資料夾的公用共用，然後按一下 [貼上]  。</span><span class="sxs-lookup"><span data-stu-id="1897a-110">Locate the public share to which you want to copy the folder on the target computer and click **Paste**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="1897a-111">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="1897a-111">Next Task in Lesson</span></span>  
 [<span data-ttu-id="1897a-112">步驟 2：執行套件安裝精靈</span><span class="sxs-lookup"><span data-stu-id="1897a-112">Step 2: Running the Package Installation Wizard</span></span>](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
<span data-ttu-id="1897a-113">![Integration Services 圖示 (小型) ](media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="1897a-113">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1897a-114">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="1897a-114">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1897a-115">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="1897a-115">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1897a-116">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="1897a-116">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
