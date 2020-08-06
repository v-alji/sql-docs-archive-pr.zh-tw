---
title: LocalDB 的 SQL Server Native Client 支援 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 127569d1-a9f7-49bf-a561-c084986a8871
author: rothja
ms.author: jroth
ms.openlocfilehash: b08ea46e8db1b665280116a439b95748f69d03ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593362"
---
# <a name="sql-server-native-client-support-for-localdb"></a><span data-ttu-id="32824-102">SQL Server Native Client 對 LocalDB 的支援</span><span class="sxs-lookup"><span data-stu-id="32824-102">SQL Server Native Client Support for LocalDB</span></span>
  <span data-ttu-id="32824-103">從 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 開始，將會提供稱為 LocalDB 的輕量版 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="32824-103">Beginning in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="32824-104">本主題將討論如何連接到 LocalDB 執行個體中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="32824-104">This topic discusses how to connect to a database in a LocalDB instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32824-105">備註</span><span class="sxs-lookup"><span data-stu-id="32824-105">Remarks</span></span>  
 <span data-ttu-id="32824-106">如需有關 LocalDB 的詳細資訊，包括如何安裝 LocalDB 和設定 LocalDB 執行個體，請參閱：</span><span class="sxs-lookup"><span data-stu-id="32824-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see:</span></span>  
  
-   [<span data-ttu-id="32824-107">SQL Server Express LocalDB 參考</span><span class="sxs-lookup"><span data-stu-id="32824-107">SQL Server Express LocalDB Reference</span></span>](../../sql-server-express-localdb-reference.md)  
  
-   [<span data-ttu-id="32824-108">SQL Server 2014 Express LocalDB</span><span class="sxs-lookup"><span data-stu-id="32824-108">SQL Server 2014 Express LocalDB</span></span>](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 <span data-ttu-id="32824-109">總而言之，LocalDB 可讓您：</span><span class="sxs-lookup"><span data-stu-id="32824-109">To summarize, LocalDB allows you to:</span></span>  
  
-   <span data-ttu-id="32824-110">使用 `sqllocaldb.exe i` 來探索預設執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="32824-110">Use `sqllocaldb.exe i` to discover the name of the default instance.</span></span>  
  
-   <span data-ttu-id="32824-111">使用 `AttachDBFilename` 連接字串關鍵字來指定伺服器應該附加的資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="32824-111">Use the `AttachDBFilename` connection string keyword to specify which database file the server should attach.</span></span> <span data-ttu-id="32824-112">使用時 `AttachDBFilename` ，如果您未以**資料庫**連接字串關鍵字來指定資料庫的名稱，當應用程式關閉時，資料庫將會從 LocalDB 實例中移除。</span><span class="sxs-lookup"><span data-stu-id="32824-112">When using `AttachDBFilename`, if you do not specify the name of the database with the **Database** connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
-   <span data-ttu-id="32824-113">在連接字串中指定 LocalDB 執行個體：</span><span class="sxs-lookup"><span data-stu-id="32824-113">Specify a LocalDB instance in your connection string:</span></span>  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 <span data-ttu-id="32824-114">必要時，您可以使用 sqllocaldb.exe 來建立 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="32824-114">If necessary, you can create a LocalDB instance with sqllocaldb.exe.</span></span> <span data-ttu-id="32824-115">您也可以使用 sqlcmd.exe，在 LocalDB 執行個體中加入和修改資料庫。</span><span class="sxs-lookup"><span data-stu-id="32824-115">You can also use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="32824-116">例如： `sqlcmd -S (localdb)\v11.0` 。</span><span class="sxs-lookup"><span data-stu-id="32824-116">For example, `sqlcmd -S (localdb)\v11.0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32824-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32824-117">See Also</span></span>  
 [<span data-ttu-id="32824-118">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="32824-118">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
