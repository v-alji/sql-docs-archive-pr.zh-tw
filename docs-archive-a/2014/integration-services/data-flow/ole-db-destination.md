---
title: OLE DB 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbdest.f1
helpviewer_keywords:
- fast-load data access mode [Integration Services]
- OLE DB destination [Integration Services]
- fast load options [Integration Services]
- fast-load options [Integration Services]
- destinations [Integration Services], OLE DB
- fast load data access mode [Integration Services]
- inserting data
ms.assetid: 873a2fa0-2a02-41fc-a80a-ec9767f36a8a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5227175e80db3a8f31a8b8db8c3d6bee3061bae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593482"
---
# <a name="ole-db-destination"></a><span data-ttu-id="4c7e3-102">OLE DB 目的地</span><span class="sxs-lookup"><span data-stu-id="4c7e3-102">OLE DB Destination</span></span>
  <span data-ttu-id="4c7e3-103">OLE DB 目的地會使用資料庫的資料表、檢視或 SQL 命令將資料載入各種符合 OLE DB 標準的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-103">The OLE DB destination loads data into a variety of OLE DB-compliant databases using a database table or view or an SQL command.</span></span> <span data-ttu-id="4c7e3-104">例如，OLE DB 來源可以將資料載入至 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的資料表中。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-104">For example, the OLE DB source can load data into tables in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="4c7e3-105">OLE DB 目的地提供用於載入資料的五種不同資料存取模式：</span><span class="sxs-lookup"><span data-stu-id="4c7e3-105">The OLE DB destination provides five different data access modes for loading data:</span></span>  
  
-   <span data-ttu-id="4c7e3-106">資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-106">A table or view.</span></span> <span data-ttu-id="4c7e3-107">您可以指定現有的資料表或檢視，或者建立新資料表。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-107">You can specify an existing table or view, or you create a new table.</span></span>  
  
-   <span data-ttu-id="4c7e3-108">使用快速載入選項的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-108">A table or view using fast-load options.</span></span> <span data-ttu-id="4c7e3-109">您可以指定現有的資料表，也可以新建資料表。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-109">You can specify an existing table or create a new table.</span></span>  
  
-   <span data-ttu-id="4c7e3-110">在變數中指定的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-110">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="4c7e3-111">在變數中指定之使用快速載入選項的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-111">A table or view specified in a variable using fast-load options.</span></span>  
  
