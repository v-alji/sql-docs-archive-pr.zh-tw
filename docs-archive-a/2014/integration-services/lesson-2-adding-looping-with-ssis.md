---
title: 第2課：新增迴圈 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 65efb84b4e50b470470e396bbe5681ce4b5dfac3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593439"
---
# <a name="lesson-2-adding-looping"></a><span data-ttu-id="73551-102">第 2 課：新增迴圈</span><span class="sxs-lookup"><span data-stu-id="73551-102">Lesson 2: Adding Looping</span></span>
  <span data-ttu-id="73551-103">在[第1課：建立專案和基本套件](lesson-1-create-a-project-and-basic-package-with-ssis.md)中，您建立了一個封裝，它會從單一一般檔案來源解壓縮資料、使用查閱轉換來轉換資料，最後將資料載入**AdventureWorksDW2012**範例資料庫的**FactCurrency**事實資料表中。</span><span class="sxs-lookup"><span data-stu-id="73551-103">In [Lesson 1: Creating the Project and Basic Package](lesson-1-create-a-project-and-basic-package-with-ssis.md), you created a package that extracted data from a single flat file source, transformed the data using Lookup transformations, and finally loaded the data into the **FactCurrency** fact table of the **AdventureWorksDW2012** sample database.</span></span>  
  
 <span data-ttu-id="73551-104">不過，擷取、轉換和載入 (ETL) 處理序使用單個一般檔案的情況很罕見。</span><span class="sxs-lookup"><span data-stu-id="73551-104">However, it is rare for an extract, transform, and load (ETL) process to use a single flat file.</span></span> <span data-ttu-id="73551-105">典型的 ETL 處理序會從多個一般檔案來源擷取資料。</span><span class="sxs-lookup"><span data-stu-id="73551-105">A typical ETL process would extract data from multiple flat file sources.</span></span> <span data-ttu-id="73551-106">從多個來源擷取資料需要反覆的控制流程。</span><span class="sxs-lookup"><span data-stu-id="73551-106">Extracting data from multiple sources requires an iterative control flow.</span></span> <span data-ttu-id="73551-107">最預期的功能之一， [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 就是能夠輕鬆地將反復專案或迴圈加入封裝中。</span><span class="sxs-lookup"><span data-stu-id="73551-107">One of the most anticipated features of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is the ability to easily add iteration or looping to packages.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="73551-108">提供兩種類型的容器來循環使用封裝迴圈：Foreach 迴圈容器和 For 迴圈容器。</span><span class="sxs-lookup"><span data-stu-id="73551-108">provides two types of containers for looping through packages: the Foreach Loop container and the For Loop container.</span></span> <span data-ttu-id="73551-109">Foreach 迴圈容器會使用列舉值來執行迴圈，而 For 迴圈容器通常會使用變數運算式。</span><span class="sxs-lookup"><span data-stu-id="73551-109">The Foreach Loop container uses an enumerator to perform the looping, whereas the For Loop container typically uses a variable expression.</span></span> <span data-ttu-id="73551-110">這一課使用 Foreach 迴圈容器。</span><span class="sxs-lookup"><span data-stu-id="73551-110">This lesson uses the Foreach Loop container.</span></span>  
  
 <span data-ttu-id="73551-111">Foreach 迴圈容器可讓封裝對指定列舉值的每一位成員重複控制流程。</span><span class="sxs-lookup"><span data-stu-id="73551-111">The Foreach Loop container enables a package to repeat the control flow for each member of a specified enumerator.</span></span> <span data-ttu-id="73551-112">利用 Foreach 迴圈容器，您可以列舉：</span><span class="sxs-lookup"><span data-stu-id="73551-112">With the Foreach Loop container, you can enumerate:</span></span>  
  
-   <span data-ttu-id="73551-113">ADO 記錄集資料列</span><span class="sxs-lookup"><span data-stu-id="73551-113">ADO recordset rows</span></span>  
  
-   <span data-ttu-id="73551-114">ADO .Net 結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="73551-114">ADO .Net schema information</span></span>  
  
-   <span data-ttu-id="73551-115">檔案和目錄結構</span><span class="sxs-lookup"><span data-stu-id="73551-115">File and directory structures</span></span>  
  
-   <span data-ttu-id="73551-116">系統、封裝和使用者變數</span><span class="sxs-lookup"><span data-stu-id="73551-116">System, package and user variables</span></span>  
  
-   <span data-ttu-id="73551-117">包含在變數中的可列舉物件</span><span class="sxs-lookup"><span data-stu-id="73551-117">Enumerable objects contained in a variable</span></span>  
  
-   <span data-ttu-id="73551-118">集合中的項目</span><span class="sxs-lookup"><span data-stu-id="73551-118">Items in a collection</span></span>  
  
-   <span data-ttu-id="73551-119">XML 路徑語言 (XPath) 運算式中的節點</span><span class="sxs-lookup"><span data-stu-id="73551-119">Nodes in an XML Path Language (XPath) expression</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="73551-120">管理物件 (SMO)</span><span class="sxs-lookup"><span data-stu-id="73551-120">Management Objects (SMO)</span></span>  
  
 <span data-ttu-id="73551-121">在這一課，您將修改在第 1 課建立的簡易 ETL 封裝，以利用 Foreach 迴圈容器的好處。</span><span class="sxs-lookup"><span data-stu-id="73551-121">In this lesson, you will modify the simple ETL package created in Lesson 1 to take advantage of the Foreach Loop container.</span></span> <span data-ttu-id="73551-122">您也可以將使用者自訂封裝變數設定為讓教學課程封裝反覆運算資料夾的所有一般檔案。</span><span class="sxs-lookup"><span data-stu-id="73551-122">You will also set user-defined package variables to enable the tutorial package to iterate through all the flat files in the folder.</span></span> <span data-ttu-id="73551-123">如果您尚未完成上一課，您也可以複製此教學課程所包含之已完成的第 1 課封裝。</span><span class="sxs-lookup"><span data-stu-id="73551-123">If you have not completed the previous lesson, you can also copy the completed Lesson 1 package that is included with the tutorial.</span></span>  
  
 <span data-ttu-id="73551-124">在這一課，您不會修改資料流程，只會修改控制流程。</span><span class="sxs-lookup"><span data-stu-id="73551-124">In this lesson, you will not modify the data flow, only the control flow.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="73551-125">這個教學課程需要 **AdventureWorksDW2012** 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="73551-125">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="73551-126">如需如何安裝和部署 **AdventureWorksDW2012**的詳細資訊，請參閱 [CodePlex 上的 Reporting Services 產品範例](https://go.microsoft.com/fwlink/p/?LinkID=526910)。</span><span class="sxs-lookup"><span data-stu-id="73551-126">For more information about how to install and deploy **AdventureWorksDW2012**, see [Reporting Services Product Samples on CodePlex](https://go.microsoft.com/fwlink/p/?LinkID=526910).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="73551-127">課程工作</span><span class="sxs-lookup"><span data-stu-id="73551-127">Lesson Tasks</span></span>  
 <span data-ttu-id="73551-128">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="73551-128">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="73551-129">步驟 1:複製第 1 課的封裝</span><span class="sxs-lookup"><span data-stu-id="73551-129">Step 1: Copying the Lesson 1 Package</span></span>](lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [<span data-ttu-id="73551-130">步驟 2:新增和設定 Foreach 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="73551-130">Step 2: Adding and Configuring the Foreach Loop Container</span></span>](lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [<span data-ttu-id="73551-131">步驟 3：修改一般檔案連線管理員</span><span class="sxs-lookup"><span data-stu-id="73551-131">Step 3: Modifying the Flat File Connection Manager</span></span>](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [<span data-ttu-id="73551-132">步驟 4：測試第 2 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="73551-132">Step 4: Testing the Lesson 2 Tutorial Package</span></span>](lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="73551-133">開始課程</span><span class="sxs-lookup"><span data-stu-id="73551-133">Start the Lesson</span></span>  
 [<span data-ttu-id="73551-134">步驟 1:複製第 1 課的封裝</span><span class="sxs-lookup"><span data-stu-id="73551-134">Step 1: Copying the Lesson 1 Package</span></span>](lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a><span data-ttu-id="73551-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73551-135">See Also</span></span>  
 [<span data-ttu-id="73551-136">For 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="73551-136">For Loop Container</span></span>](control-flow/for-loop-container.md)  
  
  
