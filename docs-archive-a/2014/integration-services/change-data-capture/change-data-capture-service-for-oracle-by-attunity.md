---
title: Attunity Oracle 異動資料擷取服務 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 22ec8a5c-9550-4d38-8a4a-485ec3e53ea8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68e68e9edd91bd1d0c718b32e29c3b29f74778c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596863"
---
# <a name="change-data-capture-service-for-oracle-by-attunity"></a><span data-ttu-id="3a1c8-102">Attunity Oracle 異動資料擷取服務</span><span class="sxs-lookup"><span data-stu-id="3a1c8-102">Change Data Capture Service for Oracle by Attunity</span></span>
  <span data-ttu-id="3a1c8-103">Oracle CDC 服務是一種 Windows 服務，可掃描 Oracle 交易記錄，並將相關 Oracle 資料表的變更擷取到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 變更資料表中。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-103">The CDC Service for Oracle is a Windows service that scans Oracle transaction logs and captures changes to Oracle tables of interest into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] change tables.</span></span> <span data-ttu-id="3a1c8-104">用來儲存從 Oracle 擷取之變更的 SQL 變更資料表與原生 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 異動資料擷取功能中所使用的變更資料表類型相同。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-104">The SQL change tables where the changes captured from Oracle are stored are the same type of change tables used in the native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Change Data Capture feature.</span></span> <span data-ttu-id="3a1c8-105">如此一來，取用這些變更就像取用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫變更一樣輕鬆。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-105">This makes consuming these changes as easy as consuming changes made to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="3a1c8-106">安裝</span><span class="sxs-lookup"><span data-stu-id="3a1c8-106">Installation</span></span>  
 <span data-ttu-id="3a1c8-107">Oracle CDC 服務可以安裝在任何支援的 Windows 電腦上，該電腦可存取正在擷取的來源 Oracle 資料庫以及目標 CDC 資料庫所在的目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-107">The CDC Service for Oracle can be installed on any supported Windows computer with access to the source Oracle database(s) being captured and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance where the target CDC database resides.</span></span> <span data-ttu-id="3a1c8-108">CDC 服務不需要 Oracle 資料庫或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的本機安裝，而只需要其支援的用戶端。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-108">The CDC Service does not need a local installation of the Oracle database or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, only their supported clients.</span></span> <span data-ttu-id="3a1c8-109">如需有關要在何處安裝必要資料庫元件的詳細資訊，請參閱本主題的＜ **資料庫必要條件** ＞。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-109">For information about where to install the required database components, see **Database Prerequisites** in this topic.</span></span>  
  
 <span data-ttu-id="3a1c8-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 服務的安裝會將服務組態 UI 和服務程式放在選取的位置。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-110">The installation of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC Service for Oracle places the service configuration UI and the service program in the selected location.</span></span> <span data-ttu-id="3a1c8-111">Oracle CDC 服務是使用 Oracle CDC 服務組態主控台所單獨設定。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-111">The CDC Service for Oracle is configured separately using the Oracle CDC Service Configuration Console.</span></span> <span data-ttu-id="3a1c8-112">如需有關設定 Oracle CDC 服務的詳細資訊，請參閱＜ [Attunity 的 Oracle 變更資料擷取 (CDC) 服務 F1 說明](change-data-capture-service-for-oracle-by-attunity-f1-help.md)＞。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-112">For more information on configuring the Oracle CDC Service, see [Change Data Capture Service for Oracle by Attunity F1 Help](change-data-capture-service-for-oracle-by-attunity-f1-help.md).</span></span>  
  
 <span data-ttu-id="3a1c8-113">若要安裝 Oracle CDC 服務，請從 SQL Server 安裝媒體手動執行**AttunityOracleCdcService.msi** 。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-113">To install the CDC Service for Oracle, manually run **AttunityOracleCdcService.msi** from the SQL Server installation media.</span></span> <span data-ttu-id="3a1c8-114">X86 和 x64 的安裝套件位於 SQL Server 安裝媒體上的 \*\*.\Tools\AttunityCDCOracle \\ \*\*中。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-114">Installation packages for x86 and x64 are located in **.\Tools\AttunityCDCOracle\\** on the SQL Server installation media.</span></span>  
  
 <span data-ttu-id="3a1c8-115">Oracle CDC 服務可以安裝在任何支援的 Windows 電腦上，該電腦上已安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client；此服務不需要安裝在目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝所在的相同電腦上。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-115">The CDC Service for Oracle can be installed on any supported Windows computer where the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client is installed; it does not need to be installed on the same computer where the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
