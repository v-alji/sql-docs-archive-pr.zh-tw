---
title: 關於 SQL Server 資料庫引擎 |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], installing
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 93e3d7a749fe6be47cc84d43509a6f378476b2ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701545"
---
# <a name="about-the-sql-server-database-engine"></a><span data-ttu-id="be3f3-102">關於 SQL Server Database Engine</span><span class="sxs-lookup"><span data-stu-id="be3f3-102">About the SQL Server Database Engine</span></span>
  <span data-ttu-id="be3f3-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件是用來儲存、處理及維護資料安全的核心服務。</span><span class="sxs-lookup"><span data-stu-id="be3f3-103">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is the core service for storing, processing, and securing data.</span></span> <span data-ttu-id="be3f3-104">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 提供控制存取和快速交易處理，以符合企業中最需要的資料耗用應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="be3f3-104">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] provides controlled access and rapid transaction processing to meet the requirements of the most demanding data consuming applications in your enterprise.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="be3f3-105">在單一電腦上最多支援 50 個 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="be3f3-105">supports up to 50 instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on a single computer.</span></span> <span data-ttu-id="be3f3-106">若要建立一般 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝，請參閱安裝[程式中的 Install SQL Server 2014 &#40;安裝&#41;](install-sql-server-from-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="be3f3-106">To create a typical [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
 <span data-ttu-id="be3f3-107">**重要事項**若為本機安裝，您必須以系統管理員的身分執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="be3f3-107">**Important** For local installations, you must run Setup as an administrator.</span></span> <span data-ttu-id="be3f3-108">如果您是從遠端共用位置安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，則必須使用對遠端共用位置具有讀取和執行權限的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="be3f3-108">If you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a remote share, you must use a domain account that has read and execute permissions on the remote share.</span></span>  
  
 <span data-ttu-id="be3f3-109">當您在 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈] 的 [要安裝的元件] 頁面上選取 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine] 時，會安裝下列功能：</span><span class="sxs-lookup"><span data-stu-id="be3f3-109">The following features are installed when you select **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine** on the Components to Install page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard:</span></span>  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   <span data-ttu-id="be3f3-110">複寫 (選擇性元件)</span><span class="sxs-lookup"><span data-stu-id="be3f3-110">Replication - is an optional component</span></span>  
  
-   <span data-ttu-id="be3f3-111">全文檢索搜尋 (選擇性元件)</span><span class="sxs-lookup"><span data-stu-id="be3f3-111">Full-Text Search - is an optional component</span></span>  
  
-   <span data-ttu-id="be3f3-112">Data Quality Services (選擇性元件)</span><span class="sxs-lookup"><span data-stu-id="be3f3-112">Data Quality Services - is an optional component</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="be3f3-113">在這版的安裝程式中選取 [Data Quality Services] 核取方塊，並不會安裝 Data Quality Services (DQS) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="be3f3-113">In this release, selecting the **Data Quality Services** check box in setup does not install the Data Quality Services (DQS) server.</span></span> <span data-ttu-id="be3f3-114">您必須執行額外的安裝後步驟，才能安裝 DQS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="be3f3-114">You will have to perform additional steps post installation to install DQS server.</span></span> <span data-ttu-id="be3f3-115">如需詳細資訊，請參閱 [安裝 Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)。</span><span class="sxs-lookup"><span data-stu-id="be3f3-115">For more information, see [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).</span></span>  
  
 <span data-ttu-id="be3f3-116">下列其他功能是許多典型使用者案例的選項：</span><span class="sxs-lookup"><span data-stu-id="be3f3-116">The following additional features are options for many typical user scenarios:</span></span>  
  
-   <span data-ttu-id="be3f3-117">Data Quality Client</span><span class="sxs-lookup"><span data-stu-id="be3f3-117">Data Quality Client</span></span>  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   <span data-ttu-id="be3f3-118">連接元件</span><span class="sxs-lookup"><span data-stu-id="be3f3-118">Connectivity components</span></span>  
  
-   <span data-ttu-id="be3f3-119">程式設計模型</span><span class="sxs-lookup"><span data-stu-id="be3f3-119">Programming models</span></span>  
  
-   <span data-ttu-id="be3f3-120">管理工具</span><span class="sxs-lookup"><span data-stu-id="be3f3-120">Management tools</span></span>  
  
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
-   <span data-ttu-id="be3f3-121">文件集元件</span><span class="sxs-lookup"><span data-stu-id="be3f3-121">Documentation components</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be3f3-122">根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程序中不會安裝範例資料庫和範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="be3f3-122">By default, sample databases and sample code are not installed as part of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="be3f3-123">若要安裝範例資料庫和範例程式碼，請參閱 [CodePlex 網站](https://go.microsoft.com/fwlink/?LinkId=87843)。</span><span class="sxs-lookup"><span data-stu-id="be3f3-123">To install sample databases and sample code, see the [CodePlex Web site](https://go.microsoft.com/fwlink/?LinkId=87843).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be3f3-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be3f3-124">See Also</span></span>  
 <span data-ttu-id="be3f3-125">[SQL Server 2014 版本所支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="be3f3-125">[Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="be3f3-126">[SQL Server 2014 的版本和元件](../../sql-server/editions-and-components-of-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="be3f3-126">[Editions and Components of SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) </span></span>  
 <span data-ttu-id="be3f3-127">[規劃 SQL Server 安裝](../../sql-server/install/planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="be3f3-127">[Planning a SQL Server Installation](../../sql-server/install/planning-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="be3f3-128">[高可用性解決方案 &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="be3f3-128">[High Availability Solutions &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span></span>  
 [<span data-ttu-id="be3f3-129">使用安裝精靈 &#40;安裝程式升級至 SQL Server 2014&#41;</span><span class="sxs-lookup"><span data-stu-id="be3f3-129">Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;</span></span>](upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
