---
title: 第4課：加入錯誤流程重新導向 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5b1d1ff9abf59a6288d1b693fce5a6fb707a129b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708482"
---
# <a name="lesson-4-adding-error-flow-redirection"></a><span data-ttu-id="c7934-102">第 4 課：新增錯誤流程重新導向</span><span class="sxs-lookup"><span data-stu-id="c7934-102">Lesson 4: Adding Error Flow Redirection</span></span>
  <span data-ttu-id="c7934-103">為了處理轉換程式中可能發生的錯誤， [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 讓您能夠決定每個元件和每個資料行如何處理無法轉換的資料。</span><span class="sxs-lookup"><span data-stu-id="c7934-103">To handle errors that may occur in the transformation process, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] gives you the ability to decide on a per component and per column basis how to handle data that cannot be transformed.</span></span> <span data-ttu-id="c7934-104">您可以選擇忽略特定資料行的失敗、將整個失敗的資料列重新導向，或僅使該元件失敗。</span><span class="sxs-lookup"><span data-stu-id="c7934-104">You can choose to ignore a failure in certain columns, redirect the entire failed row, or just fail the component.</span></span> <span data-ttu-id="c7934-105">依預設， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的所有元件都設定為發生錯誤時失敗。</span><span class="sxs-lookup"><span data-stu-id="c7934-105">By default, all components in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] are configured to fail when errors occur.</span></span> <span data-ttu-id="c7934-106">使元件失敗會造成封裝失敗及所有後續處理停止。</span><span class="sxs-lookup"><span data-stu-id="c7934-106">Failing a component, in turn, causes the package to fail and all subsequent processing to stop.</span></span>  
  
 <span data-ttu-id="c7934-107">若不要因為失敗而停止封裝執行，則設定及處理在轉換中可能發生的處理錯誤，是不錯的作法。</span><span class="sxs-lookup"><span data-stu-id="c7934-107">Instead of letting failures stop package execution, it is good practice to configure and handle potential processing errors as they occur within the transformation.</span></span> <span data-ttu-id="c7934-108">與其選擇忽略失敗以確保封裝可順利執行，不如將失敗的資料列重新導向至另一個處理路徑，讓資料和錯誤都可以保存、檢查及稍後再重新處理。</span><span class="sxs-lookup"><span data-stu-id="c7934-108">While you might choose to ignore failures to ensure your package runs successfully, it is often better to redirect the failed row to another processing path where the data and the error can be persisted, examined and reprocessed at a later time.</span></span>  
  
 <span data-ttu-id="c7934-109">在這一課，您會建立您在＜ [Lesson 3: Adding Logging](lesson-3-add-logging-with-ssis.md)＞所開發的封裝副本。</span><span class="sxs-lookup"><span data-stu-id="c7934-109">In this lesson, you will create a copy of the package that you developed in [Lesson 3: Adding Logging](lesson-3-add-logging-with-ssis.md).</span></span> <span data-ttu-id="c7934-110">利用這個新的封裝，您可以建立其中一個範例資料檔的損毀版本。</span><span class="sxs-lookup"><span data-stu-id="c7934-110">Working with this new package, you will create a corrupted version of one of the sample data files.</span></span> <span data-ttu-id="c7934-111">當您執行封裝時，損毀的檔案將強迫發生處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="c7934-111">The corrupted file will force a processing error to occur when you run the package.</span></span>  
  
 <span data-ttu-id="c7934-112">為了處理錯誤資料，您會加入及設定一般檔案目的地，將在 [查閱貨幣索引鍵] 轉換中找不到查閱值的資料列寫入檔案中。</span><span class="sxs-lookup"><span data-stu-id="c7934-112">To handle the error data, you will add and configure a Flat File destination that will write any rows that fail to locate a lookup value in the Lookup Currency Key transformation to a file.</span></span>  
  
 <span data-ttu-id="c7934-113">將錯誤資料寫入檔案之前，您要併入一個指令碼元件，利用指令碼來取得錯誤描述。</span><span class="sxs-lookup"><span data-stu-id="c7934-113">Before the error data is written to the file, you will include a Script component that uses script to get error descriptions.</span></span> <span data-ttu-id="c7934-114">然後您會重新設定 [查閱貨幣索引鍵] 轉換，將任何無法處理的資料重新導向至 [指令碼] 轉換。</span><span class="sxs-lookup"><span data-stu-id="c7934-114">You will then reconfigure the Lookup Currency Key transformation to redirect any data that could not be processed to the Script transformation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c7934-115">這個教學課程需要 **AdventureWorksDW2012** 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="c7934-115">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="c7934-116">如需更多有關如何安裝和部署 **AdventureWorksDW2012**的資訊，請參閱 [CodePlex 上 Reporting Services 產品範例專案](https://go.microsoft.com/fwlink/p/?LinkId=526910)。</span><span class="sxs-lookup"><span data-stu-id="c7934-116">For more information about how to install and deploy **AdventureWorksDW2012**, see [Reporting Services Product Samples Project on CodePlex](https://go.microsoft.com/fwlink/p/?LinkId=526910).</span></span>  
  
## <a name="tasks-in-lesson"></a><span data-ttu-id="c7934-117">本課程的工作</span><span class="sxs-lookup"><span data-stu-id="c7934-117">Tasks in Lesson</span></span>  
 <span data-ttu-id="c7934-118">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="c7934-118">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="c7934-119">步驟 1:複製第 3 課的封裝</span><span class="sxs-lookup"><span data-stu-id="c7934-119">Step 1: Copying the Lesson 3 Package</span></span>](lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [<span data-ttu-id="c7934-120">步驟 2:建立損毀的檔案</span><span class="sxs-lookup"><span data-stu-id="c7934-120">Step 2: Creating a Corrupted File</span></span>](lesson-4-2-creating-a-corrupted-file.md)  
  
-   [<span data-ttu-id="c7934-121">步驟 3：新增錯誤流程重新導向</span><span class="sxs-lookup"><span data-stu-id="c7934-121">Step 3: Adding Error Flow Redirection</span></span>](lesson-4-3-adding-error-flow-redirection.md)  
  
-   [<span data-ttu-id="c7934-122">步驟 4：新增一般檔案目的地</span><span class="sxs-lookup"><span data-stu-id="c7934-122">Step 4: Adding a Flat File Destination</span></span>](lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [<span data-ttu-id="c7934-123">步驟 5：測試第 4 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="c7934-123">Step 5: Testing the Lesson 4 Tutorial Package</span></span>](lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="c7934-124">開始課程</span><span class="sxs-lookup"><span data-stu-id="c7934-124">Start the Lesson</span></span>  
 [<span data-ttu-id="c7934-125">步驟 1:複製第 3 課的封裝</span><span class="sxs-lookup"><span data-stu-id="c7934-125">Step 1: Copying the Lesson 3 Package</span></span>](lesson-4-1-copying-the-lesson-3-package.md)  
  
  
