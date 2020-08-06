---
title: 步驟 9：測試第 1 課的教學課程套件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dff1132489c1683430b1003e88f5037664b11983
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596121"
---
# <a name="step-9-testing-the-lesson-1-tutorial-package"></a><span data-ttu-id="ebb93-102">步驟 9：測試第 1 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="ebb93-102">Step 9: Testing the Lesson 1 Tutorial Package</span></span>
  <span data-ttu-id="ebb93-103">在這一課，您完成了下列工作：</span><span class="sxs-lookup"><span data-stu-id="ebb93-103">In this lesson, you have done the following tasks:</span></span>  
  
-   <span data-ttu-id="ebb93-104">建立新的 [!INCLUDE[ssIS](../includes/ssis-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="ebb93-104">Created a new [!INCLUDE[ssIS](../includes/ssis-md.md)] project.</span></span>  
  
-   <span data-ttu-id="ebb93-105">設定封裝要連接到來源和目的地資料時所需的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ebb93-105">Configured the connection managers that the package needs to connect to the source and destination data.</span></span>  
  
-   <span data-ttu-id="ebb93-106">加入資料流程來取得一般檔案來源的資料，對資料執行必要的查閱轉換，以及設定目的地的資料。</span><span class="sxs-lookup"><span data-stu-id="ebb93-106">Added a data flow that takes the data from a flat file source, performs the necessary Lookup transformations on the data, and configures the data for the destination.</span></span>  
  
 <span data-ttu-id="ebb93-107">現在已完成封裝！</span><span class="sxs-lookup"><span data-stu-id="ebb93-107">Your package is now complete!</span></span> <span data-ttu-id="ebb93-108">測試封裝的時間到了。</span><span class="sxs-lookup"><span data-stu-id="ebb93-108">It is time to test your package.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="ebb93-109">檢查封裝配置</span><span class="sxs-lookup"><span data-stu-id="ebb93-109">Checking the Package Layout</span></span>  
 <span data-ttu-id="ebb93-110">在測試封裝之前，您應該確認第 1 課封裝中的控制流程和資料流程是否包含下圖所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="ebb93-110">Before you test the package you should verify that the control and data flows in the Lesson 1 package contain the objects shown in the following diagrams.</span></span>  
  
 <span data-ttu-id="ebb93-111">**控制流程**</span><span class="sxs-lookup"><span data-stu-id="ebb93-111">**Control Flow**</span></span>  
  
 <span data-ttu-id="ebb93-112">![套件中的控制流程](../../2014/tutorials/media/task9lesson1control.gif "套件中的控制流程")</span><span class="sxs-lookup"><span data-stu-id="ebb93-112">![Control flow in package](../../2014/tutorials/media/task9lesson1control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="ebb93-113">**資料流程**</span><span class="sxs-lookup"><span data-stu-id="ebb93-113">**Data Flow**</span></span>  
  
 <span data-ttu-id="ebb93-114">![套件中的資料流程](../../2014/tutorials/media/task9lesson1data.gif "套件中的資料流程")</span><span class="sxs-lookup"><span data-stu-id="ebb93-114">![Data flow in package](../../2014/tutorials/media/task9lesson1data.gif "Data flow in package")</span></span>  
  
### <a name="to-run-the-lesson-1-tutorial-package"></a><span data-ttu-id="ebb93-115">若要執行第 1 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="ebb93-115">To run the Lesson 1 tutorial package</span></span>  
  
1.  <span data-ttu-id="ebb93-116">在 [偵錯] 功能表上，按一下 [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="ebb93-116">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="ebb93-117">封裝隨即執行，讓 1097 個資料列順利加入 **AdventureWorksDW2012** 的 **FactCurrency**事實資料表中。</span><span class="sxs-lookup"><span data-stu-id="ebb93-117">The package will run, resulting in 1097 rows successfully added into the **FactCurrency** fact table in **AdventureWorksDW2012**.</span></span>  
  
2.  <span data-ttu-id="ebb93-118">在封裝完成執行之後，在 **[偵錯]** 功能表上，按一下 **[停止偵錯]**。</span><span class="sxs-lookup"><span data-stu-id="ebb93-118">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="ebb93-119">下一課</span><span class="sxs-lookup"><span data-stu-id="ebb93-119">Next Lesson</span></span>  
 [<span data-ttu-id="ebb93-120">第 2 課：新增迴圈</span><span class="sxs-lookup"><span data-stu-id="ebb93-120">Lesson 2: Adding Looping</span></span>](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a><span data-ttu-id="ebb93-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebb93-121">See Also</span></span>  
 [<span data-ttu-id="ebb93-122">執行專案和套件</span><span class="sxs-lookup"><span data-stu-id="ebb93-122">Execution of Projects and Packages</span></span>](packages/run-integration-services-ssis-packages.md)  
  
  
