---
title: 設定資料庫鏡像的登入帳戶，或 AlwaysOn 可用性群組 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- logins [SQL Server], database mirroring
ms.assetid: e9f5287b-1325-4cda-88a6-19eaaa52a652
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d149016dabd0239bd76eadc8655b6752afd916d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701767"
---
# <a name="set-up-login-accounts-for-database-mirroring-or-alwayson-availability-groups-sql-server"></a><span data-ttu-id="32b98-102">設定資料庫鏡像或 AlwaysOn 可用性群組的登入帳戶 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="32b98-102">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="32b98-103">若要讓兩個伺服器執行個體連接到對方的 [資料庫鏡像端點](the-database-mirroring-endpoint-sql-server.md) ，這兩個執行個體的登入帳戶都必須要有對方的存取權。</span><span class="sxs-lookup"><span data-stu-id="32b98-103">For two server instances to connect to each other's [database mirroring endpoint](the-database-mirroring-endpoint-sql-server.md) point, the login account of each instance requires access to the other instance.</span></span> <span data-ttu-id="32b98-104">而且，這兩個登入帳戶都必須要有連接權限來連接到對方的資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="32b98-104">Also, each login account requires connect permission to the Database Mirroring endpoint of the other instance.</span></span>  
  
 <span data-ttu-id="32b98-105">此需求的影響視伺服器執行個體是否以相同網域使用者帳戶執行而定：</span><span class="sxs-lookup"><span data-stu-id="32b98-105">The impact of this requirement depends on whether the server instances run as the same domain user account:</span></span>  
  
-   <span data-ttu-id="32b98-106">如果伺服器執行個體是以相同的網域使用者帳戶執行，兩個 **master** 資料庫中都會自動存在正確的使用者登入。</span><span class="sxs-lookup"><span data-stu-id="32b98-106">If the server instances run as the same domain user account, the correct user logins exist automatically in both **master** databases.</span></span> <span data-ttu-id="32b98-107">這樣可簡化資料庫鏡像和 AlwaysOn 可用性群組的安全性組態。</span><span class="sxs-lookup"><span data-stu-id="32b98-107">This simplifies the security configuration for Database Mirroring and AlwaysOn Availability Groups.</span></span>  
  
