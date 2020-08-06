---
title: '使用 Visual Basic 或 Visual c # 來存取報表伺服器 Web 服務 (SSRS 教學課程) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- walkthroughs [Reporting Services]
- Reporting Services, Web service
- Web service [Reporting Services], tutorials
ms.assetid: cf688163-4ac0-475b-b6dd-6f2f05b553c6
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 3dc2599b4fafe682d74089d637918e04db9ed219
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704517"
---
# <a name="accessing-the-report-server-web-service-using-visual-basic-or-visual-c-ssrs-tutorial"></a><span data-ttu-id="08d47-102">利用 Visual Basic 或 Visual C# 存取報表伺服器 Web 服務 (SSRS 教學課程)</span><span class="sxs-lookup"><span data-stu-id="08d47-102">Accessing the Report Server Web Service Using Visual Basic or Visual C# (SSRS Tutorial)</span></span>
  <span data-ttu-id="08d47-103">下列教學課程將示範如何從使用或所建立的應用程式存取報表伺服器 Web 服務 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="08d47-103">The following tutorial shows you how to access the Report Server Web service from an application created with [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] or [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)].</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="08d47-104">學習內容</span><span class="sxs-lookup"><span data-stu-id="08d47-104">What You Will Learn</span></span>  
 <span data-ttu-id="08d47-105">在這個教學課程進行期間，您將完成下列活動：</span><span class="sxs-lookup"><span data-stu-id="08d47-105">During the course of this tutorial, you will complete the following:</span></span>  
  
-   <span data-ttu-id="08d47-106">使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 主控台應用程式專案範本建立用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="08d47-106">Create a client application using the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Console Application project template.</span></span>  
  
-   <span data-ttu-id="08d47-107">加入報表伺服器 Web 服務的 Web 參考。</span><span class="sxs-lookup"><span data-stu-id="08d47-107">Add a Web reference for the Report Server Web service.</span></span>  
  
-   <span data-ttu-id="08d47-108">撰寫程式碼來存取 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="08d47-108">Write code to access the Web service.</span></span>  
  
-   <span data-ttu-id="08d47-109">在偵錯模式下執行主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="08d47-109">Run the console application in debug mode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08d47-110">需求</span><span class="sxs-lookup"><span data-stu-id="08d47-110">Requirements</span></span>  
 <span data-ttu-id="08d47-111">若要完成教學課程，必須具備下列項目：</span><span class="sxs-lookup"><span data-stu-id="08d47-111">To complete the tutorial, you must have the following:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="08d47-112">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="08d47-112">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="08d47-113">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]或類似 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 的相容的開發工具。</span><span class="sxs-lookup"><span data-stu-id="08d47-113">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] or a similar [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-compatible development tool.</span></span>  
  
-   <span data-ttu-id="08d47-114">足以存取報表伺服器所在電腦之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 報表伺服器 Web 服務的權限。</span><span class="sxs-lookup"><span data-stu-id="08d47-114">Sufficient permissions to be able to access the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Report Server Web service on the computer where your report server is located.</span></span>  
  
-   <span data-ttu-id="08d47-115">安裝在您報表伺服器中的報表。</span><span class="sxs-lookup"><span data-stu-id="08d47-115">A report installed on your report server.</span></span> <span data-ttu-id="08d47-116">本教學課程使用範例報表 Company Sales。</span><span class="sxs-lookup"><span data-stu-id="08d47-116">This tutorial uses the sample report, Company Sales.</span></span> <span data-ttu-id="08d47-117">如需範例報表的詳細資訊，請參閱[SQL Server Reporting Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=177889)。</span><span class="sxs-lookup"><span data-stu-id="08d47-117">For more information about sample reports, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="08d47-118">安裝期間不會自動安裝範例，但是您可在任何時間加以安裝。</span><span class="sxs-lookup"><span data-stu-id="08d47-118">The samples are not installed automatically during setup, but you can install them at any time.</span></span> <span data-ttu-id="08d47-119">如需範例的詳細資訊，請參閱[SQL Server 產品範例](https://go.microsoft.com/fwlink/?LinkId=182887)。</span><span class="sxs-lookup"><span data-stu-id="08d47-119">For information about samples, see [SQL Server Product Samples](https://go.microsoft.com/fwlink/?LinkId=182887).</span></span>  
  
 <span data-ttu-id="08d47-120">**完成本教學課程的估計時間：** 60 分鐘</span><span class="sxs-lookup"><span data-stu-id="08d47-120">**Estimated time to complete the tutorial:** 60 minutes</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="08d47-121">工作</span><span class="sxs-lookup"><span data-stu-id="08d47-121">Tasks</span></span>  
 [<span data-ttu-id="08d47-122">第 1 課：建立 Web 服務用戶端專案</span><span class="sxs-lookup"><span data-stu-id="08d47-122">Lesson 1: Creating the Web Service Client Project</span></span>](../../2014/tutorials/lesson-1-creating-the-web-service-client-project.md)  
  
 [<span data-ttu-id="08d47-123">第 2 課：新增 Web 參考</span><span class="sxs-lookup"><span data-stu-id="08d47-123">Lesson 2: Adding a Web Reference</span></span>](../../2014/tutorials/lesson-2-adding-a-web-reference.md)  
  
 [<span data-ttu-id="08d47-124">第 3 課：存取 Web 服務</span><span class="sxs-lookup"><span data-stu-id="08d47-124">Lesson 3: Accessing the Web Service</span></span>](../../2014/tutorials/lesson-3-accessing-the-web-service.md)  
  
 [<span data-ttu-id="08d47-125">第4課：執行應用程式 &#40;VB-VC&#35;&#41;</span><span class="sxs-lookup"><span data-stu-id="08d47-125">Lesson 4: Running the Application &#40;VB-VC&#35;&#41;</span></span>](../../2014/tutorials/lesson-4-running-the-application-vb-vcsharp.md)  
  
  
