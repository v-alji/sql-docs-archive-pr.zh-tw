---
title: SQL Server XML 大量載入物件模型 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], object model
- ErrorLogFile property
- SGDropTables property
- SGUseID property
- KeepNulls property
- ConnectionCommand property
- SchemaGen property
- XMLFragment property
- SQLXMLBulkLoad object
- ForceTableLock property
- CheckConstraints property
- BulkLoad property
- TempFilePath property
- IgnoreDuplicateKeys property
- Transaction property
- KeepIdentity property
- ConnectionString property
- FireTriggers property
- Execute method
- XML Bulk Load [SQLXML], object model
ms.assetid: a9efbbde-ed2b-4929-acc1-261acaaed19d
author: rothja
ms.author: jroth
ms.openlocfilehash: 364515afaea17ce403f8eb38cb10bbe6003dfe2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686871"
---
# <a name="sql-server-xml-bulk-load-object-model-sqlxml-40"></a><span data-ttu-id="b9da5-102">SQL Server XML 大量載入物件模型 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="b9da5-102">SQL Server XML Bulk Load Object Model (SQLXML 4.0)</span></span>
  <span data-ttu-id="b9da5-103">Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML 大量載入物件模型是由 sqlxmlbulkload.sqlxmlbulkload.4.0 物件所組成。</span><span class="sxs-lookup"><span data-stu-id="b9da5-103">The Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML Bulk Load object model consists of the SQLXMLBulkLoad object.</span></span> <span data-ttu-id="b9da5-104">這個物件支援下列方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="b9da5-104">This object supports the following methods and properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9da5-105">方法</span><span class="sxs-lookup"><span data-stu-id="b9da5-105">Methods</span></span>  
 <span data-ttu-id="b9da5-106">執行</span><span class="sxs-lookup"><span data-stu-id="b9da5-106">Execute</span></span>  
 <span data-ttu-id="b9da5-107">使用當做參數提供的結構描述檔案和資料檔案 (或資料流) 大量載入資料。</span><span class="sxs-lookup"><span data-stu-id="b9da5-107">Bulk loads the data by using the schema file and data file (or stream) that are provided as parameters.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b9da5-108">屬性</span><span class="sxs-lookup"><span data-stu-id="b9da5-108">Properties</span></span>  
 <span data-ttu-id="b9da5-109">BulkLoad</span><span class="sxs-lookup"><span data-stu-id="b9da5-109">BulkLoad</span></span>  
 <span data-ttu-id="b9da5-110">指定是否應該執行大量載入。</span><span class="sxs-lookup"><span data-stu-id="b9da5-110">Specifies whether a Bulk Load should be performed.</span></span> <span data-ttu-id="b9da5-111">如果您只想要產生架構 (查看遵循) 而不執行大量載入的 SchemaGen、SGDropTables 和 SGUseID 屬性，這個屬性就很有用。</span><span class="sxs-lookup"><span data-stu-id="b9da5-111">This property is useful if you want to generate only the schemas (see the SchemaGen, SGDropTables, and SGUseID properties that follow) and not perform a bulk load.</span></span> <span data-ttu-id="b9da5-112">這是布林屬性。</span><span class="sxs-lookup"><span data-stu-id="b9da5-112">This is a Boolean property.</span></span> <span data-ttu-id="b9da5-113">當屬性設定為 TRUE 時，XML 大量載入會執行。</span><span class="sxs-lookup"><span data-stu-id="b9da5-113">When the property is set to TRUE, XML Bulk Load executes.</span></span> <span data-ttu-id="b9da5-114">設定為 FALSE 時，XML 大量載入則不會執行。</span><span class="sxs-lookup"><span data-stu-id="b9da5-114">When it is set to FALSE, XML Bulk Load does not execute.</span></span>  
  
 <span data-ttu-id="b9da5-115">預設值為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-115">The default value is TRUE.</span></span>  
  
 <span data-ttu-id="b9da5-116">CheckConstraints</span><span class="sxs-lookup"><span data-stu-id="b9da5-116">CheckConstraints</span></span>  
 <span data-ttu-id="b9da5-117">指定當 XML 大量載入將資料插入資料行時，是否要檢查在資料行上指定的條件約束 (例如，由於資料行間之主索引鍵/外部索引鍵關聯性緣故的條件約束)。</span><span class="sxs-lookup"><span data-stu-id="b9da5-117">Specifies whether the constraints (such as constraints due to the primary key/foreign key relationship among columns) that are specified on the column should be checked when XML Bulk Load inserts data into the columns.</span></span> <span data-ttu-id="b9da5-118">這是布林屬性。</span><span class="sxs-lookup"><span data-stu-id="b9da5-118">This is a Boolean property.</span></span>  
  
 <span data-ttu-id="b9da5-119">當屬性設定為 TRUE 時，XML 大量載入會檢查插入之每個值的條件約束 (也就是說，條件約束違規會導致錯誤)。</span><span class="sxs-lookup"><span data-stu-id="b9da5-119">When the property is set to TRUE, XML Bulk Load checks the constraints for each value inserted (which means that a constraint violation results in an error).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9da5-120">若要將此屬性保留為 FALSE，您必須具有目標資料表的**ALTER TABLE**許可權。</span><span class="sxs-lookup"><span data-stu-id="b9da5-120">To leave this property as FALSE, you must have **ALTER TABLE** permissions on target tables.</span></span> <span data-ttu-id="b9da5-121">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b9da5-121">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="b9da5-122">預設值為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-122">The default value is FALSE.</span></span> <span data-ttu-id="b9da5-123">設定為 FALSE 時，XML 大量載入會在插入作業期間忽略條件約束。</span><span class="sxs-lookup"><span data-stu-id="b9da5-123">When it is set to FALSE, XML Bulk Load ignores the constraints during an insert operation.</span></span> <span data-ttu-id="b9da5-124">在目前的實作中，您必須以對應結構描述中，主索引鍵和外部索引鍵關聯性的順序定義資料表。</span><span class="sxs-lookup"><span data-stu-id="b9da5-124">In the current implementation, you must define the tables in the order of primary key and foreign key relationships in the mapping schema.</span></span> <span data-ttu-id="b9da5-125">也就是說，具有主索引鍵的資料表必須在具有外部索引鍵的對應資料表之前定義，否則，XML 大量載入會失敗。</span><span class="sxs-lookup"><span data-stu-id="b9da5-125">That is, a table with a primary key must be defined before the corresponding table with the foreign key; otherwise, XML Bulk Load fails.</span></span>  
  
 <span data-ttu-id="b9da5-126">請注意，如果識別碼擴展即將完成，則此選項不會套用，而且條件約束檢查將會保持開啟。</span><span class="sxs-lookup"><span data-stu-id="b9da5-126">Note that if ID Propagation is being done, then this option does not apply and constraint checking will be left on.</span></span> <span data-ttu-id="b9da5-127">如果 `KeepIdentity=False`，而且有定義一個關聯性，其中父系是識別欄位，並在產生值時將其提供給子系，則會發生這個狀況。</span><span class="sxs-lookup"><span data-stu-id="b9da5-127">This occurs when `KeepIdentity=False` and there is a relationship defined where the parent is an identity field and the value is given to the child as it is generated.</span></span>  
  
 <span data-ttu-id="b9da5-128">ConnectionCommand</span><span class="sxs-lookup"><span data-stu-id="b9da5-128">ConnectionCommand</span></span>  
 <span data-ttu-id="b9da5-129">識別現有的連線物件 (例如，XML 大量載入應使用的 ADO 或 ICommand command 物件) 。</span><span class="sxs-lookup"><span data-stu-id="b9da5-129">Identifies an existing connection object (for example, the ADO or ICommand command object) that XML Bulk Load should use.</span></span> <span data-ttu-id="b9da5-130">您可以使用 ConnectionCommand 屬性，而不是使用 ConnectionString 屬性指定連接字串。</span><span class="sxs-lookup"><span data-stu-id="b9da5-130">You can use the ConnectionCommand property instead of specifying a connection string with the ConnectionString property.</span></span> <span data-ttu-id="b9da5-131">如果您使用 ConnectionCommand，則 Transaction 屬性必須設定為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-131">The Transaction property must be set to TRUE if you use ConnectionCommand.</span></span>  
  
 <span data-ttu-id="b9da5-132">如果您同時使用 ConnectionString 和 ConnectionCommand 屬性，則 XML 大量載入會使用最後指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="b9da5-132">If you use both the ConnectionString and ConnectionCommand properties, XML Bulk Load uses the last specified property.</span></span>  
  
 <span data-ttu-id="b9da5-133">預設值是 NULL。</span><span class="sxs-lookup"><span data-stu-id="b9da5-133">The default value is NULL.</span></span>  
  
 <span data-ttu-id="b9da5-134">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="b9da5-134">ConnectionString</span></span>  
 <span data-ttu-id="b9da5-135">識別 OLE DB 連接字串，提供必要的資訊來建立資料庫執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="b9da5-135">Identifies the OLE DB connection string that provides the necessary information to establish a connection to an instance of the database.</span></span> <span data-ttu-id="b9da5-136">如果您同時使用 ConnectionString 和 ConnectionCommand 屬性，則 XML 大量載入會使用最後指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="b9da5-136">If you use both the ConnectionString and ConnectionCommand properties, XML Bulk Load uses the last specified property.</span></span>  
  
 <span data-ttu-id="b9da5-137">預設值是 NULL。</span><span class="sxs-lookup"><span data-stu-id="b9da5-137">The default value is NULL.</span></span>  
  
 <span data-ttu-id="b9da5-138">ErrorLogFile</span><span class="sxs-lookup"><span data-stu-id="b9da5-138">ErrorLogFile</span></span>  
 <span data-ttu-id="b9da5-139">指定 XML 大量載入記錄錯誤和訊息所在的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b9da5-139">Specifies the file name into which the XML Bulk Load logs errors and messages.</span></span> <span data-ttu-id="b9da5-140">預設為空字串，在此情況下，沒有做任何記錄。</span><span class="sxs-lookup"><span data-stu-id="b9da5-140">The default is an empty string, in which case no logging takes place.</span></span>  
  
 <span data-ttu-id="b9da5-141">FireTriggers</span><span class="sxs-lookup"><span data-stu-id="b9da5-141">FireTriggers</span></span>  
 <span data-ttu-id="b9da5-142">指定在目標資料表上定義的觸發程序是否應該在大量載入作業期間引發。</span><span class="sxs-lookup"><span data-stu-id="b9da5-142">Specifies if triggers defined on target tables should fire during the Bulk Load operation.</span></span> <span data-ttu-id="b9da5-143">預設值為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-143">The default is FALSE.</span></span>  
  
 <span data-ttu-id="b9da5-144">設定為 TRUE 時，觸發程序一般將會在插入作業期間引發。</span><span class="sxs-lookup"><span data-stu-id="b9da5-144">When set to TRUE, triggers will fire as per normal during insert operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9da5-145">若要將此屬性保留為 FALSE，您必須具有目標資料表的**ALTER TABLE**許可權。</span><span class="sxs-lookup"><span data-stu-id="b9da5-145">To leave this property as FALSE, you must have **ALTER TABLE** permissions on target tables.</span></span> <span data-ttu-id="b9da5-146">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b9da5-146">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="b9da5-147">請注意，如果識別碼擴展即將完成，則此選項不會套用，而且觸發條件將會保持開啟。</span><span class="sxs-lookup"><span data-stu-id="b9da5-147">Note that if ID Propagation is being done, then this option does not apply and triggers will be left on.</span></span> <span data-ttu-id="b9da5-148">如果 `KeepIdentity=False`，而且有定義一個關聯性，其中父系是識別欄位，並在產生值時將其提供給子系，則會發生這個狀況。</span><span class="sxs-lookup"><span data-stu-id="b9da5-148">This occurs when `KeepIdentity=False` and there is a relationship defined where the parent is an identity field and the value is given to the child as it is generated.</span></span>  
  
 <span data-ttu-id="b9da5-149">ForceTableLock</span><span class="sxs-lookup"><span data-stu-id="b9da5-149">ForceTableLock</span></span>  
 <span data-ttu-id="b9da5-150">指定 XML 大量載入複製資料的目標資料表是否應該在大量載入期間鎖定。</span><span class="sxs-lookup"><span data-stu-id="b9da5-150">Specifies whether the tables into which XML Bulk Load copies data should be locked for the duration of the Bulk Load.</span></span> <span data-ttu-id="b9da5-151">這是布林屬性。</span><span class="sxs-lookup"><span data-stu-id="b9da5-151">This is a Boolean property.</span></span> <span data-ttu-id="b9da5-152">當屬性設定為 TRUE 時，XML 大量載入會取得大量載入期間的資料表鎖定。</span><span class="sxs-lookup"><span data-stu-id="b9da5-152">When the property is set to TRUE, XML Bulk Load acquires table locks for the duration of the Bulk Load.</span></span> <span data-ttu-id="b9da5-153">設定為 FALSE 時，XML 大量載入會在每次將記錄插入資料表時取得資料表鎖定。</span><span class="sxs-lookup"><span data-stu-id="b9da5-153">When it is set to FALSE, XML Bulk Load acquires a table lock each time it inserts a record into a table.</span></span>  
  
 <span data-ttu-id="b9da5-154">預設值為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-154">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="b9da5-155">IgnoreDuplicateKeys</span><span class="sxs-lookup"><span data-stu-id="b9da5-155">IgnoreDuplicateKeys</span></span>  
 <span data-ttu-id="b9da5-156">指定嘗試在索引鍵資料行中插入重複的值時該怎麼辦。</span><span class="sxs-lookup"><span data-stu-id="b9da5-156">Specifies what to do if an attempt is made to insert duplicate values in a key column.</span></span> <span data-ttu-id="b9da5-157">如果此屬性設定為 TRUE，而且嘗試在索引鍵資料行中插入具有重複值的記錄，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不會插入該記錄。</span><span class="sxs-lookup"><span data-stu-id="b9da5-157">If this property is set to TRUE and an attempt is made to insert a record with a duplicate value in a key column, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not insert that record.</span></span> <span data-ttu-id="b9da5-158">但是它會插入後續的記錄，因此，大量載入作業不會失敗。</span><span class="sxs-lookup"><span data-stu-id="b9da5-158">But it does insert the subsequent record; thus, the Bulk Load operation does not fail.</span></span> <span data-ttu-id="b9da5-159">如果此屬性設定為 FALSE，嘗試在索引鍵資料行中插入重複的值時，大量載入會失敗。</span><span class="sxs-lookup"><span data-stu-id="b9da5-159">If this property is set to FALSE, Bulk Load fails when an attempt is made to insert a duplicate value in a key column.</span></span>  
  
 <span data-ttu-id="b9da5-160">當 IgnoreDuplicateKeys 屬性設定為 TRUE 時，就會針對資料表中插入的每一筆記錄發出 COMMIT 語句。</span><span class="sxs-lookup"><span data-stu-id="b9da5-160">When the IgnoreDuplicateKeys property is set to TRUE, a COMMIT statement is issued for every record inserted in the table.</span></span> <span data-ttu-id="b9da5-161">這會讓效能減慢。</span><span class="sxs-lookup"><span data-stu-id="b9da5-161">This slows down the performance.</span></span> <span data-ttu-id="b9da5-162">只有當 Transaction 屬性設定為 FALSE 時，才可以將屬性設定為 TRUE，因為交易行為是使用檔案來執行。</span><span class="sxs-lookup"><span data-stu-id="b9da5-162">The property can be set to TRUE only when the Transaction property is set to FALSE, because the transactional behavior is implemented using files.</span></span>  
  
 <span data-ttu-id="b9da5-163">預設值為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-163">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="b9da5-164">KeepIdentity</span><span class="sxs-lookup"><span data-stu-id="b9da5-164">KeepIdentity</span></span>  
 <span data-ttu-id="b9da5-165">指定如何處理來源檔案中識別類型資料行的值。</span><span class="sxs-lookup"><span data-stu-id="b9da5-165">Specifies how to deal with the values for an Identity type column in the source file.</span></span> <span data-ttu-id="b9da5-166">這是布林屬性。</span><span class="sxs-lookup"><span data-stu-id="b9da5-166">This is a Boolean property.</span></span> <span data-ttu-id="b9da5-167">當屬性設定為 TRUE 時，XML 大量載入會將來源檔案中指定的值指派給識別資料行。</span><span class="sxs-lookup"><span data-stu-id="b9da5-167">When the property is set to TRUE, XML Bulk Load assigns the values that are specified in the source file to the identity column.</span></span> <span data-ttu-id="b9da5-168">當屬性設定為 FALSE 時，大量載入作業會忽略來源檔案中指定的識別資料行值。</span><span class="sxs-lookup"><span data-stu-id="b9da5-168">When the property is set to FALSE, the bulk-load operation ignores the identity-column values that are specified in the source.</span></span> <span data-ttu-id="b9da5-169">在此情況下，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會指派值給識別資料行。</span><span class="sxs-lookup"><span data-stu-id="b9da5-169">In this case, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] assigns a value to the identity column.</span></span>  
  
 <span data-ttu-id="b9da5-170">如果大量載入包含的資料行是參考儲存 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 產生之值所在識別資料行的外部索引鍵，大量載入就會將這些識別值適當地擴展到外部索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="b9da5-170">If the Bulk Load involves a column that is a foreign key referring to an identity column in which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-generated values are stored, Bulk Load appropriately propagates these identity values to the foreign key column.</span></span>  
  
 <span data-ttu-id="b9da5-171">此屬性的值會套用到大量載入包含的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="b9da5-171">The value of this property applies to all columns involved in the bulk load.</span></span> <span data-ttu-id="b9da5-172">預設值為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-172">The default value is TRUE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9da5-173">若要將此屬性保留為 TRUE，您必須具有目標資料表的**ALTER TABLE**許可權。</span><span class="sxs-lookup"><span data-stu-id="b9da5-173">To leave this property as TRUE, you must have **ALTER TABLE** permissions on target tables.</span></span> <span data-ttu-id="b9da5-174">否則，它必須設定為值 FALSE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-174">Otherwise, it must be set to a value of FALSE.</span></span> <span data-ttu-id="b9da5-175">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b9da5-175">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="b9da5-176">KeepNulls</span><span class="sxs-lookup"><span data-stu-id="b9da5-176">KeepNulls</span></span>  
 <span data-ttu-id="b9da5-177">指定在 XML 文件中，用於缺少對應屬性或子元素之資料行的值。</span><span class="sxs-lookup"><span data-stu-id="b9da5-177">Specifies what value to use for a column that is missing a corresponding attribute or child element in the XML document.</span></span> <span data-ttu-id="b9da5-178">這是布林屬性。</span><span class="sxs-lookup"><span data-stu-id="b9da5-178">This is a Boolean property.</span></span> <span data-ttu-id="b9da5-179">當屬性設定為 TRUE 時，XML 大量載入會將 Null 值指派給資料行。</span><span class="sxs-lookup"><span data-stu-id="b9da5-179">When the property is set to TRUE, XML Bulk Load assigns a null value to the column.</span></span> <span data-ttu-id="b9da5-180">它不會將資料行的預設值指派為伺服器上的值 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="b9da5-180">It does not assign the column's default value, if any, as set on the server.</span></span> <span data-ttu-id="b9da5-181">此屬性的值會套用到大量載入包含的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="b9da5-181">The value of this property applies to all columns involved in the bulk load.</span></span>  
  
 <span data-ttu-id="b9da5-182">預設值為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-182">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="b9da5-183">SchemaGen</span><span class="sxs-lookup"><span data-stu-id="b9da5-183">SchemaGen</span></span>  
 <span data-ttu-id="b9da5-184">指定是否要在執行大量載入作業前，建立所需的資料表。</span><span class="sxs-lookup"><span data-stu-id="b9da5-184">Specifies whether to create the required tables before performing a Bulk Load operation.</span></span> <span data-ttu-id="b9da5-185">這是布林屬性。</span><span class="sxs-lookup"><span data-stu-id="b9da5-185">This is a Boolean property.</span></span> <span data-ttu-id="b9da5-186">如果此屬性設定為 TRUE，會建立對應結構描述中所識別的資料表 (資料庫必須存在)。</span><span class="sxs-lookup"><span data-stu-id="b9da5-186">If this property is set to TRUE, the tables identified in the mapping schema are created (the database must exist).</span></span> <span data-ttu-id="b9da5-187">如果一或多個資料表已經存在於資料庫中，SGDropTables 屬性會決定是否要卸載並重新建立這些預先存在的資料表。</span><span class="sxs-lookup"><span data-stu-id="b9da5-187">If one or more of the tables already exist in the database, the SGDropTables property determines whether these preexisting tables are to be dropped and re-created.</span></span>  
  
 <span data-ttu-id="b9da5-188">SchemaGen 屬性的預設值為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-188">The default value for the SchemaGen property is FALSE.</span></span> <span data-ttu-id="b9da5-189">SchemaGen 不會在新建立的資料表上建立 PRIMARY KEY 條件約束。</span><span class="sxs-lookup"><span data-stu-id="b9da5-189">SchemaGen does not create PRIMARY KEY constraints on the newly created tables.</span></span> <span data-ttu-id="b9da5-190">不過，如果可以在對應架構中找到相符 `sql:relationship` 的和 `sql:key-fields` 批註，而且索引鍵欄位是由單一資料行組成，則 SchemaGen 會在資料庫中建立 FOREIGN KEY 條件約束。</span><span class="sxs-lookup"><span data-stu-id="b9da5-190">SchemaGen does, however, create FOREIGN KEY constraints in the database if it can find matching `sql:relationship` and `sql:key-fields` annotations in the mapping schema and if the key field consists of a single column.</span></span>  
  
 <span data-ttu-id="b9da5-191">請注意，如果您將 SchemaGen 屬性設定為 TRUE，XML 大量載入會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b9da5-191">Note that if you set the SchemaGen property to TRUE, XML Bulk Load does the following:</span></span>  
  
