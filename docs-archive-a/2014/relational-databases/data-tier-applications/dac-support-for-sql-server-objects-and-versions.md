---
title: SQL Server 物件與版本的 DAC 支援 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data-tier application [SQL Server], supported objects
- objects [SQL Server], data-tier applications
ms.assetid: b1b78ded-16c0-4d69-8657-ec57925e68fd
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa1ea498f603992ce2a62b51d95e74e0f9a9c584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598990"
---
# <a name="dac-support-for-sql-server-objects-and-versions"></a><span data-ttu-id="56057-102">SQL Server 物件與版本的 DAC 支援</span><span class="sxs-lookup"><span data-stu-id="56057-102">DAC Support For SQL Server Objects and Versions</span></span>
  <span data-ttu-id="56057-103">資料層應用程式 (DAC) 支援最常用的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 物件。</span><span class="sxs-lookup"><span data-stu-id="56057-103">A data-tier application (DAC) supports the most commonly used [!INCLUDE[ssDE](../../includes/ssde-md.md)] objects.</span></span>  
  
 <span data-ttu-id="56057-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="56057-104">**In This Topic**</span></span>  
  
-   [<span data-ttu-id="56057-105">支援的 SQL Server 物件</span><span class="sxs-lookup"><span data-stu-id="56057-105">Supported SQL Server Objects</span></span>](#SupportedObjects)  
  
-   [<span data-ttu-id="56057-106">SQL Server 版本的資料層應用程式支援</span><span class="sxs-lookup"><span data-stu-id="56057-106">Data-tier Application Support by the Versions of SQL Server</span></span>](#SupportByVersion)  
  
-   [<span data-ttu-id="56057-107">資料部署限制</span><span class="sxs-lookup"><span data-stu-id="56057-107">Data Deployment Limitations</span></span>](#DeploymentLimitations)  
  
-   [<span data-ttu-id="56057-108">部署動作的其他考量</span><span class="sxs-lookup"><span data-stu-id="56057-108">Additional Considerations for Deployment Actions</span></span>](#Considerations)  
  
##  <a name="supported-sql-server-objects"></a><a name="SupportedObjects"></a><span data-ttu-id="56057-109">支援的 SQL Server 物件</span><span class="sxs-lookup"><span data-stu-id="56057-109">Supported SQL Server Objects</span></span>  
 <span data-ttu-id="56057-110">在撰寫或編輯資料層應用程式時，只能在其中指定支援的物件。</span><span class="sxs-lookup"><span data-stu-id="56057-110">Only supported objects can be specified in a data-tier application as it is being authored or edited.</span></span> <span data-ttu-id="56057-111">您無法從包含 DAC 不支援之物件的現有資料庫中擷取、註冊或匯入 DAC。</span><span class="sxs-lookup"><span data-stu-id="56057-111">You cannot extract, register, or import a DAC from an existing database that contains objects that are not supported in a DAC.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="56057-112">支援下列 DAC 中的物件。</span><span class="sxs-lookup"><span data-stu-id="56057-112">supports the following objects in a DAC.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="56057-113">DATABASE ROLE</span><span class="sxs-lookup"><span data-stu-id="56057-113">DATABASE ROLE</span></span>|<span data-ttu-id="56057-114">FUNCTION：內嵌資料表值</span><span class="sxs-lookup"><span data-stu-id="56057-114">FUNCTION: Inline Table-valued</span></span>|  
|<span data-ttu-id="56057-115">FUNCTION：多重陳述式資料表值</span><span class="sxs-lookup"><span data-stu-id="56057-115">FUNCTION: Multistatement Table-valued</span></span>|<span data-ttu-id="56057-116">FUNCTION：純量</span><span class="sxs-lookup"><span data-stu-id="56057-116">FUNCTION: Scalar</span></span>|  
|<span data-ttu-id="56057-117">INDEX：叢集</span><span class="sxs-lookup"><span data-stu-id="56057-117">INDEX: Clustered</span></span>|<span data-ttu-id="56057-118">INDEX：非叢集</span><span class="sxs-lookup"><span data-stu-id="56057-118">INDEX: Nonclustered</span></span>|  
|<span data-ttu-id="56057-119">INDEX：空間</span><span class="sxs-lookup"><span data-stu-id="56057-119">INDEX: Spacial</span></span>|<span data-ttu-id="56057-120">INDEX：唯一</span><span class="sxs-lookup"><span data-stu-id="56057-120">INDEX: Unique</span></span>|  
|<span data-ttu-id="56057-121">LOGIN</span><span class="sxs-lookup"><span data-stu-id="56057-121">LOGIN</span></span>|<span data-ttu-id="56057-122">權限</span><span class="sxs-lookup"><span data-stu-id="56057-122">Permissions</span></span>|  
|<span data-ttu-id="56057-123">角色成員資格</span><span class="sxs-lookup"><span data-stu-id="56057-123">Role Memberships</span></span>|<span data-ttu-id="56057-124">SCHEMA</span><span class="sxs-lookup"><span data-stu-id="56057-124">SCHEMA</span></span>|  
|<span data-ttu-id="56057-125">統計資料</span><span class="sxs-lookup"><span data-stu-id="56057-125">Statistics</span></span>|<span data-ttu-id="56057-126">STORED PROCEDURE：Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="56057-126">STORED PROCEDURE: Transact-SQL</span></span>|  
|<span data-ttu-id="56057-127">同義字</span><span class="sxs-lookup"><span data-stu-id="56057-127">Synonyms</span></span>|<span data-ttu-id="56057-128">TABLE：檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="56057-128">TABLE: Check Constraint</span></span>|  
|<span data-ttu-id="56057-129">TABLE：定序</span><span class="sxs-lookup"><span data-stu-id="56057-129">TABLE: Collation</span></span>|<span data-ttu-id="56057-130">TABLE：資料行，包括計算資料行</span><span class="sxs-lookup"><span data-stu-id="56057-130">TABLE: Column, including computed columns</span></span>|  
|<span data-ttu-id="56057-131">TABLE：條件約束，預設值</span><span class="sxs-lookup"><span data-stu-id="56057-131">TABLE: Constraint, Default</span></span>|<span data-ttu-id="56057-132">TABLE：條件約束，外部索引鍵</span><span class="sxs-lookup"><span data-stu-id="56057-132">TABLE: Constraint, Foreign Key</span></span>|  
|<span data-ttu-id="56057-133">TABLE：條件約束，索引</span><span class="sxs-lookup"><span data-stu-id="56057-133">TABLE: Constraint, Index</span></span>|<span data-ttu-id="56057-134">TABLE：條件約束，主索引鍵</span><span class="sxs-lookup"><span data-stu-id="56057-134">TABLE: Constraint, Primary Key</span></span>|  
|<span data-ttu-id="56057-135">TABLE：條件約束，唯一</span><span class="sxs-lookup"><span data-stu-id="56057-135">TABLE: Constraint, Unique</span></span>|<span data-ttu-id="56057-136">TRIGGER：DML</span><span class="sxs-lookup"><span data-stu-id="56057-136">TRIGGER: DML</span></span>|  
|<span data-ttu-id="56057-137">TYPE：HIERARCHYID、GEOMETRY、GEOGRAPHY</span><span class="sxs-lookup"><span data-stu-id="56057-137">TYPE: HIERARCHYID, GEOMETRY, GEOGRAPHY</span></span>|<span data-ttu-id="56057-138">TYPE：使用者定義資料類型</span><span class="sxs-lookup"><span data-stu-id="56057-138">TYPE: User-defined Data Type</span></span>|  
|<span data-ttu-id="56057-139">TYPE：使用者定義資料表類型</span><span class="sxs-lookup"><span data-stu-id="56057-139">TYPE: User-defined Table Type</span></span>|<span data-ttu-id="56057-140">USER</span><span class="sxs-lookup"><span data-stu-id="56057-140">USER</span></span>|  
|<span data-ttu-id="56057-141">VIEW</span><span class="sxs-lookup"><span data-stu-id="56057-141">VIEW</span></span>||  
  
##  <a name="data-tier-application-support-by-the-versions-of-sql-server"></a><a name="SupportByVersion"></a><span data-ttu-id="56057-142">SQL Server 版本的資料層應用程式支援</span><span class="sxs-lookup"><span data-stu-id="56057-142">Data-tier Application Support by the Versions of SQL Server</span></span>  
 <span data-ttu-id="56057-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 各版本對 DAC 作業有不同的支援層級。</span><span class="sxs-lookup"><span data-stu-id="56057-143">The versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] have different levels of support for DAC operations.</span></span> <span data-ttu-id="56057-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本支援的所有 DAC 作業，受到該版本的所有版本支援 (例如 Standard、Enterprise、Developer 或 Evaluation)。</span><span class="sxs-lookup"><span data-stu-id="56057-144">All of the DAC operations supported by a version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are supported by all editions of that version.</span></span>  
  
 <span data-ttu-id="56057-145">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體支援下列 DAC 作業：</span><span class="sxs-lookup"><span data-stu-id="56057-145">Instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] support the following DAC operations:</span></span>  
  
-   <span data-ttu-id="56057-146">所有支援的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本都支援匯出和擷取。</span><span class="sxs-lookup"><span data-stu-id="56057-146">Export and extract are supported on all supported versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="56057-147">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 以及所有 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]和 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]版本都支援所有作業。</span><span class="sxs-lookup"><span data-stu-id="56057-147">All operations are supported on [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] and all versions of [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], and [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span>  
  
-   <span data-ttu-id="56057-148">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Service Pack 2 (SP2) 或更新版本以及 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 或更新版本都支援所有作業。</span><span class="sxs-lookup"><span data-stu-id="56057-148">All operations are supported on [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Service Pack 2 (SP2) or later, and [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 or later.</span></span>  
  
 <span data-ttu-id="56057-149">DAC Framework 包含用戶端工具，以建立和處理 DAC 封裝和匯出檔案。</span><span class="sxs-lookup"><span data-stu-id="56057-149">The DAC Framework comprises the client-side tools for building and processing DAC packages and export files.</span></span> <span data-ttu-id="56057-150">下列產品包含 DAC Framework</span><span class="sxs-lookup"><span data-stu-id="56057-150">The following products include the DAC Framework</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="56057-151">和 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 包含可支援所有 DAC 作業的 DAC Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="56057-151">and [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] includes DAC Framework 3.0, which supports all DAC operations.</span></span>  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="56057-152">SP1 和 Visual Studio 2010 SP1 包含 DAC Framework 1.1，它可支援不含匯出和匯入的所有 DAC 作業。</span><span class="sxs-lookup"><span data-stu-id="56057-152">SP1 and Visual Studio 2010 SP1 included DAC Framework 1.1, which supports all DAC operations except export and import.</span></span>  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="56057-153">和 Visual Studio 2010 包含可支援不含匯出、匯入和就地升級之所有 DAC 作業的 DAC Framework 1.0。</span><span class="sxs-lookup"><span data-stu-id="56057-153">and Visual Studio 2010 included DAC Framework 1.0, which supports all DAC operations except export, import, and in-place upgrade.</span></span>  
  
-   <span data-ttu-id="56057-154">舊版 SQL Server 或 Visual Studio 的用戶端工具不支援 DAC 作業。</span><span class="sxs-lookup"><span data-stu-id="56057-154">The client tools from earlier versions of SQL Server or Visual Studio do not support DAC operations.</span></span>  
  
 <span data-ttu-id="56057-155">舊版 DAC Framework 無法處理使用其中一個 DAC Framework 版本所建立的 DAC 封裝或匯出檔案。</span><span class="sxs-lookup"><span data-stu-id="56057-155">A DAC package or export file built with one version of the DAC Framework cannot be processed by an earlier version of the DAC Framework.</span></span> <span data-ttu-id="56057-156">例如，您無法使用 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 用戶端工具部署使用 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 用戶端工具所擷取的 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="56057-156">For example, a DAC package extracted using the [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] client tools cannot be deployed using the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] client tools.</span></span>  
  
 <span data-ttu-id="56057-157">任何新版 DAC Framework 都可以處理使用其中一個 DAC Framework 版本所建立的 DAC 封裝或匯出檔案。</span><span class="sxs-lookup"><span data-stu-id="56057-157">A DAC package or export file built with one version of the DAC Framework can be processed by any later version of the DAC Framework.</span></span> <span data-ttu-id="56057-158">例如，您可以使用 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP1 或新版用戶端工具部署使用 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 用戶端工具所擷取的 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="56057-158">For example, a DAC package extracted using the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] client tools can be deployed using either the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP1 or higher client tools.</span></span>  
  
##  <a name="data-deployment-limitations"></a><a name="DeploymentLimitations"></a><span data-ttu-id="56057-159">資料部署限制</span><span class="sxs-lookup"><span data-stu-id="56057-159">Data Deployment Limitations</span></span>  
 <span data-ttu-id="56057-160">請注意在 SQL Server 2012 SP1 中 DAC Framework 資料部署引擎內的這些精確度限制。</span><span class="sxs-lookup"><span data-stu-id="56057-160">Note these fidelity limitations in the DAC Framework data deployment engine in SQL Server 2012 SP1.</span></span> <span data-ttu-id="56057-161">這些限制適用於下列 DAC Framework 動作：部署或發行 .dacpac 檔案，以及匯入 .bacpac 檔案。</span><span class="sxs-lookup"><span data-stu-id="56057-161">The limitations apply to the following DAC Framework actions: deploy or publish a .dacpac file, and import a .bacpac file.</span></span>  
  
1.  <span data-ttu-id="56057-162">在某些情況下遺失中繼資料及 sql_variant 資料行內的基底類型。</span><span class="sxs-lookup"><span data-stu-id="56057-162">Loss of metadata for certain conditions and base types within sql_variant columns.</span></span> <span data-ttu-id="56057-163">在受影響的案例下，您將會看見包含下列訊息的警告：  **當由 DAC Framework 部署時，不會保存 sql_variant 資料行內使用之某些資料類型的某些屬性。**</span><span class="sxs-lookup"><span data-stu-id="56057-163">In the affected cases, you will see a warning with the following message:  **Certain properties on certain data types used within a sql_variant column are not preserved when deployed by the DAC Framework.**</span></span>  
  
    -   <span data-ttu-id="56057-164">MONEY、SMALLMONEY、NUMERIC、DECIMAL 基底類型：不會保存有效位數。</span><span class="sxs-lookup"><span data-stu-id="56057-164">MONEY, SMALLMONEY, NUMERIC, DECIMAL base types:  Precision is not preserved.</span></span>  
  
        -   <span data-ttu-id="56057-165">DECIMAL/NUMERIC 基底類型的有效位數為 38："TotalBytes" sql_variant 中繼資料一定會設定為 21。</span><span class="sxs-lookup"><span data-stu-id="56057-165">DECIMAL/NUMERIC base types with precision 38:  the "TotalBytes" sql_variant metadata is always set to 21.</span></span>  
  
    -   <span data-ttu-id="56057-166">所有文字基底類型：所有文字都會套用資料庫的預設定序。</span><span class="sxs-lookup"><span data-stu-id="56057-166">All text base types:  The database default collation is applied for all text.</span></span>  
  
    -   <span data-ttu-id="56057-167">BINARY 基底類型：不會保留最大長度屬性。</span><span class="sxs-lookup"><span data-stu-id="56057-167">BINARY base types:  Max length property is not preserved.</span></span>  
  
    -   <span data-ttu-id="56057-168">TIME、DATETIMEOFFSET 基底類型：有效位數一定會設定為 7。</span><span class="sxs-lookup"><span data-stu-id="56057-168">TIME, DATETIMEOFFSET base types:  Precision is always set to 7.</span></span>  
  
2.  <span data-ttu-id="56057-169">在 sql_variant 資料行內遺失資料。</span><span class="sxs-lookup"><span data-stu-id="56057-169">Loss of data within sql_variant columns.</span></span> <span data-ttu-id="56057-170">在受影響的案例中，您將會看見包含下列訊息的警告：  **當由 DAC Framework 部署小數位數大於 3 之 sql_variant DATETIME2 資料行中的值，將會遺失資料。DATETIME2 值在部署期間限制為小數位數等於 3。**</span><span class="sxs-lookup"><span data-stu-id="56057-170">In the affected case, you will see a warning with the following message:  **There will be data loss when a value in a sql_variant DATETIME2 column with scale greater than 3 is deployed by the DAC Framework. The DATETIME2 value is limited to a scale equal to 3 during deployment.**</span></span>  
  
    -   <span data-ttu-id="56057-171">小數位數大於 3 的 DATETIME2 基底類型：小數位數限制為等於 3。</span><span class="sxs-lookup"><span data-stu-id="56057-171">DATETIME2 base type with scale greater than 3:  scale is limited to equal 3.</span></span>  
  
3.  <span data-ttu-id="56057-172">部署作業會因為 sql_variant 資料行內的以下情況而失敗。</span><span class="sxs-lookup"><span data-stu-id="56057-172">Deployment operation fails for the following conditions within sql_variant columns.</span></span> <span data-ttu-id="56057-173">在受影響的案例中，您將會看見包含下列訊息的對話方塊：  **由於 DAC Framework 中的資料限制，所以作業失敗。**</span><span class="sxs-lookup"><span data-stu-id="56057-173">In the affected cases, you will see a dialog with the following message:  **Operation failed due to data limitations in the DAC Framework.**</span></span>  
  
    -   <span data-ttu-id="56057-174">DATETIME2、SMALLDATETIME 和 DATE 基底類型：如果此值超出 DATETIME 範圍，例如年份小於 1753。</span><span class="sxs-lookup"><span data-stu-id="56057-174">DATETIME2, SMALLDATETIME and DATE base types:  If the value is outside of DATETIME range - for example, the year is less than 1753.</span></span>  
  
    -   <span data-ttu-id="56057-175">DECIMAL、NUMERIC 基底類型：如果值的有效位數大於 28。</span><span class="sxs-lookup"><span data-stu-id="56057-175">DECIMAL, NUMERIC base type:  when precision of the value is greater than 28.</span></span>  
  
##  <a name="additional-considerations-for-deployment-actions"></a><a name="Considerations"></a><span data-ttu-id="56057-176">部署動作的其他考慮</span><span class="sxs-lookup"><span data-stu-id="56057-176">Additional Considerations for Deployment Actions</span></span>  
 <span data-ttu-id="56057-177">請注意，DAC Framework 資料部署動作有下列考量：</span><span class="sxs-lookup"><span data-stu-id="56057-177">Note the following considerations for DAC Framework data deployment actions:</span></span>  
  
-   <span data-ttu-id="56057-178">**解壓縮/匯出**-使用 DAC Framework 從資料庫建立封裝的動作-例如，解壓縮 .dacpac 檔案、匯出 bacpac 檔案-這些限制都不適用。</span><span class="sxs-lookup"><span data-stu-id="56057-178">**Extract/Export** - On actions that use the DAC Framework to create a package from a database - for example, extract a .dacpac file, export a .bacpac file - these limitations do not apply.</span></span> <span data-ttu-id="56057-179">封裝中的資料為來源資料庫中資料的不失真表示法。</span><span class="sxs-lookup"><span data-stu-id="56057-179">The data in the package is a full-fidelity representation of the data in the source database.</span></span> <span data-ttu-id="56057-180">如果封裝中有上述的任一情況，則擷取/匯出記錄將會透過上述的訊息包含問題摘要。</span><span class="sxs-lookup"><span data-stu-id="56057-180">If any of these conditions are present in the package, the extract/export log will contain a summary of the issues via the messages noted above.</span></span> <span data-ttu-id="56057-181">這是為了警告使用者，他們所建立的封裝中可能會發生資料部署問題。</span><span class="sxs-lookup"><span data-stu-id="56057-181">This is to warn the user of potential data deployment issues with the package they created.</span></span> <span data-ttu-id="56057-182">使用者也會在記錄中看到以下摘要訊息：  **這些限制不會影響 DAC Framework 所建立之 DAC 封裝中儲存之資料類型和值的精確度，而只適用於將 DAC 封裝部署到資料庫所產生的資料類型和值。如需受影響的資料以及如何解決這個限制的詳細資訊，請參閱** [這個主題](https://go.microsoft.com/fwlink/?LinkId=267086)。</span><span class="sxs-lookup"><span data-stu-id="56057-182">The user will also see the following summary message in the log:  **These limitations do not affect the fidelity of the data types and values stored in the DAC package created by the DAC Framework; they only apply to the data types and values resulting from deploying a DAC package to a database. For more information about the data that is affected and how to work around this limitation, see** [this topic](https://go.microsoft.com/fwlink/?LinkId=267086).</span></span>  
  
-   <span data-ttu-id="56057-183">**部署/發行/匯入** - 使用 DAC Framework 將封裝部署到資料庫的動作，例如部署或發行 .dacpac 檔案以及匯入 .bacpac 檔案，這些限制都適用。</span><span class="sxs-lookup"><span data-stu-id="56057-183">**Deploy/Publish/Import** - On actions that use the DAC Framework to deploy a package to a database, like to deploy or publish a .dacpac file, and import a .bacpac file, these limitations do apply.</span></span> <span data-ttu-id="56057-184">目標資料庫中產生的資料可能不包含封裝中資料的不失真表示法。</span><span class="sxs-lookup"><span data-stu-id="56057-184">The data that results in the target database may not contain a full-fidelity representation of the data in the package.</span></span> <span data-ttu-id="56057-185">部署/匯入記錄將會在每個執行個體遇到問題時包含一則訊息 (如上所述)。</span><span class="sxs-lookup"><span data-stu-id="56057-185">The Deploy/Import log will contain a message, noted above, for every instance the issue is encountered.</span></span> <span data-ttu-id="56057-186">錯誤將封鎖此作業 (請參閱上面的類別目錄 3)，但在其他警告的情況下將會繼續。</span><span class="sxs-lookup"><span data-stu-id="56057-186">The operation will be blocked by errors - see category 3 above - but will proceed with the other warnings.</span></span>  
  
     <span data-ttu-id="56057-187">如需此案例中受影響的資料以及如何解決部署/發行/匯入動作之這項限制的詳細資訊，請參閱 [這個主題](https://go.microsoft.com/fwlink/?LinkId=267087)。</span><span class="sxs-lookup"><span data-stu-id="56057-187">For more information about the data that is affected in this scenario and how to work around this limitation for deploy/publish/import actions, see [this topic](https://go.microsoft.com/fwlink/?LinkId=267087).</span></span>  
  
-   <span data-ttu-id="56057-188">因應措施-解壓縮和匯出作業會將完全**失真的 BCP**資料檔案寫入 .dacpac 或 bacpac 檔案。</span><span class="sxs-lookup"><span data-stu-id="56057-188">**Workarounds** - Extract and export operations will write full-fidelity BCP data files into the .dacpac or .bacpac files.</span></span> <span data-ttu-id="56057-189">為了避免限制，請使用 SQL Server BCP.exe 命令列公用程式，將不失真的資料從 DAC 封裝部署到目標資料庫。</span><span class="sxs-lookup"><span data-stu-id="56057-189">To avoid limitations, use the SQL Server BCP.exe command line utility to deploy full-fidelity data to a target database from a DAC package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56057-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56057-190">See Also</span></span>  
 [<span data-ttu-id="56057-191">資料層應用程式</span><span class="sxs-lookup"><span data-stu-id="56057-191">Data-tier Applications</span></span>](data-tier-applications.md)  
  
  