## <a name="supported-windows-environments"></a><span data-ttu-id="3a1c8-116">支援的 Windows 環境</span><span class="sxs-lookup"><span data-stu-id="3a1c8-116">Supported Windows Environments</span></span>  
 <span data-ttu-id="3a1c8-117">Attunity Oracle Change Data Capture (CDC) 服務可在以下 Windows 環境中執行：</span><span class="sxs-lookup"><span data-stu-id="3a1c8-117">The Change Data Capture Service for Oracle by Attunity can run in the following Windows environments:</span></span>  
  
-   <span data-ttu-id="3a1c8-118">Windows 8</span><span class="sxs-lookup"><span data-stu-id="3a1c8-118">Windows 8</span></span>  
  
-   <span data-ttu-id="3a1c8-119">Windows 7 32 位元 (x86) 和 64 位元 (x64)</span><span class="sxs-lookup"><span data-stu-id="3a1c8-119">Windows 7 32-bit (x86) and 64-bit (x64)</span></span>  
  
-   <span data-ttu-id="3a1c8-120">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3a1c8-120">Windows Server 2012</span></span>  
  
-   <span data-ttu-id="3a1c8-121">Windows Server 2008 R2 (含 Service Pack 1)</span><span class="sxs-lookup"><span data-stu-id="3a1c8-121">Windows Server 2008 R2 with Service Pack 1</span></span>  
  
-   <span data-ttu-id="3a1c8-122">Windows Server 2008 32 位元 (x86) 和 64 位元 (x64)，含 Service Pack 2</span><span class="sxs-lookup"><span data-stu-id="3a1c8-122">Windows Server 2008 32-bit (x86) and 64-bit (x64) with Service Pack 2</span></span>  
  
## <a name="database-prerequisites"></a><span data-ttu-id="3a1c8-123">資料庫必要條件</span><span class="sxs-lookup"><span data-stu-id="3a1c8-123">Database Prerequisites</span></span>  
 <span data-ttu-id="3a1c8-124">若要使用 Oracle CDC 服務，您必須安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client Oracle 軟體。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-124">To work with the CDC Service for Oracle you must install the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client Oracle software.</span></span> <span data-ttu-id="3a1c8-125">這是應該從 Oracle 取得的必要元件，而且必須在安裝 Oracle CDC 服務之前安裝。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-125">This is a prerequisite that should be obtained from Oracle and installed before installing the Oracle CDC Service.</span></span> <span data-ttu-id="3a1c8-126">此外，您也需要使用 SQL Server 安裝程式安裝 SQL Server ODBC 用戶端。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-126">Additionally, you need to install the SQL Server ODBC Client using SQL Server Setup.</span></span>  
  
 <span data-ttu-id="3a1c8-127">Oracle CDC 服務支援以下版本：</span><span class="sxs-lookup"><span data-stu-id="3a1c8-127">The CDC Service for Oracle supports the following versions:</span></span>  
  
### <a name="source-oracle-database"></a><span data-ttu-id="3a1c8-128">來源 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="3a1c8-128">Source Oracle Database</span></span>  
  
-   <span data-ttu-id="3a1c8-129">Oracle Database 11x，任何版本</span><span class="sxs-lookup"><span data-stu-id="3a1c8-129">Oracle Database 11x, any version</span></span>  
  
-   <span data-ttu-id="3a1c8-130">Oracle Database 10x，任何版本</span><span class="sxs-lookup"><span data-stu-id="3a1c8-130">Oracle Database 10x, any version</span></span>  
  
### <a name="target-sql-server-database"></a><span data-ttu-id="3a1c8-131">目標 SQL Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="3a1c8-131">Target SQL Server Database</span></span>  
 <span data-ttu-id="3a1c8-132">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-132">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="running-the-installation-program"></a><span data-ttu-id="3a1c8-133">執行安裝程式</span><span class="sxs-lookup"><span data-stu-id="3a1c8-133">Running the Installation Program</span></span>  
 <span data-ttu-id="3a1c8-134">若要安裝 Oracle CDC 服務，請開啟您所使用之 Windows 平台 (32/64 位元) 所適用的安裝精靈，然後依照畫面上的指示進行。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-134">To install the CDC Service for Oracle, open the installation wizard for the Windows platform you are using (32/64-bit) and follow the directions on the screen.</span></span>  
  
