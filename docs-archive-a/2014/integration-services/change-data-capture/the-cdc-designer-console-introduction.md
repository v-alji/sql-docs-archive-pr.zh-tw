---
title: CDC 設計工具主控台簡介 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 45298179-4ac1-4723-8b3c-56f5926be40a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 888b111790cf3979e9d08a78502d24880fa034b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585519"
---
# <a name="the-cdc-designer-console-introduction"></a><span data-ttu-id="f6c66-102">CDC 設計工具主控台簡介</span><span class="sxs-lookup"><span data-stu-id="f6c66-102">The CDC Designer Console Introduction</span></span>
  <span data-ttu-id="f6c66-103">本節描述 Attunity Oracle Change Data Capture (CDC) 設計工具的安裝程序。</span><span class="sxs-lookup"><span data-stu-id="f6c66-103">The section describes the installation procedures for the Change Data Capture Designer for Oracle by Attunity.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="f6c66-104">安裝</span><span class="sxs-lookup"><span data-stu-id="f6c66-104">Installation</span></span>  
 <span data-ttu-id="f6c66-105">本節描述 Attunity Oracle Change Data Capture (CDC) 設計工具的安裝程序。</span><span class="sxs-lookup"><span data-stu-id="f6c66-105">The section describes the installation procedures for the Change Data Capture Designer for Oracle by Attunity.</span></span> <span data-ttu-id="f6c66-106">若要安裝 CDC 設計工具主控台，請從 SQL Server 安裝媒體手動執行**AttunityOracleCdcDesigner.msi** 。</span><span class="sxs-lookup"><span data-stu-id="f6c66-106">To install the CDC Designer Console, manually run **AttunityOracleCdcDesigner.msi** from the SQL Server installation media.</span></span>  <span data-ttu-id="f6c66-107">X86 和 x64 的安裝套件位於 SQL Server 安裝媒體上的 \*\*.\Tools\AttunityCDCOracle \\ \*\*中。</span><span class="sxs-lookup"><span data-stu-id="f6c66-107">Installation packages for x86 and x64 are located in **.\Tools\AttunityCDCOracle\\** on the SQL Server installation media.</span></span>  
  
## <a name="supported-windows-environments"></a><span data-ttu-id="f6c66-108">支援的 Windows 環境</span><span class="sxs-lookup"><span data-stu-id="f6c66-108">Supported Windows Environments</span></span>  
 <span data-ttu-id="f6c66-109">CDC 設計工具主控台可在以下 Windows 環境中執行：</span><span class="sxs-lookup"><span data-stu-id="f6c66-109">The CDC Designer Console can run in the following Windows environments:</span></span>  
  
-   <span data-ttu-id="f6c66-110">Windows Vista 32 位元 (x86) 和 64 位元 (x64)，含 Service Pack 2</span><span class="sxs-lookup"><span data-stu-id="f6c66-110">Windows Vista 32-bit (x86) and 64-bit (x64) with Service Pack 2</span></span>  
  
-   <span data-ttu-id="f6c66-111">Windows 7 32 位元 (x86) 和 64 位元 (x64)</span><span class="sxs-lookup"><span data-stu-id="f6c66-111">Windows 7 32-bit (x86) and 64-bit (x64)</span></span>  
  
-   <span data-ttu-id="f6c66-112">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="f6c66-112">Windows Server 2008 R2</span></span>  
  
-   <span data-ttu-id="f6c66-113">Windows Server 2008 32 位元 (x86) 和 64 位元 (x64)，含 Service Pack 2</span><span class="sxs-lookup"><span data-stu-id="f6c66-113">Windows Server 2008 32-bit (x86) and 64-bit (x64) with Service Pack 2</span></span>  
  
## <a name="database-prerequisites"></a><span data-ttu-id="f6c66-114">資料庫必要條件</span><span class="sxs-lookup"><span data-stu-id="f6c66-114">Database Prerequisites</span></span>  
 <span data-ttu-id="f6c66-115">若要使用 Attunity Oracle Change Data Capture (CDC) 設計工具，請使用 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f6c66-115">To work with the Change Data Capture Designer for Oracle by Attunity, you work with an Oracle database.</span></span> <span data-ttu-id="f6c66-116">Attunity Oracle Change Data Capture (CDC) 設計工具支援以下版本：</span><span class="sxs-lookup"><span data-stu-id="f6c66-116">The Change Data Capture Designer for Oracle by Attunity supports the following versions:</span></span>  
  
 <span data-ttu-id="f6c66-117">**Oracle 資料庫**</span><span class="sxs-lookup"><span data-stu-id="f6c66-117">**Oracle Database**</span></span>  
  
