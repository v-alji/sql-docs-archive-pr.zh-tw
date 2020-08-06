---
title: 建立 SQL Server 索引 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
- adding indexes
ms.assetid: 6239d440-2818-4b98-bb79-732dced41952
author: rothja
ms.author: jroth
ms.openlocfilehash: 3693355eec7a290c03658c10db500161aa52062d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707433"
---
# <a name="creating-sql-server-indexes"></a><span data-ttu-id="ee8c4-102">建立 SQL Server 索引</span><span class="sxs-lookup"><span data-stu-id="ee8c4-102">Creating SQL Server Indexes</span></span>
  <span data-ttu-id="ee8c4-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會公開**IIndexDefinition：： CreateIndex**函數，讓取用者定義資料表的新索引 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **IIndexDefinition::CreateIndex** function, allowing consumers to define new indexes on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span>  
  
 <span data-ttu-id="ee8c4-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會建立資料表索引做為索引或條件約束。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider creates table indexes as either indexes or constraints.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ee8c4-105">會將建立條件約束的權限提供給資料表擁有者、資料庫擁有者，以及特定管理角色的成員。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-105">gives constraint-creation privilege to the table owner, database owner, and members of certain administrative roles.</span></span> <span data-ttu-id="ee8c4-106">根據預設，只有資料表擁有者可以建立資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-106">By default, only the table owner can create an index on a table.</span></span> <span data-ttu-id="ee8c4-107">因此，**CreateIndex** 的成功或失敗，不但取決於應用程式使用者的存取權限，也取決於所建立之索引的類型。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-107">Therefore, the success or failure of **CreateIndex** depends not only on the application user's access rights but also on the type of index created.</span></span>  
  
 <span data-ttu-id="ee8c4-108">取用者會在 *pTableID* 參數中，將資料表名稱指定為 *uName* 聯集之 *pwszName* 成員中的 Unicode 字元字串。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-108">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="ee8c4-109">*pTableID* 的 *eKind* 成員必須是 DBKIND_NAME。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-109">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="ee8c4-110">*PIndexID*參數可以是 Null，如果是， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會為索引建立唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-110">The *pIndexID* parameter can be NULL, and if it is, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider creates a unique name for the index.</span></span> <span data-ttu-id="ee8c4-111">取用者可以在 *ppIndexID* 參數中指定 DBID 的有效指標，藉以擷取索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-111">The consumer can capture the name of the index by specifying a valid pointer to a DBID in the *ppIndexID* parameter.</span></span>  
  
 <span data-ttu-id="ee8c4-112">取用者可以將索引名稱指定為 *pIndexID* 參數 *uName* 聯集之 *pwszName* 成員中的 Unicode 字元字串。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-112">The consumer can specify the index name as a Unicode character string in the *pwszName* member of the *uName* union of the *pIndexID* parameter.</span></span> <span data-ttu-id="ee8c4-113">*pIndexID* 的 *eKind* 成員必須是 DBKIND_NAME。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-113">The *eKind* member of *pIndexID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="ee8c4-114">取用者會指定依名稱參與索引的一或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-114">The consumer specifies the column or columns participating in the index by name.</span></span> <span data-ttu-id="ee8c4-115">對於在 **CreateIndex** 中使用的每個 DBINDEXCOLUMNDESC 結構，*pColumnID* 的 *eKind* 成員必須是 DBKIND_NAME。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-115">For each DBINDEXCOLUMNDESC structure used in **CreateIndex**, the *eKind* member of the *pColumnID* must be DBKIND_NAME.</span></span> <span data-ttu-id="ee8c4-116">在 *pColumnID* 中，資料行的名稱會指定為 *uName* 聯集之 *pwszName* 成員內的 Unicode 字元字串。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-116">The name of the column is specified as a Unicode character string in the *pwszName* member of the *uName* union in the *pColumnID*.</span></span>  
  
 <span data-ttu-id="ee8c4-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者，並 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援索引中值的遞增順序。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support ascending order on values in the index.</span></span> <span data-ttu-id="ee8c4-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如果取用者在任何 DBINDEXCOLUMNDESC 結構中指定 DBINDEX_COL_ORDER_DESC，Native Client OLE DB 提供者就會傳回 E_INVALIDARG。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns E_INVALIDARG if the consumer specifies DBINDEX_COL_ORDER_DESC in any DBINDEXCOLUMNDESC structure.</span></span>  
  
 <span data-ttu-id="ee8c4-119">**CreateIndex** 會解譯索引屬性，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-119">**CreateIndex** interprets index properties as follows.</span></span>  
  