-   <span data-ttu-id="4c7e3-112">SQL 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-112">The results of an SQL statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c7e3-113">OLE DB 目的地不支援參數。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-113">The OLE DB destination does not support parameters.</span></span> <span data-ttu-id="4c7e3-114">如果需要執行參數化 INSERT 陳述式，請考慮 OLE DB 命令轉換。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-114">If you need to execute a parameterized INSERT statement, consider the OLE DB Command transformation.</span></span> <span data-ttu-id="4c7e3-115">如需相關資訊，請參閱 [OLE DB Command Transformation](transformations/ole-db-command-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-115">For more information, see [OLE DB Command Transformation](transformations/ole-db-command-transformation.md).</span></span>  
  
 <span data-ttu-id="4c7e3-116">當 OLE DB 目的地載入使用雙位元組字元集 (DBCS) 的資料時，如果資料存取模式未使用快速載入選項，而 OLE DB 連接管理員使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLOLEDB)，則資料可能會損毀。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-116">When the OLE DB destination loads data that uses a double-byte character set (DBCS), the data may be corrupted if the data access mode does not use the fast load option and if the OLE DB connection manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLOLEDB).</span></span> <span data-ttu-id="4c7e3-117">若要確定 DBCS 資料的完整性，您應該將 OLE DB 連線管理員設定為使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client，或使用下列其中一個快速載入存取模式：[資料表或檢視表 - 快速載入]  或 [資料表名稱或檢視表名稱變數 - 快速載入]  。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-117">To ensure the integrity of DBCS data you should configure the OLE DB connection manager to use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, or use one of the fast-load access modes: **Table or view - fast load** or **Table name or view name variable - fast load**.</span></span> <span data-ttu-id="4c7e3-118">兩個選項都可從 [OLE DB 目的地編輯器]  對話方塊使用。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-118">Both options are available from the **OLE DB Destination Editor** dialog box.</span></span> <span data-ttu-id="4c7e3-119">在程式設計 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 物件模型時，您應該將 AccessMode 屬性設定為 `OpenRowset Using FastLoad` 、或 `OpenRowset Using FastLoad From Variable` 。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-119">When programming the [!INCLUDE[ssIS](../../includes/ssis-md.md)] object model, you should set the AccessMode property to `OpenRowset Using FastLoad`, or `OpenRowset Using FastLoad From Variable`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c7e3-120">如果使用「[!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中的 [OLE DB 目的地編輯器]  對話方塊來建立 OLE DB 目的地插入資料的目的地資料表，則您可能必須手動選取新建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-120">If you use the **OLE DB Destination Editor** dialog box in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer to create the destination table into which the OLE DB destination inserts data, you may have to select the newly created table manually.</span></span> <span data-ttu-id="4c7e3-121">當 OLE DB 提供者 (例如 DB2 的 OLE DB 提供者) 自動將結構描述識別碼加入資料表名稱時，需進行手動選取。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-121">The need for manual selection occurs when an OLE DB provider, such as the OLE DB provider for DB2, automatically adds schema identifiers to the table name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c7e3-122">視目的地類型而定，[OLE DB 目的地編輯器]  對話方塊產生的 CREATE TABLE 陳述式可能需要進行修改。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-122">The CREATE TABLE statement that the **OLE DB Destination Editor** dialog box generates may require modification depending on the destination type.</span></span> <span data-ttu-id="4c7e3-123">例如，某些目的地並不支援 CREATE TABLE 陳述式所使用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-123">For example, some destinations do not support the data types that the CREATE TABLE statement uses.</span></span>  
  
 <span data-ttu-id="4c7e3-124">此目的地使用 OLE DB 連接管理員連接到資料來源，且連接管理員會指定要使用的 OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-124">This destination uses an OLE DB connection manager to connect to a data source and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="4c7e3-125">如需相關資訊，請參閱 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-125">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="4c7e3-126">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案亦提供您建立 OLE DB 連線管理員所在的資料來源物件，讓 OLE DB 目的地使用資料來源和資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-126">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project also provides the data source object from which you can create an OLE DB connection manager, to make data sources and data source views available to the OLE DB destination.</span></span>  
  
 <span data-ttu-id="4c7e3-127">OLE DB 目的地包含輸入資料行與目的地資料來源中資料行之間的對應。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-127">An OLE DB destination includes mappings between input columns and columns in the destination data source.</span></span> <span data-ttu-id="4c7e3-128">您不一定要將輸入資料行對應到所有目的地資料行，但因目的地資料行屬性的不同，如果輸入資料行未對應到目的地資料行，則可能發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-128">You do not have to map input columns to all destination columns, but depending on the properties of the destination columns, errors can occur if no input columns are mapped to the destination columns.</span></span> <span data-ttu-id="4c7e3-129">例如，如果目的地資料行不允許 Null 值，則輸入資料行必須對應到該資料行。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-129">For example, if a destination column does not allow null values, an input column must be mapped to that column.</span></span> <span data-ttu-id="4c7e3-130">此外，對應之資料行的資料類型必須相容。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-130">In addition, the data types of mapped columns must be compatible.</span></span> <span data-ttu-id="4c7e3-131">例如，您不能將字串資料類型的輸入資料行對應到數值資料類型的目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-131">For example, you cannot map an input column with a string data type to a destination column with a numeric data type.</span></span>  
  
 <span data-ttu-id="4c7e3-132">OLE DB 目的地具有一個規則輸入和一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-132">The OLE DB destination has one regular input and one error output.</span></span>  
  
 <span data-ttu-id="4c7e3-133">如需有關資料類型的詳細資訊，請參閱＜ [Integration Services Data Types](integration-services-data-types.md)＞。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-133">For more information about data types, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
## <a name="fast-load-options"></a><span data-ttu-id="4c7e3-134">快速載入選項</span><span class="sxs-lookup"><span data-stu-id="4c7e3-134">Fast Load Options</span></span>  
 <span data-ttu-id="4c7e3-135">如果 OLE DB 目的地使用快速載入資料存取模式，則您可以在 **OLE DB 目的地編輯器**這個使用者介面中為目的地指定下列快速載入選項：</span><span class="sxs-lookup"><span data-stu-id="4c7e3-135">If the OLE DB destination uses a fast-load data access mode, you can specify the following fast load options in the user interface, **OLE DB Destination Editor**, for the destination:</span></span>  
  
-   <span data-ttu-id="4c7e3-136">保留匯入資料檔中的識別值或使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指派的唯一值。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-136">Keep identity values from the imported data file or use unique values assigned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="4c7e3-137">大量載入作業期間保留 Null 值。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-137">Retain a null value during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="4c7e3-138">大量匯入作業期間檢查目標資料表或檢視的條件約束。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-138">Check constraints on the target table or view during the bulk import operation.</span></span>  
  
-   <span data-ttu-id="4c7e3-139">大量載入作業期間需要資料表層級鎖定。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-139">Acquire a table-level lock for the duration of the bulk load operation.</span></span>  
  
