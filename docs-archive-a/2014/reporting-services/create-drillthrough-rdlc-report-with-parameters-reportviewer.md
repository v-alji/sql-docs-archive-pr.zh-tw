---
title: 使用 ReportViewer (SSRS 教學課程) ，建立具有參數的 (.RDLC) 報表的鑽處理Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02864ea8bdd80d6f46b7aad552fa30241322370c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706265"
---
# <a name="create-a-drillthrough-rdlc-report-with-parameters-using-reportviewer-ssrs-tutorial"></a><span data-ttu-id="c5edc-102">使用 ReportViewer 建立包含參數的鑽研 (RDLC) 報表 (SSRS 教學課程)</span><span class="sxs-lookup"><span data-stu-id="c5edc-102">Create a Drillthrough (RDLC) Report with Parameters using ReportViewer (SSRS Tutorial)</span></span>
  <span data-ttu-id="c5edc-103">[鑽研](https://technet.microsoft.com/library/ff519554.aspx) 報表是使用者從另一個報表按一下連結所開啟的報表。</span><span class="sxs-lookup"><span data-stu-id="c5edc-103">A [drillthrough](https://technet.microsoft.com/library/ff519554.aspx) report is a report that a user opens by clicking a link within another report.</span></span> <span data-ttu-id="c5edc-104">鑽研報表通常包含有關原始摘要報表之項目的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c5edc-104">Drillthrough reports commonly contain details about an item that is contained in an original summary report.</span></span> <span data-ttu-id="c5edc-105">本教學課程將逐步引導您進行下列課程，以[本機模式報表](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)建立包含參數和查詢的鑽研報表。</span><span class="sxs-lookup"><span data-stu-id="c5edc-105">This tutorial will walk you through the following lessons of creating a drillthrough report with parameters and a query, in [local mode reporting](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5edc-106">需求</span><span class="sxs-lookup"><span data-stu-id="c5edc-106">Requirements</span></span>  
 <span data-ttu-id="c5edc-107">若要使用此逐步解說，您必須具有**AdventureWorks2008**範例資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="c5edc-107">To use this walkthrough, you must have access to the **AdventureWorks2008** sample database.</span></span> <span data-ttu-id="c5edc-108">本逐步解說中使用的查詢也會使用**AdventureWorks2012**資料庫。</span><span class="sxs-lookup"><span data-stu-id="c5edc-108">The query used in this walkthrough will also work with **AdventureWorks2012** database.</span></span> <span data-ttu-id="c5edc-109">如需如何取得**AdventureWorks2008**範例資料庫的詳細資訊，請參閱逐步解說：安裝適用于 Microsoft Visual Studio 2010[的 AdventureWorks 資料庫](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="c5edc-109">For more information about how to get the **AdventureWorks2008** sample database, see [Walkthrough: Installing the AdventureWorks Database](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx) for Microsoft Visual Studio 2010.</span></span>  
  
 <span data-ttu-id="c5edc-110">本逐步解說假設您熟悉 Transaction-SQL 查詢以及 ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) 和 [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) 物件。</span><span class="sxs-lookup"><span data-stu-id="c5edc-110">This walkthrough assumes that you are familiar with Transaction-SQL queries and ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) and [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) objects.</span></span>  
  
 <span data-ttu-id="c5edc-111">使用 Visual Studio 2010 或 Visual Studio 2012 和 ASP.NET 網站範本建立包含 ReportViewer 控制項的 ASP.NET 網頁。</span><span class="sxs-lookup"><span data-stu-id="c5edc-111">Use Visual Studio 2010, or Visual Studio 2012, and the ASP.NET website template to create an ASP.NET webpage with a ReportViewer control.</span></span> <span data-ttu-id="c5edc-112">控制項會設定為檢視您所建立的報表。</span><span class="sxs-lookup"><span data-stu-id="c5edc-112">The control is configured to view a report that you create.</span></span> <span data-ttu-id="c5edc-113">在此逐步解說中，您會使用 Microsoft Visual C# 建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="c5edc-113">For this walkthrough, you create the application in Microsoft Visual C#.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="c5edc-114">工作</span><span class="sxs-lookup"><span data-stu-id="c5edc-114">Tasks</span></span>  
 <span data-ttu-id="c5edc-115">[第1課：建立新的網站](../reporting-services/lesson-1-create-a-new-web-site.md) </span><span class="sxs-lookup"><span data-stu-id="c5edc-115">[Lesson 1: Create a New Web Site](../reporting-services/lesson-1-create-a-new-web-site.md) </span></span>  
 <span data-ttu-id="c5edc-116">[第2課：定義父報表的資料連線和資料表](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md) </span><span class="sxs-lookup"><span data-stu-id="c5edc-116">[Lesson 2: Define a Data Connection and Data Table for Parent Report](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md) </span></span>  
 <span data-ttu-id="c5edc-117">[第3課：使用報表精靈設計父報表](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="c5edc-117">[Lesson 3: Design the Parent Report using the Report Wizard](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md) </span></span>  
 <span data-ttu-id="c5edc-118">[第4課：定義子報表的資料連線和資料表](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md) </span><span class="sxs-lookup"><span data-stu-id="c5edc-118">[Lesson 4: Define a Data Connection and Data Table for Child Report](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md) </span></span>  
 <span data-ttu-id="c5edc-119">[第5課：使用報表精靈設計子報表](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="c5edc-119">[Lesson 5: Design the Child Report using the Report Wizard](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md) </span></span>  
 <span data-ttu-id="c5edc-120">[第6課：將 ReportViewer 控制項加入至應用程式](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md) </span><span class="sxs-lookup"><span data-stu-id="c5edc-120">[Lesson 6: Add a ReportViewer Control to the Application](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md) </span></span>  
 <span data-ttu-id="c5edc-121">[第7課：在父報表上加入鑽取動作](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md) </span><span class="sxs-lookup"><span data-stu-id="c5edc-121">[Lesson 7: Add Drillthrough Action on Parent Report](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md) </span></span>  
 <span data-ttu-id="c5edc-122">[第8課：建立資料篩選](../reporting-services/lesson-8-create-a-data-filter.md) </span><span class="sxs-lookup"><span data-stu-id="c5edc-122">[Lesson 8: Create a Data Filter](../reporting-services/lesson-8-create-a-data-filter.md) </span></span>  
 [<span data-ttu-id="c5edc-123">第 9 課：建置及執行應用程式</span><span class="sxs-lookup"><span data-stu-id="c5edc-123">Lesson 9: Build and Run the Application</span></span>](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a><span data-ttu-id="c5edc-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5edc-124">See Also</span></span>  
 <span data-ttu-id="c5edc-125">[Reporting Services SSRS &#40;的教學課程&#41;](../reporting-services/reporting-services-tutorials-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5edc-125">[Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md) </span></span>  
 [<span data-ttu-id="c5edc-126">使用報表設計師設計報表 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c5edc-126">Design Reports with Report Designer &#40;SSRS&#41;</span></span>](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
