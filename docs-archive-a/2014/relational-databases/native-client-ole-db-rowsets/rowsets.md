---
title: 資料列集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
ms.assetid: 5e7b3cbe-3670-4e18-8172-2226e0b6b142
author: rothja
ms.author: jroth
ms.openlocfilehash: 1245d17dc0f3757b3c212146c8c162de6e48a483
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593378"
---
# <a name="rowsets"></a><span data-ttu-id="01455-102">資料列集</span><span class="sxs-lookup"><span data-stu-id="01455-102">Rowsets</span></span>
  <span data-ttu-id="01455-103">資料列集是一組資料列，其中包含資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="01455-103">A rowset is a set of rows that contain columns of data.</span></span> <span data-ttu-id="01455-104">資料列集是能讓所有 OLE DB 資料提供者公開表格形式結果集資料的核心物件。</span><span class="sxs-lookup"><span data-stu-id="01455-104">Rowsets are central objects that enable all OLE DB data providers to expose result set data in tabular form.</span></span>  
  
 <span data-ttu-id="01455-105">取用者使用 **IDBCreateSession::CreateSession** 方法建立工作階段之後，就可以使用工作階段上的 **IOpenRowset** 或 **IDBCreateCommand** 介面建立資料列集。</span><span class="sxs-lookup"><span data-stu-id="01455-105">After a consumer creates a session by using the **IDBCreateSession::CreateSession** method, the consumer can use either the **IOpenRowset** or **IDBCreateCommand** interface on the session to create a rowset.</span></span> <span data-ttu-id="01455-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者同時支援這兩個介面。</span><span class="sxs-lookup"><span data-stu-id="01455-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports both of these interfaces.</span></span> <span data-ttu-id="01455-107">此處描述這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="01455-107">Both of these methods are described here.</span></span>  
  
-   <span data-ttu-id="01455-108">呼叫 **IOpenRowset::OpenRowset** 方法來建立資料列集。</span><span class="sxs-lookup"><span data-stu-id="01455-108">Create a rowset by calling the **IOpenRowset::OpenRowset** method.</span></span>  
  
     <span data-ttu-id="01455-109">這相當於在單一資料表上建立資料列集。</span><span class="sxs-lookup"><span data-stu-id="01455-109">This is equivalent to creating a rowset over a single table.</span></span> <span data-ttu-id="01455-110">此方法會從單一基底資料表開啟並傳回包含所有資料列的資料列集。</span><span class="sxs-lookup"><span data-stu-id="01455-110">This method opens and returns a rowset that includes all of the rows from a single base table.</span></span> <span data-ttu-id="01455-111">其中的 **OpenRowset** 引數是資料表識別碼，可識別要從中建立資料列集的資料表。</span><span class="sxs-lookup"><span data-stu-id="01455-111">One of the arguments to **OpenRowset** is a table ID that identifies the table from which to create the rowset.</span></span>  
  
