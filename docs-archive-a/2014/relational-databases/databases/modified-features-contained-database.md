---
title: 修改的功能 (自主資料庫) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database, modifications to DBs
ms.assetid: a2942509-39a2-4903-b504-ae80a300a9de
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc52821deeb879022881f838c61823b23c0c10c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709518"
---
# <a name="modified-features-contained-database"></a><span data-ttu-id="8492c-102">修改的功能 (自主資料庫)</span><span class="sxs-lookup"><span data-stu-id="8492c-102">Modified Features (Contained Database)</span></span>
  <span data-ttu-id="8492c-103">下列功能已經修改成部分自主資料庫所支援的功能。</span><span class="sxs-lookup"><span data-stu-id="8492c-103">The following features have been modified to be supported by a partially contained database.</span></span> <span data-ttu-id="8492c-104">由於功能通常會進行修改，因此它們不會跨越資料庫界限。</span><span class="sxs-lookup"><span data-stu-id="8492c-104">Features are usually modified so they do not cross the database boundary.</span></span>  
  
 <span data-ttu-id="8492c-105">如需相關資訊，請參閱 [自主資料庫](contained-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="8492c-105">For more information, see [Contained Databases](contained-databases.md).</span></span>  
  
## <a name="alter-database"></a><span data-ttu-id="8492c-106">ALTER DATABASE</span><span class="sxs-lookup"><span data-stu-id="8492c-106">ALTER DATABASE</span></span>  
  
### <a name="application-level"></a><span data-ttu-id="8492c-107">應用程式層級</span><span class="sxs-lookup"><span data-stu-id="8492c-107">Application Level</span></span>  
 <span data-ttu-id="8492c-108">從自主資料庫內部使用 ALTER DATABASE 陳述式時，其語法與用於非自主資料庫的語法有所不同。</span><span class="sxs-lookup"><span data-stu-id="8492c-108">When using the ALTER DATABASE statement from inside of a contained database, the syntax differs from that used for a non-contained database.</span></span> <span data-ttu-id="8492c-109">這項差異包括延伸超過資料庫至執行個體之陳述式元素的限制。</span><span class="sxs-lookup"><span data-stu-id="8492c-109">This difference includes restrictions of elements of the statement that extend beyond the database to the instance.</span></span> <span data-ttu-id="8492c-110">如需詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8492c-110">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
### <a name="instance-level"></a><span data-ttu-id="8492c-111">執行個體層級</span><span class="sxs-lookup"><span data-stu-id="8492c-111">Instance Level</span></span>  
 <span data-ttu-id="8492c-112">在自主資料庫外部使用時，ALTER DATABASE 的語法與用於非自主資料庫的語法有所不同。</span><span class="sxs-lookup"><span data-stu-id="8492c-112">The syntax for the ALTER DATABASE when used outside of a contained database differs from that used for non-contained databases.</span></span> <span data-ttu-id="8492c-113">這些變更可防止跨越資料庫界限。</span><span class="sxs-lookup"><span data-stu-id="8492c-113">These changes prevent crossing the database boundary.</span></span> <span data-ttu-id="8492c-114">如需詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8492c-114">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="create-database"></a><span data-ttu-id="8492c-115">CREATE DATABASE</span><span class="sxs-lookup"><span data-stu-id="8492c-115">CREATE DATABASE</span></span>  
 <span data-ttu-id="8492c-116">自主資料庫的 CREATE DATABASE 語法與非自主資料庫的語法有所不同。</span><span class="sxs-lookup"><span data-stu-id="8492c-116">The CREATE DATABASE syntax for a contained database differs from that for a non-contained database.</span></span> <span data-ttu-id="8492c-117">如需新語法需求和允許事項的相關資訊，請參閱 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8492c-117">See [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)for information about new syntax requirements and allowances.</span></span>  
  
## <a name="temporary-tables"></a><span data-ttu-id="8492c-118">暫存資料表</span><span class="sxs-lookup"><span data-stu-id="8492c-118">Temporary Tables</span></span>  
 <span data-ttu-id="8492c-119">雖然自主資料庫允許使用本機暫存資料表，不過其行為與非自主資料庫的資料表行為有所不同。</span><span class="sxs-lookup"><span data-stu-id="8492c-119">Local temporary tables are permitted within a contained database, but their behavior differs from those in non-contained databases.</span></span> <span data-ttu-id="8492c-120">在非自主資料庫中，暫存資料表資料是在 **tempdb**的定序中定序。</span><span class="sxs-lookup"><span data-stu-id="8492c-120">In non-contained databases, temporary table data is collated in the collation of **tempdb**.</span></span> <span data-ttu-id="8492c-121">在自主資料庫中，暫存資料表資料是在自主資料庫的定序中定序。</span><span class="sxs-lookup"><span data-stu-id="8492c-121">In a contained database temporary table data is collated in the collation of the contained database.</span></span>  
  
 <span data-ttu-id="8492c-122">與暫存資料表相關聯的所有中繼資料 (例如資料表和資料行名稱、索引等等) 都將位於目錄定序中。</span><span class="sxs-lookup"><span data-stu-id="8492c-122">All metadata associated with temporary tables (for example, table and column names, indexes, and so on) will be in the catalog collation.</span></span>  
  
 <span data-ttu-id="8492c-123">具名條件約束無法用於暫存資料表中。</span><span class="sxs-lookup"><span data-stu-id="8492c-123">Named constraints may not be used in temporary tables.</span></span>  
  
 <span data-ttu-id="8492c-124">暫存資料表無法參考使用者定義型別、XML 結構描述集合或使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="8492c-124">Temporary tables may not refer to user-defined types, XML schema collections, or user-defined functions.</span></span>  
  
## <a name="collation"></a><span data-ttu-id="8492c-125">定序</span><span class="sxs-lookup"><span data-stu-id="8492c-125">Collation</span></span>  
 <span data-ttu-id="8492c-126">在非自主資料庫模型中，有三種不同的定序類型：資料庫定序、執行個體定序和 tempdb 定序。</span><span class="sxs-lookup"><span data-stu-id="8492c-126">In the non-contained database model, there are three separate types of collation: Database collation, Instance collation, and tempdb collation.</span></span> <span data-ttu-id="8492c-127">自主資料庫只會使用兩種定序：資料庫定序和新的目錄定序。</span><span class="sxs-lookup"><span data-stu-id="8492c-127">Contained databases use only two collations, database collation and the new catalog collation.</span></span> <span data-ttu-id="8492c-128">如需自主資料庫定序的詳細資訊，請參閱 [自主資料庫定序](contained-database-collations.md) 。</span><span class="sxs-lookup"><span data-stu-id="8492c-128">See [Contained Database Collations](contained-database-collations.md) for more details on contained database collation.</span></span>  
  
## <a name="user-options"></a><span data-ttu-id="8492c-129">User Options</span><span class="sxs-lookup"><span data-stu-id="8492c-129">User Options</span></span>  
 <span data-ttu-id="8492c-130">啟用自主資料庫時， [執行個體的](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) user options 選項 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]必須設定為 0。</span><span class="sxs-lookup"><span data-stu-id="8492c-130">When enabling contained databases, the [user options Option](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) must be set to 0 for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8492c-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8492c-131">See Also</span></span>  
 <span data-ttu-id="8492c-132">[自主資料庫定序](contained-database-collations.md) </span><span class="sxs-lookup"><span data-stu-id="8492c-132">[Contained Database Collations](contained-database-collations.md) </span></span>  
 [<span data-ttu-id="8492c-133">自主資料庫</span><span class="sxs-lookup"><span data-stu-id="8492c-133">Contained Databases</span></span>](contained-databases.md)  
  
  
