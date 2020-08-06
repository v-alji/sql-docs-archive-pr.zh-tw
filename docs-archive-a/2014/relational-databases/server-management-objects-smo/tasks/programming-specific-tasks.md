---
title: 程式設計特定工作 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual Basic [SMO]
- Visual C# [SMO]
- programming [SMO]
- SQL Server Management Objects, programming
- SQL Server Management Objects, tasks
- SMO [SQL Server], programming
- SMO [SQL Server], tasks
ms.assetid: a15949ef-88d9-4205-892e-0b66588b4fcc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 215e31cb4e88403f5936c987029203736bb1300a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598245"
---
# <a name="programming-specific-tasks"></a><span data-ttu-id="9d20a-102">程式設計特有的工作</span><span class="sxs-lookup"><span data-stu-id="9d20a-102">Programming Specific Tasks</span></span>
  <span data-ttu-id="9d20a-103">使用 SMO 物件的程式設計特有工作包含只有具備特定功能之程式所需要的複雜主題，例如，備份、監視統計資料、複寫、管理執行個體物件，以及設定組態選項。</span><span class="sxs-lookup"><span data-stu-id="9d20a-103">Programming-specific tasks using SMO objects include complex subjects that would only be required by programs with a specific function, such as backing up, monitoring statistics, replication, managing instance objects, and setting configuration options.</span></span>  
  