-   <span data-ttu-id="32b98-108">如果伺服器執行個體是以不同使用者帳戶執行，則裝載主體伺服器或主要複本的伺服器執行個體上的使用者登入必須以手動方式重新產生在裝載鏡像伺服器的伺服器執行個體或裝載次要複本的每個伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="32b98-108">If the server instances run as different user accounts, user logins on the server instance that hosts the principal server or primary replica must be manually reproduced on the server instance that hosts the mirror server or on every server instance that hosts a secondary replica.</span></span> <span data-ttu-id="32b98-109">如需詳細資訊，請參閱本主題稍後的 [＜為不同的帳戶建立登入＞](#CreateLogin) 和 [＜授與連接權限＞](#GrantConnect)。</span><span class="sxs-lookup"><span data-stu-id="32b98-109">For more information, see [Create a Login for a Different Account](#CreateLogin) and [Grant Connect Permission](#GrantConnect), later in this topic.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="32b98-110">若要建立更安全的環境，請考慮針對每個伺服器執行個體使用不同的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="32b98-110">To create a more secure environment, consider using separate domain accounts for each server instance.</span></span>  
  
##  <a name="create-a-login-for-a-different-account"></a><a name="CreateLogin"></a><span data-ttu-id="32b98-111">為不同的帳戶建立登入</span><span class="sxs-lookup"><span data-stu-id="32b98-111">Create a Login for a Different Account</span></span>  
 <span data-ttu-id="32b98-112">如果兩個伺服器執行個體是以不同的帳戶執行，系統管理員必須使用 CREATE LOGIN [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，為每個伺服器執行個體之遠端執行個體的啟動服務帳戶建立登入。</span><span class="sxs-lookup"><span data-stu-id="32b98-112">If two server instances run as different accounts, the system administrator must use the CREATE LOGIN [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to create a login for the startup service account of the remote instance for each server instance.</span></span> <span data-ttu-id="32b98-113">如需詳細資訊，請參閱 [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="32b98-113">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="32b98-114">如果您是在非網域帳戶之下執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，則必須使用憑證。</span><span class="sxs-lookup"><span data-stu-id="32b98-114">If you run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] under a non-domain account, you must use certificates.</span></span> <span data-ttu-id="32b98-115">如需詳細資訊，請參閱[使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="32b98-115">For more information, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
 <span data-ttu-id="32b98-116">例如，若要讓伺服器執行個體 sqlA (在 loginA 之下執行) 連接到伺服器執行個體 sqlB (在 loginB 之下執行)，則 loginA 必須在 sqlB 中，而 loginB 必須在 sqlA 中。</span><span class="sxs-lookup"><span data-stu-id="32b98-116">For example, for the server instance sqlA, which runs under loginA, to connect to the server instance sqlB, which runs under loginB, loginA must exist on sqlB, and loginB must exist on sqlA.</span></span> <span data-ttu-id="32b98-117">此外，若資料庫鏡像工作階段中包含見證伺服器執行個體 (sqlC)，而且其中的三個伺服器執行個體都是在不同的網域帳戶下執行，則必須建立下列登入：</span><span class="sxs-lookup"><span data-stu-id="32b98-117">In addition, for a database mirroring session that includes a witness server instance (sqlC) and in which the three server instances run under different domain accounts, the following logins must be created:</span></span>  
  
|<span data-ttu-id="32b98-118">在執行個體</span><span class="sxs-lookup"><span data-stu-id="32b98-118">On instance...</span></span>|<span data-ttu-id="32b98-119">建立登入及授與連接權限給...</span><span class="sxs-lookup"><span data-stu-id="32b98-119">Create logins for and grant connection permission to ...</span></span>|  
|--------------------|--------------------------------------------------------------|  
|<span data-ttu-id="32b98-120">sqlA</span><span class="sxs-lookup"><span data-stu-id="32b98-120">sqlA</span></span>|<span data-ttu-id="32b98-121">sqlB 和 sqlC</span><span class="sxs-lookup"><span data-stu-id="32b98-121">sqlB and sqlC</span></span>|  
|<span data-ttu-id="32b98-122">sqlB</span><span class="sxs-lookup"><span data-stu-id="32b98-122">sqlB</span></span>|<span data-ttu-id="32b98-123">sqlA 和 sqlC</span><span class="sxs-lookup"><span data-stu-id="32b98-123">sqlA and sqlC</span></span>|  
|<span data-ttu-id="32b98-124">sqlC</span><span class="sxs-lookup"><span data-stu-id="32b98-124">sqlC</span></span>|<span data-ttu-id="32b98-125">sqlA 與 sqlB</span><span class="sxs-lookup"><span data-stu-id="32b98-125">sqlA and sqlB</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="32b98-126">您也可以利用電腦帳戶代替網域使用者，與網路服務帳戶連接。</span><span class="sxs-lookup"><span data-stu-id="32b98-126">It is possible to connect with the network service account by using the machine account instead of a domain user.</span></span> <span data-ttu-id="32b98-127">如果使用電腦帳戶，則必須將該帳戶新增為其他個伺服器執行個體的使用者。</span><span class="sxs-lookup"><span data-stu-id="32b98-127">If the machine account is used, it must be added as a user on the other server instance.</span></span>  
  
##  <a name="grant-connect-permission"></a><a name="GrantConnect"></a><span data-ttu-id="32b98-128">Grant Connect 許可權</span><span class="sxs-lookup"><span data-stu-id="32b98-128">Grant Connect Permission</span></span>  
 <span data-ttu-id="32b98-129">一旦在伺服器執行個體上建立登入，就必須授權該登入來連接伺服器執行個體的資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="32b98-129">Once a login has been created on a server instance, the login must be granted permission to connect to the database mirroring endpoint of the server instance.</span></span> <span data-ttu-id="32b98-130">系統管理員可使用 GRANT [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式來授與連接權限。</span><span class="sxs-lookup"><span data-stu-id="32b98-130">The system administrator grants the connect permission using a GRANT [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="32b98-131">如需詳細資訊，請參閱 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="32b98-131">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="32b98-132">相關工作</span><span class="sxs-lookup"><span data-stu-id="32b98-132">Related Tasks</span></span>  
  
-   [<span data-ttu-id="32b98-133">建立登入</span><span class="sxs-lookup"><span data-stu-id="32b98-133">Create a Login</span></span>](../../relational-databases/security/authentication-access/create-a-login.md)  
  
-   <span data-ttu-id="32b98-134">[允許使用 Windows 驗證 &#40;SQL Server&#41;，對資料庫鏡像端點進行網路存取](../database-mirroring-allow-network-access-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="32b98-134">[Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
-   [<span data-ttu-id="32b98-135">使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="32b98-135">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="32b98-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32b98-136">See Also</span></span>  
 <span data-ttu-id="32b98-137">[資料庫鏡像端點 &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="32b98-137">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="32b98-138">[為資料庫鏡像組態進行疑難排解 &#40;SQL Server&#41; &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="32b98-138">[Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span></span>  
 [<span data-ttu-id="32b98-139">針對 AlwaysOn 可用性群組 Configuration &#40;SQL Server&#41;進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="32b98-139">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;</span></span>](../availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