## <a name="uninstalling-change-data-capture-service-for-oracle-by-attunity"></a><span data-ttu-id="3a1c8-135">解除安裝 Attunity Oracle Change Data Capture (CDC) 服務</span><span class="sxs-lookup"><span data-stu-id="3a1c8-135">Uninstalling Change Data Capture Service for Oracle by Attunity</span></span>  
 <span data-ttu-id="3a1c8-136">使用 [控制台] 的 [程式和功能] 解除安裝 Oracle CDC 服務。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-136">You uninstall the CDC Service for Oracle using Control Panel, Programs and Features.</span></span>  
  
 <span data-ttu-id="3a1c8-137">解除安裝 CDC 服務並不會刪除所建立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-137">Uninstalling the CDC Service does not delete the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases created.</span></span> <span data-ttu-id="3a1c8-138">若要完全移除此工具，您必須移除 MSXDBCDC 資料庫以及您在使用之目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中所建立的特定 CDC 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-138">For complete removal of the tool, you must remove the MSXDBCDC database and the specific CDC databases that were created in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you worked with.</span></span>  
  
 <span data-ttu-id="3a1c8-139">如果您從一部電腦解除安裝 CDC 服務軟體並將它安裝在另一部電腦上，您只需要提供以下定義：</span><span class="sxs-lookup"><span data-stu-id="3a1c8-139">If you uninstall the CDC Service software from one machine and install it on another computer, you only need to provide the following definitions:</span></span>  
  
-   <span data-ttu-id="3a1c8-140">服務帳戶</span><span class="sxs-lookup"><span data-stu-id="3a1c8-140">Service account</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3a1c8-141">連接字串和認證</span><span class="sxs-lookup"><span data-stu-id="3a1c8-141">connect string and credentials</span></span>  
  
-   <span data-ttu-id="3a1c8-142">主要密碼</span><span class="sxs-lookup"><span data-stu-id="3a1c8-142">The master password</span></span>  
  
 <span data-ttu-id="3a1c8-143">所有其他定義都會儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，而且可從另一部電腦上的前一個安裝來使用。</span><span class="sxs-lookup"><span data-stu-id="3a1c8-143">All the other definitions are stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and are available from the previous installation on another computer.</span></span>  
  
## <a name="in-this-documentation"></a><span data-ttu-id="3a1c8-144">在此文件集中</span><span class="sxs-lookup"><span data-stu-id="3a1c8-144">In This Documentation</span></span>  
  
-   [<span data-ttu-id="3a1c8-145">Attunity Oracle Change Data Capture (CDC) 服務系統架構</span><span class="sxs-lookup"><span data-stu-id="3a1c8-145">Change Data Capture Service for Oracle by Attunity System Architecture</span></span>](change-data-capture-service-for-oracle-by-attunity-system-architecture.md)  
  
-   [<span data-ttu-id="3a1c8-146">Oracle CDC 服務</span><span class="sxs-lookup"><span data-stu-id="3a1c8-146">The Oracle CDC Service</span></span>](the-oracle-cdc-service.md)  
  
-   [<span data-ttu-id="3a1c8-147">Attunity Oracle Change Data Capture (CDC) 服務 F1 說明</span><span class="sxs-lookup"><span data-stu-id="3a1c8-147">Change Data Capture Service for Oracle by Attunity F1 Help</span></span>](change-data-capture-service-for-oracle-by-attunity-f1-help.md)  
  
-   [<span data-ttu-id="3a1c8-148">Attunity Oracle Change Data Capture (CDC) 服務使用說明指南</span><span class="sxs-lookup"><span data-stu-id="3a1c8-148">Change Data Capture Service for Oracle by Attunity How to Guide</span></span>](change-data-capture-service-for-oracle-by-attunity-how-to-guide.md)  
  
## <a name="see-also"></a><span data-ttu-id="3a1c8-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a1c8-149">See Also</span></span>  
 [<span data-ttu-id="3a1c8-150">使用 Oracle CDC 服務</span><span class="sxs-lookup"><span data-stu-id="3a1c8-150">Working with the Oracle CDC Service</span></span>](working-with-the-oracle-cdc-service.md)  
  
  
