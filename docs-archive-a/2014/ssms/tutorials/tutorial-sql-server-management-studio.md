---
title: 教學課程：SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.tutorialstart.ssms.f1
helpviewer_keywords:
- projects [SQL Server Management Studio], tutorials
- templates [SQL Server], SQL Server Management Studio
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- solutions [SQL Server Management Studio], tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: d2bade70-07cf-4d94-b5d2-88aecb538ed1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8206fea828d6169975dc1d026a22e18e682f71e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606014"
---
# <a name="tutorial-sql-server-management-studio"></a><span data-ttu-id="8cd45-102">教學課程：SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8cd45-102">Tutorial: SQL Server Management Studio</span></span>
  <span data-ttu-id="8cd45-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 教學課程將為您介紹用來管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 基礎結構的整合式環境。</span><span class="sxs-lookup"><span data-stu-id="8cd45-103">The [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] tutorial introduces you to the integrated environment for managing your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] infrastructure.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="8cd45-104">提供設定、監視和管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的圖形介面。</span><span class="sxs-lookup"><span data-stu-id="8cd45-104">presents a graphical interface for configuring, monitoring, and administering instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8cd45-105">也讓您部署、監視以及升級應用程式所使用的資料層元件，例如資料庫和資料倉儲。</span><span class="sxs-lookup"><span data-stu-id="8cd45-105">It also allows you to deploy, monitor, and upgrade the data-tier components used by your applications, such as databases and data warehouses.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="8cd45-106">也提供用於編輯和偵錯指令碼的 [!INCLUDE[tsql](../../includes/tsql-md.md)]、MDX、DMX 和 XML 語言編輯器。</span><span class="sxs-lookup"><span data-stu-id="8cd45-106">also provides [!INCLUDE[tsql](../../includes/tsql-md.md)], MDX, DMX, and XML language editors for editing and debugging scripts.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="8cd45-107">學習內容</span><span class="sxs-lookup"><span data-stu-id="8cd45-107">What You Will Learn</span></span>  
 <span data-ttu-id="8cd45-108">這個教學課程將協助您了解資訊在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中的呈現方式，以及如何運用各項功能。</span><span class="sxs-lookup"><span data-stu-id="8cd45-108">This tutorial will help you understand the presentation of information in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and how to take advantage of the features.</span></span> <span data-ttu-id="8cd45-109">請注意，本教學課程適用於 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 除外之所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本所隨附的 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 完整安裝。</span><span class="sxs-lookup"><span data-stu-id="8cd45-109">Note that this tutorial applies to the complete installation of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] that is included with all editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] except [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="8cd45-110">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 隨附的 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 基本安裝和 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 安裝的功能與本教學課程呈現的功能稍微不同。</span><span class="sxs-lookup"><span data-stu-id="8cd45-110">Functionality for basic installations of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and for [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] installations that ship with [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] is slightly different than what is presented in this tutorial.</span></span>  
  
 <span data-ttu-id="8cd45-111">熟悉 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的最佳方式是親自練習。</span><span class="sxs-lookup"><span data-stu-id="8cd45-111">The best way to get acquainted with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] is through hands-on practice.</span></span> <span data-ttu-id="8cd45-112">這個教學課程將告訴您如何管理 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的元件及如何尋找您經常使用的功能。</span><span class="sxs-lookup"><span data-stu-id="8cd45-112">This tutorial will teach you how to manage the components of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and how to find the features that you use regularly.</span></span>  
  
 <span data-ttu-id="8cd45-113">本教學課程分成三個課程：</span><span class="sxs-lookup"><span data-stu-id="8cd45-113">This tutorial is divided into three lessons:</span></span>  
  
 [<span data-ttu-id="8cd45-114">第 1 課：SQL Server Management Studio 中的基本導覽</span><span class="sxs-lookup"><span data-stu-id="8cd45-114">Lesson 1: Basic Navigation in SQL Server Management Studio</span></span>](lesson-1-basic-navigation-in-sql-server-management-studio.md)  
 <span data-ttu-id="8cd45-115">在這一課，您將學習如何使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]的元件、如何重新設定環境配置，以及如何還原預設配置。</span><span class="sxs-lookup"><span data-stu-id="8cd45-115">In this lesson you will learn how to use the components of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], how to reconfigure the environment layout, and how to restore the default layout.</span></span>  
  
 [<span data-ttu-id="8cd45-116">第 2 課：撰寫 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8cd45-116">Lesson 2: Writing Transact-SQL</span></span>](lesson-2-writing-transact-sql.md)  
 <span data-ttu-id="8cd45-117">在這個課程中，您將學習如何開啟查詢編輯器、如何管理程式碼，以及如何使用查詢編輯器的其他新功能。</span><span class="sxs-lookup"><span data-stu-id="8cd45-117">In this lesson, you will learn how to open Query Editor, how to manage code, and how to use the other new features of Query Editor.</span></span>  
  
 [<span data-ttu-id="8cd45-118">第 3 課：使用範本、方案和指令碼專案</span><span class="sxs-lookup"><span data-stu-id="8cd45-118">Lesson 3: Working with Templates, Solutions, and Script Projects</span></span>](lesson-3-working-with-templates-solutions-and-script-projects.md)  
 <span data-ttu-id="8cd45-119">在這一課，您將學習如何使用範本，並將指令碼組織到方案和專案中。</span><span class="sxs-lookup"><span data-stu-id="8cd45-119">In this lesson you will learn how to use templates, and organize scripts into solutions and projects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cd45-120">需求</span><span class="sxs-lookup"><span data-stu-id="8cd45-120">Requirements</span></span>  
 <span data-ttu-id="8cd45-121">這個教學課程適用於不熟悉 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]的資深資料庫管理員和資料庫開發人員，但是這些人很熟悉資料庫概念和 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語言。</span><span class="sxs-lookup"><span data-stu-id="8cd45-121">This tutorial is intended for experienced database administrators and database developers who are not familiar with [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], but who are who are familiar with database concepts and the [!INCLUDE[tsql](../../includes/tsql-md.md)] language.</span></span>  
  
 <span data-ttu-id="8cd45-122">您的系統必須已經安裝下列項目，才能使用這個教學課程：</span><span class="sxs-lookup"><span data-stu-id="8cd45-122">Your system must have the following installed to use this tutorial:</span></span>  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="8cd45-123">或更新版本，具有 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="8cd45-123">or a later version with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample databases.</span></span> <span data-ttu-id="8cd45-124">為了加強安全性，依預設，不會安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="8cd45-124">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="8cd45-125">若要安裝範例資料庫，請參閱＜ [安裝 SQL Server 範例和範例資料庫](http://sqlserversamples.codeplex.com)＞。</span><span class="sxs-lookup"><span data-stu-id="8cd45-125">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
-   <span data-ttu-id="8cd45-126">Internet Explorer 9.0 或更新的版本。</span><span class="sxs-lookup"><span data-stu-id="8cd45-126">Internet Explorer 9.0 or later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cd45-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cd45-127">See Also</span></span>  
 [<span data-ttu-id="8cd45-128">Database Engine 教學課程</span><span class="sxs-lookup"><span data-stu-id="8cd45-128">Database Engine Tutorials</span></span>](../../relational-databases/database-engine-tutorials.md)  
  
  
