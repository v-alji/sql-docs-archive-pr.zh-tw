---
title: 第9課：建立觀點 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 417b6a4d3b16857f48bcc2f39dc8ec4c010a2b10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706914"
---
# <a name="lesson-9-create-perspectives"></a><span data-ttu-id="f4583-102">第 9 課：建立檢視方塊</span><span class="sxs-lookup"><span data-stu-id="f4583-102">Lesson 9: Create Perspectives</span></span>
  <span data-ttu-id="f4583-103">在這一課，您將建立一個 [網際網路銷售] 檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="f4583-103">In this lesson, you will create an Internet Sales perspective.</span></span> <span data-ttu-id="f4583-104">檢視方塊會定義可檢視的模型子集，以提供聚焦、商務特有或應用程式特有的觀點。</span><span class="sxs-lookup"><span data-stu-id="f4583-104">A perspective defines a viewable subset of a model that provides focused, business-specific, or application-specific viewpoints.</span></span> <span data-ttu-id="f4583-105">使用者使用檢視方塊連接到模型時，只會將那些模型物件 (資料表、資料行、量值、階層和 KPI) 視為該檢視方塊中定義的欄位。</span><span class="sxs-lookup"><span data-stu-id="f4583-105">When a user connects to a model using a perspective, they see only those model objects (tables, columns, measures, hierarchies, and KPIs) as fields defined in that perspective.</span></span>  
  
 <span data-ttu-id="f4583-106">您在本課中所建立的網際網路銷售額檢視方塊將不包含 Customer 資料表物件。</span><span class="sxs-lookup"><span data-stu-id="f4583-106">The Internet Sales perspective you create in this lesson will exclude the Customer table object.</span></span> <span data-ttu-id="f4583-107">當您建立從檢視表中排除某些物件的檢視方塊時，該物件仍然會存在於模型中，但是在報表用戶端欄位清單中看不到。</span><span class="sxs-lookup"><span data-stu-id="f4583-107">When you create a perspective that excludes certain objects from view, that object still exists in the model; however, it is not visible in a reporting client field list.</span></span> <span data-ttu-id="f4583-108">導出資料行嗨量值無論是否包含在檢視方塊中，都仍然可以從遭排除之物件資料中計算。</span><span class="sxs-lookup"><span data-stu-id="f4583-108">Calculated columns and measures either included in a perspective or not can still calculate from object data that is excluded.</span></span>  
  
 <span data-ttu-id="f4583-109">本課程的目的在於描述如何建立檢視方塊，以及熟悉表格式模型撰寫工具。</span><span class="sxs-lookup"><span data-stu-id="f4583-109">The purpose of this lesson is to describe how to create perspectives and become familiar with the tabular model authoring tools.</span></span> <span data-ttu-id="f4583-110">如果您之後展開此模型納入其他資料表，可以建立其他檢視方塊來定義不同的模型視點，例如存貨和銷售人員。</span><span class="sxs-lookup"><span data-stu-id="f4583-110">If you later expand this model to include additional tables, you can create additional perspectives to define different viewpoints of the model, for example, Inventory and Sales Force.</span></span>  
  
 <span data-ttu-id="f4583-111">如需詳細資訊，請參閱[檢視方塊 &#40;SSAS 表格式&#41;](tabular-models/perspectives-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="f4583-111">To learn more, see [Perspectives &#40;SSAS Tabular&#41;](tabular-models/perspectives-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="f4583-112">完成本課程的估計時間： **5 分鐘**</span><span class="sxs-lookup"><span data-stu-id="f4583-112">Estimated time to complete this lesson: **5 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f4583-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f4583-113">Prerequisites</span></span>  
 <span data-ttu-id="f4583-114">本主題是表格式模型教學課程的一部分，請依序完成。</span><span class="sxs-lookup"><span data-stu-id="f4583-114">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="f4583-115">在執行本課中的工作之前，您應已完成上一課： [第 8 課：建立關鍵效能指標](lesson-7-create-key-performance-indicators.md)。</span><span class="sxs-lookup"><span data-stu-id="f4583-115">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 8: Create Key Performance Indicators](lesson-7-create-key-performance-indicators.md).</span></span>  
  
## <a name="create-perspectives"></a><span data-ttu-id="f4583-116">建立檢視方塊</span><span class="sxs-lookup"><span data-stu-id="f4583-116">Create Perspectives</span></span>  
  
#### <a name="to-create-an-internet-sales-perspective"></a><span data-ttu-id="f4583-117">建立網際網路銷售檢視方塊</span><span class="sxs-lookup"><span data-stu-id="f4583-117">To create an Internet Sales perspective</span></span>  
  
1.  <span data-ttu-id="f4583-118">在模型設計師中，按一下 [**模型**] 功能表，然後按一下 [**透視圖**]。</span><span class="sxs-lookup"><span data-stu-id="f4583-118">In the model designer, click the **Model** menu, and then click **Perspectives**.</span></span>  
  
2.  <span data-ttu-id="f4583-119">在 [檢視方塊]\*\*\*\* 對話方塊中，按一下 [新增檢視方塊]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4583-119">In the **Perspectives** dialog box, click **New Perspective**.</span></span>  
  
3.  <span data-ttu-id="f4583-120">若要重新命名此觀點，請按兩下**新的 [觀點 1** ] 資料行標題，然後輸入 `Internet Sales` 。</span><span class="sxs-lookup"><span data-stu-id="f4583-120">To rename the perspective, double-click the **New Perspective 1** column heading, and then type `Internet Sales`.</span></span>  
  
4.  <span data-ttu-id="f4583-121">在 [**欄位**] 中，選取下列資料表**日期**、**地理位置**、**產品**、**產品類別目錄**、**產品子類別**目錄和 `Internet Sales` 。</span><span class="sxs-lookup"><span data-stu-id="f4583-121">In **Fields**, select the following tables **Date**, **Geography**, **Product**, **Product Category**, **Product Subcategory**, and `Internet Sales`.</span></span>  
  
     <span data-ttu-id="f4583-122">請注意，您從此檢視方塊中排除了 Customer 資料表及其所有資料行。</span><span class="sxs-lookup"><span data-stu-id="f4583-122">Notice you excluded the Customer table and all of its columns from this perspective.</span></span> <span data-ttu-id="f4583-123">稍後，您將在第 12 課中使用 [在 Excel 中進行分析] 功能測試此檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="f4583-123">Later, in Lesson 12, you will use the Analyze in Excel feature to test this perspective.</span></span> <span data-ttu-id="f4583-124">Excel 樞紐分析表欄位清單將包含 Customer 資料表之外的每個資料表。</span><span class="sxs-lookup"><span data-stu-id="f4583-124">The Excel PivotTable Field List will include each table except the Customer table.</span></span>  
  
5.  <span data-ttu-id="f4583-125">驗證您所做的選擇，確定未核取 [Customer]\*\*\*\* 資料表，然後按一下 [確定]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="f4583-125">Verify your selections, making sure the **Customer** table is not checked, and then click **OK**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f4583-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f4583-126">Next Steps</span></span>  
 <span data-ttu-id="f4583-127">若要繼續進行本教學課程，請前往下一課： [第 10 課：建立階層](lesson-9-create-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="f4583-127">To continue this tutorial, go to the next lesson: [Lesson 10: Create Hierarchies](lesson-9-create-hierarchies.md).</span></span>  
  
  
