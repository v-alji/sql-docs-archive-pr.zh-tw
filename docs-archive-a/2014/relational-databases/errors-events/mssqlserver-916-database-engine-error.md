---
title: MSSQLSERVER_916 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 916 (Database Engine error)
ms.assetid: 73eb6581-99fe-49a5-9b42-e239d7ffe27f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ee67c1e2f67c3c7903c67082ec3793d9d9820061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595041"
---
# <a name="mssqlserver_916"></a><span data-ttu-id="8cd15-102">MSSQLSERVER_916</span><span class="sxs-lookup"><span data-stu-id="8cd15-102">MSSQLSERVER_916</span></span>
    
## <a name="details"></a><span data-ttu-id="8cd15-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8cd15-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8cd15-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8cd15-104">Product Name</span></span>|<span data-ttu-id="8cd15-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8cd15-105">SQL Server</span></span>|  
|<span data-ttu-id="8cd15-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8cd15-106">Event ID</span></span>|<span data-ttu-id="8cd15-107">916</span><span class="sxs-lookup"><span data-stu-id="8cd15-107">916</span></span>|  
|<span data-ttu-id="8cd15-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="8cd15-108">Event Source</span></span>|<span data-ttu-id="8cd15-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8cd15-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8cd15-110">元件</span><span class="sxs-lookup"><span data-stu-id="8cd15-110">Component</span></span>|<span data-ttu-id="8cd15-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8cd15-111">SQLEngine</span></span>|  
|<span data-ttu-id="8cd15-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8cd15-112">Symbolic Name</span></span>|<span data-ttu-id="8cd15-113">NOTUSER</span><span class="sxs-lookup"><span data-stu-id="8cd15-113">NOTUSER</span></span>|  
|<span data-ttu-id="8cd15-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8cd15-114">Message Text</span></span>|<span data-ttu-id="8cd15-115">伺服器主體 "%.\*ls" 在目前的安全性內容下無法存取資料庫 "%.\*ls"。</span><span class="sxs-lookup"><span data-stu-id="8cd15-115">The server principal "%.\*ls" is not able to access the database "%.\*ls" under the current security context.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8cd15-116">說明</span><span class="sxs-lookup"><span data-stu-id="8cd15-116">Explanation</span></span>  
 <span data-ttu-id="8cd15-117">登入沒有足夠的權限來連接至具名資料庫。</span><span class="sxs-lookup"><span data-stu-id="8cd15-117">The login does not have sufficient permissions to connect to the named database.</span></span> <span data-ttu-id="8cd15-118">可以連接至這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體但在資料庫中沒有特定權限的登入會接收 guest 使用者的權限。</span><span class="sxs-lookup"><span data-stu-id="8cd15-118">Logins that can connect to this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but that do not have specific permissions in a database receive the permissions of the guest user.</span></span> <span data-ttu-id="8cd15-119">此安全措施可以避免某資料庫的使用者無法連接其無權存取的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8cd15-119">This is a security measure to prevent users in one database from connecting to other databases where they do not have privileges.</span></span> <span data-ttu-id="8cd15-120">當 guest 使用者沒有具名資料庫的 CONNECT 權限，也沒有設定可信任的屬性時，即可能會出現此錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="8cd15-120">This error message can occur when the guest user does not have CONNECT permission to the named database and the trustworthy property is not set.</span></span> <span data-ttu-id="8cd15-121">當 guest 使用者沒有具名資料庫的 CONNECT 權限時，可能就會出現這個錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="8cd15-121">This error message can occur when the guest user does not have CONNECT permission to the named database.</span></span>  
  
 <span data-ttu-id="8cd15-122">當 msdb 資料庫的 CONNECT 權限遭到拒絕或撤銷時，如果 [物件總管] 嘗試顯示每個資料庫的以原則為基礎的管理狀態，[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 可能會收到這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="8cd15-122">When CONNECT permission to the msdb database is denied or revoked, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] can receive this error when Object Explorer tries to show the Policy Based Management status of each database.</span></span> <span data-ttu-id="8cd15-123">[物件總管] 會使用目前登入的權限，在 msdb 資料庫中查詢這項資訊，因而導致錯誤發生。</span><span class="sxs-lookup"><span data-stu-id="8cd15-123">Object Explorer uses the permissions of the current login to query the msdb database for this information, which causes the error.</span></span> <span data-ttu-id="8cd15-124">此外，系統也會出現下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="8cd15-124">The following error message also occurs:</span></span>  
  
 <span data-ttu-id="8cd15-125">無法擷取此要求的資料。</span><span class="sxs-lookup"><span data-stu-id="8cd15-125">Failed to retrieve data for this request.</span></span> <span data-ttu-id="8cd15-126">(Microsoft.SqlServer.Management.Sdk.Sfc)</span><span class="sxs-lookup"><span data-stu-id="8cd15-126">(Microsoft.SqlServer.Management.Sdk.Sfc)</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8cd15-127">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8cd15-127">User Action</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="8cd15-128">只要確實了解使用者在不同資料庫是否皆能通過驗證，即可避開此安全性措施。</span><span class="sxs-lookup"><span data-stu-id="8cd15-128">Before circumventing this security measure be sure to have a clear understanding of users are authenticated in various databases.</span></span> <span data-ttu-id="8cd15-129">下列幾種方法可能會允許具有某資料庫權限的使用者，連接其他可能會將資料公開給惡意使用者的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8cd15-129">The following methods may allow users that have permissions in one database to connect to other databases which could expose data to a malicious user.</span></span> <span data-ttu-id="8cd15-130">在啟用自主資料庫時，以下步驟可讓某資料庫的資料庫擁有者授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上其他資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="8cd15-130">When contained databases are enabled, the following steps can allow database owners in one database to grant access to other database on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="8cd15-131">您可以透過下列其中一種方式連接資料庫：</span><span class="sxs-lookup"><span data-stu-id="8cd15-131">You can connect to the database in one of the following ways:</span></span>  
  
