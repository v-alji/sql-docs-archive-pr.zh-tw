---
title: 移動資料庫檔案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], moving database files
- files [SQL Server], moving
- data files [SQL Server], moving
- file moving [SQL Server]
- moving full-text catalogs
- moving databases
- full-text catalogs [SQL Server], moving
- moving database files
- scheduled disk maintenance [SQL Server]
- moving files
- relocating database files
- planned database relocations [SQL Server]
- databases [SQL Server], moving
ms.assetid: 89f01b10-5fae-4ed8-b0fb-a4b9f540fd28
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5491f3c4dfd47cac4047d0409c78001be80d6f13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705154"
---
# <a name="move-database-files"></a><span data-ttu-id="d3256-102">移動資料庫檔案</span><span class="sxs-lookup"><span data-stu-id="d3256-102">Move Database Files</span></span>
  <span data-ttu-id="d3256-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，您可以在 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 陳述式的 FILENAME 子句中指定新的檔案位置，以移動系統和使用者資料庫。</span><span class="sxs-lookup"><span data-stu-id="d3256-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can move system and user databases by specifying the new file location in the FILENAME clause of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span> <span data-ttu-id="d3256-104">可以使用此方式來移動資料、記錄以及全文檢索目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="d3256-104">Data, log, and full-text catalog files can be moved in this way.</span></span> <span data-ttu-id="d3256-105">在下列狀況下這個方法將非常有用：</span><span class="sxs-lookup"><span data-stu-id="d3256-105">This may be useful in the following situations:</span></span>  
  
-   <span data-ttu-id="d3256-106">失敗復原。</span><span class="sxs-lookup"><span data-stu-id="d3256-106">Failure recovery.</span></span> <span data-ttu-id="d3256-107">例如，資料庫因硬體失敗而導致在質疑模式下或被關閉。</span><span class="sxs-lookup"><span data-stu-id="d3256-107">For example, the database is in suspect mode or has shut down, because of a hardware failure.</span></span>  
  
-   <span data-ttu-id="d3256-108">計畫的重新放置。</span><span class="sxs-lookup"><span data-stu-id="d3256-108">Planned relocation.</span></span>  
  
-   <span data-ttu-id="d3256-109">排程的磁碟維護重新放置。</span><span class="sxs-lookup"><span data-stu-id="d3256-109">Relocation for scheduled disk maintenance.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3256-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="d3256-110">In This Section</span></span>  
  
|<span data-ttu-id="d3256-111">主題</span><span class="sxs-lookup"><span data-stu-id="d3256-111">Topic</span></span>|<span data-ttu-id="d3256-112">描述</span><span class="sxs-lookup"><span data-stu-id="d3256-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d3256-113">移動使用者資料庫</span><span class="sxs-lookup"><span data-stu-id="d3256-113">Move User Databases</span></span>](move-user-databases.md)|<span data-ttu-id="d3256-114">描述將使用者資料庫檔案和全文檢索目錄檔案移到新位置的程序。</span><span class="sxs-lookup"><span data-stu-id="d3256-114">Describes the procedures for moving user database files and full-text catalog files to a new location.</span></span>|  
|[<span data-ttu-id="d3256-115">移動系統資料庫</span><span class="sxs-lookup"><span data-stu-id="d3256-115">Move System Databases</span></span>](system-databases.md)|<span data-ttu-id="d3256-116">描述將系統資料庫檔案移到新位置的程序。</span><span class="sxs-lookup"><span data-stu-id="d3256-116">Describes the procedures for moving system database files to a new location.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3256-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3256-117">See Also</span></span>  
 <span data-ttu-id="d3256-118">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d3256-118">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="d3256-119">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d3256-119">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="d3256-120">資料庫卸離與附加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d3256-120">Database Detach and Attach &#40;SQL Server&#41;</span></span>](database-detach-and-attach-sql-server.md)  
  
  
