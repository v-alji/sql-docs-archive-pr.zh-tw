---
title: 步驟 3：部署第 6 課的封裝 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3c7ab82e9b04fe0752252102374f745e311d830d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705282"
---
# <a name="step-3-testing-the-lesson-6-package"></a><span data-ttu-id="476e2-102">步驟 3：測試第 6 課的封裝</span><span class="sxs-lookup"><span data-stu-id="476e2-102">Step 3: Testing the Lesson 6 Package</span></span>
  <span data-ttu-id="476e2-103">在執行階段，您的封裝會從 VarFolderName 參數取得目錄屬性的值。</span><span class="sxs-lookup"><span data-stu-id="476e2-103">At run time, your package will obtain the value for the Directory property from the VarFolderName parameter.</span></span>  
  
 <span data-ttu-id="476e2-104">若要確認封裝在執行階段使用新值來更新 Directory 屬性，只要執行封裝即可。</span><span class="sxs-lookup"><span data-stu-id="476e2-104">To verify that the package updates the Directory property with the new value during run time, simply execute the package.</span></span> <span data-ttu-id="476e2-105">因為只有 3 個範例資料檔會複製到新目錄，所以資料流程只會執行 3 次，而不是反覆執行原始資料夾的 14 個檔案。</span><span class="sxs-lookup"><span data-stu-id="476e2-105">Because only three sample data files were copied to the new directory, the data flow will run only three times, rather than iterate through the 14 files in the original folder.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="476e2-106">檢查封裝配置</span><span class="sxs-lookup"><span data-stu-id="476e2-106">Checking the Package Layout</span></span>  
 <span data-ttu-id="476e2-107">在測試封裝之前，您應該確認第 6 課封裝中的控制流程和資料流程是否包含下圖所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="476e2-107">Before you test the package you should verify that the control and data flows in the Lesson 6 package contains the objects shown in the following diagrams.</span></span> <span data-ttu-id="476e2-108">其控制流程應該與第 5 課的控制流程相同。</span><span class="sxs-lookup"><span data-stu-id="476e2-108">The control flow should be identical to the control flow in lesson 5.</span></span> <span data-ttu-id="476e2-109">資料流程應該與第 5 課的資料流程相同。</span><span class="sxs-lookup"><span data-stu-id="476e2-109">The data flow should be identical to the data flow in lesson 5.</span></span>  
  
 <span data-ttu-id="476e2-110">**控制流程**</span><span class="sxs-lookup"><span data-stu-id="476e2-110">**Control Flow**</span></span>  
  
 <span data-ttu-id="476e2-111">![控制流程](../../2014/tutorials/media/task3lesson6control.jpg "控制流程")</span><span class="sxs-lookup"><span data-stu-id="476e2-111">![Control Flow](../../2014/tutorials/media/task3lesson6control.jpg "Control Flow")</span></span>  
  
 <span data-ttu-id="476e2-112">**資料流程**</span><span class="sxs-lookup"><span data-stu-id="476e2-112">**Data Flow**</span></span>  
  
 <span data-ttu-id="476e2-113">![資料流程](../../2014/tutorials/media/task3lesson6data.jpg "資料流程")</span><span class="sxs-lookup"><span data-stu-id="476e2-113">![Data Flow](../../2014/tutorials/media/task3lesson6data.jpg "Data Flow")</span></span>  
  
### <a name="to-test-the-lesson-6-tutorial-package"></a><span data-ttu-id="476e2-114">若要測試第 6 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="476e2-114">TO test the Lesson 6 tutorial package</span></span>  
  
1.  <span data-ttu-id="476e2-115">在 [偵錯] 功能表上，按一下 [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="476e2-115">On the Debug menu, click Start Debugging.</span></span>  
  
2.  <span data-ttu-id="476e2-116">在封裝完成執行之後，在 [偵錯] 功能表上，按一下 [停止偵錯]。</span><span class="sxs-lookup"><span data-stu-id="476e2-116">After the package has completed running, on the Debug menu, and then click Stop Debugging.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="476e2-117">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="476e2-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="476e2-118">步驟 4：部署第 6 課的封裝</span><span class="sxs-lookup"><span data-stu-id="476e2-118">Step 4: Deploying the Lesson 6 Package</span></span>](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
