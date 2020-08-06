---
title: 安裝及設定語意搜尋 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], installing
- semantic search [SQL Server], configuring
ms.assetid: 2cdd0568-7799-474b-82fb-65d79df3057c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8d95e0bb2adf3bacf7057b881ab2e85afd50feef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702625"
---
# <a name="install-and-configure-semantic-search"></a><span data-ttu-id="1b8d6-102">安裝及設定語意搜尋</span><span class="sxs-lookup"><span data-stu-id="1b8d6-102">Install and Configure Semantic Search</span></span>
  <span data-ttu-id="1b8d6-103">描述統計語意搜尋的必要元件以及如何安裝或檢查這些必要元件。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-103">Describes the prerequisites for statistical semantic search and how to install or check them.</span></span>  
  
## <a name="installing-semantic-search"></a><span data-ttu-id="1b8d6-104">安裝語意搜尋</span><span class="sxs-lookup"><span data-stu-id="1b8d6-104">Installing Semantic Search</span></span>  
  
###  <a name="how-to-check-whether-semantic-search-is-installed"></a><a name="HowToCheckInstalled"></a><span data-ttu-id="1b8d6-105">如何：檢查是否已安裝語義搜尋</span><span class="sxs-lookup"><span data-stu-id="1b8d6-105">How To: Check Whether Semantic Search Is Installed</span></span>  
 <span data-ttu-id="1b8d6-106">查詢 [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) 中繼資料函數的 **IsFullTextInstalled** 屬性。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-106">Query the **IsFullTextInstalled** property of the [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) metadata function.</span></span>  
  
 <span data-ttu-id="1b8d6-107">傳回值 1 表示已安裝全文檢索搜尋和語意搜尋；傳回值 0 表示未安裝這兩個搜尋。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-107">A return value of 1 indicates that Full-Text Search and Semantic Search are installed; a return value of 0 indicates that they are not installed.</span></span>  
  
```sql  
SELECT SERVERPROPERTY('IsFullTextInstalled');  
GO  
```  
  
###  <a name="how-to-install-semantic-search"></a><a name="BasicsSemanticSearch"></a><span data-ttu-id="1b8d6-108">如何：安裝語義搜尋</span><span class="sxs-lookup"><span data-stu-id="1b8d6-108">How To: Install Semantic Search</span></span>  
 <span data-ttu-id="1b8d6-109">若要安裝語意搜尋，請在安裝期間選取 [要安裝的功能]\*\*\*\* 頁面上的 [搜尋的全文檢索和語意擷取]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-109">To install Semantic Search, select **Full-Text and Semantic Extractions for Search** on the **Features to Install** page during setup.</span></span>  
  
 <span data-ttu-id="1b8d6-110">統計語意搜尋相依於全文檢索搜尋。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-110">Statistical Semantic Search depends on Full-Text Search.</span></span> <span data-ttu-id="1b8d6-111">這兩個選擇性功能會同時安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-111">These two optional features of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] are installed together.</span></span>  
  
## <a name="installing-or-removing-the-semantic-language-statistics-database"></a><span data-ttu-id="1b8d6-112">安裝或移除語意語言統計資料庫</span><span class="sxs-lookup"><span data-stu-id="1b8d6-112">Installing or Removing the Semantic Language Statistics Database</span></span>  
 <span data-ttu-id="1b8d6-113">語意搜尋的其他外部相依性稱為語意語言統計資料庫。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-113">Semantic Search has an additional external dependency that is called the semantic language statistics database.</span></span> <span data-ttu-id="1b8d6-114">此資料庫包含語意搜尋所需的語意語言模型。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-114">This database contains the statistical language models required by semantic search.</span></span> <span data-ttu-id="1b8d6-115">單一語意語言統計資料庫會包含支援語意索引之所有語言的語言模型。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-115">A single semantic language statistics database contains the language models for all the languages that are supported for semantic indexing.</span></span>  
  
