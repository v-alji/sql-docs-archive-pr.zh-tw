---
title: 步驟 5：測試更新的封裝 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a075af2e030c8257d01abf5eba7d330b1cc8efe7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596129"
---
# <a name="step-5-testing-the-updated-packages"></a><span data-ttu-id="54bd2-102">步驟 5：測試更新的封裝</span><span class="sxs-lookup"><span data-stu-id="54bd2-102">Step 5: Testing the Updated Packages</span></span>
  <span data-ttu-id="54bd2-103">在進入下一課之前，請先測試封裝，因為在下一課中，您將會建立部署配套，以便在目的地電腦上用來安裝教學課程封裝。</span><span class="sxs-lookup"><span data-stu-id="54bd2-103">Before you go on to the next lesson, in which you will create the deployment bundle to use to install the tutorial packages on the destination computer, you should test the packages.</span></span> <span data-ttu-id="54bd2-104">在這項工作中，您會執行 DataTransfer.dtsx 和 LoadXMLData 封裝，這兩個封裝都已加入至「部署教學課程」專案中，並且以組態進行擴充。</span><span class="sxs-lookup"><span data-stu-id="54bd2-104">In this task, you will run the packages, DataTransfer.dtsx and LoadXMLData, that you added to the Deployment Tutorial project and then extended with configurations.</span></span>  
  
 <span data-ttu-id="54bd2-105">當封裝執行時，封裝中的每一個可執行檔在順利完成後都會變成綠色。</span><span class="sxs-lookup"><span data-stu-id="54bd2-105">When the packages run, each executable in the package becomes a green color as it completes successfully.</span></span> <span data-ttu-id="54bd2-106">當所有可執行檔都變成綠色時，就表示該封裝已順利完成。</span><span class="sxs-lookup"><span data-stu-id="54bd2-106">When all executables are green, the package has completed successfully.</span></span> <span data-ttu-id="54bd2-107">您也可以在 [進度]  索引標籤上檢視套件的執行進度。</span><span class="sxs-lookup"><span data-stu-id="54bd2-107">You can also view the package execution progress on the **Progress** tab.</span></span>  
  
 <span data-ttu-id="54bd2-108">如果封裝未能順利執行，則必須加以修正，才能進入下一課。</span><span class="sxs-lookup"><span data-stu-id="54bd2-108">If the packages do not run successfully, you must fix them before you go on to the next lesson.</span></span>  
  
### <a name="to-run-the-datatransfer-package"></a><span data-ttu-id="54bd2-109">若要執行 DataTransfer 封裝</span><span class="sxs-lookup"><span data-stu-id="54bd2-109">To run the DataTransfer package</span></span>  
  
1.  <span data-ttu-id="54bd2-110">在 [方案總管] 中，按一下 DataTransfer.dtsx。</span><span class="sxs-lookup"><span data-stu-id="54bd2-110">In Solution Explorer, click DataTransfer.dtsx.</span></span>  
  
2.  <span data-ttu-id="54bd2-111">在 **[偵錯]** 功能表上，按一下 **[開始偵錯]** 。</span><span class="sxs-lookup"><span data-stu-id="54bd2-111">On **Debug** menu, click **Start Debugging**.</span></span>  
  
3.  <span data-ttu-id="54bd2-112">在封裝完成執行之後，在 **[偵錯]** 功能表上，按一下 **[停止偵錯]** 。</span><span class="sxs-lookup"><span data-stu-id="54bd2-112">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
### <a name="to-run-the-loadxmldata-package"></a><span data-ttu-id="54bd2-113">若要執行 LoadXMLData 封裝</span><span class="sxs-lookup"><span data-stu-id="54bd2-113">To run the LoadXMLData package</span></span>  
  
1.  <span data-ttu-id="54bd2-114">在 [方案總管] 中，按一下 LoadXMLData.dtsx。</span><span class="sxs-lookup"><span data-stu-id="54bd2-114">In Solution Explorer, click LoadXMLData.dtsx.</span></span>  
  
2.  <span data-ttu-id="54bd2-115">在 **[偵錯]** 功能表上，按一下 **[開始偵錯]** 。</span><span class="sxs-lookup"><span data-stu-id="54bd2-115">On **Debug** menu, click **Start Debugging**.</span></span>  
  
3.  <span data-ttu-id="54bd2-116">在封裝完成執行之後，在 **[偵錯]** 功能表上，按一下 **[停止偵錯]** 。</span><span class="sxs-lookup"><span data-stu-id="54bd2-116">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="54bd2-117">下一課</span><span class="sxs-lookup"><span data-stu-id="54bd2-117">Next Lesson</span></span>  
 [<span data-ttu-id="54bd2-118">第 2 課：建立部署套件組合</span><span class="sxs-lookup"><span data-stu-id="54bd2-118">Lesson 2: Creating the Deployment Bundle</span></span>](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
  
<span data-ttu-id="54bd2-119">![Integration Services 圖示 (小型) ](media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="54bd2-119">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="54bd2-120">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="54bd2-120">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="54bd2-121">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="54bd2-121">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="54bd2-122">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="54bd2-122">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
