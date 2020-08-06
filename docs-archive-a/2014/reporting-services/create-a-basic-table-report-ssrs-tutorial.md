---
title: 建立基本資料表報表 (SSRS 教學課程) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [Reporting Services]
- tutorials [Reporting Services]
- reports [Reporting Services], creating
ms.assetid: 3b539b4b-26f2-4c0b-b506-80f175679a46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02e0f42869a3bfa88e0c6646fd447968c8ba3a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584291"
---
# <a name="create-a-basic-table-report-ssrs-tutorial"></a><span data-ttu-id="ff0f4-102">建立基本資料表報表 (SSRS 教學課程)</span><span class="sxs-lookup"><span data-stu-id="ff0f4-102">Create a Basic Table Report (SSRS Tutorial)</span></span>
  <span data-ttu-id="ff0f4-103">此教學課程的設計目的是要協助您使用 [報表設計師]，根據 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫來建立基本資料表報表。</span><span class="sxs-lookup"><span data-stu-id="ff0f4-103">This tutorial is designed to help you create a basic table report based on the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database using Report Designer.</span></span> <span data-ttu-id="ff0f4-104">您也可以使用報表產生器或報表精靈來建立報表。</span><span class="sxs-lookup"><span data-stu-id="ff0f4-104">You can also use Report Builder or the Report Wizard to create reports.</span></span> <span data-ttu-id="ff0f4-105">在這個教學課程中，您將建立報表專案、設定連接資訊、定義查詢、加入資料表資料區域、群組與加總某些欄位，以及預覽報表。</span><span class="sxs-lookup"><span data-stu-id="ff0f4-105">In this tutorial, you will create a report project, set up connection information, define a query, add a Table data region, group and total some fields, and preview the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ff0f4-106">為了完成這個教學課程，[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 必須以原生模式執行。</span><span class="sxs-lookup"><span data-stu-id="ff0f4-106">To complete this tutorial, you must be running [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in native mode.</span></span> <span data-ttu-id="ff0f4-107">如果 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 是在 SharePoint 整合模式中執行，則所有用到報表伺服器 URL 的步驟都將無法運作。</span><span class="sxs-lookup"><span data-stu-id="ff0f4-107">If you are running [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in SharePoint integrated mode, the steps that use report server URLs do not work.</span></span> <span data-ttu-id="ff0f4-108">如需有關模式的詳細資訊 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ，請參閱[Reporting Services 報表伺服器](reporting-services-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ff0f4-108">For more information about [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] modes, see [Reporting Services Report Server](reporting-services-report-server.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff0f4-109">需求</span><span class="sxs-lookup"><span data-stu-id="ff0f4-109">Requirements</span></span>  
 <span data-ttu-id="ff0f4-110">您的系統必須已經安裝下列項目，才能使用這個教學課程：</span><span class="sxs-lookup"><span data-stu-id="ff0f4-110">Your system must have the following installed to use this tutorial:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="ff0f4-111">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]資料庫引擎。</span><span class="sxs-lookup"><span data-stu-id="ff0f4-111">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database engine.</span></span>  
  
-   <span data-ttu-id="ff0f4-112">[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ff0f4-112">The [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  <span data-ttu-id="ff0f4-113">如需詳細資訊，請參閱[SQL Server 2012 的「艾德作品」 (SQL Server 2012)  (的「艾德作品](https://go.microsoft.com/fwlink/?LinkId=245471)」 https://go.microsoft.com/fwlink/?LinkId=245471). 。</span><span class="sxs-lookup"><span data-stu-id="ff0f4-113">For more information, see [Adventure Works for SQL Server 2012 (Adventure Works for SQL Server 2012)](https://go.microsoft.com/fwlink/?LinkId=245471) (https://go.microsoft.com/fwlink/?LinkId=245471)..</span></span> <span data-ttu-id="ff0f4-114">如需 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 範例資料庫和範例程式碼支援的詳細資訊 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] ，請參閱 CodePlex 網站上的[資料庫和範例總覽](https://go.microsoft.com/fwlink/?LinkId=110391)。</span><span class="sxs-lookup"><span data-stu-id="ff0f4-114">For more information about support for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sample databases and sample code for [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], see [Databases and Samples Overview](https://go.microsoft.com/fwlink/?LinkId=110391) on the CodePlex Web site.</span></span>  
  
-   [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]<span data-ttu-id="ff0f4-115">.</span><span class="sxs-lookup"><span data-stu-id="ff0f4-115">.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="ff0f4-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff0f4-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNote64Samp](../includes/ssnote64samp-md.md)]  
  
 <span data-ttu-id="ff0f4-117">另外，您也必須擁有從 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫擷取資料的唯讀權限。</span><span class="sxs-lookup"><span data-stu-id="ff0f4-117">You must also have read-only permissions to retrieve data from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="ff0f4-118">工作</span><span class="sxs-lookup"><span data-stu-id="ff0f4-118">Tasks</span></span>  
 [<span data-ttu-id="ff0f4-119">第 1 課：建立報表伺服器專案 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ff0f4-119">Lesson 1: Creating a Report Server Project &#40;Reporting Services&#41;</span></span>](lesson-1-creating-a-report-server-project-reporting-services.md)  
  
 [<span data-ttu-id="ff0f4-120">第 2 課：指定連接資訊 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ff0f4-120">Lesson 2: Specifying Connection Information &#40;Reporting Services&#41;</span></span>](lesson-2-specifying-connection-information-reporting-services.md)  
  
 [<span data-ttu-id="ff0f4-121">第 3 課：定義資料表報表的資料集 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ff0f4-121">Lesson 3: Defining a Dataset for the Table Report &#40;Reporting Services&#41;</span></span>](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)  
  
 [<span data-ttu-id="ff0f4-122">第 4 課：將資料表加入至報表 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ff0f4-122">Lesson 4: Adding a Table to the Report &#40;Reporting Services&#41;</span></span>](lesson-4-adding-a-table-to-the-report-reporting-services.md)  
  
 [<span data-ttu-id="ff0f4-123">第 5 課：格式化報表 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ff0f4-123">Lesson 5: Formatting a Report &#40;Reporting Services&#41;</span></span>](lesson-5-formatting-a-report-reporting-services.md)  
  
 [<span data-ttu-id="ff0f4-124">課程 6：加入群組和總計 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ff0f4-124">Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;</span></span>](lesson-6-adding-grouping-and-totals-reporting-services.md)  
  
> [!NOTE]  
>  <span data-ttu-id="ff0f4-125">在審核教學課程時，建議您在檔檢視器工具列上加入 **[下一個]** 和 [**上一個**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ff0f4-125">When reviewing tutorials, we recommend that you add **Next** and **Previous** buttons to the document viewer toolbar.</span></span> <span data-ttu-id="ff0f4-126">如需詳細資訊，請參閱。</span><span class="sxs-lookup"><span data-stu-id="ff0f4-126">For more information, see.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff0f4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff0f4-127">See Also</span></span>  
 [<span data-ttu-id="ff0f4-128">Reporting Services 教學課程 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ff0f4-128">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](reporting-services-tutorials-ssrs.md)  
  
  