|<span data-ttu-id="9d20a-104">主題</span><span class="sxs-lookup"><span data-stu-id="9d20a-104">Topic</span></span>|<span data-ttu-id="9d20a-105">描述</span><span class="sxs-lookup"><span data-stu-id="9d20a-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9d20a-106">在 SMO 中使用連結的伺服器</span><span class="sxs-lookup"><span data-stu-id="9d20a-106">Using Linked Servers in SMO</span></span>](using-linked-servers-in-smo.md)|<span data-ttu-id="9d20a-107">描述 SMO 如何使用 <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> 物件連結 OLE-DB 伺服器。</span><span class="sxs-lookup"><span data-stu-id="9d20a-107">Describes how SMO uses the <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> object to link OLE-DB servers.</span></span>|  
|[<span data-ttu-id="9d20a-108">在 SMO 中設定 SQL Server</span><span class="sxs-lookup"><span data-stu-id="9d20a-108">Configuring SQL Server in SMO</span></span>](configuring-sql-server-in-smo.md)|<span data-ttu-id="9d20a-109">描述如何在 SMO 中檢視與修改 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的組態設定。</span><span class="sxs-lookup"><span data-stu-id="9d20a-109">Describes how to view and modify configuration settings for the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in SMO.</span></span>|  
|[<span data-ttu-id="9d20a-110">使用資料表和索引資料分割</span><span class="sxs-lookup"><span data-stu-id="9d20a-110">Using Table and Index Partitioning</span></span>](using-table-and-index-partitioning.md)|<span data-ttu-id="9d20a-111">描述如何在 SMO 中使用索引和資料表資料分割。</span><span class="sxs-lookup"><span data-stu-id="9d20a-111">Describes how to use index and table partitioning in SMO.</span></span>|  
|[<span data-ttu-id="9d20a-112">使用檔案群組和檔案來儲存資料</span><span class="sxs-lookup"><span data-stu-id="9d20a-112">Using Filegroups and Files to Store Data</span></span>](using-filegroups-and-files-to-store-data.md)|<span data-ttu-id="9d20a-113">描述如何在 SMO 中使用檔案群組。</span><span class="sxs-lookup"><span data-stu-id="9d20a-113">Describes how to use file groups in SMO.</span></span>|  
|[<span data-ttu-id="9d20a-114">使用 WMI 提供者管理服務和網路設定</span><span class="sxs-lookup"><span data-stu-id="9d20a-114">Managing Services and Network Settings by Using WMI Provider</span></span>](managing-services-and-network-settings-by-using-wmi-provider.md)|<span data-ttu-id="9d20a-115">描述使用代表組態管理的 WMI 提供者之 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 物件，追蹤 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的數個方式。</span><span class="sxs-lookup"><span data-stu-id="9d20a-115">Describes several ways to keep track of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using the <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object that represents the WMI Provider for Configuration Management.</span></span>|  
|[<span data-ttu-id="9d20a-116">使用資料庫物件</span><span class="sxs-lookup"><span data-stu-id="9d20a-116">Working with Database Objects</span></span>](creating-altering-and-removing-database-objects.md)|<span data-ttu-id="9d20a-117">描述如何建立代表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體之物件的執行個體類別。</span><span class="sxs-lookup"><span data-stu-id="9d20a-117">Describes how to create instance classes that represent objects on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="9d20a-118">管理使用者、角色和登入</span><span class="sxs-lookup"><span data-stu-id="9d20a-118">Managing Users, Roles, and Logins</span></span>](managing-users-roles-and-logins.md)|<span data-ttu-id="9d20a-119">描述如何在 SMO 中使用安全性角色。</span><span class="sxs-lookup"><span data-stu-id="9d20a-119">Describes how to use security roles in SMO.</span></span>|  
|[<span data-ttu-id="9d20a-120">授與、撤銷和拒絕權限</span><span class="sxs-lookup"><span data-stu-id="9d20a-120">Granting, Revoking, and Denying Permissions</span></span>](granting-revoking-and-denying-permissions.md)|<span data-ttu-id="9d20a-121">描述如何使用 SMO 授與、撤銷與拒絕使用者或角色成員的權限。</span><span class="sxs-lookup"><span data-stu-id="9d20a-121">Describes how to use the SMO to grant, revoke, and deny permissions to users or members of a role.</span></span>|  
|[<span data-ttu-id="9d20a-122">使用加密</span><span class="sxs-lookup"><span data-stu-id="9d20a-122">Using Encryption</span></span>](using-encryption.md)|<span data-ttu-id="9d20a-123">描述如何在 SMO 中使用加密來保護資料。</span><span class="sxs-lookup"><span data-stu-id="9d20a-123">Describes how to protect data using encryption in SMO.</span></span>|  
|[<span data-ttu-id="9d20a-124">使用 SQL Server Agent 排程自動管理工作</span><span class="sxs-lookup"><span data-stu-id="9d20a-124">Scheduling Automatic Administrative Tasks in SQL Server Agent</span></span>](../../../ssms/agent/sql-server-agent.md)|<span data-ttu-id="9d20a-125">描述如何使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 監視、報告與排程 SMO 中的工作。</span><span class="sxs-lookup"><span data-stu-id="9d20a-125">Describes how to use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to monitor, report, and schedule jobs in SMO.</span></span>|  
|[<span data-ttu-id="9d20a-126">備份和還原資料庫與交易記錄</span><span class="sxs-lookup"><span data-stu-id="9d20a-126">Backing Up and Restoring Databases and Transaction Logs</span></span>](backing-up-and-restoring-databases-and-transaction-logs.md)|<span data-ttu-id="9d20a-127">描述如何在 SMO 中備份及還原資料庫和交易記錄。</span><span class="sxs-lookup"><span data-stu-id="9d20a-127">Describes how to back up and restore databases and transaction logs in SMO.</span></span>|  
|[<span data-ttu-id="9d20a-128">指令碼</span><span class="sxs-lookup"><span data-stu-id="9d20a-128">Scripting</span></span>](scripting.md)|<span data-ttu-id="9d20a-129">描述如何在 SMO 中撰寫物件的指令碼，並探索物件之間的相依性。</span><span class="sxs-lookup"><span data-stu-id="9d20a-129">Describes how to script objects and discover dependencies between objects in SMO.</span></span>|  
|[<span data-ttu-id="9d20a-130">傳送資料</span><span class="sxs-lookup"><span data-stu-id="9d20a-130">Transferring Data</span></span>](transferring-data.md)|<span data-ttu-id="9d20a-131">描述如何在 SMO 中傳送資料。</span><span class="sxs-lookup"><span data-stu-id="9d20a-131">Describes how to transfer data in SMO.</span></span>|  
|[<span data-ttu-id="9d20a-132">使用 Database Mail</span><span class="sxs-lookup"><span data-stu-id="9d20a-132">Using Database Mail</span></span>](using-database-mail.md)|<span data-ttu-id="9d20a-133">描述 SMO 如何使用電子郵件服務。</span><span class="sxs-lookup"><span data-stu-id="9d20a-133">Describes how SMO makes use of e-mail services.</span></span>|  
|[<span data-ttu-id="9d20a-134">管理 Service Broker</span><span class="sxs-lookup"><span data-stu-id="9d20a-134">Managing Service Broker</span></span>](managing-service-broker.md)|<span data-ttu-id="9d20a-135">描述如何使用 SMO 設定 Service Broker。</span><span class="sxs-lookup"><span data-stu-id="9d20a-135">Describes how to set up Service Broker using SMO.</span></span>|  
|[<span data-ttu-id="9d20a-136">使用 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="9d20a-136">Using XML Schemas</span></span>](using-xml-schemas.md)|<span data-ttu-id="9d20a-137">描述如何在 SMO 中使用 XML 資料類型。</span><span class="sxs-lookup"><span data-stu-id="9d20a-137">Describes how to use the XML data type in SMO.</span></span>|  
|[<span data-ttu-id="9d20a-138">使用同義字</span><span class="sxs-lookup"><span data-stu-id="9d20a-138">Using Synonyms</span></span>](using-synonyms.md)|<span data-ttu-id="9d20a-139">描述如何在 SMO 中建立同義字。</span><span class="sxs-lookup"><span data-stu-id="9d20a-139">Describes how to create synonyms in SMO.</span></span>|  
|[<span data-ttu-id="9d20a-140">使用訊息</span><span class="sxs-lookup"><span data-stu-id="9d20a-140">Using Messages</span></span>](using-messages.md)|<span data-ttu-id="9d20a-141">描述如何使用系統訊息，以及如何定義您自己的使用者定義訊息。</span><span class="sxs-lookup"><span data-stu-id="9d20a-141">Describes how to use system messages, and how to define your own user-defined messages.</span></span>|  
|[<span data-ttu-id="9d20a-142">實作全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="9d20a-142">Implementing Full-Text Search</span></span>](implementing-full-text-search.md)|<span data-ttu-id="9d20a-143">描述如何在 SMO 中實作全文檢索搜尋目錄與索引。</span><span class="sxs-lookup"><span data-stu-id="9d20a-143">Describes how to implement full-text search catalogs and indexes in SMO.</span></span>|  
|[<span data-ttu-id="9d20a-144">實作端點</span><span class="sxs-lookup"><span data-stu-id="9d20a-144">Implementing Endpoints</span></span>](implementing-endpoints.md)|<span data-ttu-id="9d20a-145">描述如何建立端點來處理資料庫鏡像、SOAP 要求與 Service Broker 的裝載。</span><span class="sxs-lookup"><span data-stu-id="9d20a-145">Describes how to create endpoints to handle payloads for Database Mirroring, SOAP requests, and Service Broker.</span></span>|  
|[<span data-ttu-id="9d20a-146">建立和更新統計資料</span><span class="sxs-lookup"><span data-stu-id="9d20a-146">Creating and Updating Statistics</span></span>](../../statistics/statistics.md)|<span data-ttu-id="9d20a-147">描述如何在 SMO 中設定與監視資料庫上的統計資料。</span><span class="sxs-lookup"><span data-stu-id="9d20a-147">Describes how to set up and monitor statistics on a database in SMO.</span></span>|  
|[<span data-ttu-id="9d20a-148">追蹤及重新執行事件</span><span class="sxs-lookup"><span data-stu-id="9d20a-148">Tracing and Replaying Events</span></span>](tracing-and-replaying-events.md)|<span data-ttu-id="9d20a-149">描述如何在 SMO 中使用 `Trace` 和 `Replay` 物件來追蹤和重新執行事件。</span><span class="sxs-lookup"><span data-stu-id="9d20a-149">Describes how to use the `Trace` and `Replay` objects in SMO to trace and replay events.</span></span>|  
  
  