-   <span data-ttu-id="4c7e3-140">指定批次中的資料列數目以及認可大小。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-140">Specify the number of rows in the batch and the commit size.</span></span>  
  
 <span data-ttu-id="4c7e3-141">部分快速載入選項儲存在 OLE DB 目的地的特定屬性中。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-141">Some fast load options are stored in specific properties of the OLE DB destination.</span></span> <span data-ttu-id="4c7e3-142">例如，FastLoadKeepIdentity 指定是否要保留識別值、FastLoadKeepNulls 指定是否要保留 Null 值，而 FastLoadMaxInsertCommitSize 則指定要認可為批次的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-142">For example, FastLoadKeepIdentity specifies whether to keep identify values, FastLoadKeepNulls specifies whether to keep null values, and FastLoadMaxInsertCommitSize specifies the number of rows to commit as a batch.</span></span> <span data-ttu-id="4c7e3-143">其他快速載入選項儲存在 FastLoadOptions 屬性的逗號分隔清單中。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-143">Other fast load options are stored in a comma-separated list in the FastLoadOptions property.</span></span> <span data-ttu-id="4c7e3-144">如果 OLE DB 目的地使用儲存在 FastLoadOptions 中的所有快速載入選項，並列在 [ **OLE DB 目的地編輯器**] 對話方塊中，則屬性的值會設定為 `TABLOCK, CHECK_CONSTRAINTS, ROWS_PER_BATCH=1000` 。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-144">If the OLE DB destination uses all the fast load options that are stored in FastLoadOptions and listed in the **OLE DB Destination Editor** dialog box, the value of the property is set to `TABLOCK, CHECK_CONSTRAINTS, ROWS_PER_BATCH=1000`.</span></span> <span data-ttu-id="4c7e3-145">1000 值代表目的地設定為使用 1000 列的批次。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-145">The value 1000 indicates that the destination is configured to use batches of 1000 rows.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c7e3-146">目的地的任何條件約束失敗都會使 FastLoadMaxInsertCommitSize 所定義的整個資料列批次失敗。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-146">Any constraint failure at the destination causes the entire batch of rows defined by FastLoadMaxInsertCommitSize to fail.</span></span>  
  
 <span data-ttu-id="4c7e3-147">除了 [OLE DB 目的地編輯器]  對話方塊中公開的快速載入選項以外，您還可以在 [進階編輯器]  對話方塊的 FastLoadOptions 屬性中輸入選項，將 OLE DB 目的地設定為使用下列大量載入選項。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-147">In addition to the fast load options exposed in the **OLE DB Destination Editor** dialog box,you can configure the OLE DB destination to use the following bulk load options by typing the options in FastLoadOptions property in the **Advanced Editor** dialog box.</span></span>  
  
