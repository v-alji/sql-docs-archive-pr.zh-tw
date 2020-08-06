---
title: 第2課：建立目標郵寄結構 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9d0d6ceb-49b5-47c7-9ee6-464da43cc1f6
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 005baa09e802a9ffe98f87239070401f170ddfa9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584910"
---
# <a name="lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial"></a><span data-ttu-id="40bf6-102">第 2 課：建立目標郵寄結構 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="40bf6-102">Lesson 2: Building a Targeted Mailing Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="40bf6-103">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 的行銷部門想要鎖定郵寄活動的特定客戶來增加銷售量。</span><span class="sxs-lookup"><span data-stu-id="40bf6-103">The Marketing department of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] wants to increase sales by targeting specific customers for a mailing campaign.</span></span> <span data-ttu-id="40bf6-104">公司的資料庫包含一份原有客戶的清單，以及一份潛在的新客戶清單。</span><span class="sxs-lookup"><span data-stu-id="40bf6-104">The company's database contains a list of past customers and a list of potential new customers.</span></span> <span data-ttu-id="40bf6-105">這家公司會調查原有客戶的屬性，希望能夠找出適用於潛在客戶的模式。</span><span class="sxs-lookup"><span data-stu-id="40bf6-105">By investigating the attributes of previous customers, the company hopes to discover patterns that they can then apply to potential customers.</span></span> <span data-ttu-id="40bf6-106">例如，他們可能會使用過去的趨勢來預測哪些潛在客戶最有可能購買自行車 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] ，或針對未來的行銷活動建立客戶區段。</span><span class="sxs-lookup"><span data-stu-id="40bf6-106">For example, they might use past trends to predict which potential customers are most likely to purchase a bike from [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], or create customer segments for future marketing campaigns.</span></span>  
  
 <span data-ttu-id="40bf6-107">在這一課，您將使用**資料採礦嚮導**來建立目標郵寄結構。</span><span class="sxs-lookup"><span data-stu-id="40bf6-107">In this lesson you will use the **Data Mining Wizard** to create the targeted mailing structure.</span></span> <span data-ttu-id="40bf6-108">當您完成本課的工作以後，您將會有一個具有單一模型的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="40bf6-108">After you complete the tasks in this lesson, you will have a mining structure with a single model.</span></span> <span data-ttu-id="40bf6-109">因為建立結構時牽涉到許多步驟和重要概念，所以我們將這個程序分成以下三個工作：</span><span class="sxs-lookup"><span data-stu-id="40bf6-109">Because there are many steps and important concepts involved in creating a structure, we have separated this process into the following three tasks:</span></span>  
  
 [<span data-ttu-id="40bf6-110">建立目標郵寄採礦模型結構 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="40bf6-110">Creating a Targeted Mailing Mining Model Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="40bf6-111">&#40;基本資料採礦教學課程中指定資料類型和內容類型&#41;</span><span class="sxs-lookup"><span data-stu-id="40bf6-111">Specifying the Data Type and Content Type &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="40bf6-112">為結構指定測試資料集 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="40bf6-112">Specifying a Testing Data Set for the Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial.md)  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="40bf6-113">本課程的第一項工作</span><span class="sxs-lookup"><span data-stu-id="40bf6-113">First Task in Lesson</span></span>  
 [<span data-ttu-id="40bf6-114">建立目標郵寄採礦模型結構 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="40bf6-114">Creating a Targeted Mailing Mining Model Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="40bf6-115">上一課</span><span class="sxs-lookup"><span data-stu-id="40bf6-115">Previous Lesson</span></span>  
 [<span data-ttu-id="40bf6-116">第1課：準備 Analysis Services 資料庫 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="40bf6-116">Lesson 1: Preparing the Analysis Services Database &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial.md)  
  
## <a name="next--lesson"></a><span data-ttu-id="40bf6-117">下一課</span><span class="sxs-lookup"><span data-stu-id="40bf6-117">Next  Lesson</span></span>  
 [<span data-ttu-id="40bf6-118">第 3 課：新增及處理模型</span><span class="sxs-lookup"><span data-stu-id="40bf6-118">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="see-also"></a><span data-ttu-id="40bf6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40bf6-119">See Also</span></span>  
 <span data-ttu-id="40bf6-120">[建立資料採礦結構 &#40;資料採礦嚮導&#41;](../../2014/analysis-services/create-the-data-mining-structure-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="40bf6-120">[Create the Data Mining Structure &#40;Data Mining Wizard&#41;](../../2014/analysis-services/create-the-data-mining-structure-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="40bf6-121">建立關聯式採礦結構</span><span class="sxs-lookup"><span data-stu-id="40bf6-121">Create a Relational Mining Structure</span></span>](../../2014/analysis-services/data-mining/create-a-relational-mining-structure.md)  
  
  
