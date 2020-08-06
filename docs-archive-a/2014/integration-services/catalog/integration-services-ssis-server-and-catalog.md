---
title: Integration Services (SSIS) 伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0da83cdac269499dfbde7a6387a4af4690c83ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597286"
---
# <a name="integration-services-ssis-server"></a><span data-ttu-id="55247-102">Integration Services (SSIS) 伺服器</span><span class="sxs-lookup"><span data-stu-id="55247-102">Integration Services (SSIS) Server</span></span>
  <span data-ttu-id="55247-103">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中設計和測試封裝之後，可以將含有那些封裝的專案部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="55247-103">After you design and test packages in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], you can deploy the projects that contain the packages to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="55247-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器為主控 `SSISDB` 資料庫之 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="55247-104">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server is an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the `SSISDB` database.</span></span> <span data-ttu-id="55247-105">資料庫會儲存封裝、專案、參數、權限、伺服器屬性與作業歷程記錄等物件。</span><span class="sxs-lookup"><span data-stu-id="55247-105">The database stores the following objects: packages, projects, parameters, permissions, server properties, and operational history.</span></span>  
  
 <span data-ttu-id="55247-106">`SSISDB` 資料庫會透過可供您查詢的公用檢視，公開物件資訊。</span><span class="sxs-lookup"><span data-stu-id="55247-106">The `SSISDB` database exposes the object information in public views that you can query.</span></span> <span data-ttu-id="55247-107">此資料庫也會提供預存程序，讓您可加以呼叫來管理物件。</span><span class="sxs-lookup"><span data-stu-id="55247-107">The database also provides stored procedures that you can call to manage the objects.</span></span>  
  
 <span data-ttu-id="55247-108">在您將專案部署至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器之前，必須先建立 `SSISDB` 目錄。</span><span class="sxs-lookup"><span data-stu-id="55247-108">Before you can deploy the projects to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, you need to create the `SSISDB` catalog.</span></span>  
  
 <span data-ttu-id="55247-109">如需 SSISDB 目錄功能的概觀，請參閱 [SSIS 目錄](ssis-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="55247-109">For an overview of the SSISDB catalog functionality, see [SSIS Catalog](ssis-catalog.md).</span></span>  
  
## <a name="high-availability"></a><span data-ttu-id="55247-110">高可用性</span><span class="sxs-lookup"><span data-stu-id="55247-110">High Availability</span></span>  
 <span data-ttu-id="55247-111">與其他使用者資料庫一樣，`SSISDB` 資料庫也支援資料庫鏡像和複寫。</span><span class="sxs-lookup"><span data-stu-id="55247-111">Like other user databases, the `SSISDB` database does support database mirroring and replication.</span></span> <span data-ttu-id="55247-112">如需鏡像及複寫的詳細資訊，請參閱[資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="55247-112">For more information about mirroring and replication, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="55247-113">您也可以使用 SSIS 和 AlwaysOn 可用性群組提供 SSISDB 及其內容的高可用性。</span><span class="sxs-lookup"><span data-stu-id="55247-113">You can also provide high-availability of SSISDB and its contents by making use of SSIS and AlwaysOn Availability Groups.</span></span> <span data-ttu-id="55247-114">如需詳細資訊，請參閱 blogs.msdn.com 上這篇 Matt Masson 的部落格文章： [SSIS 與 AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873)。</span><span class="sxs-lookup"><span data-stu-id="55247-114">For more information, see this blog post by Matt Masson, [SSIS with AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873), at blogs.msdn.com.</span></span>  
  
##  <a name="integration-services-server-in-sql-server-management-studio"></a><a name="ssms"></a><span data-ttu-id="55247-115">SQL Server Management Studio 中的 Integration Services Server</span><span class="sxs-lookup"><span data-stu-id="55247-115">Integration Services Server in SQL Server Management Studio</span></span>  
 <span data-ttu-id="55247-116">當您連接到主控 `SSISDB` 資料庫的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體時，您會在 [物件總管] 中看到以下物件：</span><span class="sxs-lookup"><span data-stu-id="55247-116">When you connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the `SSISDB` database, you see the following objects in Object Explorer:</span></span>  
  
-   <span data-ttu-id="55247-117">**SSISDB 資料庫**</span><span class="sxs-lookup"><span data-stu-id="55247-117">**SSISDB Database**</span></span>  
  
     <span data-ttu-id="55247-118">`SSISDB`資料庫會出現在 [物件流覽] 的 [**資料庫**] 節點底下。</span><span class="sxs-lookup"><span data-stu-id="55247-118">The `SSISDB` database appears under the **Databases** node in Object Explore.</span></span> <span data-ttu-id="55247-119">您可以查詢檢視，並呼叫管理 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器和儲存在伺服器上之物件的預存程序。</span><span class="sxs-lookup"><span data-stu-id="55247-119">You can query the views and call the stored procedures that manage the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server and the objects that are stored on the server.</span></span>  
  
-   <span data-ttu-id="55247-120">**Integration Services 目錄**</span><span class="sxs-lookup"><span data-stu-id="55247-120">**Integration Services Catalogs**</span></span>  
  
     <span data-ttu-id="55247-121">**[Integration Services 目錄]** 節點下方有 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案和環境的資料夾。</span><span class="sxs-lookup"><span data-stu-id="55247-121">Under the **Integration Services Catalogs** node there are folders for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] projects and environments.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="55247-122">相關工作</span><span class="sxs-lookup"><span data-stu-id="55247-122">Related Tasks</span></span>  
  
-   [<span data-ttu-id="55247-123">建立 SSIS 目錄</span><span class="sxs-lookup"><span data-stu-id="55247-123">Create the SSIS Catalog</span></span>](../create-the-ssis-catalog.md)  
  
-   [<span data-ttu-id="55247-124">檢視 Integration Services 伺服器上的套件清單</span><span class="sxs-lookup"><span data-stu-id="55247-124">View the List of Packages on the Integration Services Server</span></span>](view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [<span data-ttu-id="55247-125">將專案部署至 Integration Services 伺服器</span><span class="sxs-lookup"><span data-stu-id="55247-125">Deploy Projects to Integration Services Server</span></span>](../deploy-projects-to-integration-services-server.md)  
  
-   [<span data-ttu-id="55247-126">使用 SQL Server Management Studio 在 SSIS 伺服器上執行套件</span><span class="sxs-lookup"><span data-stu-id="55247-126">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>](../run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a><span data-ttu-id="55247-127">相關內容</span><span class="sxs-lookup"><span data-stu-id="55247-127">Related Content</span></span>  
 <span data-ttu-id="55247-128">blogs.msdn.com 上的部落格文章： [SSIS 與 AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873)。</span><span class="sxs-lookup"><span data-stu-id="55247-128">Blog entry, [SSIS with AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873), at blogs.msdn.com.</span></span>  
  
  
