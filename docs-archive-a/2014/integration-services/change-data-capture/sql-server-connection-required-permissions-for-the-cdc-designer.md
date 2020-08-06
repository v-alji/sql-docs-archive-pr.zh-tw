---
title: SQL Server 連線所需的 CDC 設計工具權限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 80334de2-17c1-43c9-951e-21a9f864e9cb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0815a5d8f1cb66dee0d290a45166ebb395c8efa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585525"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-designer"></a><span data-ttu-id="19dd0-102">SQL Server 連接所需的 CDC 設計工具權限</span><span class="sxs-lookup"><span data-stu-id="19dd0-102">SQL Server Connection Required Permissions for the CDC Designer</span></span>
  <span data-ttu-id="19dd0-103">CDC 設計工具主控台需要與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之間的連接資訊，才能執行工作。</span><span class="sxs-lookup"><span data-stu-id="19dd0-103">The CDC Designer Console requires connection information to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to perform its tasks.</span></span> <span data-ttu-id="19dd0-104">本主題描述可以在 **[連接到 SQL Server]** 對話方塊中提供的資訊，以便設定與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的連接。</span><span class="sxs-lookup"><span data-stu-id="19dd0-104">This topic describes the information that can be provided in the **Connect to SQL Server** dialog box for setting up the connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="19dd0-105">必要時會開啟 **[連接到 SQL Server]** 對話方塊，例如當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接資訊無法取得時，或是當資訊存在但是連接沒有必要的權限時。</span><span class="sxs-lookup"><span data-stu-id="19dd0-105">The **Connect to SQL Server** dialog box opens when necessary, such as when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection information is not available or when the information exists but the connection does not have the required permissions.</span></span>  
  
 <span data-ttu-id="19dd0-106">下表描述需要連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的各種工作以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入/使用者的必要權限。</span><span class="sxs-lookup"><span data-stu-id="19dd0-106">The following table describes the various tasks where a connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is required and the required permissions from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login/user.</span></span>  
  
|<span data-ttu-id="19dd0-107">Task</span><span class="sxs-lookup"><span data-stu-id="19dd0-107">Task</span></span>|<span data-ttu-id="19dd0-108">最低權限</span><span class="sxs-lookup"><span data-stu-id="19dd0-108">Minimum Permissions</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="19dd0-109">使用關聯的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體檢視 CDC 服務和執行個體的清單。</span><span class="sxs-lookup"><span data-stu-id="19dd0-109">View the list of CDC Services and Instances using the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>|<span data-ttu-id="19dd0-110">`db_datareader` 角色</span><span class="sxs-lookup"><span data-stu-id="19dd0-110">`db_datareader` role on MSXDBCDC</span></span>|  
|<span data-ttu-id="19dd0-111">啟動/停止 CDC 執行個體</span><span class="sxs-lookup"><span data-stu-id="19dd0-111">Start/Stop CDC Instance(s)</span></span>|<span data-ttu-id="19dd0-112">`db_datareader` 和 `db_datawriter` 角色</span><span class="sxs-lookup"><span data-stu-id="19dd0-112">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
|<span data-ttu-id="19dd0-113">檢視 CDC 執行個體狀態。</span><span class="sxs-lookup"><span data-stu-id="19dd0-113">View the CDC Instance status.</span></span>|<span data-ttu-id="19dd0-114">`db_owner` 角色</span><span class="sxs-lookup"><span data-stu-id="19dd0-114">`db_owner` role on the CDC Instance database</span></span>|  
|<span data-ttu-id="19dd0-115">建立新的 Oracle CDC 執行個體資料庫。</span><span class="sxs-lookup"><span data-stu-id="19dd0-115">Create a new Oracle CDC Instance database.</span></span>|<span data-ttu-id="19dd0-116">`dbcreator` 固定伺服器角色</span><span class="sxs-lookup"><span data-stu-id="19dd0-116">`dbcreator` fixed-server role</span></span>|  
|<span data-ttu-id="19dd0-117">建立新的 Oracle CDC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="19dd0-117">Create a new Oracle CDC Instance.</span></span>|<span data-ttu-id="19dd0-118">`db_datareader` 角色</span><span class="sxs-lookup"><span data-stu-id="19dd0-118">`db_datareader` role on MSXDBCDC</span></span><br /><br /> <span data-ttu-id="19dd0-119">`db_owner` 角色。</span><span class="sxs-lookup"><span data-stu-id="19dd0-119">`db_owner` role on the CDC database that was created.</span></span>|  
|<span data-ttu-id="19dd0-120">取得部署指令碼。</span><span class="sxs-lookup"><span data-stu-id="19dd0-120">Get deployment scripts.</span></span>|<span data-ttu-id="19dd0-121">`db_datareader` 和 `db_datawriter` 角色</span><span class="sxs-lookup"><span data-stu-id="19dd0-121">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span><br /><br /> <span data-ttu-id="19dd0-122">`db_owner` 角色</span><span class="sxs-lookup"><span data-stu-id="19dd0-122">`db_owner` role on the relatedCDC database</span></span>|  
|<span data-ttu-id="19dd0-123">變更組態及加入/移除擷取執行個體。</span><span class="sxs-lookup"><span data-stu-id="19dd0-123">Change configuration and add/remove capture instances.</span></span>|<span data-ttu-id="19dd0-124">`db_datareader` 和 `db_datawriter` 角色</span><span class="sxs-lookup"><span data-stu-id="19dd0-124">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span><br /><br /> <span data-ttu-id="19dd0-125">`db_owner` 角色</span><span class="sxs-lookup"><span data-stu-id="19dd0-125">`db_owner` role on the related CDC database</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19dd0-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19dd0-126">See Also</span></span>  
 <span data-ttu-id="19dd0-127">[存取 CDC 設計工具主控台](access-the-cdc-designer-console.md) </span><span class="sxs-lookup"><span data-stu-id="19dd0-127">[Access the CDC Designer Console](access-the-cdc-designer-console.md) </span></span>  
 [<span data-ttu-id="19dd0-128">用來建立執行個體的 SQL Server 連接</span><span class="sxs-lookup"><span data-stu-id="19dd0-128">SQL Server Connection for Instance Creation</span></span>](sql-server-connection-for-instance-creation.md)  
  
  