|<span data-ttu-id="ee8c4-120">屬性識別碼</span><span class="sxs-lookup"><span data-stu-id="ee8c4-120">Property ID</span></span>|<span data-ttu-id="ee8c4-121">描述</span><span class="sxs-lookup"><span data-stu-id="ee8c4-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ee8c4-122">DBPROP_INDEX_AUTOUPDATE</span><span class="sxs-lookup"><span data-stu-id="ee8c4-122">DBPROP_INDEX_AUTOUPDATE</span></span>|<span data-ttu-id="ee8c4-123">R/W︰讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="ee8c4-123">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="ee8c4-124">預設值：無</span><span class="sxs-lookup"><span data-stu-id="ee8c4-124">Default: None</span></span><br /><br /> <span data-ttu-id="ee8c4-125">描述： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者不支援這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-125">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="ee8c4-126">嘗試在 **CreateIndex** 中設定屬性會使 DB_S_ERRORSOCCURRED 傳回值。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-126">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="ee8c4-127">屬性結構的 *dwStatus* 成員表示 DBPROPSTATUS_BADVALUE。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-127">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="ee8c4-128">DBPROP_INDEX_CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="ee8c4-128">DBPROP_INDEX_CLUSTERED</span></span>|<span data-ttu-id="ee8c4-129">R/W︰讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="ee8c4-129">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="ee8c4-130">預設值：VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="ee8c4-130">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="ee8c4-131">描述：控制索引叢集。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-131">Description: Controls index clustering.</span></span><br /><br /> <span data-ttu-id="ee8c4-132">VARIANT_TRUE： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會嘗試在資料表上建立叢集索引 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-132">VARIANT_TRUE: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider attempts to create a clustered index on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ee8c4-133">在任何資料表上，最多支援一個叢集索引。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-133">supports at most one clustered index on any table.</span></span><br /><br /> <span data-ttu-id="ee8c4-134">VARIANT_FALSE： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會嘗試在資料表上建立非叢集索引 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-134">VARIANT_FALSE: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider attempts to create a nonclustered index on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>|  
|<span data-ttu-id="ee8c4-135">DBPROP_INDEX_FILLFACTOR</span><span class="sxs-lookup"><span data-stu-id="ee8c4-135">DBPROP_INDEX_FILLFACTOR</span></span>|<span data-ttu-id="ee8c4-136">R/W︰讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="ee8c4-136">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="ee8c4-137">預設值：0</span><span class="sxs-lookup"><span data-stu-id="ee8c4-137">Default: 0</span></span><br /><br /> <span data-ttu-id="ee8c4-138">描述：指定儲存所使用之索引頁的百分比。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-138">Description: Specifies the percentage of an index page used for storage.</span></span> <span data-ttu-id="ee8c4-139">如需詳細資訊，請參閱 [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-139">For more information, see [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql).</span></span><br /><br /> <span data-ttu-id="ee8c4-140">變數的類型為 VT_I4。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-140">The type of the variant is VT_I4.</span></span> <span data-ttu-id="ee8c4-141">其值必須大於或等於 1 且小於或等於 100。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-141">The value must be greater than or equal to 1 and less than or equal to 100.</span></span>|  
|<span data-ttu-id="ee8c4-142">DBPROP_INDEX_INITIALIZE</span><span class="sxs-lookup"><span data-stu-id="ee8c4-142">DBPROP_INDEX_INITIALIZE</span></span>|<span data-ttu-id="ee8c4-143">R/W︰讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="ee8c4-143">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="ee8c4-144">預設值：無</span><span class="sxs-lookup"><span data-stu-id="ee8c4-144">Default: None</span></span><br /><br /> <span data-ttu-id="ee8c4-145">描述： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者不支援這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-145">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="ee8c4-146">嘗試在 **CreateIndex** 中設定屬性會使 DB_S_ERRORSOCCURRED 傳回值。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-146">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="ee8c4-147">屬性結構的 *dwStatus* 成員表示 DBPROPSTATUS_BADVALUE。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-147">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="ee8c4-148">DBPROP_INDEX_NULLCOLLATION</span><span class="sxs-lookup"><span data-stu-id="ee8c4-148">DBPROP_INDEX_NULLCOLLATION</span></span>|<span data-ttu-id="ee8c4-149">R/W︰讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="ee8c4-149">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="ee8c4-150">預設值：無</span><span class="sxs-lookup"><span data-stu-id="ee8c4-150">Default: None</span></span><br /><br /> <span data-ttu-id="ee8c4-151">描述： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者不支援這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-151">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="ee8c4-152">嘗試在 **CreateIndex** 中設定屬性會使 DB_S_ERRORSOCCURRED 傳回值。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-152">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="ee8c4-153">屬性結構的 *dwStatus* 成員表示 DBPROPSTATUS_BADVALUE。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-153">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="ee8c4-154">DBPROP_INDEX_NULLS</span><span class="sxs-lookup"><span data-stu-id="ee8c4-154">DBPROP_INDEX_NULLS</span></span>|<span data-ttu-id="ee8c4-155">R/W︰讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="ee8c4-155">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="ee8c4-156">預設值：無</span><span class="sxs-lookup"><span data-stu-id="ee8c4-156">Default: None</span></span><br /><br /> <span data-ttu-id="ee8c4-157">描述： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者不支援這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-157">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="ee8c4-158">嘗試在 **CreateIndex** 中設定屬性會使 DB_S_ERRORSOCCURRED 傳回值。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-158">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="ee8c4-159">屬性結構的 *dwStatus* 成員表示 DBPROPSTATUS_BADVALUE。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-159">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="ee8c4-160">DBPROP_INDEX_PRIMARYKEY</span><span class="sxs-lookup"><span data-stu-id="ee8c4-160">DBPROP_INDEX_PRIMARYKEY</span></span>|<span data-ttu-id="ee8c4-161">R/W︰讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="ee8c4-161">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="ee8c4-162">預設值：VARIANT_FALSE 描述：建立索引做為參考完整性，也就是 PRIMARY KEY 條件約束。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-162">Default: VARIANT_FALSE Description: Creates the index as a referential integrity, PRIMARY KEY constraint.</span></span><br /><br /> <span data-ttu-id="ee8c4-163">VARIANT_TRUE：索引建立之後，即可支援資料表的 PRIMARY KEY 條件約束。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-163">VARIANT_TRUE: The index is created to support the PRIMARY KEY constraint of the table.</span></span> <span data-ttu-id="ee8c4-164">資料行必須是不允許為 Null。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-164">The columns must be nonnullable.</span></span><br /><br /> <span data-ttu-id="ee8c4-165">VARIANT_FALSE：索引不會當做資料表中之資料列值的 PRIMARY KEY 條件約束使用。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-165">VARIANT_FALSE: The index is not used as a PRIMARY KEY constraint for row values in the table.</span></span>|  
|<span data-ttu-id="ee8c4-166">DBPROP_INDEX_SORTBOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="ee8c4-166">DBPROP_INDEX_SORTBOOKMARKS</span></span>|<span data-ttu-id="ee8c4-167">R/W︰讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="ee8c4-167">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="ee8c4-168">預設值：無</span><span class="sxs-lookup"><span data-stu-id="ee8c4-168">Default: None</span></span><br /><br /> <span data-ttu-id="ee8c4-169">描述： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者不支援這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-169">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="ee8c4-170">嘗試在 **CreateIndex** 中設定屬性會使 DB_S_ERRORSOCCURRED 傳回值。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-170">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="ee8c4-171">屬性結構的 *dwStatus* 成員表示 DBPROPSTATUS_BADVALUE。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-171">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="ee8c4-172">DBPROP_INDEX_TEMPINDEX</span><span class="sxs-lookup"><span data-stu-id="ee8c4-172">DBPROP_INDEX_TEMPINDEX</span></span>|<span data-ttu-id="ee8c4-173">R/W︰讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="ee8c4-173">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="ee8c4-174">預設值：無</span><span class="sxs-lookup"><span data-stu-id="ee8c4-174">Default: None</span></span><br /><br /> <span data-ttu-id="ee8c4-175">描述： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者不支援這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-175">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="ee8c4-176">嘗試在 **CreateIndex** 中設定屬性會使 DB_S_ERRORSOCCURRED 傳回值。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-176">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="ee8c4-177">屬性結構的 *dwStatus* 成員表示 DBPROPSTATUS_BADVALUE。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-177">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="ee8c4-178">DBPROP_INDEX_TYPE</span><span class="sxs-lookup"><span data-stu-id="ee8c4-178">DBPROP_INDEX_TYPE</span></span>|<span data-ttu-id="ee8c4-179">R/W︰讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="ee8c4-179">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="ee8c4-180">預設值：無</span><span class="sxs-lookup"><span data-stu-id="ee8c4-180">Default: None</span></span><br /><br /> <span data-ttu-id="ee8c4-181">描述： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者不支援這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-181">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="ee8c4-182">嘗試在 **CreateIndex** 中設定屬性會使 DB_S_ERRORSOCCURRED 傳回值。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-182">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="ee8c4-183">屬性結構的 *dwStatus* 成員表示 DBPROPSTATUS_BADVALUE。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-183">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="ee8c4-184">DBPROP_INDEX_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="ee8c4-184">DBPROP_INDEX_UNIQUE</span></span>|<span data-ttu-id="ee8c4-185">R/W︰讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="ee8c4-185">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="ee8c4-186">預設值：VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="ee8c4-186">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="ee8c4-187">描述：建立索引做為參與之一或多個資料行的 UNIQUE 條件約束。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-187">Description: Creates the index as a UNIQUE constraint on the participating column or columns.</span></span><br /><br /> <span data-ttu-id="ee8c4-188">VARIANT_TRUE：此索引用於唯一限制資料表中的資料列值。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-188">VARIANT_TRUE: The index is used to uniquely constrain row values in the table.</span></span><br /><br /> <span data-ttu-id="ee8c4-189">VARIANT_FALSE：此索引不會唯一限制資料列值。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-189">VARIANT_FALSE: The index does not uniquely constrain row values.</span></span>|  
  
 <span data-ttu-id="ee8c4-190">在提供者特定的屬性集 DBPROPSET_SQLSERVERINDEX 中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會定義下列資料來源資訊屬性。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-190">In the provider-specific property set DBPROPSET_SQLSERVERINDEX, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following data source information property.</span></span>  
  
