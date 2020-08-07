---
title: 資料庫鏡像端點的網路存取
description: 瞭解如何允許 SQL Server 的 windows authenticatino 網路存取資料庫鏡像端點。
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 28c8fec5-5feb-4c84-8d72-f2bd1ae3b40d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0d1d8786d128ef2cc99fe571e33f89c4c4e7699c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598513"
---
# <a name="allow-network-access-to-a-database-mirroring-endpoint-using-windows-authentication-sql-server"></a><span data-ttu-id="380cc-103">使用 Windows 驗證允許資料庫鏡像的網路存取 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="380cc-103">Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication (SQL Server)</span></span>
  <span data-ttu-id="380cc-104">若要將 Windows 驗證用於連接兩個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的資料庫鏡像端點，在下列狀況下，需要手動設定登入帳戶：</span><span class="sxs-lookup"><span data-stu-id="380cc-104">Using Windows Authentication for connecting the database mirroring endpoints of two instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requires manual configuration of login accounts under the following conditions:</span></span>  
  
-   <span data-ttu-id="380cc-105">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體會以服務的形式在不同的網域帳戶底下執行 (在相同或受信任的網域中)，您就必須在每個遠端伺服器執行個體的 **master** 中建立每個帳戶的登入，而且該登入必須被授與端點的 CONNECT 權限。</span><span class="sxs-lookup"><span data-stu-id="380cc-105">If the instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] run as services under different domain accounts (in the same or trusted domains), the login of each account must be created in **master** on each of the remote server instances and that login must be granted CONNECT permissions on the endpoint.</span></span>  
  
-   <span data-ttu-id="380cc-106">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體會以網路服務帳戶的身分執行，您就必須在每個遠端伺服器執行個體的 **master** 中建立每個主機電腦帳戶的登入 (*DomainName***\\***ComputerName$* )，而且該登入必須被授與端點的 CONNECT 權限。</span><span class="sxs-lookup"><span data-stu-id="380cc-106">If the instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] run as the Network Service account, the login of the each host computer account (*DomainName***\\***ComputerName$*) must be created in **master** on each of the remote server instances and that login must be granted CONNECT permissions on the endpoint.</span></span> <span data-ttu-id="380cc-107">這是因為在 Network Service 帳戶底下執行的伺服器執行個體會使用主機電腦的網域帳戶進行驗證。</span><span class="sxs-lookup"><span data-stu-id="380cc-107">This is because a server instance running under the Network Service account authenticates using the domain account of the host computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="380cc-108">請確定每個伺服器執行個體都有端點存在。</span><span class="sxs-lookup"><span data-stu-id="380cc-108">Ensure that an endpoint exists for each of the server instances.</span></span> <span data-ttu-id="380cc-109">如需詳細資訊，請參閱[建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;](database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="380cc-109">For more information, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
### <a name="to-configure-logins-for-windows-authentication"></a><span data-ttu-id="380cc-110">若要設定 Windows 驗證登入</span><span class="sxs-lookup"><span data-stu-id="380cc-110">To configure logins for Windows Authentication</span></span>  
  
1.  <span data-ttu-id="380cc-111">針對每個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體的使用者帳戶，在其他 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體上建立登入。</span><span class="sxs-lookup"><span data-stu-id="380cc-111">For the user account of each instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], create a login on the other instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="380cc-112">將 [CREATE LOGIN](/sql/t-sql/statements/create-login-transact-sql) 陳述式與 FROM WINDOWS 子句搭配使用。</span><span class="sxs-lookup"><span data-stu-id="380cc-112">Use a [CREATE LOGIN](/sql/t-sql/statements/create-login-transact-sql) statement with the FROM WINDOWS clause.</span></span>  
  
     <span data-ttu-id="380cc-113">如需詳細資訊，請參閱 [建立登入](../relational-databases/security/authentication-access/create-a-login.md)。</span><span class="sxs-lookup"><span data-stu-id="380cc-113">For more information, see [Create a Login](../relational-databases/security/authentication-access/create-a-login.md).</span></span>  
  
2.  <span data-ttu-id="380cc-114">另外，若要確定登入使用者擁有端點的存取權，請使用 [GRANT](/sql/t-sql/statements/grant-transact-sql) 陳述式將端點上的連接權限授與登入。</span><span class="sxs-lookup"><span data-stu-id="380cc-114">Also, to ensure that the login user has access to the endpoint, use the [GRANT](/sql/t-sql/statements/grant-transact-sql) statement to grant connect permissions on the endpoint to the login.</span></span> <span data-ttu-id="380cc-115">請注意，如果使用者是 Administrator，就不需要授與端點的連接權限。</span><span class="sxs-lookup"><span data-stu-id="380cc-115">Note that granting connect permissions to the endpoint is unnecessary if the user is an Administrator.</span></span>  
  
     <span data-ttu-id="380cc-116">如需詳細資訊，請參閱 [Grant a Permission to a Principal](../relational-databases/security/authentication-access/grant-a-permission-to-a-principal.md)。</span><span class="sxs-lookup"><span data-stu-id="380cc-116">For more information, see [Grant a Permission to a Principal](../relational-databases/security/authentication-access/grant-a-permission-to-a-principal.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="380cc-117">範例</span><span class="sxs-lookup"><span data-stu-id="380cc-117">Example</span></span>  
 <span data-ttu-id="380cc-118">下列 [!INCLUDE[tsql](../includes/tsql-md.md)] 範例會為屬於 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 網域的 `Otheruser` 使用者帳戶建立 `Adomain`登入。</span><span class="sxs-lookup"><span data-stu-id="380cc-118">The following [!INCLUDE[tsql](../includes/tsql-md.md)] example creates a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login for a user account named `Otheruser` that belongs to a domain called `Adomain`.</span></span> <span data-ttu-id="380cc-119">接著，此範例會將預先存在的鏡像資料庫端點 `Mirroring_Endpoint`的連接權限授與此使用者。</span><span class="sxs-lookup"><span data-stu-id="380cc-119">The example then grants this user connect permissions to a pre-existing database mirroring endpoint named `Mirroring_Endpoint`.</span></span>  
  
```  
USE master;  
GO  
CREATE LOGIN [Adomain\Otheruser] FROM WINDOWS;  
GO  
GRANT CONNECT on ENDPOINT::Mirroring_Endpoint TO [Adomain\Otheruser];  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="380cc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="380cc-120">See Also</span></span>  
 <span data-ttu-id="380cc-121">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="380cc-121">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="380cc-122">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="380cc-122">[Database Mirroring &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="380cc-123">[資料庫鏡像和 AlwaysOn 可用性群組的傳輸安全性 &#40;SQL Server&#41;](database-mirroring/transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="380cc-123">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](database-mirroring/transport-security-database-mirroring-always-on-availability.md) </span></span>  
 [<span data-ttu-id="380cc-124">資料庫鏡像端點 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="380cc-124">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  
