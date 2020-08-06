---
title: 第3課：加入和處理模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: cc29927a-c368-4b8a-bbd0-af89a9f54dc9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5da034089d8bbe7f1a967258d195a56ddbf13c03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585693"
---
# <a name="lesson-3-adding-and-processing-models"></a><span data-ttu-id="2a228-102">第 3 課：新增及處理模型</span><span class="sxs-lookup"><span data-stu-id="2a228-102">Lesson 3: Adding and Processing Models</span></span>
  <span data-ttu-id="2a228-103">上一課所建立的採礦結構包含了以 [!INCLUDE[msCoName](../includes/msconame-md.md)] 決策樹演算法為根據的單一採礦模型。</span><span class="sxs-lookup"><span data-stu-id="2a228-103">The mining structure that you created in the previous lesson contains a single mining model that is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="2a228-104">您可以使用此模型識別目標郵寄活動的客戶。</span><span class="sxs-lookup"><span data-stu-id="2a228-104">You can use this model to identify customers for the targeted mailing campaign.</span></span> <span data-ttu-id="2a228-105">不過，為確保您的分析很徹底，一般作法是使用不同的演算法建立相關的模型，然後比較其結果。</span><span class="sxs-lookup"><span data-stu-id="2a228-105">However, to ensure that your analysis is thorough, it is a common practice to create related models using different algorithms and compare their results.</span></span> <span data-ttu-id="2a228-106">這種方式可讓您獲得不同角度的資料。</span><span class="sxs-lookup"><span data-stu-id="2a228-106">That way you can get different insights as well.</span></span> <span data-ttu-id="2a228-107">因此，您將建立另外兩個模型，然後處理及部署這兩個模型。</span><span class="sxs-lookup"><span data-stu-id="2a228-107">Therefore, you will create two additional models, then process and deploy the models.</span></span>  
  
 <span data-ttu-id="2a228-108">在這一課，您將會建立一組採礦模型，它將建議潛在客戶清單中最可能購買的客戶。</span><span class="sxs-lookup"><span data-stu-id="2a228-108">In this lesson, you will create a set of mining models that will suggest the most likely customers from a list of potential customers.</span></span>  
  
 <span data-ttu-id="2a228-109">若要完成本課程中的工作，您將使用[Microsoft 群集演算法](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)和[Microsoft 貝氏貝氏機率分類演算法](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="2a228-109">To complete the tasks in this lesson, you will use the [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) and the [Microsoft Naive Bayes Algorithm](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md).</span></span>  
  
 <span data-ttu-id="2a228-110">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="2a228-110">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="2a228-111">將新模型加入至目標郵寄結構 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="2a228-111">Adding New Models to the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="2a228-112">處理目標郵寄結構中的模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="2a228-112">Processing Models in the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="2a228-113">本課程的第一項工作</span><span class="sxs-lookup"><span data-stu-id="2a228-113">First Task in Lesson</span></span>  
 [<span data-ttu-id="2a228-114">將新模型加入至目標郵寄結構 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="2a228-114">Adding New Models to the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="2a228-115">上一課</span><span class="sxs-lookup"><span data-stu-id="2a228-115">Previous Lesson</span></span>  
 [<span data-ttu-id="2a228-116">第2課：建立目標郵寄結構 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="2a228-116">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="2a228-117">下一課</span><span class="sxs-lookup"><span data-stu-id="2a228-117">Next Lesson</span></span>  
 [<span data-ttu-id="2a228-118">第4課：探索目標郵寄模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="2a228-118">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="2a228-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a228-119">See Also</span></span>  
 [<span data-ttu-id="2a228-120">將採礦模型加入結構 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="2a228-120">Add Mining Models to a Structure &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)  
  
  