|<span data-ttu-id="4c7e3-148">快速載入選項</span><span class="sxs-lookup"><span data-stu-id="4c7e3-148">Fast load option</span></span>|<span data-ttu-id="4c7e3-149">描述</span><span class="sxs-lookup"><span data-stu-id="4c7e3-149">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="4c7e3-150">KILOBYTES_PER_BATCH</span><span class="sxs-lookup"><span data-stu-id="4c7e3-150">KILOBYTES_PER_BATCH</span></span>|<span data-ttu-id="4c7e3-151">指定要插入的大小 (以 KB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-151">Specifies the size in kilobytes to insert.</span></span> <span data-ttu-id="4c7e3-152">選項的格式為 `KILOBYTES_PER_BATCH`  =  \<positive integer value**> \* \*。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-152">The option has the form `KILOBYTES_PER_BATCH` = \<positive integer value**>\*\*.</span></span>|  
|<span data-ttu-id="4c7e3-153">FIRE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="4c7e3-153">FIRE_TRIGGERS</span></span>|<span data-ttu-id="4c7e3-154">指定是否要針對插入資料表上引發觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-154">Specifies whether triggers fire on the insert table.</span></span> <span data-ttu-id="4c7e3-155">選項的格式為 **FIRE_TRIGGERS**。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-155">The option has the form **FIRE_TRIGGERS**.</span></span> <span data-ttu-id="4c7e3-156">選項的存在代表觸發程序會引發。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-156">The presence of the option indicates that triggers fire.</span></span>|  
|<span data-ttu-id="4c7e3-157">ORDER</span><span class="sxs-lookup"><span data-stu-id="4c7e3-157">ORDER</span></span>|<span data-ttu-id="4c7e3-158">指定如何儲存輸入資料。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-158">Specifies how the input data is sorted.</span></span> <span data-ttu-id="4c7e3-159">選項的格式為 ORDER \<column name> ASC&#124;DESC。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-159">The option has the form ORDER \<column name> ASC&#124;DESC.</span></span> <span data-ttu-id="4c7e3-160">可以列出任何數目的資料行，也可以選擇包含排序順序。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-160">Any number of columns may be listed and it is optional to include the sort order.</span></span> <span data-ttu-id="4c7e3-161">如果省略排序順序，大量插入作業會假設資料沒有排序。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-161">If sort order is omitted, the insert operation assumes the data is unsorted.</span></span><br /><br /> <span data-ttu-id="4c7e3-162">注意:如果您使用 ORDER 選項依照資料表的叢集索引來排序輸入資料，將可改善效能。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-162">Note: Performance can be improved if you use the ORDER option to sort the input data according to the clustered index on the table.</span></span>|  
  
 <span data-ttu-id="4c7e3-163">[!INCLUDE[tsql](../../includes/tsql-md.md)] 關鍵字通常是以大寫字母輸入，但是這些關鍵字並不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-163">The [!INCLUDE[tsql](../../includes/tsql-md.md)] keywords are traditionally typed using uppercase letters, but the keywords are not case sensitive.</span></span>  
  
 <span data-ttu-id="4c7e3-164">若要深入了解有關快速載入選項的詳細資訊，請參閱 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-164">To learn more about fast load options, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
## <a name="troubleshooting-the-ole-db-destination"></a><span data-ttu-id="4c7e3-165">疑難排解 OLE DB 目的地</span><span class="sxs-lookup"><span data-stu-id="4c7e3-165">Troubleshooting the OLE DB Destination</span></span>  
 <span data-ttu-id="4c7e3-166">您可以記錄 OLE DB 目的地對外部資料提供者執行的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-166">You can log the calls that the OLE DB destination makes to external data providers.</span></span> <span data-ttu-id="4c7e3-167">您可以使用這項記錄功能，針對 OLE DB 目的地所執行的將資料儲存至外部資料來源的作業進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-167">You can use this logging capability to troubleshoot the saving of data to external data sources that the OLE DB destination performs.</span></span> <span data-ttu-id="4c7e3-168">若要記錄 OLE DB 目的地對外部資料提供者執行的呼叫，請啟用封裝記錄，然後在封裝層級選取 [診斷]  事件。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-168">To log the calls that the OLE DB destination makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="4c7e3-169">如需詳細資訊，請參閱 [封裝執行的疑難排解工具](../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-169">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuring-the-ole-db-destination"></a><span data-ttu-id="4c7e3-170">設定 OLE DB 目的地</span><span class="sxs-lookup"><span data-stu-id="4c7e3-170">Configuring the OLE DB Destination</span></span>  
 <span data-ttu-id="4c7e3-171">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-171">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="4c7e3-172">如需有關可以在 [OLE DB 目的地編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="4c7e3-172">For more information about the properties that you can set in the **OLE DB Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="4c7e3-173">OLE DB 目的地編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="4c7e3-173">OLE DB Destination Editor &#40;Connection Manager Page&#41;</span></span>](../ole-db-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="4c7e3-174">OLE DB 目的地編輯器 &#40;對應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="4c7e3-174">OLE DB Destination Editor &#40;Mappings Page&#41;</span></span>](../ole-db-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="4c7e3-175">OLE DB 目的地編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="4c7e3-175">OLE DB Destination Editor &#40;Error Output Page&#41;</span></span>](../ole-db-destination-editor-error-output-page.md)  
  
 <span data-ttu-id="4c7e3-176">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="4c7e3-176">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="4c7e3-177">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="4c7e3-177">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="4c7e3-178">Common Properties</span><span class="sxs-lookup"><span data-stu-id="4c7e3-178">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="4c7e3-179">OLE DB 自訂屬性</span><span class="sxs-lookup"><span data-stu-id="4c7e3-179">OLE DB Custom Properties</span></span>](ole-db-custom-properties.md)  
  
 <span data-ttu-id="4c7e3-180">如需有關如何設定屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="4c7e3-180">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="4c7e3-181">使用 OLE DB 目的地來載入資料</span><span class="sxs-lookup"><span data-stu-id="4c7e3-181">Load Data by Using the OLE DB Destination</span></span>](ole-db-destination.md)  
  
-   [<span data-ttu-id="4c7e3-182">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="4c7e3-182">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="4c7e3-183">相關內容</span><span class="sxs-lookup"><span data-stu-id="4c7e3-183">Related Content</span></span>  
 [<span data-ttu-id="4c7e3-184">OLE DB 來源</span><span class="sxs-lookup"><span data-stu-id="4c7e3-184">OLE DB Source</span></span>](ole-db-source.md)  
  
 [<span data-ttu-id="4c7e3-185">Integration Services &#40;SSIS&#41; 變數</span><span class="sxs-lookup"><span data-stu-id="4c7e3-185">Integration Services &#40;SSIS&#41; Variables</span></span>](../integration-services-ssis-variables.md)  
  
 [<span data-ttu-id="4c7e3-186">資料流程</span><span class="sxs-lookup"><span data-stu-id="4c7e3-186">Data Flow</span></span>](data-flow.md)  
  
  
