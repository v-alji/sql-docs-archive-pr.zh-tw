---
title: 規劃 SQL Server 安裝 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, planning
ms.assetid: b1d56f2f-603f-48f2-b902-c715f14a6db9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e5b1dae9d2ef32298a9ddf2eeed1530e5ae97683
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598722"
---
# <a name="planning-a-sql-server-installation"></a><span data-ttu-id="94714-102">規劃 SQL Server 安裝</span><span class="sxs-lookup"><span data-stu-id="94714-102">Planning a SQL Server Installation</span></span>
  <span data-ttu-id="94714-103">若要安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="94714-103">To install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], follow these steps:</span></span>  
  
-   <span data-ttu-id="94714-104">檢閱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝的安裝需求、系統組態檢查與安全性考量。</span><span class="sxs-lookup"><span data-stu-id="94714-104">Review installation requirements, system configuration checks, and security considerations for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
-   <span data-ttu-id="94714-105">執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式來安裝或升級至更新版本。</span><span class="sxs-lookup"><span data-stu-id="94714-105">Run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to install or upgrade to a later version.</span></span>  
  
-   <span data-ttu-id="94714-106">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式來設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="94714-106">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilities to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="94714-107">除非軟體的使用方式受到個別的合約 (例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 大量授權合約或與 ISV 或 OEM 簽訂的協力廠商合約) 所管制，否則不論安裝方法為何，您都必須確認以個人身分或代表實體接受軟體授權條款。</span><span class="sxs-lookup"><span data-stu-id="94714-107">Regardless of the installation method, you are required to confirm acceptance of the software license terms as an individual or on behalf of an entity, unless your use of the software is governed by a separate agreement such as a [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing agreement or a third-party agreement with an ISV or OEM.</span></span>  
  
 <span data-ttu-id="94714-108">這些授權條款會顯示在安裝程式使用者介面中，供您檢閱和接受。</span><span class="sxs-lookup"><span data-stu-id="94714-108">The license terms are displayed for review and acceptance in the Setup user interface.</span></span> <span data-ttu-id="94714-109">自動安裝 (使用 /Q 或 /QS 參數) 必須包括 /IAcceptSQLServerLicenseTerms 參數。</span><span class="sxs-lookup"><span data-stu-id="94714-109">Unattended installations (using the /Q or /QS parameters) must include the /IAcceptSQLServerLicenseTerms parameter.</span></span> <span data-ttu-id="94714-110">您可以另外在 [Microsoft 軟體授權合約](https://go.microsoft.com/fwlink/?LinkID=148209)檢閱授權條款。</span><span class="sxs-lookup"><span data-stu-id="94714-110">You can review the license terms separately at [Microsoft Software License Terms](https://go.microsoft.com/fwlink/?LinkID=148209).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="94714-111">根據您收到本軟體的方式 (例如，透過 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 大量授權)，軟體的使用方式可能會受到其他條款與條件的限制。</span><span class="sxs-lookup"><span data-stu-id="94714-111">Depending on how you received the software (for example, through [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing), your use of the software may be subject to additional terms and conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94714-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="94714-112">In This Section</span></span>  
 [<span data-ttu-id="94714-113">SQL Server 安裝的新增功能</span><span class="sxs-lookup"><span data-stu-id="94714-113">What's New in SQL Server Installation</span></span>](../../../2014/sql-server/install/what-s-new-in-sql-server-installation.md)  
 <span data-ttu-id="94714-114">本主題描述有關這一版 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中新增或改進安裝功能的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="94714-114">This topic describes the details about the new or improved features of installation in this version of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="94714-115">安裝 SQL Server 2014 的硬體與軟體需求</span><span class="sxs-lookup"><span data-stu-id="94714-115">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
 <span data-ttu-id="94714-116">本主題列出安裝和執行 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]執行個體的最低軟硬體需求。</span><span class="sxs-lookup"><span data-stu-id="94714-116">This topic lists the minimum hardware and software requirements to install and run an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="94714-117">SQL Server 安裝的安全性考量</span><span class="sxs-lookup"><span data-stu-id="94714-117">Security Considerations for a SQL Server Installation</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
 <span data-ttu-id="94714-118">本主題說明您在安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前及安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之後應該考慮的一些安全性最佳做法。</span><span class="sxs-lookup"><span data-stu-id="94714-118">This topic describes some security best practices that you should consider before you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and after you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="94714-119">設定 Windows 服務帳戶與權限</span><span class="sxs-lookup"><span data-stu-id="94714-119">Configure Windows Service Accounts and Permissions</span></span>](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
 <span data-ttu-id="94714-120">本主題描述此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本的預設服務組態，以及可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝期間和安裝完成後設定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務組態選項。</span><span class="sxs-lookup"><span data-stu-id="94714-120">This topic describes the default configuration of services in this release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and configuration options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services that you can set during and after [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
 [<span data-ttu-id="94714-121">網路通訊協定和網路程式庫</span><span class="sxs-lookup"><span data-stu-id="94714-121">Network Protocols and Network Libraries</span></span>](../../../2014/sql-server/install/network-protocols-and-network-libraries.md)  
 <span data-ttu-id="94714-122">本主題描述這一版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中網路通訊協定的預設組態，以及可用的組態選項。</span><span class="sxs-lookup"><span data-stu-id="94714-122">This topic describes the default configuration of network protocols in this release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and the configuration options available.</span></span>  
  
 [<span data-ttu-id="94714-123">使用 SQL Server 的多個版本和實例</span><span class="sxs-lookup"><span data-stu-id="94714-123">Work with Multiple Versions and Instances of SQL Server</span></span>](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)  
 <span data-ttu-id="94714-124">本主題描述安裝多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本及執行個體的考量。</span><span class="sxs-lookup"><span data-stu-id="94714-124">This topic describes the considerations for installing multiple versions and instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="94714-125">SQL Server 中的地區語言版本</span><span class="sxs-lookup"><span data-stu-id="94714-125">Local Language Versions in SQL Server</span></span>](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
 <span data-ttu-id="94714-126">本主題描述有關 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的當地語系化版本。</span><span class="sxs-lookup"><span data-stu-id="94714-126">This topic describes about the localized versions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="94714-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="94714-127">Related Sections</span></span>  
 [<span data-ttu-id="94714-128">安裝 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="94714-128">Install SQL Server 2014</span></span>](../../database-engine/install-windows/install-sql-server.md)  
 <span data-ttu-id="94714-129">本節提供可以用於安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]之不同安裝選項的概觀。</span><span class="sxs-lookup"><span data-stu-id="94714-129">This section provides an overview of different installation options we have for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="94714-130">安裝 SQL Server 2014 BI 功能</span><span class="sxs-lookup"><span data-stu-id="94714-130">Install SQL Server 2014 BI Features</span></span>](install-sql-server-business-intelligence-features.md)  
 <span data-ttu-id="94714-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式文件集的這一節說明如何安裝屬於 Microsoft BI 平台一部分的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="94714-131">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features that are part of the Microsoft BI platform.</span></span>  
  
 [<span data-ttu-id="94714-132">升級為 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="94714-132">Upgrade to SQL Server 2014</span></span>](../../database-engine/install-windows/upgrade-sql-server.md)  
 <span data-ttu-id="94714-133">本節提供將舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的概觀。</span><span class="sxs-lookup"><span data-stu-id="94714-133">The section provides an overview of upgrading instances of previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="94714-134">解除安裝 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="94714-134">Uninstall SQL Server 2014</span></span>](uninstall-sql-server.md)  
 <span data-ttu-id="94714-135">請參閱本節完整解除安裝現存的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 執行個體，並將系統準備好重新安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="94714-135">Refer this section to uninstall an existing instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] completely, and prepare the system so that you can reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="94714-136">SQL Server 容錯移轉叢集安裝</span><span class="sxs-lookup"><span data-stu-id="94714-136">SQL Server Failover Cluster Installation</span></span>](../failover-clusters/install/sql-server-failover-cluster-installation.md)  
 <span data-ttu-id="94714-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式文件集中的這一節將說明如何安裝及設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集。</span><span class="sxs-lookup"><span data-stu-id="94714-137">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install, and configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94714-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94714-138">See Also</span></span>  
 <span data-ttu-id="94714-139">[SQL Server 2014 的快速入門安裝](../../../2014/getting-started/quick-start-installation-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="94714-139">[Quick-Start Installation of SQL Server 2014](../../../2014/getting-started/quick-start-installation-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="94714-140">[從命令提示字元安裝 SQL Server 2014](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="94714-140">[Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="94714-141">[高可用性解決方案 &#40;SQL Server&#41;](../failover-clusters/high-availability-solutions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="94714-141">[High Availability Solutions &#40;SQL Server&#41;](../failover-clusters/high-availability-solutions-sql-server.md) </span></span>  
 <span data-ttu-id="94714-142">[安裝容錯移轉叢集之前](../failover-clusters/install/before-installing-failover-clustering.md) </span><span class="sxs-lookup"><span data-stu-id="94714-142">[Before Installing Failover Clustering](../failover-clusters/install/before-installing-failover-clustering.md) </span></span>  
 [<span data-ttu-id="94714-143">使用安裝精靈 &#40;安裝程式升級至 SQL Server 2014&#41;</span><span class="sxs-lookup"><span data-stu-id="94714-143">Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;</span></span>](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
