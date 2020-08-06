---
title: SharePoint 模式下 Reporting Services 的硬體和軟體需求 |Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ed91877d-4f74-4266-a932-b824b4810c99
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a4fc19b2871d7d5731649c61a8d5231d7e3479dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606053"
---
# <a name="hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode"></a><span data-ttu-id="9a0d9-102">SharePoint 模式的 Reporting Services 之硬體和軟體需求</span><span class="sxs-lookup"><span data-stu-id="9a0d9-102">Hardware and Software Requirements for Reporting Services in SharePoint Mode</span></span>

  <span data-ttu-id="9a0d9-103">本主題描述以 SharePoint 模式執行的必要條件、硬體需求和安裝考慮 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-103">This topic describes prerequisites, hardware requirements, and installation considerations for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] running in SharePoint mode.</span></span> <span data-ttu-id="9a0d9-104">由於 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式需要 SharePoint 伺服器，因此大部分需求都是以 SharePoint 環境為基礎。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-104">Because [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode requires a SharePoint server, most of the requirements are based on the SharePoint environment.</span></span> <span data-ttu-id="9a0d9-105">若是原生模式報表伺服器，您的硬體應符合執行 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的最低硬體和軟體需求。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-105">For native mode report servers, your hardware should meet minimum hardware and software requirements for running [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9a0d9-106">如需詳細資訊，請參閱＜ [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-106">For more information, see [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
-   [<span data-ttu-id="9a0d9-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="9a0d9-107">Prerequisites</span></span>](#bkmk_prereq)  
  
-   [<span data-ttu-id="9a0d9-108">報表伺服器資料庫需求</span><span class="sxs-lookup"><span data-stu-id="9a0d9-108">Report Server Database Requirements</span></span>](#bkmk_report_server_database)  
  
-   [<span data-ttu-id="9a0d9-109">Power View 需求</span><span class="sxs-lookup"><span data-stu-id="9a0d9-109">Power View Requirements</span></span>](#bkmk_powerview)  
  
-   [<span data-ttu-id="9a0d9-110">其他資訊</span><span class="sxs-lookup"><span data-stu-id="9a0d9-110">More Information</span></span>](#bkmk_more_information)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="9a0d9-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="9a0d9-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="9a0d9-112">若為本機安裝，在 SharePoint 和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝時登入的帳戶必須是本機作業系統中系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-112">For local installations, the account logged in during installation of SharePoint and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] needs to be a member of the administrators group in the local operating system.</span></span> <span data-ttu-id="9a0d9-113">安裝程式帳戶不必是 SharePoint 伺服器陣列管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-113">The setup account does not need to be a member of the SharePoint farm administrators group.</span></span>  
  
     <span data-ttu-id="9a0d9-114">如需詳細資訊，請參閱 [SharePoint 2013 中的帳戶權限及安全性設定](https://technet.microsoft.com/library/cc678863.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-114">For more information, see [Account permissions and security settings in SharePoint 2013](https://technet.microsoft.com/library/cc678863.aspx).</span></span>  
  
-   <span data-ttu-id="9a0d9-115">以 SharePoint 模式執行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 需要 SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] running in SharePoint mode requires SharePoint Server.</span></span> <span data-ttu-id="9a0d9-116">如需有關 SharePoint 需求和組態的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="9a0d9-116">For more information about SharePoint requirements and configurations, see the following:</span></span>  
  
    -   <span data-ttu-id="9a0d9-117">[ (SharePoint 2013)  (的硬體和軟體需求](https://go.microsoft.com/fwlink/p/?LinkId=256365)https://go.microsoft.com/fwlink/p/?LinkId=256365)</span><span class="sxs-lookup"><span data-stu-id="9a0d9-117">[Hardware and software requirements (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=256365) (https://go.microsoft.com/fwlink/p/?LinkId=256365)</span></span>  
  
    -   [<span data-ttu-id="9a0d9-118">SharePoint Server 2013 的容量管理和調整大小</span><span class="sxs-lookup"><span data-stu-id="9a0d9-118">Capacity management and sizing for SharePoint Server 2013</span></span>](https://technet.microsoft.com/library/cc261700.aspx)  
  
    -   [<span data-ttu-id="9a0d9-119">商業智慧的軟體需求 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="9a0d9-119">Software requirements for business intelligence (SharePoint 2013)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=256367)  
  
    -   <span data-ttu-id="9a0d9-120">[硬體和軟體需求 (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262485\(v=office.14\))</span><span class="sxs-lookup"><span data-stu-id="9a0d9-120">[Hardware and software requirements (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262485\(v=office.14\))</span></span>  
  
    -   <span data-ttu-id="9a0d9-121">[SharePoint Server 2010 的容量管理和調整大小](https://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))</span><span class="sxs-lookup"><span data-stu-id="9a0d9-121">[Capacity management and sizing for SharePoint Server 2010](https://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))</span></span>  
  
-   <span data-ttu-id="9a0d9-122">如果您要使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 升級或更新現有的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]SharePoint 安裝，請參閱＜ [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)的最低硬體和軟體需求。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-122">If you want to upgrade or update existing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint installation with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).</span></span>  
  
-   <span data-ttu-id="9a0d9-123">確認已在 Windows 伺服器管理員中啟動 **[SharePoint 2013 Administration]** 服務。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-123">Verify the **SharePoint 2013 Administration** service is started in Windows Server Manager.</span></span>  
  
###  <a name="report-server-database-requirements"></a><a name="bkmk_report_server_database"></a><span data-ttu-id="9a0d9-124">報表伺服器資料庫需求</span><span class="sxs-lookup"><span data-stu-id="9a0d9-124">Report Server Database Requirements</span></span>  
  
-   <span data-ttu-id="9a0d9-125">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 和 SharePoint 產品及技術都使用 SQL Server 關聯式資料庫儲存應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-125">Both [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and SharePoint products and technologies use SQL Server relational databases to store application data.</span></span>  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] <span data-ttu-id="9a0d9-126">需要相容 SQL Server 版本的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-126">requires an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] of a compatible SQL Server edition.</span></span> <span data-ttu-id="9a0d9-127">如需有關硬體和軟體需求的詳細資訊，請參閱＜ [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-127">For more information on hardware and software requirements, see [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
-   <span data-ttu-id="9a0d9-128">SharePoint 產品可以使用現有的資料庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-128">SharePoint products can use an existing database instance.</span></span> <span data-ttu-id="9a0d9-129">如果沒有安裝 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體，SharePoint 產品安裝程式會安裝 SQL Server Express Edition 做為 SharePoint 應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-129">If an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] is not installed, the SharePoint Products Setup program installs SQL Server Express Edition for the SharePoint application databases.</span></span>  
  
-   <span data-ttu-id="9a0d9-130">報表伺服器執行個體無法使用 SQL Server Express Edition 做為其資料庫；</span><span class="sxs-lookup"><span data-stu-id="9a0d9-130">The report server instance cannot use the SQL Server Express Edition for its database.</span></span> <span data-ttu-id="9a0d9-131">但是，由 SharePoint 產品所安裝的 SQL Server Express Edition 執行個體可以與其他 Database Engine 版本並存。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-131">However, the SQL Server Express Edition instance installed by the SharePoint product can exist side-by-side with other Database Engine editions.</span></span>  
  
##  <a name="sscrescent-requirements"></a><a name="bkmk_powerview"></a><span data-ttu-id="9a0d9-132">[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]需求</span><span class="sxs-lookup"><span data-stu-id="9a0d9-132">[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Requirements</span></span>

 <span data-ttu-id="9a0d9-133">請檢閱 Office.Microsoft.com 上最新的 [Power View 文件集](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-133">Review the most up-to-date [Power View documentation](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) on Office.Microsoft.com.</span></span> [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] <span data-ttu-id="9a0d9-134">是 Microsoft Excel 2013 的一項功能，而且屬於適用於 Microsoft SharePoint Server 2010 和 2013 Enterprise 版之 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services 增益集的一部分。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-134">is a feature of Microsoft Excel 2013, and is part of the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services add-in for Microsoft SharePoint Server 2010 and 2013 Enterprise Editions.</span></span>  
  
##  <a name="more-information"></a><a name="bkmk_more_information"></a> <span data-ttu-id="9a0d9-135">其他資訊</span><span class="sxs-lookup"><span data-stu-id="9a0d9-135">More Information</span></span>

 <span data-ttu-id="9a0d9-136">如需 SharePoint 變更的相關資訊，請參閱[從 sharepoint 2010 變更為 sharepoint 2013](https://technet.microsoft.com/library/ff607742\(office.15\).aspx) (https://technet.microsoft.com/library/ff607742(office.15).aspx) 。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-136">For information on SharePoint changes, see [Changes from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/library/ff607742\(office.15\).aspx) (https://technet.microsoft.com/library/ff607742(office.15).aspx).</span></span>  
  
 <span data-ttu-id="9a0d9-137">[SQL Server 2014 版本](https://go.microsoft.com/fwlink/?LinkID=296445)資訊。</span><span class="sxs-lookup"><span data-stu-id="9a0d9-137">[SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/?LinkID=296445).</span></span>  
  
