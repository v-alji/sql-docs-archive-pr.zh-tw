---
title: 使用 BULK INSERT 或 OPENROWSET (BULK...) 匯入大量資料 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- BULK INSERT statement, importing data from a remote data file
- bulk importing [SQL Server], methods
- bulk exporting [SQL Server], methods
- OPENROWSET function, BULK INSERT
- bulk importing [SQL Server], security
- bulk rowset providers [SQL Server]
- bulk exporting [SQL Server], BULK INSERT statement
- remote data access [SQL Server], bulk importing
- bulk importing [SQL Server], BULK INSERT statement
- Transact-SQL bulk export/import operations
ms.assetid: 18a64236-0285-46ea-8929-6ee9bcc020b9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: be36167020b96dba6d494685d958c38e0e6afbba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598379"
---
# <a name="import-bulk-data-by-using-bulk-insert-or-openrowsetbulk-sql-server"></a><span data-ttu-id="19f82-102">使用 BULK INSERT 或 OPENROWSET(BULK...) 匯入大量資料 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="19f82-102">Import Bulk Data by Using BULK INSERT or OPENROWSET(BULK...) (SQL Server)</span></span>
  <span data-ttu-id="19f82-103">本主題提供一個概觀，說明如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] BULK INSERT 陳述式與 INSERT...SELECT \* FROM OPENROWSET(BULK...) 陳述式，從資料檔案大量匯入資料到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中。</span><span class="sxs-lookup"><span data-stu-id="19f82-103">This topic provides an overview of how to use the [!INCLUDE[tsql](../../includes/tsql-md.md)] BULK INSERT statement and the INSERT...SELECT \* FROM OPENROWSET(BULK...) statement to bulk import data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="19f82-104">本主題也將說明有關使用 BULK INSERT 和 OPENROWSET(BULK…)，以及使用這些方法從遠端資料來源大量匯入時的安全性考量。</span><span class="sxs-lookup"><span data-stu-id="19f82-104">This topic also describes security considerations for using BULK INSERT and OPENROWSET(BULK...), and using these methods to bulk import from a remote data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19f82-105">當您使用 BULK INSERT 或 OPENROWSET(BULK…) 時，了解 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本處理模擬的方式相當重要。</span><span class="sxs-lookup"><span data-stu-id="19f82-105">When you use BULK INSERT or OPENROWSET(BULK...), it is important to understand how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version handles impersonation.</span></span> <span data-ttu-id="19f82-106">如需詳細資訊，請參閱本主題稍後的「安全性考量」。</span><span class="sxs-lookup"><span data-stu-id="19f82-106">For more information, see "Security Considerations," later in this topic.</span></span>  
  
## <a name="bulk-insert-statement"></a><span data-ttu-id="19f82-107">BULK INSERT 陳述式</span><span class="sxs-lookup"><span data-stu-id="19f82-107">BULK INSERT Statement</span></span>  
 <span data-ttu-id="19f82-108">BULK INSERT 會從資料檔案將資料載入資料表。</span><span class="sxs-lookup"><span data-stu-id="19f82-108">BULK INSERT loads data from a data file into a table.</span></span> <span data-ttu-id="19f82-109">此功能與 **bcp** 命令的 **in** 選項相似，但卻是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序來讀取資料檔案。</span><span class="sxs-lookup"><span data-stu-id="19f82-109">This functionality is similar to that provided by the **in** option of the **bcp** command; however, the data file is read by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="19f82-110">如需 BULK INSERT 語法的描述，請參閱 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="19f82-110">For a description of the BULK INSERT syntax, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="19f82-111">範例</span><span class="sxs-lookup"><span data-stu-id="19f82-111">Examples</span></span>  
 <span data-ttu-id="19f82-112">如需 BULK INSERT 範例，請參閱：</span><span class="sxs-lookup"><span data-stu-id="19f82-112">For BULK INSERT examples, see:</span></span>  
  
