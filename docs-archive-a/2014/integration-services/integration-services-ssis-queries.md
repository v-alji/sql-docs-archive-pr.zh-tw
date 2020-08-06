---
title: Integration Services (SSIS) 查詢 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Query Builder [Integration Services]
- queries [Integration Services]
- statements [Integration Services]
- queries [Integration Services], about queries in packages
ms.assetid: 8822bd29-4575-46c8-92a0-1a39bc2604c1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5119ff27606ce4e43f65cc129f3caac764e78e0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596162"
---
# <a name="integration-services-ssis-queries"></a><span data-ttu-id="480b6-102">Integration Services (SSIS) 查詢</span><span class="sxs-lookup"><span data-stu-id="480b6-102">Integration Services (SSIS) Queries</span></span>
  <span data-ttu-id="480b6-103">「執行 SQL」工作、OLE DB 來源、OLE DB 目的地和「查閱」轉換可使用 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="480b6-103">The Execute SQL task, the OLE DB source, the OLE DB destination, and the Lookup transformation can use SQL queries.</span></span> <span data-ttu-id="480b6-104">在「執行 SQL」工作中，SQL 陳述式可建立、更新和刪除資料庫物件和資料；執行預存程序；以及執行 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="480b6-104">In the Execute SQL task, the SQL statements can create, update, and delete database objects and data; run stored procedures; and perform SELECT statements.</span></span> <span data-ttu-id="480b6-105">在 OLE DB 來源和「查閱」轉換中的 SQL 陳述式通常都是 SELECT 陳述式或 EXEC 陳述式。</span><span class="sxs-lookup"><span data-stu-id="480b6-105">In the OLE DB source and the Lookup transformation, the SQL statements are typically SELECT statements or EXEC statements.</span></span> <span data-ttu-id="480b6-106">後者最常執行傳回結果集的預存程序。</span><span class="sxs-lookup"><span data-stu-id="480b6-106">The latter most frequently run stored procedures that return result sets.</span></span>  
  
 <span data-ttu-id="480b6-107">可以剖析查詢，以確定它是否有效。</span><span class="sxs-lookup"><span data-stu-id="480b6-107">A query can be parsed to establish whether it is valid.</span></span> <span data-ttu-id="480b6-108">剖析使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]連接的查詢時，會剖析和執行該查詢，並將執行結果 (成功或失敗) 指派給剖析結果。</span><span class="sxs-lookup"><span data-stu-id="480b6-108">When parsing a query that uses a connection to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the query is parsed, executed, and the execution outcome (success or failure) is assigned to the parsing outcome.</span></span> <span data-ttu-id="480b6-109">如果查詢使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]以外的資料連接，就只會剖析陳述式。</span><span class="sxs-lookup"><span data-stu-id="480b6-109">If the query uses a connection to a data other than [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the statement is parsed only.</span></span>  
  
 <span data-ttu-id="480b6-110">SQL 陳述式可藉由下列方式定義：直接輸入到設計師中，或指定包含該陳述式的檔案連接或變數。</span><span class="sxs-lookup"><span data-stu-id="480b6-110">The SQL statement can be defined either by entering it directly in the designer, or by specifying a file connection or a variable that contains the statement.</span></span>  
  
## <a name="direct-input-sql"></a><span data-ttu-id="480b6-111">直接輸入 SQL</span><span class="sxs-lookup"><span data-stu-id="480b6-111">Direct Input SQL</span></span>  
 <span data-ttu-id="480b6-112">「查詢產生器」可在「執行 SQL」工作、OLE DB 來源、OLE DB 目的地和「查閱」轉換的使用者介面上取得。</span><span class="sxs-lookup"><span data-stu-id="480b6-112">Query Builder is available in the user interface for the Execute SQL task, the OLE DB source, the OLE DB destination, and the Lookup transformation.</span></span> <span data-ttu-id="480b6-113">「查詢產生器」有下列優點：</span><span class="sxs-lookup"><span data-stu-id="480b6-113">Query Builder offers the following advantages:</span></span>  
  
-   <span data-ttu-id="480b6-114">以視覺化方式或利用 SQL 命令工作。</span><span class="sxs-lookup"><span data-stu-id="480b6-114">Work visually or with SQL commands.</span></span>  
  
     <span data-ttu-id="480b6-115">「查詢產生器」包含以視覺化方式撰寫查詢的圖形窗格，以及顯示查詢之 SQL 文字的文字窗格。</span><span class="sxs-lookup"><span data-stu-id="480b6-115">Query Builder includes graphical panes that compose your query visually and a text pane that displays the SQL text of your query.</span></span> <span data-ttu-id="480b6-116">您可使用圖形或文字窗格。</span><span class="sxs-lookup"><span data-stu-id="480b6-116">You can work in either the graphical or text panes.</span></span> <span data-ttu-id="480b6-117">「查詢產生器」會同步處理檢視，讓查詢文字和圖形表示永遠都相符。</span><span class="sxs-lookup"><span data-stu-id="480b6-117">Query Builder synchronizes the views so that the query text and graphical representation always match.</span></span>  
  
-   <span data-ttu-id="480b6-118">聯結相關的資料表。</span><span class="sxs-lookup"><span data-stu-id="480b6-118">Join related tables.</span></span>  
  
     <span data-ttu-id="480b6-119">若您加入一個以上的資料表到查詢，「查詢產生器」會自動決定資料表相關的方式，並建構適當的聯結指令。</span><span class="sxs-lookup"><span data-stu-id="480b6-119">If you add more than one table to your query, Query Builder automatically determines how the tables are related and constructs the appropriate join command.</span></span>  
  
-   <span data-ttu-id="480b6-120">查詢或更新資料庫。</span><span class="sxs-lookup"><span data-stu-id="480b6-120">Query or update databases.</span></span>  
  
     <span data-ttu-id="480b6-121">您可以使用「查詢產生器」，利用 Transact-SQL SELECT 陳述式傳回資料，或建立更新、加入或刪除資料庫中資料錄的查詢。</span><span class="sxs-lookup"><span data-stu-id="480b6-121">You can use Query Builder to return data using Transact-SQL SELECT statements, or to create queries that update, add, or delete records in a database.</span></span>  
  
-   <span data-ttu-id="480b6-122">立即檢視並編輯結果。</span><span class="sxs-lookup"><span data-stu-id="480b6-122">View and edit results immediately.</span></span>  
  
     <span data-ttu-id="480b6-123">您可以執行您的查詢並使用方格 (可讓您在資料庫中捲動並編輯資料錄) 中的資料錄集。</span><span class="sxs-lookup"><span data-stu-id="480b6-123">You can execute your query and work with a recordset in a grid that lets you scroll through and edit records in the database.</span></span>  
  
 <span data-ttu-id="480b6-124">儘管「查詢產生器」受到視覺化方式的限制，只能建立 SELECT 查詢，但您可在文字窗格中輸入其他類型的 SQL 陳述式，例如，DELETE 和 UPDATE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="480b6-124">Although Query Builder is visually limited to creating SELECT queries, you can type the SQL for other types of statements such as DELETE and UPDATE statements in the text pane.</span></span> <span data-ttu-id="480b6-125">圖形窗格會自動進行更新，以反映您所輸入的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="480b6-125">The graphical pane is automatically updated to reflect the SQL statement that you typed.</span></span>  
  
 <span data-ttu-id="480b6-126">您還可在工作或資料流程元件對話方塊或 [屬性] 視窗中輸入查詢，以提供直接輸入。</span><span class="sxs-lookup"><span data-stu-id="480b6-126">You can also provide direct input by typing the query in the task or data flow component dialog box or the Properties window.</span></span>  
  
 <span data-ttu-id="480b6-127">如需詳細資訊，請參閱 [查詢產生器](../../2014/integration-services/query-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="480b6-127">For more information, see [Query Builder](../../2014/integration-services/query-builder.md).</span></span>  
  
## <a name="sql-in-files"></a><span data-ttu-id="480b6-128">檔案中的 SQL</span><span class="sxs-lookup"><span data-stu-id="480b6-128">SQL in Files</span></span>  
 <span data-ttu-id="480b6-129">「執行 SQL」工作的 SQL 陳述式也可位於個別檔案中。</span><span class="sxs-lookup"><span data-stu-id="480b6-129">The SQL statement for the Execute SQL task can also reside in a separate file.</span></span> <span data-ttu-id="480b6-130">例如，在執行封裝時，您可以使用工具 (例如， [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中的「查詢編輯器」) 撰寫查詢、將查詢儲存至檔案，然後從檔案讀取該查詢。</span><span class="sxs-lookup"><span data-stu-id="480b6-130">For example, you can write queries using tools such as the Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], save the query to a file, and then read the query from the file when running a package.</span></span> <span data-ttu-id="480b6-131">檔案只能包含要執行的 SQL 陳述式和註解。</span><span class="sxs-lookup"><span data-stu-id="480b6-131">The file can contain only the SQL statements to run and comments.</span></span> <span data-ttu-id="480b6-132">若要使用在檔案中儲存的 SQL 陳述式，您必須提供指定檔案名稱和位置的檔案連接。</span><span class="sxs-lookup"><span data-stu-id="480b6-132">To use a SQL statement stored in a file, you must provide a file connection that specifies the file name and location.</span></span> <span data-ttu-id="480b6-133">如需相關資訊，請參閱 [File Connection Manager](connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="480b6-133">For more information, see [File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="sql-in-variables"></a><span data-ttu-id="480b6-134">變數中的 SQL</span><span class="sxs-lookup"><span data-stu-id="480b6-134">SQL in Variables</span></span>  
 <span data-ttu-id="480b6-135">如果「執行 SQL」工作中的 SQL 陳述式來源是一個變數，則您要提供包含查詢之變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="480b6-135">If the source of the SQL statement in the Execute SQL task is a variable, you provide the name of the variable that contains the query.</span></span> <span data-ttu-id="480b6-136">變數的 Value 屬性包含查詢文字。</span><span class="sxs-lookup"><span data-stu-id="480b6-136">The Value property of the variable contains the query text.</span></span> <span data-ttu-id="480b6-137">您可以將變數的 ValueType 屬性設為字串資料類型，然後將 SQL 陳述式輸入或複製到 Value 屬性中。</span><span class="sxs-lookup"><span data-stu-id="480b6-137">You set the ValueType property of the variable to a string data type and then type or copy the SQL statement into the Value property.</span></span> <span data-ttu-id="480b6-138">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)和[在封裝中使用變數](../../2014/integration-services/use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="480b6-138">For more information, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) and [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md).</span></span>  
  
  