|<span data-ttu-id="ee8c4-191">屬性識別碼</span><span class="sxs-lookup"><span data-stu-id="ee8c4-191">Property ID</span></span>|<span data-ttu-id="ee8c4-192">描述</span><span class="sxs-lookup"><span data-stu-id="ee8c4-192">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ee8c4-193">SSPROP_INDEX_XML</span><span class="sxs-lookup"><span data-stu-id="ee8c4-193">SSPROP_INDEX_XML</span></span>|<span data-ttu-id="ee8c4-194">類型：VT_BOOL (R/W)</span><span class="sxs-lookup"><span data-stu-id="ee8c4-194">Type: VT_BOOL (R/W)</span></span><br /><br /> <span data-ttu-id="ee8c4-195">預設值：VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="ee8c4-195">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="ee8c4-196">描述：利用包含 IIndexDefinition::CreateIndex 的 VARIANT_TRUE 值指定此屬性時，會建立對應到要建立索引之資料行的主要 xml 索引。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-196">Description: When this property is specified with a value of VARIANT_TRUE with IIndexDefinition::CreateIndex, it results in a primary xml index being created corresponding to the column being indexed.</span></span> <span data-ttu-id="ee8c4-197">如果此屬性為 VARIANT_TRUE，cIndexColumnDescs 應該為 1，否則就是錯誤。</span><span class="sxs-lookup"><span data-stu-id="ee8c4-197">If this property is VARIANT_TRUE, cIndexColumnDescs should be 1, otherwise it is an error.</span></span>|  
  
 <span data-ttu-id="ee8c4-198">此範例會建立一個主索引鍵索引：</span><span class="sxs-lookup"><span data-stu-id="ee8c4-198">This example creates a primary key index:</span></span>  
  
