---
title: 步驟 4：測試第 5 課的教學課程封裝 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5215b77d-c2ec-4b25-a3de-ca49ea197d74
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 76e4692de4daa9ddd6ed0e418bed5cda74ec7650
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593436"
---
# <a name="step-4-testing-the-lesson-5-tutorial-package"></a><span data-ttu-id="422f6-102">步驟 4：測試第 5 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="422f6-102">Step 4: Testing the Lesson 5 Tutorial Package</span></span>
  <span data-ttu-id="422f6-103">在執行階段，您的封裝將從執行階段更新的變數中取得 `Directory` 屬性的值，而不是使用您建立封裝時指定的原始目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="422f6-103">At run time, your package will obtain the value for the `Directory` property from a variable updated at run time, rather than using the original directory name that you specified when you created the package.</span></span> <span data-ttu-id="422f6-104">變數的值會由 SSISTutorial.dtsConfig 檔案擴展。</span><span class="sxs-lookup"><span data-stu-id="422f6-104">The value of the variable is populated by the SSISTutorial.dtsConfig file.</span></span>  
  
 <span data-ttu-id="422f6-105">若要確認封裝在執行階段使用新值來更新 Directory 屬性，只要執行封裝即可。</span><span class="sxs-lookup"><span data-stu-id="422f6-105">To verify that the package updates the Directory property with the new value during run time, simply execute the package.</span></span> <span data-ttu-id="422f6-106">因為只有 3 個範例資料檔會複製到新目錄，所以資料流程只會執行 3 次，而不是反覆執行原始資料夾的 14 個檔案。</span><span class="sxs-lookup"><span data-stu-id="422f6-106">Because only three sample data files were copied to the new directory, the data flow will run only three times, rather than iterate through the 14 files in the original folder.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="422f6-107">檢查封裝配置</span><span class="sxs-lookup"><span data-stu-id="422f6-107">Checking the Package Layout</span></span>  
 <span data-ttu-id="422f6-108">在測試封裝之前，您應該確認第 5 課封裝中的控制流程和資料流程是否包含下圖所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="422f6-108">Before you test the package you should verify that the control and data flows in the Lesson 5 package contains the objects shown in the following diagrams.</span></span> <span data-ttu-id="422f6-109">其控制流程應該與第 4 課的控制流程相同。</span><span class="sxs-lookup"><span data-stu-id="422f6-109">The control flow should be identical to the control flow in lesson 4.</span></span> <span data-ttu-id="422f6-110">資料流程應該與第 4 課的資料流程完全相同。</span><span class="sxs-lookup"><span data-stu-id="422f6-110">The data flow should be identical to the data flow in lessons 4.</span></span>  
  
 <span data-ttu-id="422f6-111">**控制流程**</span><span class="sxs-lookup"><span data-stu-id="422f6-111">**Control Flow**</span></span>  
  
 <span data-ttu-id="422f6-112">![套件中的控制流程](../../2014/tutorials/media/task4lesson2control.gif "套件中的控制流程")</span><span class="sxs-lookup"><span data-stu-id="422f6-112">![Control flow in package](../../2014/tutorials/media/task4lesson2control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="422f6-113">**資料流程**</span><span class="sxs-lookup"><span data-stu-id="422f6-113">**Data Flow**</span></span>  
  
 <span data-ttu-id="422f6-114">![套件中的資料流程](../../2014/tutorials/media/task9lesson1data.gif "套件中的資料流程")</span><span class="sxs-lookup"><span data-stu-id="422f6-114">![Data flow in package](../../2014/tutorials/media/task9lesson1data.gif "Data flow in package")</span></span>  
  
### <a name="to-test-the-lesson-5-tutorial-package"></a><span data-ttu-id="422f6-115">若要測試第 5 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="422f6-115">To test the Lesson 5 tutorial package</span></span>  
  
1.  <span data-ttu-id="422f6-116">在 [偵錯] 功能表上，按一下 [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="422f6-116">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
2.  <span data-ttu-id="422f6-117">在封裝完成執行之後，請在 [**調試**程式] 功能表上，按一下 [**停止調試**程式]。</span><span class="sxs-lookup"><span data-stu-id="422f6-117">After the package has completed running, on the **Debug** menu, and then click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="422f6-118">下一課</span><span class="sxs-lookup"><span data-stu-id="422f6-118">Next Lesson</span></span>  
 [<span data-ttu-id="422f6-119">第 6 課：搭配專案部署模型使用參數</span><span class="sxs-lookup"><span data-stu-id="422f6-119">Lesson 6: Using Parameters with the Project Deployment Model</span></span>](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
  
  
