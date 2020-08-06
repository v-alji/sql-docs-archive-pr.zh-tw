---
title: 步驟 4：將資料流程工作新增至套件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 96af3073-8f11-4444-b934-fe8613a2d084
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4fda1de99e9fcaa683f9063e2feb1b71886a5cd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596135"
---
# <a name="step-4-adding-a-data-flow-task-to-the-package"></a><span data-ttu-id="fb729-102">步驟 4：將資料流程工作新增至封裝</span><span class="sxs-lookup"><span data-stu-id="fb729-102">Step 4: Adding a Data Flow Task to the Package</span></span>
  <span data-ttu-id="fb729-103">在建立來源和目的地資料的連接管理員之後，下一項工作是將資料流程工作加入封裝中。</span><span class="sxs-lookup"><span data-stu-id="fb729-103">After you have created the connection managers for the source and destination data, the next task is to add a Data Flow task to your package.</span></span> <span data-ttu-id="fb729-104">資料流程工作封裝資料流程引擎，它在來源和目的地之間移動資料，以及提供轉換、清理和修改移動中資料的功能。</span><span class="sxs-lookup"><span data-stu-id="fb729-104">The Data Flow task encapsulates the data flow engine that moves data between sources and destinations, and provides the functionality for transforming, cleaning, and modifying data as it is moved.</span></span> <span data-ttu-id="fb729-105">資料流程工作是進行擷取、轉換和載入 (ETL) 處理序大部份工作之處。</span><span class="sxs-lookup"><span data-stu-id="fb729-105">The Data Flow task is where most of the work of an extract, transform, and load (ETL) process occurs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="fb729-106">將資料流程 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 與控制流程分開。</span><span class="sxs-lookup"><span data-stu-id="fb729-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] separates data flow from control flow.</span></span>  
  
### <a name="to-add-a-data-flow-task"></a><span data-ttu-id="fb729-107">若要加入資料流程工作</span><span class="sxs-lookup"><span data-stu-id="fb729-107">To add a Data Flow task</span></span>  
  
1.  <span data-ttu-id="fb729-108">按一下 **[控制流程]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fb729-108">Click the **Control Flow** tab.</span></span>  
  
2.  <span data-ttu-id="fb729-109">在 [SSIS 工具箱]\*\*\*\* 中，展開 [我的最愛]\*\*\*\*，然後將 [資料流程工作]\*\*\*\* 拖曳至 [控制流程]\*\*\*\* 索引標籤的設計介面中。</span><span class="sxs-lookup"><span data-stu-id="fb729-109">In the **SSIS Toolbox**, expand **Favorites**, and drag a **Data Flow Task** onto the design surfaceof the **Control Flow** tab.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fb729-110">如果 [SSIS 工具箱] 無法使用，請在主功能表上，依序選取 [SSIS] 和 [SSIS 工具箱]，即可顯示 [SSIS 工具箱]。</span><span class="sxs-lookup"><span data-stu-id="fb729-110">If the SSIS Toolbox isn't available, on the main menu select SSIS then SSIS Toolbox to display the SSIS Toolbox.</span></span>  
  
3.  <span data-ttu-id="fb729-111">在 [**控制流程**] 設計介面上，以滑鼠右鍵按一下新加入的 [**資料流程**工作]，按一下 [**重新命名**]，然後將名稱變更為 `Extract Sample Currency Data` 。</span><span class="sxs-lookup"><span data-stu-id="fb729-111">On the **Control Flow** design surface, right-click the newly added **Data Flow Task**, click **Rename**, and change the name to `Extract Sample Currency Data`.</span></span>  
  
     <span data-ttu-id="fb729-112">提供唯一名稱給所有您要加入設計介面中的元件，是不錯的作法。</span><span class="sxs-lookup"><span data-stu-id="fb729-112">It is good practice to provide unique names to all components that you add to a design surface.</span></span> <span data-ttu-id="fb729-113">為了使用和維護上的方便，名稱應該要描述每一個元件執行的功能。</span><span class="sxs-lookup"><span data-stu-id="fb729-113">For ease of use and maintainability, the names should describe the function that each component performs.</span></span> <span data-ttu-id="fb729-114">遵照這些命名指導方針可讓 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 套件自我記錄。</span><span class="sxs-lookup"><span data-stu-id="fb729-114">Following these naming guidelines allows your [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to be self-documenting.</span></span> <span data-ttu-id="fb729-115">記錄封裝的另一個方法是使用註解。</span><span class="sxs-lookup"><span data-stu-id="fb729-115">Another way to document your packages is by using annotations.</span></span> <span data-ttu-id="fb729-116">如需使用註解的詳細資訊，請參閱 [在套件中使用註解](use-annotations-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="fb729-116">For more information about annotations, see [Use Annotations in Packages](use-annotations-in-packages.md).</span></span>  
  
4.  <span data-ttu-id="fb729-117">以滑鼠右鍵按一下 [資料流程] 工作，按一下 [**屬性**]，然後在 [屬性視窗中，確認 `LocaleID` 屬性是設為 [\*\*英文] ([美國]) \*\*。</span><span class="sxs-lookup"><span data-stu-id="fb729-117">Right-click the Data Flow task, click **Properties**, and in the Properties window, verify that the `LocaleID` property is set to **English (United States)**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="fb729-118">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="fb729-118">Next Task in Lesson</span></span>  
 [<span data-ttu-id="fb729-119">步驟 5：新增和設定一般檔案來源</span><span class="sxs-lookup"><span data-stu-id="fb729-119">Step 5: Adding and Configuring the Flat File Source</span></span>](lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
## <a name="see-also"></a><span data-ttu-id="fb729-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb729-120">See Also</span></span>  
 [<span data-ttu-id="fb729-121">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="fb729-121">Data Flow Task</span></span>](control-flow/data-flow-task.md)  
  
  
