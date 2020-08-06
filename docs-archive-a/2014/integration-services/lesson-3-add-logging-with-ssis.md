---
title: 第3課：加入記錄 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58fcc29759f19ad215a76a1b9ed9bf313b4c869c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595181"
---
# <a name="lesson-3-adding-logging"></a><span data-ttu-id="de970-102">第 3 課：新增記錄</span><span class="sxs-lookup"><span data-stu-id="de970-102">Lesson 3: Adding Logging</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="de970-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包含的記錄功能，可讓您藉由提供工作和容器事件的追蹤來對套件執行進行疑難排解和監視。</span><span class="sxs-lookup"><span data-stu-id="de970-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] includes logging features that let you troubleshoot and monitor package execution by providing a trace of task and container events.</span></span> <span data-ttu-id="de970-104">記錄功能很有彈性，可在封裝層級或在封裝內的個別工作和容器上啟用。</span><span class="sxs-lookup"><span data-stu-id="de970-104">The logging features are flexible, and can be enabled at the package level or on individual tasks and containers within the package.</span></span> <span data-ttu-id="de970-105">您可以選取要記錄的事件，以及針對單一封裝建立多個記錄。</span><span class="sxs-lookup"><span data-stu-id="de970-105">You can select which events you want to log, and create multiple logs against a single package.</span></span>  
  
 <span data-ttu-id="de970-106">記錄是由記錄提供者提供。</span><span class="sxs-lookup"><span data-stu-id="de970-106">Logging is provided by a log provider.</span></span> <span data-ttu-id="de970-107">每一個記錄提供者都可將記錄資訊寫入至不同格式和目的地類型。</span><span class="sxs-lookup"><span data-stu-id="de970-107">Each log provider can write logging information to different formats and destination types.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="de970-108">提供下列記錄提供者：</span><span class="sxs-lookup"><span data-stu-id="de970-108">provides the following log providers:</span></span>  
  
-   <span data-ttu-id="de970-109">文字檔</span><span class="sxs-lookup"><span data-stu-id="de970-109">Text file</span></span>  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   <span data-ttu-id="de970-110">Windows 事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="de970-110">Windows Event log</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   <span data-ttu-id="de970-111">XML 檔</span><span class="sxs-lookup"><span data-stu-id="de970-111">XML file</span></span>  
  
 <span data-ttu-id="de970-112">在這一課，您將建立在[第2課：新增迴圈](lesson-2-adding-looping-with-ssis.md)中建立的封裝複本。</span><span class="sxs-lookup"><span data-stu-id="de970-112">In this lesson, you will create a copy of the package that you created in [Lesson 2: Adding Looping](lesson-2-adding-looping-with-ssis.md).</span></span> <span data-ttu-id="de970-113">利用這個新的封裝，您可以加入和設定記錄，在封裝執行期間監視特定事件。</span><span class="sxs-lookup"><span data-stu-id="de970-113">Working with this new package, you will then add and configure logging to monitor specific events during package execution.</span></span> <span data-ttu-id="de970-114">如果您尚未完成前面任何一課，您也可以複製此教學課程所包含之已完成的第 2 課封裝。</span><span class="sxs-lookup"><span data-stu-id="de970-114">If you have not completed any of the previous lessons, you can also copy the completed Lesson 2 package that is included with the tutorial.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="de970-115">這個教學課程需要 **AdventureWorksDW2012** 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="de970-115">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="de970-116">如需有關如何安裝和部署**AdventureWorksDW2012**的詳細資訊，請[Reporting Services GitHub 上的產品範例](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)。</span><span class="sxs-lookup"><span data-stu-id="de970-116">For more information about how to install and deploy **AdventureWorksDW2012**, [Reporting Services Product Samples on GitHub](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="de970-117">課程工作</span><span class="sxs-lookup"><span data-stu-id="de970-117">Lesson Tasks</span></span>  
 <span data-ttu-id="de970-118">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="de970-118">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="de970-119">步驟 1:複製第 2 課的封裝</span><span class="sxs-lookup"><span data-stu-id="de970-119">Step 1: Copying the Lesson 2 Package</span></span>](lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [<span data-ttu-id="de970-120">步驟 2:新增和設定記錄</span><span class="sxs-lookup"><span data-stu-id="de970-120">Step 2: Adding and Configuring Logging</span></span>](lesson-3-2-adding-and-configuring-logging.md)  
  
-   [<span data-ttu-id="de970-121">步驟 3：測試第 3 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="de970-121">Step 3: Testing the Lesson 3 Tutorial Package</span></span>](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="de970-122">開始課程</span><span class="sxs-lookup"><span data-stu-id="de970-122">Start the Lesson</span></span>  
 [<span data-ttu-id="de970-123">步驟 1:複製第 2 課的封裝</span><span class="sxs-lookup"><span data-stu-id="de970-123">Step 1: Copying the Lesson 2 Package</span></span>](lesson-3-1-copying-the-lesson-2-package.md)  
  
  
