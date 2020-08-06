---
title: 建立 AlwaysOn 可用性群組 (SQL Server PowerShell) 的資料庫鏡像端點 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], endpoint
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 56058ff8aa72d2471381dd87fb25a3b68356ed36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710793"
---
# <a name="create-a-database-mirroring-endpoint-for-alwayson-availability-groups-sql-server-powershell"></a><span data-ttu-id="21e32-102">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups (SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="21e32-102">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups (SQL Server PowerShell)</span></span>
  <span data-ttu-id="21e32-103">此主題描述如何使用 PowerShell，在 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中建立 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 所用的資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="21e32-103">This topic describes how to create a database mirroring endpoint for use by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using PowerShell.</span></span>  
  
 <span data-ttu-id="21e32-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="21e32-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="21e32-105">**開始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="21e32-105">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="21e32-106">**若要使用下列項目建立資料庫鏡像端點：**  [PowerShell](#PowerShellProcedure)</span><span class="sxs-lookup"><span data-stu-id="21e32-106">**To create a database mirroring endpoint, using:**  [PowerShell](#PowerShellProcedure)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="21e32-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="21e32-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="21e32-108">Security</span><span class="sxs-lookup"><span data-stu-id="21e32-108">Security</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="21e32-109">RC4 演算法已被取代。</span><span class="sxs-lookup"><span data-stu-id="21e32-109">The RC4 algorithm is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="21e32-110">我們建議您改用 AES。</span><span class="sxs-lookup"><span data-stu-id="21e32-110">We recommend that you use AES.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="21e32-111">權限</span><span class="sxs-lookup"><span data-stu-id="21e32-111">Permissions</span></span>  
 <span data-ttu-id="21e32-112">需要 CREATE ENDPOINT 權限或系統管理員 (sysadmin) 固定伺服器角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="21e32-112">Requires CREATE ENDPOINT permission, or membership in the sysadmin fixed server role.</span></span> <span data-ttu-id="21e32-113">如需詳細資訊，請參閱 [GRANT 端點權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="21e32-113">For more information, see [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="21e32-114">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="21e32-114">Using PowerShell</span></span>  
 <span data-ttu-id="21e32-115">**若要建立資料庫鏡像端點**</span><span class="sxs-lookup"><span data-stu-id="21e32-115">**To create a database mirroring endpoint**</span></span>  
  
1.  <span data-ttu-id="21e32-116">將目錄切換到 (`cd`) 您要建立資料庫鏡像端點的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="21e32-116">Change directory (`cd`) to the server instance for which you want to create the database mirroring endpoint.</span></span>  
  
2.  <span data-ttu-id="21e32-117">使用 `New-SqlHadrEndpoint` 指令程式建立端點，然後使用 `Set-SqlHadrEndpoint` 啟動端點。</span><span class="sxs-lookup"><span data-stu-id="21e32-117">Use the `New-SqlHadrEndpoint` cmdlet to create the endpoint and then use the `Set-SqlHadrEndpoint` to start the endpoint.</span></span>  
  
###  <a name="example-powershell"></a><a name="PShellExample"></a> <span data-ttu-id="21e32-118">範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="21e32-118">Example (PowerShell)</span></span>  
 <span data-ttu-id="21e32-119">下列 PowerShell 命令會在 SQL Server (*機* \\ *實例*) 的實例上建立資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="21e32-119">The following PowerShell commands create a database mirroring endpoint on an instance of SQL Server (*Machine*\\*Instance*).</span></span> <span data-ttu-id="21e32-120">此端點使用通訊埠 5022。</span><span class="sxs-lookup"><span data-stu-id="21e32-120">The endpoint uses port 5022.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="21e32-121">這個範例只適用於目前缺少資料庫鏡像端點的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="21e32-121">This example works only on a server instance that currently lack a database mirroring endpoint.</span></span>  
  
```powershell
# Create the endpoint.  
$endpoint = New-SqlHadrEndpoint MyMirroringEndpoint -Port 5022 -Path SQLSERVER:\SQL\Machine\Instance  
  
# Start the endpoint  
Set-SqlHadrEndpoint -InputObject $endpoint -State "Started"
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="21e32-122">相關工作</span><span class="sxs-lookup"><span data-stu-id="21e32-122">Related Tasks</span></span>  
 <span data-ttu-id="21e32-123">**若要設定資料庫鏡像端點**</span><span class="sxs-lookup"><span data-stu-id="21e32-123">**To Configure a Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="21e32-124">建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21e32-124">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="21e32-125">使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21e32-125">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [<span data-ttu-id="21e32-126">允許資料庫鏡像端點使用輸出連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21e32-126">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [<span data-ttu-id="21e32-127">允許資料庫鏡像端點使用輸入連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21e32-127">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="21e32-128">指定伺服器網路位址 &#40;資料庫鏡像&#41;</span><span class="sxs-lookup"><span data-stu-id="21e32-128">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](../../database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [<span data-ttu-id="21e32-129">在新增或修改可用性複本時指定端點 URL &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="21e32-129">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="21e32-130">**若要檢視有關資料庫鏡像端點的資訊**</span><span class="sxs-lookup"><span data-stu-id="21e32-130">**To View Information About the Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="21e32-131">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21e32-131">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="21e32-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21e32-132">See Also</span></span>  
 <span data-ttu-id="21e32-133">[&#40;Transact-sql 建立可用性群組&#41;](create-an-availability-group-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="21e32-133">[Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md) </span></span>  
 [<span data-ttu-id="21e32-134">AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;</span><span class="sxs-lookup"><span data-stu-id="21e32-134">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
