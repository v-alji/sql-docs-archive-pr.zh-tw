---
title: 第1課：準備 Analysis Services 資料庫 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2a796977-6568-4705-9d27-86a9b36658c2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 07647a940851fbdbdc65357e168747662dc88380
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710077"
---
# <a name="lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial"></a><span data-ttu-id="6352c-102">第 1 課：準備 Analysis Services 資料庫 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="6352c-102">Lesson 1: Preparing the Analysis Services Database (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="6352c-103">您是 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 在中設計商業智慧應用程式之人員的新員工 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6352c-103">You are a new employee of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] who has been tasked with designing a business intelligence application in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]<span data-ttu-id="6352c-104">想要利用您的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料採礦經驗，探索已購買自行車之人員的有趣且可操作的資訊。</span><span class="sxs-lookup"><span data-stu-id="6352c-104">hopes to leverage your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data mining experience to discover interesting and actionable information about people who have purchased bicycles.</span></span> <span data-ttu-id="6352c-105">然後，還希望您預測未來最有可能購買自行車的潛在客戶。</span><span class="sxs-lookup"><span data-stu-id="6352c-105">They then want you to predict which prospective customers are most likely to purchase a bicycle in the future.</span></span>  
  
 <span data-ttu-id="6352c-106">在中設計此應用程式時，會 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 從 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 根據多 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 維度模型化和資料採礦的專案範本，在專案中建立。</span><span class="sxs-lookup"><span data-stu-id="6352c-106">Designing this application in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] starts with the creation in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project based on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project template for multidimensional modeling and data mining.</span></span> <span data-ttu-id="6352c-107">建立好 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案之後，您將建立一個或多個資料來源。</span><span class="sxs-lookup"><span data-stu-id="6352c-107">After you create an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, you define one or more data sources.</span></span> <span data-ttu-id="6352c-108">然後，您可以從資料來源中選取的資料表和 views 定義中繼資料的視圖，稱為*資料來源視圖*。</span><span class="sxs-lookup"><span data-stu-id="6352c-108">Then, you define a view of the metadata, called a *data source view*, from selected tables and views from the data sources.</span></span>  
  
 <span data-ttu-id="6352c-109">在這個課程中，您將建立一個 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案、定義單一資料來源，以及將資料表子集加入資料來源檢視中。</span><span class="sxs-lookup"><span data-stu-id="6352c-109">In this lesson, you will create an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, define a single data source, and add a subset of tables to a data source view.</span></span> <span data-ttu-id="6352c-110">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="6352c-110">This lesson includes the following tasks:</span></span>  
  
 [<span data-ttu-id="6352c-111">建立 Analysis Services 專案 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="6352c-111">Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="6352c-112">建立資料來源 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="6352c-112">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="6352c-113">建立資料來源視圖 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="6352c-113">Creating a Data Source View &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="6352c-114">本課程的第一項工作</span><span class="sxs-lookup"><span data-stu-id="6352c-114">First Task in Lesson</span></span>  
 [<span data-ttu-id="6352c-115">建立 Analysis Services 專案 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="6352c-115">Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="6352c-116">下一課</span><span class="sxs-lookup"><span data-stu-id="6352c-116">Next Lesson</span></span>  
 [<span data-ttu-id="6352c-117">第2課：建立目標郵寄結構 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="6352c-117">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="6352c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6352c-118">See Also</span></span>  
 <span data-ttu-id="6352c-119">[多維度模型中的資料來源視圖](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models) </span><span class="sxs-lookup"><span data-stu-id="6352c-119">[Data Source Views in Multidimensional Models](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models) </span></span>  
 <span data-ttu-id="6352c-120">[&#40;SSAS 多維度&#41;支援的資料來源](https://docs.microsoft.com/analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional) </span><span class="sxs-lookup"><span data-stu-id="6352c-120">[Data Sources Supported &#40;SSAS Multidimensional&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional) </span></span>  
 <span data-ttu-id="6352c-121">[組建 Analysis Services 專案 &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span><span class="sxs-lookup"><span data-stu-id="6352c-121">[Build Analysis Services Projects &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span></span>  
 [<span data-ttu-id="6352c-122">建立 Analysis Services 專案</span><span class="sxs-lookup"><span data-stu-id="6352c-122">Creating an Analysis Services Project</span></span>](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md)  
  
  