-   [<span data-ttu-id="19f82-113">BULK INSERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-113">BULK INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
-   [<span data-ttu-id="19f82-114">大量匯入與匯出 XML 文件的範例 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-114">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="19f82-115">大量匯入資料時保留識別值 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-115">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="19f82-116">大量匯入期間保留 Null 或使用預設值 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-116">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="19f82-117">指定欄位與資料列結束字元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-117">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="19f82-118">使用格式檔案大量匯入資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-118">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="19f82-119">使用字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-119">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="19f82-120">使用原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-120">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="19f82-121">使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-121">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="19f82-122">使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-122">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="19f82-123">使用格式檔案略過資料表資料行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-123">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="19f82-124">使用格式檔案將資料表資料行對應至資料檔案欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-124">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="openrowsetbulk-function"></a><span data-ttu-id="19f82-125">OPENROWSET(BULK...)函式</span><span class="sxs-lookup"><span data-stu-id="19f82-125">OPENROWSET(BULK...) Function</span></span>  
 <span data-ttu-id="19f82-126">OPENROWSET BULK 資料列集提供者可透過呼叫 OPENROWSET 函數及指定 BULK 選項加以存取。</span><span class="sxs-lookup"><span data-stu-id="19f82-126">The OPENROWSET bulk rowset provider is accessed by calling the OPENROWSET function and specifying the BULK option.</span></span> <span data-ttu-id="19f82-127">OPENROWSET(BULK…) 函數可讓您透過 OLE DB 提供者連接到遠端資料來源 (例如資料檔案)，以存取遠端資料。</span><span class="sxs-lookup"><span data-stu-id="19f82-127">The OPENROWSET(BULK...) function allows you to access remote data by connecting to a remote data source, such as a data file, through an OLE DB provider.</span></span>  
  
 <span data-ttu-id="19f82-128">若要大量匯入資料，請從 INSERT 陳述式內的 SELECT…FROM 子句呼叫 OPENROWSET(BULK…)。</span><span class="sxs-lookup"><span data-stu-id="19f82-128">To bulk import data, call OPENROWSET(BULK...) from a SELECT...FROM clause within an INSERT statement.</span></span> <span data-ttu-id="19f82-129">大量匯入資料的基本語法是：</span><span class="sxs-lookup"><span data-stu-id="19f82-129">The basic syntax for bulk importing data is:</span></span>  
  
 <span data-ttu-id="19f82-130">INSERT ...SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="19f82-130">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
  
 <span data-ttu-id="19f82-131">當用於 INSERT 陳述式時，OPENROWSET(BULK...) 支援資料表提示。</span><span class="sxs-lookup"><span data-stu-id="19f82-131">When used in an INSERT statement, OPENROWSET(BULK...) supports table hints.</span></span> <span data-ttu-id="19f82-132">除了一般的資料表提示 (例如 TABLOCK) 之外，BULK 子句也接受下列特殊化資料表提示：IGNORE_CONSTRAINTS (僅忽略 CHECK 條件約束)、IGNORE_TRIGGERS、KEEPDEFAULTS 及 KEEPIDENTITY。</span><span class="sxs-lookup"><span data-stu-id="19f82-132">In addition to the regular table hints, such as TABLOCK, the BULK clause can accept the following specialized table hints: IGNORE_CONSTRAINTS (ignores only the CHECK constraints), IGNORE_TRIGGERS, KEEPDEFAULTS, and KEEPIDENTITY.</span></span> <span data-ttu-id="19f82-133">如需詳細資訊，請參閱[資料表提示 &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)。</span><span class="sxs-lookup"><span data-stu-id="19f82-133">For more information, see [Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span></span>  
  
 <span data-ttu-id="19f82-134">如需 BULK 選項其他用法的資訊，請參閱 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="19f82-134">For information about additional uses of the BULK option, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="19f82-135">範例</span><span class="sxs-lookup"><span data-stu-id="19f82-135">Examples</span></span>  
 <span data-ttu-id="19f82-136">如需 INSERT...SELECT \* FROM OPENROWSET(BULK...) 陳述式的範例，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="19f82-136">For examples of INSERT...SELECT \* FROM OPENROWSET(BULK...) statements, see the following topics:</span></span>  
  
-   [<span data-ttu-id="19f82-137">大量匯入與匯出 XML 文件的範例 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-137">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="19f82-138">大量匯入資料時保留識別值 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-138">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="19f82-139">大量匯入期間保留 Null 或使用預設值 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-139">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="19f82-140">使用格式檔案大量匯入資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-140">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="19f82-141">使用字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-141">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="19f82-142">使用格式檔案略過資料表資料行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-142">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="19f82-143">使用格式檔案略過資料欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-143">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="19f82-144">使用格式檔案將資料表資料行對應至資料檔案欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-144">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="security-considerations"></a><span data-ttu-id="19f82-145">安全性考量</span><span class="sxs-lookup"><span data-stu-id="19f82-145">Security Considerations</span></span>  
 <span data-ttu-id="19f82-146">如果使用者是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入，則會使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序帳戶的安全性設定檔。</span><span class="sxs-lookup"><span data-stu-id="19f82-146">If a user uses a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login, the security profile of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process account is used.</span></span> <span data-ttu-id="19f82-147">使用 SQL Server 驗證的登入無法於 Database Engine 外部進行驗證。</span><span class="sxs-lookup"><span data-stu-id="19f82-147">A login using SQL Server authentication cannot be authenticated outside of the Database Engine.</span></span> <span data-ttu-id="19f82-148">因此，一旦使用 SQL Server 驗證的登入起始 BULK INSERT 命令，將會使用 SQL Server 處理序帳戶 (即 SQL Server Database Engine 服務所使用的帳戶) 的安全性內容建立與資料的連接。</span><span class="sxs-lookup"><span data-stu-id="19f82-148">Therefore, when a BULK INSERT command is initiated by a login using SQL Server authentication, the connection to the data is made using the security context of the SQL Server process account (the account used by the SQL Server Database Engine service).</span></span> <span data-ttu-id="19f82-149">為了能夠成功讀取來源資料，您必須授與 SQL Server Database Engine 所使用的帳戶對來源資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="19f82-149">To successfully read the source data you must grant the account used by the SQL Server Database Engine, access to the source data.</span></span> <span data-ttu-id="19f82-150">相反地，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者是使用 Windows 驗證登入，則該使用者只能讀取其使用者帳戶可存取的檔案，而與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序的安全性設定檔無關。</span><span class="sxs-lookup"><span data-stu-id="19f82-150">In contrast, if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user logs on by using Windows Authentication, the user can read only those files that can be accessed by the user account, regardless of the security profile of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span>  
  
 <span data-ttu-id="19f82-151">例如，有個使用者使用 Windows 驗證登入了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="19f82-151">For example, consider a user who logged in to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span> <span data-ttu-id="19f82-152">如果這個使用者要用 BULK INSERT 或 OPENROWSET 從資料檔案匯入資料到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中，則使用者帳戶必須具有資料檔案的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="19f82-152">For the user to be able to use BULK INSERT or OPENROWSET to import data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, the user account requires read access to the data file.</span></span> <span data-ttu-id="19f82-153">有了資料檔案的存取權之後，即使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序沒有權限存取檔案，使用者還是可以將檔案中的資料匯入到資料表。</span><span class="sxs-lookup"><span data-stu-id="19f82-153">With access to the data file, the user can import data from the file into a table even if the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process does not have permission to access the file.</span></span> <span data-ttu-id="19f82-154">使用者不需要將檔案存取權限授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序。</span><span class="sxs-lookup"><span data-stu-id="19f82-154">The user does not have to grant file-access permission to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="19f82-155">和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 可以設定為，透過轉送已驗證 Windows 使用者的認證，讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體連接到另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="19f82-155">and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows can be configured to enable an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to connect to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by forwarding the credentials of an authenticated Windows user.</span></span> <span data-ttu-id="19f82-156">此設置也稱為「模擬」或「委派」。</span><span class="sxs-lookup"><span data-stu-id="19f82-156">This arrangement is known as *impersonation* or *delegation*.</span></span> <span data-ttu-id="19f82-157">當您使用 BULK INSERT 或 OPENROWSET 時，請務必了解 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本如何處理使用者模擬的安全性。</span><span class="sxs-lookup"><span data-stu-id="19f82-157">Understanding how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version handle security for user impersonation is important when you use BULK INSERT or OPENROWSET.</span></span> <span data-ttu-id="19f82-158">使用者模擬允許資料檔案位於和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序或使用者不同的電腦上。</span><span class="sxs-lookup"><span data-stu-id="19f82-158">User impersonation allows the data file to reside on a different computer than either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process or the user.</span></span> <span data-ttu-id="19f82-159">例如，如果位於 **Computer_A** 的使用者可以存取 **Computer_B**上的資料檔案，且已適當設定認證委派，則使用者可以連接到執行於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Computer_C **上的**執行個體，然後存取 **Computer_B**上的資料檔案，並從該檔案大量匯入資料到 **Computer_C**上的資料表。</span><span class="sxs-lookup"><span data-stu-id="19f82-159">For example, if a user on **Computer_A** has access to a data file on **Computer_B**, and the delegation of credentials has been set appropriately, the user can connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on **Computer_C**, access the data file on **Computer_B**, and bulk import data from that file into a table on **Computer_C**.</span></span>  
  
## <a name="bulk-importing-from-a-remote-data-file"></a><span data-ttu-id="19f82-160">從遠端資料檔案大量匯入</span><span class="sxs-lookup"><span data-stu-id="19f82-160">Bulk Importing from a Remote Data File</span></span>  
 <span data-ttu-id="19f82-161">若要使用 BULK INSERT 或 INSERT...SELECT \* FROM OPENROWSET(BULK...) 從另一部電腦大量匯入資料，則必須在兩部電腦之間共用資料檔案。</span><span class="sxs-lookup"><span data-stu-id="19f82-161">To use BULK INSERT or INSERT...SELECT \* FROM OPENROWSET(BULK...) to bulk import data from another computer, the data file must be shared between the two computers.</span></span> <span data-ttu-id="19f82-162">若要指定共用資料檔案，請使用它的通用命名慣例 (UNC) 名稱，其使用一般格式： **\\\\** <伺服器名稱> **\\** <共用名稱> **\\** <路徑> **\\** <檔案名稱>。</span><span class="sxs-lookup"><span data-stu-id="19f82-162">To specify a shared data file, use its universal naming convention (UNC) name, which takes the general form, **\\\\**_Servername_**\\**_Sharename_**\\**_Path_**\\**_Filename_.</span></span> <span data-ttu-id="19f82-163">此外，用來存取資料檔案的帳戶必須擁有在遠端磁碟上讀取檔案所需的權限。</span><span class="sxs-lookup"><span data-stu-id="19f82-163">Additionally, the account used to access the data file must have the permissions that are required for reading the file on the remote disk.</span></span>  
  
 <span data-ttu-id="19f82-164">例如，下列 `BULK INSERT` 陳述式會從名為 `SalesOrderDetail` 的資料檔案大量匯入資料到 `AdventureWorks` 資料庫的 `newdata.txt`資料表。</span><span class="sxs-lookup"><span data-stu-id="19f82-164">For example, the following `BULK INSERT` statement bulk imports data into the `SalesOrderDetail` table of the `AdventureWorks` database from a data file that is named `newdata.txt`.</span></span> <span data-ttu-id="19f82-165">此資料檔案位於 `\dailyorders` 系統上的 `salesforce` 網路共用目錄上的 `computer2`共用資料夾中。</span><span class="sxs-lookup"><span data-stu-id="19f82-165">This data file resides in a shared folder named `\dailyorders` on a network share directory named `salesforce` on a system named `computer2`.</span></span>  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM '\\computer2\salesforce\dailyorders\neworders.txt';  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="19f82-166">這個限制並不適用於 **bcp** 公用程式，因為用戶端可以獨立讀取檔案，不受 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 影響。</span><span class="sxs-lookup"><span data-stu-id="19f82-166">This restriction does not apply to the **bcp** utility because the client reads the file independently of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19f82-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19f82-167">See Also</span></span>  
 <span data-ttu-id="19f82-168">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="19f82-168">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="19f82-169">[SELECT 子句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="19f82-169">[SELECT Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span></span>  
 <span data-ttu-id="19f82-170">[資料的大量匯入及匯出 &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="19f82-170">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="19f82-171">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="19f82-171">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="19f82-172">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="19f82-172">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 <span data-ttu-id="19f82-173">[FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="19f82-173">[FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) </span></span>  
 <span data-ttu-id="19f82-174">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="19f82-174">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 [<span data-ttu-id="19f82-175">BULK INSERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="19f82-175">BULK INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
  
