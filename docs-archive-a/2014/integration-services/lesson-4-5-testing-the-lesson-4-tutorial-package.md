---
title: 步驟 5：測試第 4 課的教學課程封裝
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5f18df92-0248-4858-836b-c8b02f0e0439
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4a897f99bf68805e4e66c3b6bbe818b312077fb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704297"
---
# <a name="step-5-testing-the-lesson-4-tutorial-package"></a><span data-ttu-id="73e96-102">步驟 5：測試第 4 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="73e96-102">Step 5: Testing the Lesson 4 Tutorial Package</span></span>
  <span data-ttu-id="73e96-103">在執行階段，損毀的檔案 Currency_BAD.txt 將無法在 [貨幣索引鍵查閱] 轉換中產生相符者。</span><span class="sxs-lookup"><span data-stu-id="73e96-103">At run time, the corrupted file, Currency_BAD.txt, will fail to generate a match within the Currency Key Lookup transformation.</span></span> <span data-ttu-id="73e96-104">因為 [貨幣索引鍵查閱] 的錯誤輸出現在已設定為將失敗的資料列重新導向至新的失敗資料列目的地，所以該元件不會失敗，且封裝會順利執行。</span><span class="sxs-lookup"><span data-stu-id="73e96-104">Because the error output of Currency Key Lookup has now been configured to redirect failed rows to the new Failed Rows destination, the component does not fail, and the package runs successfully.</span></span> <span data-ttu-id="73e96-105">所有失敗的錯誤資料列會寫入至 ErrorOutput.txt。</span><span class="sxs-lookup"><span data-stu-id="73e96-105">All failed error rows are written to ErrorOutput.txt.</span></span>  
  
 <span data-ttu-id="73e96-106">在這項工作中，您將執行封裝來測試修改過的錯誤輸出組態。</span><span class="sxs-lookup"><span data-stu-id="73e96-106">In this task, you will test the revised error output configuration by running the package.</span></span> <span data-ttu-id="73e96-107">在封裝順利執行後，即會看到 ErrorOutput.txt 檔的內容。</span><span class="sxs-lookup"><span data-stu-id="73e96-107">Upon successful package execution, you will then view the contents of the ErrorOutput.txt file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73e96-108">如果您不想要在 ErrorOutput.txt 檔案中累計錯誤資料列，應該手動刪除封裝執行之間的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="73e96-108">If you do not want to accumulate error rows in the ErrorOutput.txt file, you should manually delete the file content between package runs.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="73e96-109">檢查封裝配置</span><span class="sxs-lookup"><span data-stu-id="73e96-109">Checking the Package layout</span></span>  
 <span data-ttu-id="73e96-110">在測試封裝之前，您應該確認第 4 課封裝中的控制流程和資料流程是否包含下圖所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="73e96-110">Before you test the package you should verify that the control flow and the data flow in the Lesson 4 package contain the objects shown in the following diagrams.</span></span> <span data-ttu-id="73e96-111">其控制流程應該與第 2 - 4 課的控制流程相同。</span><span class="sxs-lookup"><span data-stu-id="73e96-111">The control flow should be identical to the control flow in lessons 2 - 4.</span></span>  
  
 <span data-ttu-id="73e96-112">**控制流程**</span><span class="sxs-lookup"><span data-stu-id="73e96-112">**Control Flow**</span></span>  
  
 <span data-ttu-id="73e96-113">![套件中的控制流程](../../2014/tutorials/media/task4lesson2control.gif "套件中的控制流程")</span><span class="sxs-lookup"><span data-stu-id="73e96-113">![Control flow in package](../../2014/tutorials/media/task4lesson2control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="73e96-114">**資料流程**</span><span class="sxs-lookup"><span data-stu-id="73e96-114">**Data Flow**</span></span>  
  
 <span data-ttu-id="73e96-115">![套件中的資料流程](../../2014/tutorials/media/task5lesson5data.gif "套件中的資料流程")</span><span class="sxs-lookup"><span data-stu-id="73e96-115">![Data flow in package](../../2014/tutorials/media/task5lesson5data.gif "Data flow in package")</span></span>  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a><span data-ttu-id="73e96-116">若要執行第 4 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="73e96-116">To run the Lesson 4 tutorial package</span></span>  
  
1.  <span data-ttu-id="73e96-117">在 [偵錯] 功能表上，按一下 [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="73e96-117">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
2.  <span data-ttu-id="73e96-118">在封裝完成執行之後，在 **[偵錯]** 功能表上，按一下 **[停止偵錯]**。</span><span class="sxs-lookup"><span data-stu-id="73e96-118">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
### <a name="to-verify-the-contents-of-the-erroroutputtxt-file"></a><span data-ttu-id="73e96-119">若要驗證 ErrorOutput.txt 檔的內容</span><span class="sxs-lookup"><span data-stu-id="73e96-119">To verify the contents of the ErrorOutput.txt file</span></span>  
  
-   <span data-ttu-id="73e96-120">在記事本或任何其他文字編輯器中開啟 ErrorOutput.txt 檔。</span><span class="sxs-lookup"><span data-stu-id="73e96-120">In Notepad or any other text editor, open the ErrorOutput.txt file.</span></span> <span data-ttu-id="73e96-121">預設資料行順序為：AverageRate、CurrencyID、CurrencyDate、EndOfDateRate、ErrorCode、ErrorColumn、ErrorDescription。</span><span class="sxs-lookup"><span data-stu-id="73e96-121">The default column order is: AverageRate, CurrencyID, CurrencyDate, EndOfDateRate, ErrorCode, ErrorColumn, ErrorDescription.</span></span>  
  
     <span data-ttu-id="73e96-122">請注意，檔案中的所有資料列都包含不相符的 CurrencyID 值 BAD、ErrorCode 值 -1071607778、ErrorColumn 值 0 和 ErrorDescription 值「查閱期間產生的資料列不符」。</span><span class="sxs-lookup"><span data-stu-id="73e96-122">Notice that all the rows in the file contain the unmatched CurrencyID value of BAD, the ErrorCode value of -1071607778, the ErrorColumn value of 0, and the ErrorDescription value "Row yielded no match during lookup".</span></span> <span data-ttu-id="73e96-123">ErrorColumn 的值是設為 0，因為該錯誤不是特定資料行的錯誤。</span><span class="sxs-lookup"><span data-stu-id="73e96-123">The value of the ErrorColumn is set to 0 because the error is not column specific.</span></span> <span data-ttu-id="73e96-124">它是失敗的查閱作業。</span><span class="sxs-lookup"><span data-stu-id="73e96-124">It is the lookup operation that failed.</span></span> <span data-ttu-id="73e96-125">.</span><span class="sxs-lookup"><span data-stu-id="73e96-125">.</span></span>  
  
  
