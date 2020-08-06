---
title: 步驟 4：測試第 2 課的教學課程封裝 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0e8c0a25-8f79-41df-8ed2-f82a74b129cd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c055f80cbe9e6748b82569204e3a2d82e2f437e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592111"
---
# <a name="step-4-testing-the-lesson-2-tutorial-package"></a><span data-ttu-id="cbbe4-102">步驟 4：測試第 2 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="cbbe4-102">Step 4: Testing the Lesson 2 Tutorial Package</span></span>
  <span data-ttu-id="cbbe4-103">利用現在已設定的 Foreach 迴圈容器和一般檔案連接管理員，第 2 課的封裝可反覆進行範例資料夾之 14 個一般檔案的集合。</span><span class="sxs-lookup"><span data-stu-id="cbbe4-103">With the Foreach Loop container and the Flat File connection manager now configured, the Lesson 2 package can iterate through the collection of 14 flat files in the Sample Data folder.</span></span> <span data-ttu-id="cbbe4-104">每次一找到符合指定檔案名稱準則的檔案名稱時，Foreach 迴圈容器就會以該檔案名稱擴展使用者自訂變數。</span><span class="sxs-lookup"><span data-stu-id="cbbe4-104">Each time a file name is found that matches the specified file name criteria, the Foreach Loop container populates the user-defined variable with the file name.</span></span> <span data-ttu-id="cbbe4-105">然後，這個變數會更新一般檔案連接管理員的 ConnectionString 屬性，並建立與新的一般檔案之連接。</span><span class="sxs-lookup"><span data-stu-id="cbbe4-105">This variable, in turn, updates the ConnectionString property of the Flat File connection manager, and a connection to the new flat file is made.</span></span> <span data-ttu-id="cbbe4-106">在連接到資料夾的下一個檔案之前，Foreach 迴圈容器會對新的一般檔案中的資料執行未修改過的資料流程工作。</span><span class="sxs-lookup"><span data-stu-id="cbbe4-106">The Foreach Loop container then runs the unmodified data flow task against the data in the new flat file before connecting to the next file in the folder.</span></span>  
  
 <span data-ttu-id="cbbe4-107">請利用下列程序來測試您已加入封裝中的新迴圈功能。</span><span class="sxs-lookup"><span data-stu-id="cbbe4-107">Use the following procedure to test the new looping functionality that you have added to your package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cbbe4-108">如果您執行了第 1 課的封裝，就必須先從 AdventureWorksDW2012 的 dbo.FactCurrency 中刪除記錄，然後再執行這一課的封裝，否則封裝會失敗並出現錯誤，指出主索引鍵條件約束的違規。</span><span class="sxs-lookup"><span data-stu-id="cbbe4-108">If you ran the package from Lesson 1, you will need to delete the records from dbo.FactCurrency in AdventureWorksDW2012 before you run the package from this lesson or the package will fail with errors indicating a Violation of Primary Key constraint.</span></span> <span data-ttu-id="cbbe4-109">如果您是透過選取 [偵錯]/[開始偵錯] (或按下 F5) 來執行封裝，也會收到相同的錯誤，因為第 1 課和第 2 課都將執行。</span><span class="sxs-lookup"><span data-stu-id="cbbe4-109">You will receive the same errors if you run the package by selecting Debug/Start Debugging (or press F5) because both Lesson 1 and Lesson 2 will run.</span></span> <span data-ttu-id="cbbe4-110">第 2 課會嘗試插入已經在第 1 課中插入的記錄。</span><span class="sxs-lookup"><span data-stu-id="cbbe4-110">Lesson 2 will attempt to insert records already inserted in Lesson 1.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="cbbe4-111">檢查封裝配置</span><span class="sxs-lookup"><span data-stu-id="cbbe4-111">Checking the Package Layout</span></span>  
 <span data-ttu-id="cbbe4-112">在測試封裝之前，您應該確認第 2 課封裝中的控制流程和資料流程是否包含下圖所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="cbbe4-112">Before you test the package you should verify that the control and data flows in the Lesson 2 package contains the objects shown in the following diagrams.</span></span> <span data-ttu-id="cbbe4-113">資料流程應該與第 1 課的資料流程相同。</span><span class="sxs-lookup"><span data-stu-id="cbbe4-113">The data flow should be identical to the data flow in lesson 1.</span></span>  
  
 <span data-ttu-id="cbbe4-114">**控制流程**</span><span class="sxs-lookup"><span data-stu-id="cbbe4-114">**Control Flow**</span></span>  
  
 <span data-ttu-id="cbbe4-115">![套件中的控制流程](../../2014/tutorials/media/task4lesson2control.gif "套件中的控制流程")</span><span class="sxs-lookup"><span data-stu-id="cbbe4-115">![Control flow in package](../../2014/tutorials/media/task4lesson2control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="cbbe4-116">**資料流程**</span><span class="sxs-lookup"><span data-stu-id="cbbe4-116">**Data Flow**</span></span>  
  
 <span data-ttu-id="cbbe4-117">![套件中的資料流程](../../2014/tutorials/media/task9lesson1data.gif "套件中的資料流程")</span><span class="sxs-lookup"><span data-stu-id="cbbe4-117">![Data flow in package](../../2014/tutorials/media/task9lesson1data.gif "Data flow in package")</span></span>  
  
### <a name="to-test-the-lesson-2-tutorial-package"></a><span data-ttu-id="cbbe4-118">若要測試第 2 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="cbbe4-118">To test the Lesson 2 tutorial package</span></span>  
  
1.  <span data-ttu-id="cbbe4-119">在 **[方案總管]** 中，以滑鼠右鍵按一下 **[Lesson 2.dtsx]** ，然後按一下 **[執行封裝]**。</span><span class="sxs-lookup"><span data-stu-id="cbbe4-119">In **Solution Explorer**, right-click **Lesson 2.dtsx** and click **Execute Package**.</span></span>  
  
     <span data-ttu-id="cbbe4-120">此時會執行封裝。</span><span class="sxs-lookup"><span data-stu-id="cbbe4-120">The package will run.</span></span> <span data-ttu-id="cbbe4-121">您可以在 [輸出] 視窗中驗證每個迴圈的狀態，或按一下 [**進度**] 索引標籤來確認。例如，您可以看到1097行已從檔案 Currency_VEB.txt 新增至目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="cbbe4-121">You can verify the status of each loop in the Output window, or by clicking on the **Progress** tab. For example, you can see that 1097 lines were added to the destination table from the file Currency_VEB.txt.</span></span>  
  
2.  <span data-ttu-id="cbbe4-122">在封裝完成執行之後，在 **[偵錯]** 功能表上，按一下 **[停止偵錯]**。</span><span class="sxs-lookup"><span data-stu-id="cbbe4-122">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="cbbe4-123">下一課</span><span class="sxs-lookup"><span data-stu-id="cbbe4-123">Next Lesson</span></span>  
 [<span data-ttu-id="cbbe4-124">第 5 課：新增封裝部署模型的封裝組態</span><span class="sxs-lookup"><span data-stu-id="cbbe4-124">Lesson 5: Adding Package Configurations for the Package Deployment Model</span></span>](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="cbbe4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbbe4-125">See Also</span></span>  
 [<span data-ttu-id="cbbe4-126">執行專案和套件</span><span class="sxs-lookup"><span data-stu-id="cbbe4-126">Execution of Projects and Packages</span></span>](packages/run-integration-services-ssis-packages.md)  
  
  