###  <a name="how-to-check-whether-the-semantic-language-statistics-database-is-installed"></a><a name="HowToCheckDatabase"></a><span data-ttu-id="1b8d6-116">如何：檢查是否已安裝語意語言統計資料資料庫</span><span class="sxs-lookup"><span data-stu-id="1b8d6-116">How To: Check Whether the Semantic Language Statistics Database Is Installed</span></span>  
 <span data-ttu-id="1b8d6-117">查詢目錄檢視 [sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-117">Query the catalog view [sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql).</span></span>  
  
 <span data-ttu-id="1b8d6-118">如果已安裝並註冊該執行個體的語意語言統計資料庫，則查詢結果會包含有關資料庫的一列資訊。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-118">If the semantic language statistics database is installed and registered for the instance, then the query results contain a single row of information about the database.</span></span>  
  
```vb  
SELECT * FROM sys.fulltext_semantic_language_statistics_database;  
GO  
```  
  
###  <a name="how-to-install-attach-and-register-the-semantic-language-statistics-database"></a><a name="HowToInstallModel"></a><span data-ttu-id="1b8d6-119">如何：安裝、附加及註冊語意語言統計資料資料庫</span><span class="sxs-lookup"><span data-stu-id="1b8d6-119">How To: Install, Attach, and Register the Semantic Language Statistics Database</span></span>  
 <span data-ttu-id="1b8d6-120">語意語言統計資料庫不是由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程式所安裝。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-120">The semantic language statistics database is not installed by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] setup program.</span></span> <span data-ttu-id="1b8d6-121">若要將語意語言統計資料庫設定為語意索引的必要元件，請執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="1b8d6-121">To set up the Semantic Language Statistics database as a prerequisite for semantic indexing, do the following tasks:</span></span>  
  
 <span data-ttu-id="1b8d6-122">**1.安裝語意語言統計資料庫。**</span><span class="sxs-lookup"><span data-stu-id="1b8d6-122">**1. Install the semantic language statistics database.**</span></span>  
 1.  <span data-ttu-id="1b8d6-123">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝媒體上尋找語意語言統計資料庫，或從網站下載。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-123">Locate the semantic language statistics database on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation media or download it from the Web.</span></span>  
  
    -   <span data-ttu-id="1b8d6-124">在 **安裝媒體上，找到名稱為** SemanticLanguageDatabase.msi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的 Windows Installer 套件。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-124">Locate the Windows installer package named **SemanticLanguageDatabase.msi** on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation media.</span></span> <span data-ttu-id="1b8d6-125">找到 32 位元或 64 位元版本的 Installer 套件 (視目標系統而定)。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-125">Locate the 32-bit or 64-bit version of the installer package depending on the target system.</span></span> <span data-ttu-id="1b8d6-126">包含資料夾名稱可識別檔案的 32 位元或 64 位元版本；這兩種版本的檔案名稱本身相同。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-126">The name of the containing folder identifies the 32-bit or 64-bit version of the file; the file name itself is the same for both versions.</span></span>  
  
    -   <span data-ttu-id="1b8d6-127">要從 Microsoft 下載安裝程式套件[嗎？SQL Server？？2014語意語言統計資料](https://go.microsoft.com/fwlink/?LinkID=296743)] 頁面上的 [ [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 下載中心]。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-127">Download the installer package from the [Microsoft?? SQL Server?? 2014 Semantic Language Statistics](https://go.microsoft.com/fwlink/?LinkID=296743) page on the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Download Center.</span></span>  
  
2.  <span data-ttu-id="1b8d6-128">執行**SemanticLanguageDatabase.msi**的 Windows installer 套件，以將資料庫和記錄檔解壓縮。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-128">Run the **SemanticLanguageDatabase.msi** Windows installer package to extract the database and log file.</span></span>  
  
     <span data-ttu-id="1b8d6-129">您可以選擇性地變更目的地目錄。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-129">You can optionally change the destination directory.</span></span> <span data-ttu-id="1b8d6-130">根據預設，安裝程式會將檔案解壓縮至32位或64位 Program Files 資料夾中名為**Microsoft 語義語言資料庫**的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-130">By default, the installer extracts the files to a folder named **Microsoft Semantic Language Database** in the 32-bit or 64-bit Program Files folder.</span></span> <span data-ttu-id="1b8d6-131">MSI 檔案包含壓縮的資料庫檔案和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-131">The MSI file contains a compressed database file and log file.</span></span>  
  
3.  <span data-ttu-id="1b8d6-132">將擷取的資料庫檔案和記錄檔移至檔案系統中的適當位置。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-132">Move the extracted database file and log file to a suitable location in the file system.</span></span>  
  
     <span data-ttu-id="1b8d6-133">如果將檔案保留在預設位置，則不可能為另一個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體擷取資料庫的另一個副本。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-133">If you leave the files in their default location, it will not be possible to extract another copy of the database for another instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1b8d6-134">擷取語意語言統計資料庫時，會將有限權限指派給檔案系統中預設位置的資料庫檔案和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-134">When the semantic language statistics database is extracted, restricted permissions are assigned to the database file and log file in the default location in the file system.</span></span> <span data-ttu-id="1b8d6-135">因此，如果您將資料庫保留在預設位置，則可能沒有附加資料庫的權限。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-135">As a result, you may not have permission to attach the database if you leave it in the default location.</span></span> <span data-ttu-id="1b8d6-136">如果在嘗試附加資料庫時發生錯誤，請適當地移動檔案、檢查及修正檔案系統權限。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-136">If an error is raised when you try to attach the database, move the files, or check and fix file system permissions as appropriate.</span></span>  
  
 <span data-ttu-id="1b8d6-137">**2.附加語意語言統計資料庫。**</span><span class="sxs-lookup"><span data-stu-id="1b8d6-137">**2. Attach the semantic language statistics database.**</span></span>  
 <span data-ttu-id="1b8d6-138">使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 或使用 **FOR ATTACH** 語法呼叫 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)，將資料庫附加至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-138">Attach the database to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or by calling [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) with the **FOR ATTACH** syntax.</span></span> <span data-ttu-id="1b8d6-139">如需詳細資訊，請參閱[資料庫卸離和附加 &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-139">For more information, see [Database Detach and Attach &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md).</span></span>  
  
 <span data-ttu-id="1b8d6-140">根據預設，資料庫的名稱是**預設 semanticsdb**。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-140">By default, the name of the database is **semanticsdb**.</span></span> <span data-ttu-id="1b8d6-141">您可以選擇性地在附加資料庫時提供該資料庫不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-141">You can optionally give the database a different name when you attach it.</span></span> <span data-ttu-id="1b8d6-142">您在後續步驟註冊資料庫時，必須提供此名稱。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-142">You have to provide this name when you register the database in the subsequent step.</span></span>  
  
```sql  
CREATE DATABASE semanticsdb  
            ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb.mdf' )  
            LOG ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb_log.ldf' )  
            FOR ATTACH;  
GO  
```  
  
 <span data-ttu-id="1b8d6-143">此程式碼範例假設您已將資料庫從其預設位置移到新位置。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-143">This code sample assumes that you have moved the database from its default location to a new location.</span></span>  
  
 <span data-ttu-id="1b8d6-144">**3.註冊語意語言統計資料庫。**</span><span class="sxs-lookup"><span data-stu-id="1b8d6-144">**3. Register the semantic language statistics database.**</span></span>  
 <span data-ttu-id="1b8d6-145">呼叫 [sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql) 預存程序，並在附加資料庫時提供您為資料庫命名的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-145">Call the stored procedure [sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql) and provide the name that you gave to the database when you attached it.</span></span>  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = N'semanticsdb';  
GO  
```  
  
###  <a name="how-to-unregister-detach-and-remove-the-semantic-language-statistics-database"></a><a name="HowToUnregister"></a><span data-ttu-id="1b8d6-146">如何：取消註冊、卸離及移除語意語言統計資料資料庫</span><span class="sxs-lookup"><span data-stu-id="1b8d6-146">How To: Unregister, Detach, and Remove the Semantic Language Statistics Database</span></span>  
 <span data-ttu-id="1b8d6-147">**取消註冊語義語言統計資料庫。**</span><span class="sxs-lookup"><span data-stu-id="1b8d6-147">**Unregister the semantic language statistics database.**</span></span>  
 <span data-ttu-id="1b8d6-148">呼叫 [sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql) 預存程序。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-148">Call the stored procedure [sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql).</span></span> <span data-ttu-id="1b8d6-149">執行個體只能有一個語意語言統計資料庫，因此您不需要提供資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-149">You do not have to provide the name of the database since an instance can have only one semantic language statistics database.</span></span>  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
 <span data-ttu-id="1b8d6-150">**卸離語義語言統計資料庫。**</span><span class="sxs-lookup"><span data-stu-id="1b8d6-150">**Detach the semantic language statistics database.**</span></span>  
 <span data-ttu-id="1b8d6-151">呼叫 [sp_detach_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql) 預存程序，並提供資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-151">Call the stored procedure [sp_detach_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql) and provide the name of the database.</span></span>  
  
```sql  
USE master;  
GO  
  
EXEC sp_detach_db @dbname = N'semanticsdb';  
GO  
```  
  
 <span data-ttu-id="1b8d6-152">**移除語義語言統計資料庫。**</span><span class="sxs-lookup"><span data-stu-id="1b8d6-152">**Remove the semantic language statistics database.**</span></span>  
 <span data-ttu-id="1b8d6-153">取消註冊及卸離資料庫之後，就只能刪除資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-153">After unregistering and detaching the database, you can simply delete the database file.</span></span> <span data-ttu-id="1b8d6-154">目前沒有解除安裝程式，而且 [控制台] 的 **[程式和功能]** 也沒有對應的項目。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-154">There is no uninstall program and there is no entry in **Programs and Features** in the Control Panel.</span></span>  
  
###  <a name="requirements-and-restrictions-for-installing-and-removing-the-semantic-language-statistics-database"></a><a name="reqinstall"></a><span data-ttu-id="1b8d6-155">安裝和移除語意語言統計資料資料庫的需求和限制</span><span class="sxs-lookup"><span data-stu-id="1b8d6-155">Requirements and Restrictions for Installing and Removing the Semantic Language Statistics Database</span></span>  
  
-   <span data-ttu-id="1b8d6-156">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體上，您只能附加並註冊一個語意語言統計資料庫。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-156">You can only attach and register one semantic language statistics database on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="1b8d6-157">單一電腦上的每個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體都需要語意語言統計資料庫不同的實體複本。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-157">Each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on a single computer requires a separate physical copy of the semantic language statistics database.</span></span> <span data-ttu-id="1b8d6-158">將一個複本附加至每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-158">Attach one copy to each instance.</span></span>  
  
-   <span data-ttu-id="1b8d6-159">您無法卸離有效且已註冊的語意語言統計資料庫，然後將它取代成具有相同名稱的任意資料庫。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-159">You cannot detach a valid and registered semantic language statistics database and replace it with an arbitrary database that has the same name.</span></span> <span data-ttu-id="1b8d6-160">這樣做會導致使用中或未來的索引母體擴展失敗。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-160">Doing so will cause active or future index populations to fail.</span></span>  
  
-   <span data-ttu-id="1b8d6-161">語意語言統計資料庫是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-161">The semantic language statistics database is read-only.</span></span> <span data-ttu-id="1b8d6-162">您不能自訂這個資料庫。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-162">You cannot customize this database.</span></span> <span data-ttu-id="1b8d6-163">如果您以任何方式改變資料庫的內容，則未來語意索引的結果就不具決定性。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-163">If you alter the content of the database in any way, the results for future semantic indexing are indeterministic.</span></span> <span data-ttu-id="1b8d6-164">若要還原這項資料的原始狀態，您可以卸除已改變的資料庫，然後下載並附加全新且尚未改變的資料庫複本。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-164">To restore the original state of this data, you can drop the altered database, and download and attach a new and unaltered copy of the database.</span></span>  
  
-   <span data-ttu-id="1b8d6-165">您可以卸離或卸除語意語言統計資料庫。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-165">It is possible to detach or drop the semantic language statistics database.</span></span> <span data-ttu-id="1b8d6-166">如果有任何作用中的索引作業在資料庫上有讀取鎖定，則卸離或卸載操作將會失敗或超時。這與現有的行為一致。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-166">If there are any active indexing operations that have read locks on the database, then the detach or drop operation will fail or time out. This is consistent with existing behavior.</span></span> <span data-ttu-id="1b8d6-167">移除資料庫之後，語意索引作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-167">After the database is removed, semantic indexing operations will fail.</span></span>  
  
## <a name="installing-optional-support-for-newer-document-types"></a><span data-ttu-id="1b8d6-168">安裝選擇性的新版文件類型支援</span><span class="sxs-lookup"><span data-stu-id="1b8d6-168">Installing Optional Support for Newer Document Types</span></span>  
  
###  <a name="how-to-install-the-latest-filters-for-microsoft-office-and-other-microsoft-document-types"></a><a name="office"></a><span data-ttu-id="1b8d6-169">如何：安裝 Microsoft Office 和其他 Microsoft 檔案類型的最新篩選</span><span class="sxs-lookup"><span data-stu-id="1b8d6-169">How to: Install the Latest Filters for Microsoft Office and other Microsoft Document Types</span></span>  
 <span data-ttu-id="1b8d6-170">此版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會安裝最新的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 斷詞工具和字幹，但是不會安裝 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office 文件和其他 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 文件類型的最新篩選。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-170">This release of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installs the latest [!INCLUDE[msCoName](../../../includes/msconame-md.md)] word breakers and stemmers, but does not install the latest filters for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office documents and other [!INCLUDE[msCoName](../../../includes/msconame-md.md)] document types.</span></span> <span data-ttu-id="1b8d6-171">這些篩選是針對以最新版 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office 和其他 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 應用程式建立的文件編製索引時所必要。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-171">These filters are required for indexing documents created with recent versions of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office and other [!INCLUDE[msCoName](../../../includes/msconame-md.md)] applications.</span></span> <span data-ttu-id="1b8d6-172">若要下載最新的篩選，請參閱 [Microsoft Office 2010 篩選套件](https://www.microsoft.com/download/details.aspx?id=17062)。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-172">To download the latest filters, see [Microsoft Office 2010 Filter Packs](https://www.microsoft.com/download/details.aspx?id=17062).</span></span>  
  
  