-   <span data-ttu-id="b9da5-192">從元素和屬性名稱建立所需的資料表。</span><span class="sxs-lookup"><span data-stu-id="b9da5-192">Creates the necessary tables from the element and attribute names.</span></span> <span data-ttu-id="b9da5-193">因此，您最好不要將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 保留字用於結構描述中的元素和屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="b9da5-193">Therefore, it is important that you do not use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] reserved words for element and attribute names in the schema.</span></span>  
  
-   <span data-ttu-id="b9da5-194">針對使用[xml 資料類型](/sql/t-sql/xml/xml-transact-sql)格式的[sql：溢位欄位](annotation-interpretation-sql-overflow-field.md)所指定的任何資料行，傳回溢位資料。</span><span class="sxs-lookup"><span data-stu-id="b9da5-194">Returns overflow data for any column designated using the [sql:overflow-field](annotation-interpretation-sql-overflow-field.md) in [xml data type](/sql/t-sql/xml/xml-transact-sql) format.</span></span>  
  
 <span data-ttu-id="b9da5-195">SGDropTables</span><span class="sxs-lookup"><span data-stu-id="b9da5-195">SGDropTables</span></span>  
 <span data-ttu-id="b9da5-196">指定應該卸除或重新建立現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="b9da5-196">Specifies whether existing tables should be dropped and re-created.</span></span> <span data-ttu-id="b9da5-197">當 SchemaGen 屬性設定為 TRUE 時，您可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="b9da5-197">You use this property when the SchemaGen property is set to TRUE.</span></span> <span data-ttu-id="b9da5-198">如果 SGDropTables 為 FALSE，則會保留現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="b9da5-198">If SGDropTables is FALSE, the existing tables are retained.</span></span> <span data-ttu-id="b9da5-199">當此屬性為 TRUE 時，會刪除並重新建立現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="b9da5-199">When this property is TRUE, the existing tables are deleted and re-created.</span></span>  
  
 <span data-ttu-id="b9da5-200">預設值為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-200">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="b9da5-201">SGUseID</span><span class="sxs-lookup"><span data-stu-id="b9da5-201">SGUseID</span></span>  
 <span data-ttu-id="b9da5-202">指定在建立資料表時，對應結構描述中識別為 `id` 類型的屬性是否可用於建立 PRIMARY KEY 條件約束。</span><span class="sxs-lookup"><span data-stu-id="b9da5-202">Specifies whether the attribute in the mapping schema that is identified as `id` type can be used in creating a PRIMARY KEY constraint when the table is created.</span></span> <span data-ttu-id="b9da5-203">當 SchemaGen 屬性設定為 TRUE 時，請使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="b9da5-203">Use this property when the SchemaGen property is set to TRUE.</span></span> <span data-ttu-id="b9da5-204">如果 SGUseID 為 TRUE，SchemaGen 公用程式會使用 `dt:type="id"` 指定為主鍵資料行的屬性，並在建立資料表時加入適當的 PRIMARY key 條件約束。</span><span class="sxs-lookup"><span data-stu-id="b9da5-204">If SGUseID is TRUE, the SchemaGen utility uses an attribute for which `dt:type="id"` is specified as the primary key column and adds the appropriate PRIMARY KEY constraint when creating the table.</span></span>  
  
 <span data-ttu-id="b9da5-205">預設值為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-205">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="b9da5-206">TempFilePath</span><span class="sxs-lookup"><span data-stu-id="b9da5-206">TempFilePath</span></span>  
 <span data-ttu-id="b9da5-207">針對交易的大量載入，指定 XML 大量載入建立暫存檔案所在的檔案路徑 </span><span class="sxs-lookup"><span data-stu-id="b9da5-207">Specifies the file path where XML Bulk Load creates the temporary files for a transacted bulk load.</span></span> <span data-ttu-id="b9da5-208"> (只有當 Transaction 屬性設定為 TRUE 時，這個屬性才有用。 ) 您必須確定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用於 XML 大量載入的帳戶具有這個路徑的存取權。</span><span class="sxs-lookup"><span data-stu-id="b9da5-208">(This property is useful only when the Transaction property is set to TRUE.) You must ensure that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account that is used for XML Bulk Load has access to this path.</span></span> <span data-ttu-id="b9da5-209">如果未設定此屬性，XML 大量載入會將暫存檔案儲存在 TEMP 環境變數中所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="b9da5-209">If this property is not set, XML Bulk Load stores the temporary files in the location that is specified in the TEMP environment variable.</span></span>  
  
 <span data-ttu-id="b9da5-210">交易</span><span class="sxs-lookup"><span data-stu-id="b9da5-210">Transaction</span></span>  
 <span data-ttu-id="b9da5-211">指定大量載入是否應該當做交易完成，在此情況下，保證會在大量載入失敗時回復。</span><span class="sxs-lookup"><span data-stu-id="b9da5-211">Specifies whether the Bulk Load should be done as a transaction, in which case the rollback is guaranteed if the Bulk Load fails.</span></span> <span data-ttu-id="b9da5-212">這是布林屬性。</span><span class="sxs-lookup"><span data-stu-id="b9da5-212">This is a Boolean property.</span></span> <span data-ttu-id="b9da5-213">如果屬性設定為 TRUE，大量載入會在交易內容中發生。</span><span class="sxs-lookup"><span data-stu-id="b9da5-213">If the property is set to TRUE, the Bulk Load occurs in a transactional context.</span></span> <span data-ttu-id="b9da5-214">只有當 Transaction 設定為 TRUE 時，TempFilePath 屬性才有用。</span><span class="sxs-lookup"><span data-stu-id="b9da5-214">The TempFilePath property is useful only when Transaction is set to TRUE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9da5-215">如果您要將二進位資料 (例如，將 bin. 十六進位、bin base64 XML 資料類型載入至二進位、影像 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型) ，交易屬性必須設定為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-215">If you are loading binary data (such as the bin.hex, bin.base64 XML data types to the binary, image [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types), the Transaction property must be set to FALSE.</span></span>  
  
 <span data-ttu-id="b9da5-216">預設值為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-216">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="b9da5-217">XMLFragment</span><span class="sxs-lookup"><span data-stu-id="b9da5-217">XMLFragment</span></span>  
 <span data-ttu-id="b9da5-218">指定來源資料是否為 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="b9da5-218">Specifies whether the source data is an XML fragment.</span></span> <span data-ttu-id="b9da5-219">XML 片段是沒有單一、最上層 (根) 元素的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="b9da5-219">An XML fragment is an XML document with no single, top-level (root) element.</span></span> <span data-ttu-id="b9da5-220">這是布林屬性。</span><span class="sxs-lookup"><span data-stu-id="b9da5-220">This is a Boolean property.</span></span> <span data-ttu-id="b9da5-221">如果來源檔案由 XML 片段所組成，此屬性必須設定為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-221">This property must be set to TRUE if the source file consists of an XML fragment.</span></span>  
  
 <span data-ttu-id="b9da5-222">預設值為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="b9da5-222">The default value is FALSE.</span></span>  
  
  