-   <span data-ttu-id="01455-112">呼叫 **IDBCreateCommand::CreateCommand** 方法來建立命令物件。</span><span class="sxs-lookup"><span data-stu-id="01455-112">Create a command object by calling the **IDBCreateCommand::CreateCommand** method.</span></span>  
  
     <span data-ttu-id="01455-113">命令物件會執行提供者支援的命令。</span><span class="sxs-lookup"><span data-stu-id="01455-113">The command object executes commands that the provider supports.</span></span> <span data-ttu-id="01455-114">利用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者，取用者可以指定任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，例如 SELECT 陳述式或預存程序的呼叫。</span><span class="sxs-lookup"><span data-stu-id="01455-114">With the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the consumer can specify any [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, such as a SELECT statement or a call to a stored procedure.</span></span> <span data-ttu-id="01455-115">使用命令物件建立資料列集的步驟如下：</span><span class="sxs-lookup"><span data-stu-id="01455-115">The steps for creating a rowset by using a command object are:</span></span>  
  
    1.  <span data-ttu-id="01455-116">取用者會呼叫工作階段上的 **IDBCreateCommand::CreateCommand** 方法來取得在命令物件上要求 **ICommandText** 介面的命令物件。</span><span class="sxs-lookup"><span data-stu-id="01455-116">The consumer calls the **IDBCreateCommand::CreateCommand** method on the session to get a command object requesting the **ICommandText** interface on the command object.</span></span> <span data-ttu-id="01455-117">這個 **ICommandText** 介面會設定及擷取實際的命令文字。</span><span class="sxs-lookup"><span data-stu-id="01455-117">This **ICommandText** interface sets and retrieves the actual command text.</span></span> <span data-ttu-id="01455-118">取用者會呼叫 **ICommandText::SetCommandText** 方法來填入文字命令。</span><span class="sxs-lookup"><span data-stu-id="01455-118">The consumer fills in the text command by calling the **ICommandText::SetCommandText** method.</span></span>  
  
    2.  <span data-ttu-id="01455-119">使用者會針對命令呼叫 **ICommand::Execute** 方法。</span><span class="sxs-lookup"><span data-stu-id="01455-119">The user calls the **ICommand::Execute** method on the command.</span></span> <span data-ttu-id="01455-120">命令執行時所建立的資料列集物件包含來自命令的結果集。</span><span class="sxs-lookup"><span data-stu-id="01455-120">The rowset object built when the command executes contains the result set from the command.</span></span>  
  
 <span data-ttu-id="01455-121">取用者可以使用 **ICommandProperties** 介面來取得或設定 **ICommand::Execute** 介面所執行之命令傳回的資料列集屬性。</span><span class="sxs-lookup"><span data-stu-id="01455-121">The consumer can use the **ICommandProperties** interface to get or set the properties for the rowset returned by the command executed by the **ICommand::Execute** interfaces.</span></span> <span data-ttu-id="01455-122">最常要求的屬性為資料列集必須支援的介面。</span><span class="sxs-lookup"><span data-stu-id="01455-122">The most commonly requested properties are the interfaces the rowset must support.</span></span> <span data-ttu-id="01455-123">除了介面之外，取用者可以要求修改資料列集或介面之行為的屬性。</span><span class="sxs-lookup"><span data-stu-id="01455-123">In addition to interfaces, the consumer can request properties that modify the behavior of the rowset or interface.</span></span>  
  
 <span data-ttu-id="01455-124">取用者會使用 **IRowset::Release** 方法釋放資料列集。</span><span class="sxs-lookup"><span data-stu-id="01455-124">Consumers release rowsets with the **IRowset::Release** method.</span></span> <span data-ttu-id="01455-125">釋放資料列集時，也會釋放取用者在該資料列集上保留的所有資料列控制代碼。</span><span class="sxs-lookup"><span data-stu-id="01455-125">Releasing a rowset releases any row handles held by the consumer on that rowset.</span></span> <span data-ttu-id="01455-126">釋放資料列集不會釋放存取子。</span><span class="sxs-lookup"><span data-stu-id="01455-126">Releasing a rowset does not release the accessors.</span></span> <span data-ttu-id="01455-127">如果您有 **IAccessor** 介面，仍然必須釋放該介面。</span><span class="sxs-lookup"><span data-stu-id="01455-127">If you have an **IAccessor** interface, it still has to be released.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="01455-128">本節內容</span><span class="sxs-lookup"><span data-stu-id="01455-128">In This Section</span></span>  
  
-   [<span data-ttu-id="01455-129">以 IOpenRowset 建立資料列集</span><span class="sxs-lookup"><span data-stu-id="01455-129">Creating a Rowset with IOpenRowset</span></span>](creating-a-rowset-with-iopenrowset.md)  
  
-   [<span data-ttu-id="01455-130">使用 ICommand:: Execute 建立資料列集</span><span class="sxs-lookup"><span data-stu-id="01455-130">Creating Rowsets with ICommand::Execute</span></span>](creating-rowsets-with-icommand-execute.md)  
  
-   [<span data-ttu-id="01455-131">資料列集屬性和行為</span><span class="sxs-lookup"><span data-stu-id="01455-131">Rowset Properties and Behaviors</span></span>](rowset-properties-and-behaviors.md)  
  
-   [<span data-ttu-id="01455-132">資料列集和 SQL Server 資料指標</span><span class="sxs-lookup"><span data-stu-id="01455-132">Rowsets and SQL Server Cursors</span></span>](rowsets-and-sql-server-cursors.md)  
  
-   [<span data-ttu-id="01455-133">擷取資料列</span><span class="sxs-lookup"><span data-stu-id="01455-133">Fetching Rows</span></span>](fetching-rows.md)  
  
-   [<span data-ttu-id="01455-134">使用 IRow 來提取單一資料列</span><span class="sxs-lookup"><span data-stu-id="01455-134">Fetching a Single Row with IRow</span></span>](fetching-a-single-row-with-irow.md)  
  
-   [<span data-ttu-id="01455-135">Bookmarks</span><span class="sxs-lookup"><span data-stu-id="01455-135">Bookmarks</span></span>](bookmarks.md)  
  
-   [<span data-ttu-id="01455-136">更新資料列集內的資料</span><span class="sxs-lookup"><span data-stu-id="01455-136">Updating Data in Rowsets</span></span>](updating-data-in-rowsets.md)  
  
## <a name="see-also"></a><span data-ttu-id="01455-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01455-137">See Also</span></span>  
 [<span data-ttu-id="01455-138">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="01455-138">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
