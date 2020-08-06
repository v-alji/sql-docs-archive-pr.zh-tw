---
title: 使用從 RDL 架構產生的類別更新報表 (SSRS 教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RDL [Reporting Services], generating
- RDL [Reporting Services], tutorials
- RDL [Reporting Services], serializing
ms.assetid: 8f81d48f-7ab9-4ef8-bce0-7d16d9a47fbd
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f3972b8e1af6d50ccc6f5188c8f671fe333ebce8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592365"
---
# <a name="updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial"></a><span data-ttu-id="af5fb-102">使用 RDL 結構描述產生的類別更新報表 (SSRS 教學課程)</span><span class="sxs-lookup"><span data-stu-id="af5fb-102">Updating Reports Using Classes Generated from the RDL Schema (SSRS Tutorial)</span></span>
  <span data-ttu-id="af5fb-103">本教學課程說明如何使用 XML 架構定義工具 ( # A0) 來產生類別，讓您以類別序列化和還原序列化報表定義檔案 ( .rdl 和 .rdlc) 。 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="af5fb-103">This tutorial illustrates how to use the XML Schema Definition Tool (Xsd.exe) to generate classes that allow you to serialize and deserialize report definition files (.rdl and .rdlc) with the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="af5fb-104">學習內容</span><span class="sxs-lookup"><span data-stu-id="af5fb-104">What You Will Learn</span></span>  
 <span data-ttu-id="af5fb-105">這個教學課程進行期間，您將完成下列活動：</span><span class="sxs-lookup"><span data-stu-id="af5fb-105">During the course of this tutorial, you will complete the following activities:</span></span>  
  
-   <span data-ttu-id="af5fb-106">使用 [ [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 主控台應用程式] 專案範本建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="af5fb-106">Create an application using the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Console Application project template.</span></span>  
  
-   <span data-ttu-id="af5fb-107">使用**xsd**工具，從報表定義語言 (RDL) 架構產生類別。</span><span class="sxs-lookup"><span data-stu-id="af5fb-107">Generate classes from the Report Definition Language (RDL) schema using the **xsd** tool.</span></span>  
  
-   <span data-ttu-id="af5fb-108">連接到報表伺服器，並擷取報表定義。</span><span class="sxs-lookup"><span data-stu-id="af5fb-108">Connect to a report server and retrieve a report definition.</span></span>  
  
-   <span data-ttu-id="af5fb-109">撰寫程式碼，以更新報表定義檔案。</span><span class="sxs-lookup"><span data-stu-id="af5fb-109">Write code to update the report definition file.</span></span>  
  
-   <span data-ttu-id="af5fb-110">將已更新的報表定義存回報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="af5fb-110">Save the updated report definition back to the report server.</span></span>  
  
-   <span data-ttu-id="af5fb-111">執行 RDL 結構描述應用程式 (VB/C#)。</span><span class="sxs-lookup"><span data-stu-id="af5fb-111">Run the RDL Schema Application (VB/C#).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af5fb-112">如果報表沒有描述，本教學課程提供的程式碼範例可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="af5fb-112">The code samples provided in this tutorial might fail for reports having no description.</span></span> <span data-ttu-id="af5fb-113">發生失敗是因為報表未指定描述以致描述屬性不存在。</span><span class="sxs-lookup"><span data-stu-id="af5fb-113">The failure is because the description property does not exist for the reports with description not specified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af5fb-114">需求</span><span class="sxs-lookup"><span data-stu-id="af5fb-114">Requirements</span></span>  
 <span data-ttu-id="af5fb-115">若要完成教學課程，必須具備下列項目：</span><span class="sxs-lookup"><span data-stu-id="af5fb-115">To complete the tutorial, you must have the following:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="af5fb-116">[!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af5fb-116">[!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="af5fb-117">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af5fb-117">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].</span></span>  
  
-   <span data-ttu-id="af5fb-118">足以存取及發行報表至報表伺服器所在電腦之報表伺服器 Web 服務的權限。</span><span class="sxs-lookup"><span data-stu-id="af5fb-118">Sufficient permissions to be able to access and publish reports to the Report Server Web service on the computer where your report server is located.</span></span>  
  
-   <span data-ttu-id="af5fb-119">安裝到 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 執行個體的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="af5fb-119">The [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database installed to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="af5fb-120">安裝在您報表伺服器中的報表。</span><span class="sxs-lookup"><span data-stu-id="af5fb-120">A report installed on your report server.</span></span> <span data-ttu-id="af5fb-121">本教學課程使用範例報表 Company Sales 2012。</span><span class="sxs-lookup"><span data-stu-id="af5fb-121">This tutorial uses the sample report, Company Sales 2012.</span></span> <span data-ttu-id="af5fb-122">如需範例報表的詳細資訊，請參閱[SQL Server Reporting Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=177889)。</span><span class="sxs-lookup"><span data-stu-id="af5fb-122">For more information about sample reports, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af5fb-123">安裝期間不會自動安裝範例，但是您可在任何時間加以安裝。</span><span class="sxs-lookup"><span data-stu-id="af5fb-123">The samples are not installed automatically during setup, but you can install them at any time.</span></span> <span data-ttu-id="af5fb-124">如需範例的詳細資訊，請參閱[SQL Server 產品範例](https://go.microsoft.com/fwlink/?LinkId=182887)。</span><span class="sxs-lookup"><span data-stu-id="af5fb-124">For information about samples, see [SQL Server Product Samples](https://go.microsoft.com/fwlink/?LinkId=182887).</span></span>  
  
 <span data-ttu-id="af5fb-125">**完成本教學課程的估計時間：** 30 分鐘</span><span class="sxs-lookup"><span data-stu-id="af5fb-125">**Estimated time to complete the tutorial:** 30 minutes</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="af5fb-126">工作</span><span class="sxs-lookup"><span data-stu-id="af5fb-126">Tasks</span></span>  
 [<span data-ttu-id="af5fb-127">第 1 課：建立 RDL 結構描述 Visual Studio 專案</span><span class="sxs-lookup"><span data-stu-id="af5fb-127">Lesson 1: Create the RDL Schema Visual Studio Project</span></span>](../../2014/tutorials/lesson-1-create-the-rdl-schema-visual-studio-project.md)  
  
 [<span data-ttu-id="af5fb-128">第 2 課：使用 xsd 工具，從 RDL 結構描述產生類別</span><span class="sxs-lookup"><span data-stu-id="af5fb-128">Lesson 2: Generate Classes from the RDL Schema using the xsd Tool</span></span>](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)  
  
 [<span data-ttu-id="af5fb-129">第 3 課：從報表伺服器載入報表定義</span><span class="sxs-lookup"><span data-stu-id="af5fb-129">Lesson 3: Load a Report Definition from the Report Server</span></span>](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)  
  
 [<span data-ttu-id="af5fb-130">第 4 課：以程式設計方式更新報表定義</span><span class="sxs-lookup"><span data-stu-id="af5fb-130">Lesson 4: Update the Report Definition Programmatically</span></span>](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)  
  
 [<span data-ttu-id="af5fb-131">第 5 課：將報表定義發行到報表伺服器</span><span class="sxs-lookup"><span data-stu-id="af5fb-131">Lesson 5: Publish the Report Definition to the Report Server</span></span>](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)  
  
 [<span data-ttu-id="af5fb-132">第6課：執行 RDL 架構應用程式 &#40;VB-C&#35;&#41;</span><span class="sxs-lookup"><span data-stu-id="af5fb-132">Lesson 6: Run the RDL Schema Application &#40;VB-C&#35;&#41;</span></span>](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)  
  
## <a name="see-also"></a><span data-ttu-id="af5fb-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af5fb-133">See Also</span></span>  
 [<span data-ttu-id="af5fb-134">報表定義語言 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="af5fb-134">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