-   <span data-ttu-id="8cd15-132">將具名資料庫的存取權授與特定的登入。</span><span class="sxs-lookup"><span data-stu-id="8cd15-132">Grant the specific login access to the named database.</span></span> <span data-ttu-id="8cd15-133">下列範例會將 `Adventure-Works\Larry` 資料庫的存取權授與 `msdb` 登入。</span><span class="sxs-lookup"><span data-stu-id="8cd15-133">The following example grants the login `Adventure-Works\Larry` access to the `msdb` database.</span></span>  
  
     <span data-ttu-id="8cd15-134">USE msdb ;</span><span class="sxs-lookup"><span data-stu-id="8cd15-134">USE msdb ;</span></span>  
  
     <span data-ttu-id="8cd15-135">GO</span><span class="sxs-lookup"><span data-stu-id="8cd15-135">GO</span></span>  
  
     <span data-ttu-id="8cd15-136">GRANT CONNECT TO [Adventure-Works\Larry] ;</span><span class="sxs-lookup"><span data-stu-id="8cd15-136">GRANT CONNECT TO [Adventure-Works\Larry] ;</span></span>  
  
-   <span data-ttu-id="8cd15-137">將錯誤訊息中指定之資料庫的 CONNECT 權限授與 guest 使用者。</span><span class="sxs-lookup"><span data-stu-id="8cd15-137">Grant the CONNECT permission to the database named in the error message for the guest user.</span></span> <span data-ttu-id="8cd15-138">下列範例會將 `CONNECT` 資料庫的 `msdb` 權限授與 `guest` 使用者。</span><span class="sxs-lookup"><span data-stu-id="8cd15-138">The following example grants the `CONNECT` permission to the `msdb` database for the user `guest`.</span></span>  
  
     <span data-ttu-id="8cd15-139">USE msdb ;</span><span class="sxs-lookup"><span data-stu-id="8cd15-139">USE msdb ;</span></span>  
  
     <span data-ttu-id="8cd15-140">GO</span><span class="sxs-lookup"><span data-stu-id="8cd15-140">GO</span></span>  
  
     <span data-ttu-id="8cd15-141">GRANT CONNECT TO guest ;</span><span class="sxs-lookup"><span data-stu-id="8cd15-141">GRANT CONNECT TO guest ;</span></span>  
  
-   <span data-ttu-id="8cd15-142">啟用已經驗證使用者之資料庫的 TRUSTWORTHY 屬性。</span><span class="sxs-lookup"><span data-stu-id="8cd15-142">Enable the TRUSTWORTHY property on the database that has authenticated the user.</span></span>  
  
     `ALTER DATABASE AdventureWorks SET TRUSTWORTHY ON;`  
  
  