```  
// This CREATE TABLE statement shows the referential integrity and   
// PRIMARY KEY constraint on the OrderDetails table that will be created   
// by the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//        CONSTRAINT PK_OrderDetails  
//        PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
HRESULT CreatePrimaryKey  
    (  
    IIndexDefinition* pIIndexDefinition  
    )  
    {  
    HRESULT             hr = S_OK;  
  
    DBID                dbidTable;  
    DBID                dbidIndex;  
    const ULONG         nCols = 2;  
    ULONG               nCol;  
    const ULONG         nProps = 2;  
    ULONG               nProp;  
  
    DBINDEXCOLUMNDESC   dbidxcoldesc[nCols];  
    DBPROP              dbpropIndex[nProps];  
    DBPROPSET           dbpropset;  
  
    DBID*               pdbidIndexOut = NULL;  
  
    // Set up identifiers for the table and index.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    dbidIndex.eKind = DBKIND_NAME;  
    dbidIndex.uName.pwszName = L"PK_OrderDetails";  
  
    // Set up column identifiers.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbidxcoldesc[nCol].pColumnID = new DBID;  
        dbidxcoldesc[nCol].pColumnID->eKind = DBKIND_NAME;  
  
        dbidxcoldesc[nCol].eIndexColOrder = DBINDEX_COL_ORDER_ASC;  
        }  
    dbidxcoldesc[0].pColumnID->uName.pwszName = L"OrderID";  
    dbidxcoldesc[1].pColumnID->uName.pwszName = L"ProductID";  
  
    // Set properties for the index. The index is clustered,  
    // PRIMARY KEY.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        dbpropIndex[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        dbpropIndex[nProp].colid = DB_NULLID;  
  
        VariantInit(&(dbpropIndex[nProp].vValue));  
  
        dbpropIndex[nProp].vValue.vt = VT_BOOL;  
        }  
    dbpropIndex[0].dwPropertyID = DBPROP_INDEX_CLUSTERED;  
    dbpropIndex[0].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropIndex[1].dwPropertyID = DBPROP_INDEX_PRIMARYKEY;  
    dbpropIndex[1].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropset.rgProperties = dbpropIndex;  
    dbpropset.cProperties = nProps;  
    dbpropset.guidPropertySet = DBPROPSET_INDEX;  
  
    hr = pIIndexDefinition->CreateIndex(&dbidTable, &dbidIndex, nCols,  
        dbidxcoldesc, 1, &dbpropset, &pdbidIndexOut);  
  
    // Clean up dynamically allocated DBIDs.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        delete dbidxcoldesc[nCol].pColumnID;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee8c4-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee8c4-199">See Also</span></span>  
 [<span data-ttu-id="ee8c4-200">資料表和索引</span><span class="sxs-lookup"><span data-stu-id="ee8c4-200">Tables and Indexes</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