-   <span data-ttu-id="f6c66-118">Oracle Database 10g Release 2：10.2.0.1-10.2.0.5 (2010 年 4 月的修補集)</span><span class="sxs-lookup"><span data-stu-id="f6c66-118">Oracle Database 10g Release 2: 10.2.0.1-10.2.0.5 (patchset as of April 2010)</span></span>  
  
-   <span data-ttu-id="f6c66-119">Oracle Database 11g Release 1：11.1.0.6-11.1.0.7 (2008 年 9 月的修補集)</span><span class="sxs-lookup"><span data-stu-id="f6c66-119">Oracle Database 11g Release 1: 11.1.0.6-11.1.0.7 (patchset as of September 2008)</span></span>  
  
-   <span data-ttu-id="f6c66-120">Oracle Database 11g Release 2：11.2.0.1-11.2.0.3 (2011 年 9 月的修補集)</span><span class="sxs-lookup"><span data-stu-id="f6c66-120">Oracle Database 11g Release 2: 11.2.0.1-11.2.0.3 (patchset as of September 2011)</span></span>  
  
 <span data-ttu-id="f6c66-121">**SQL Server 資料庫**</span><span class="sxs-lookup"><span data-stu-id="f6c66-121">**SQL Server Database**</span></span>  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="f6c66-122">版本，支援 SQL Server CDC</span><span class="sxs-lookup"><span data-stu-id="f6c66-122">edition with support for SQL Server CDC</span></span>  
  
## <a name="software-prerequisites"></a><span data-ttu-id="f6c66-123">軟體必要條件</span><span class="sxs-lookup"><span data-stu-id="f6c66-123">Software Prerequisites</span></span>  
 <span data-ttu-id="f6c66-124">以下是必要的軟體：</span><span class="sxs-lookup"><span data-stu-id="f6c66-124">The following software is required:</span></span>  
  
-   <span data-ttu-id="f6c66-125">Oracle 10. x 用戶端</span><span class="sxs-lookup"><span data-stu-id="f6c66-125">Oracle 10.x client</span></span>  
  
-   <span data-ttu-id="f6c66-126">Oracle 11.x 用戶端</span><span class="sxs-lookup"><span data-stu-id="f6c66-126">Oracle 11.x client</span></span>  
  
 <span data-ttu-id="f6c66-127">**注意**：您必須根據所安裝的 Oracle CDC 設計工具主控台版本，使用32位或64位版本的此軟體。</span><span class="sxs-lookup"><span data-stu-id="f6c66-127">**Note**: You must use the 32-bit or 64-bit version of this software according to the version of the Oracle CDC Designer console installed.</span></span>  
  
 <span data-ttu-id="f6c66-128">Oracle CDC 設計工具主控台會使用 Oracle ODBC 提供者與來源 Oracle 資料庫通訊。</span><span class="sxs-lookup"><span data-stu-id="f6c66-128">The Oracle CDC Designer Console uses the Oracle ODBC provider to communicate with the source Oracle database.</span></span>  
  
## <a name="running-the-installation-program"></a><span data-ttu-id="f6c66-129">執行安裝程式</span><span class="sxs-lookup"><span data-stu-id="f6c66-129">Running the Installation Program</span></span>  
 <span data-ttu-id="f6c66-130">本節描述如何安裝 CDC 設計工具主控台。</span><span class="sxs-lookup"><span data-stu-id="f6c66-130">This section describes how to install the CDC Designer Console.</span></span>  
  
 <span data-ttu-id="f6c66-131">**若要安裝 CDC 設計工具主控台**</span><span class="sxs-lookup"><span data-stu-id="f6c66-131">**To install the CDC Designer Console**</span></span>  
  
 <span data-ttu-id="f6c66-132">按兩下 CDC 設計工具主控台安裝套件，並依照安裝精靈的指示進行。</span><span class="sxs-lookup"><span data-stu-id="f6c66-132">Double-click the CDC Designer Console installation kit and follow the directions in the installation wizard.</span></span>  
  
## <a name="uninstalling-the-cdc-designer-console"></a><span data-ttu-id="f6c66-133">解除安裝 CDC 設計工具主控台</span><span class="sxs-lookup"><span data-stu-id="f6c66-133">Uninstalling the CDC Designer Console</span></span>  
 <span data-ttu-id="f6c66-134">使用 [控制台] 的 [程式和功能] 解除安裝 CDC 設計工具主控台。</span><span class="sxs-lookup"><span data-stu-id="f6c66-134">You uninstall the CDC Designer Console using Control Panel, Programs and Features.</span></span>  
  
  
