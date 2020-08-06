---
title: SQL Server 連線所需的 CDC 服務權限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e63b98ffd0371bd5b70ecc0ac843ad40a4a5d03e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594637"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-service"></a><span data-ttu-id="43408-102">SQL Server 連接所需的 CDC 服務權限</span><span class="sxs-lookup"><span data-stu-id="43408-102">SQL Server Connection Required Permissions for the CDC Service</span></span>
  <span data-ttu-id="43408-103">CDC 服務組態主控台需要與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之間的連接資訊，才能執行其工作。</span><span class="sxs-lookup"><span data-stu-id="43408-103">The CDC Service Configuration Console requires connection information to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to perform their tasks.</span></span> <span data-ttu-id="43408-104">本主題描述可以在 [連接到 SQL Server] 對話方塊中提供的資訊，以便設定與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的連接。</span><span class="sxs-lookup"><span data-stu-id="43408-104">This topic describes the information that can be provided in the Connect to SQL Server dialog box for setting up the connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="43408-105">必要時會開啟 [連接到 SQL Server] 對話方塊，例如當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接資訊無法取得時，或是當資訊存在但是連接沒有必要的權限時。</span><span class="sxs-lookup"><span data-stu-id="43408-105">The Connect to SQL Server dialog box opens when necessary, such as when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection information is not available or when the information exists but the connection does not have the required permissions.</span></span>  
  
 <span data-ttu-id="43408-106">下表描述需要連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的各種工作以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入/使用者的必要權限。</span><span class="sxs-lookup"><span data-stu-id="43408-106">The following table describes the various tasks where a connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is required and the required permissions from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login/user.</span></span>  
  
|<span data-ttu-id="43408-107">Task</span><span class="sxs-lookup"><span data-stu-id="43408-107">Task</span></span>|<span data-ttu-id="43408-108">最低權限</span><span class="sxs-lookup"><span data-stu-id="43408-108">Minimum Permissions</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="43408-109">準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="43408-109">Prepare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instance.</span></span>|<span data-ttu-id="43408-110">`dbcreator` 固定伺服器角色</span><span class="sxs-lookup"><span data-stu-id="43408-110">`dbcreator` fixed-server role</span></span>|  
|<span data-ttu-id="43408-111">建立 Oracle CDC 服務 SQL Server 登入，以供 Oracle CDC 服務使用。</span><span class="sxs-lookup"><span data-stu-id="43408-111">Create an Oracle CDC Service-SQL Server login for use by the Oracle CDC service.</span></span>|<span data-ttu-id="43408-112">`public` 固定伺服器角色</span><span class="sxs-lookup"><span data-stu-id="43408-112">`public` fixed-server role</span></span>|  
|<span data-ttu-id="43408-113">建立 Oracle CDC 服務登入，以供在 MSXDBCDC 中註冊新服務使用。</span><span class="sxs-lookup"><span data-stu-id="43408-113">Create an Oracle CDC Service-login to use for registering the new service in MSXDBCDC.</span></span>|<span data-ttu-id="43408-114">`db_datareader` 和 `db_datawriter` 角色</span><span class="sxs-lookup"><span data-stu-id="43408-114">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
|<span data-ttu-id="43408-115">編輯 Oracle CDC 服務登入，以供在 MSXDBCDC 中更新服務註冊使用。</span><span class="sxs-lookup"><span data-stu-id="43408-115">Edit an Oracle CDC Service-login to use for updating the registration of the service in MSXDBCDC.</span></span>|<span data-ttu-id="43408-116">`db_datareader` 和 `db_datawriter` 角色</span><span class="sxs-lookup"><span data-stu-id="43408-116">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
|<span data-ttu-id="43408-117">刪除 Oracle CDC 服務登入，以供在 MSXDBCDC 中更新服務註冊使用。</span><span class="sxs-lookup"><span data-stu-id="43408-117">Delete an Oracle CDC Service-login to use for updating the registration of the service in MSXDBCDC.</span></span>|<span data-ttu-id="43408-118">`db_datareader` 和 `db_datawriter` 角色</span><span class="sxs-lookup"><span data-stu-id="43408-118">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43408-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43408-119">See Also</span></span>  
 <span data-ttu-id="43408-120">[連接到 SQL Server](connection-to-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="43408-120">[Connection to SQL Server](connection-to-sql-server.md) </span></span>  
 [<span data-ttu-id="43408-121">連接到 SQL Server 以進行刪除作業</span><span class="sxs-lookup"><span data-stu-id="43408-121">Connection to SQL Server for Delete</span></span>](connection-to-sql-server-for-delete.md)  
  
  
