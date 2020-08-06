---
title: cross db ownership chaining 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cross-database ownership chaining
- cross db ownership chaining option
- chaining ownership
ms.assetid: 7b2d49f2-b91c-4aee-a52b-6cc49bed03af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cfb768065cc0aa2aaa7aed0f996b18e46f1da7ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596904"
---
# <a name="cross-db-ownership-chaining-server-configuration-option"></a><span data-ttu-id="19d29-102">跨資料庫擁有權鏈結伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="19d29-102">cross db ownership chaining Server Configuration Option</span></span>
  <span data-ttu-id="19d29-103">使用 [跨資料庫擁有權鏈結] 選項，可為 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體設定跨資料庫擁有權鏈結。</span><span class="sxs-lookup"><span data-stu-id="19d29-103">Use the **cross db ownership chaining** option to configure cross-database ownership chaining for an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="19d29-104">此伺服器選項允許您在資料庫層級控制跨資料庫擁有權鏈結，或允許所有資料庫的跨資料庫擁有權鏈結：</span><span class="sxs-lookup"><span data-stu-id="19d29-104">This server option allows you to control cross-database ownership chaining at the database level or to allow cross-database ownership chaining for all databases:</span></span>  
  
-   <span data-ttu-id="19d29-105">當執行個體的 [跨資料庫擁有權鏈結] 設定為關閉 (0) 時，所有資料庫的跨資料庫擁有權鏈結都會停用。</span><span class="sxs-lookup"><span data-stu-id="19d29-105">When **cross db ownership chaining** is off (0) for the instance, cross-database ownership chaining is disabled for all databases.</span></span>  
  
-   <span data-ttu-id="19d29-106">當執行個體的 [跨資料庫擁有權鏈結] 設定為開啟 (1) 時，所有資料庫的跨資料庫擁有權鏈結都會開啟。</span><span class="sxs-lookup"><span data-stu-id="19d29-106">When **cross db ownership chaining** is on (1) for the instance, cross-database ownership chaining is on for all databases.</span></span>  
  
-   <span data-ttu-id="19d29-107">您可以使用 ALTER DATABASE 陳述式的 SET 子句，來設定個別資料庫的跨資料庫擁有權鏈結。</span><span class="sxs-lookup"><span data-stu-id="19d29-107">You can set cross-database ownership chaining for individual databases using the SET clause of the ALTER DATABASE statement.</span></span> <span data-ttu-id="19d29-108">若您要建立新的資料庫，您可以使用 CREATE DATABASE 陳述式，來為新的資料庫設定跨資料庫擁有權鏈結選項。</span><span class="sxs-lookup"><span data-stu-id="19d29-108">If you are creating a new database, you can set the cross-database ownership chaining option for the new database using the CREATE DATABASE statement.</span></span>  
  
     <span data-ttu-id="19d29-109">除非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體所裝載的資料庫都必須參與跨資料庫擁有權鏈結，而且您了解此設定的安全性含意，否則不建議將 [跨資料庫擁有權鏈結] 設定為 1。</span><span class="sxs-lookup"><span data-stu-id="19d29-109">Setting **cross db ownership chaining** to 1 is not recommended unless all of the databases hosted by the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must participate in cross-database ownership chaining and you are aware of the security implications of this setting.</span></span>  
  
## <a name="controlling-cross-database-ownership-chaining"></a><span data-ttu-id="19d29-110">控制跨資料庫擁有權鏈結</span><span class="sxs-lookup"><span data-stu-id="19d29-110">Controlling Cross-Database Ownership Chaining</span></span>  
 <span data-ttu-id="19d29-111">在開啟或關閉跨資料庫擁有權鏈結之前，請考量下列事項：</span><span class="sxs-lookup"><span data-stu-id="19d29-111">Before turning cross-database ownership chaining on or off, consider the following:</span></span>  
  
-   <span data-ttu-id="19d29-112">您必須是 **系統管理員** 固定伺服器角色的成員，才能開啟或關閉跨資料庫擁有權鏈結。</span><span class="sxs-lookup"><span data-stu-id="19d29-112">You must be a member of the **sysadmin** fixed server role to turn cross-database ownership chaining on or off.</span></span>  
  
-   <span data-ttu-id="19d29-113">在產品伺服器上關閉跨資料庫擁有權鏈結，請完整測試所有的應用程式 (包含協力廠商應用程式)，才能確定變更不會影響應用程式功能。</span><span class="sxs-lookup"><span data-stu-id="19d29-113">Before turning off cross-database ownership chaining on a production server, fully test all applications, including third-party applications, to ensure that the changes do not affect application functionality.</span></span>  
  
-   <span data-ttu-id="19d29-114">若您以 **sp_configure** 來指定 RECONFIGURE，當伺服器執行時，您可以變更 [跨資料庫擁有權鏈結] 選項。</span><span class="sxs-lookup"><span data-stu-id="19d29-114">You can change the **cross db ownership chaining** option while the server is running if you specify RECONFIGURE with **sp_configure**.</span></span>  
  
-   <span data-ttu-id="19d29-115">若您有資料庫需要跨資料庫擁有權鏈結，建議您使用 **sp_configure** 來關閉執行個體的 [跨資料庫擁有權鏈結] 選項，再使用 ALTER DATABASE 陳述式來為有需要的個別資料庫，開啟跨資料庫擁有權鏈結。</span><span class="sxs-lookup"><span data-stu-id="19d29-115">If you have databases that require cross-database ownership chaining, the recommended practice is to turn off the **cross db ownership chaining** option for the instance using **sp_configure**; then turn on cross-database ownership chaining for individual databases that require it using the ALTER DATABASE statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d29-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19d29-116">See Also</span></span>  
 <span data-ttu-id="19d29-117">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="19d29-117">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="19d29-118">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="19d29-118">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="19d29-119">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="19d29-119">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="19d29-120">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="19d29-120">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="19d29-121">RECONFIGURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="19d29-121">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
