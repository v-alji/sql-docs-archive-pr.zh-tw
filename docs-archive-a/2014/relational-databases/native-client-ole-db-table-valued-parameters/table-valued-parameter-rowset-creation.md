---
title: 建立資料表值參數資料列集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, rowset creation
ms.assetid: ffe213ca-cc0e-465e-b31c-a8272324c4fe
author: rothja
ms.author: jroth
ms.openlocfilehash: a22ccbd583d95c41daa0a113363985828cf1e9d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594024"
---
# <a name="table-valued-parameter-rowset-creation"></a><span data-ttu-id="2648a-102">建立資料表值參數資料列集</span><span class="sxs-lookup"><span data-stu-id="2648a-102">Table-Valued Parameter Rowset Creation</span></span>
  <span data-ttu-id="2648a-103">雖然取用者可以提供資料表值參數的任何資料列集物件，但是一般的資料列集物件都會針對後端資料存放區來實作，因此所提供的效能會受到限制。</span><span class="sxs-lookup"><span data-stu-id="2648a-103">Although consumers can provide any rowset object for table-valued parameters, typical rowset objects are implemented against back-end data stores, and therefore provide limited performance.</span></span> <span data-ttu-id="2648a-104">基於這個原因，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會讓取用者在記憶體中的資料之上建立特殊的資料列集物件。</span><span class="sxs-lookup"><span data-stu-id="2648a-104">For this reason, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider enables consumers to create a specialized rowset object on top of in-memory data.</span></span> <span data-ttu-id="2648a-105">這個特殊的記憶體內部資料列集物件是新的 COM 物件，稱為資料表值參數資料列集。</span><span class="sxs-lookup"><span data-stu-id="2648a-105">This special, in-memory rowset object is a new COM object called a table-valued parameter rowset .</span></span> <span data-ttu-id="2648a-106">它會提供類似參數集的功能。</span><span class="sxs-lookup"><span data-stu-id="2648a-106">It provides functionality similar to parameter sets.</span></span>  
  
 <span data-ttu-id="2648a-107">資料表值參數資料列集物件是由取用者針對輸入參數所明確建立，而且是透過多個工作階段層級介面。</span><span class="sxs-lookup"><span data-stu-id="2648a-107">Table-valued parameter rowset objects are created explicitly by the consumer for input parameters through multiple session-level interfaces.</span></span> <span data-ttu-id="2648a-108">每個資料表值參數都有資料表值參數資料列集物件的一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="2648a-108">There is one instance of a table-valued parameter rowset object per table-valued parameter.</span></span> <span data-ttu-id="2648a-109">取用者可以建立資料表值參數資料列集物件，其方式是提供已知的中繼資料資訊 (靜態案例) 或是透過提供者介面來探索 (動態案例)。</span><span class="sxs-lookup"><span data-stu-id="2648a-109">The consumer can create the table-valued parameter rowset objects either by providing metadata information that is already known (static scenario), or by discovering it through provider interfaces (dynamic scenario).</span></span> <span data-ttu-id="2648a-110">下列章節描述這兩個案例。</span><span class="sxs-lookup"><span data-stu-id="2648a-110">The following sections describe these two scenarios.</span></span>  
  
## <a name="static-scenario"></a><span data-ttu-id="2648a-111">靜態案例</span><span class="sxs-lookup"><span data-stu-id="2648a-111">Static Scenario</span></span>  
 <span data-ttu-id="2648a-112">當類型資訊已知時，取用者會使用 ITableDefinitionWithConstraints::CreateTableWithConstraints 來具現化對應至資料表值參數的資料表值參數資料列集物件。</span><span class="sxs-lookup"><span data-stu-id="2648a-112">When the type information is known, the consumer uses ITableDefinitionWithConstraints::CreateTableWithConstraints to instantiate a table-valued parameter rowset object that corresponds to a table-valued parameter.</span></span>  
  
 <span data-ttu-id="2648a-113">*guid* 欄位 (*pTableID* 參數) 包含特殊 GUID (CLSID_ROWSET_TVP)。</span><span class="sxs-lookup"><span data-stu-id="2648a-113">The *guid* field (*pTableID* parameter) contains the special GUID (CLSID_ROWSET_TVP).</span></span> <span data-ttu-id="2648a-114">*pwszName* 成員包含取用者想要具現化之資料表值參數類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="2648a-114">The *pwszName* member contains the name of the table-valued parameter type that the consumer wants to instantiate.</span></span> <span data-ttu-id="2648a-115">*eKind* 欄位將會設定為 DBKIND_GUID_NAME。</span><span class="sxs-lookup"><span data-stu-id="2648a-115">The *eKind* field will be set to DBKIND_GUID_NAME.</span></span> <span data-ttu-id="2648a-116">當此陳述式為特定的 SQL 時，就需要這個名稱；如果它是程序呼叫，則此名稱為選擇性。</span><span class="sxs-lookup"><span data-stu-id="2648a-116">This name is required when the statement is ad hoc SQL; the name is optional if it is a procedure call.</span></span>  
  
 <span data-ttu-id="2648a-117">為了彙總，取用者會傳遞具有控制之 IUnknown 的 *pUnkOuter* 參數。</span><span class="sxs-lookup"><span data-stu-id="2648a-117">For aggregation, the consumer passes the *pUnkOuter* parameter with the controlling IUnknown.</span></span>  
  
 <span data-ttu-id="2648a-118">資料表值參數資料列集物件屬性是唯讀的，因此取用者不應該在*rgPropertySets*中設定任何屬性。</span><span class="sxs-lookup"><span data-stu-id="2648a-118">The table-valued parameter rowset object properties are read only, so the consumer is not expected to set any properties in *rgPropertySets*.</span></span>  
  
 <span data-ttu-id="2648a-119">對於每一個 DBCOLUMNDESC 結構的 *rgPropertySets* 數目而言，取用者可以為每一個資料行指定其他屬性。</span><span class="sxs-lookup"><span data-stu-id="2648a-119">For the *rgPropertySets* member of each DBCOLUMNDESC structure, the consumer can specify additional properties for each column.</span></span> <span data-ttu-id="2648a-120">這些屬性屬於 DBPROPSET_SQLSERVERCOLUMN 屬性集，</span><span class="sxs-lookup"><span data-stu-id="2648a-120">These properties belong to the DBPROPSET_SQLSERVERCOLUMN property set.</span></span> <span data-ttu-id="2648a-121">它們可讓您針對每一個資料行指定計算和預設的設定，</span><span class="sxs-lookup"><span data-stu-id="2648a-121">They enable you to specify computed and default settings for each column.</span></span> <span data-ttu-id="2648a-122">它們也支援現有的資料行屬性，例如 Null 屬性和識別。</span><span class="sxs-lookup"><span data-stu-id="2648a-122">They also support existing column properties, such as nullability and identity.</span></span>  
  
 <span data-ttu-id="2648a-123">若要從資料表值參數資料列集物件擷取對應的資訊，取用者會使用 IRowsetInfo::GetProperties。</span><span class="sxs-lookup"><span data-stu-id="2648a-123">To retrieve corresponding information from a table-valued parameter rowset object, the consumer uses IRowsetInfo::GetProperties.</span></span>  
  
 <span data-ttu-id="2648a-124">若要取得每個資料行之 null、唯一、計算和更新狀態的相關資訊，取用者會使用 IColumnsRowset：： GetColumnsRowset 或 IColumnsInfo：： GetColumnInfo。</span><span class="sxs-lookup"><span data-stu-id="2648a-124">To retrieve information about the null, unique, computed, and update status of each column, the consumer use IColumnsRowset::GetColumnsRowset or IColumnsInfo::GetColumnInfo.</span></span> <span data-ttu-id="2648a-125">這些方法會提供有關每一個資料表值參數資料列集資料行的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2648a-125">These methods provide detailed information about each table-valued parameter rowset column.</span></span>  
  
 <span data-ttu-id="2648a-126">取用者會指定資料表值參數之每一個資料行的類型。</span><span class="sxs-lookup"><span data-stu-id="2648a-126">The consumer specifies the type of each column of the table-valued parameter.</span></span> <span data-ttu-id="2648a-127">這類似於在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中建立資料表時指定資料行的方式。</span><span class="sxs-lookup"><span data-stu-id="2648a-127">This is similar to how columns are specified when a table is created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2648a-128">取用者會 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 透過*ppRowset*輸出參數，從 Native Client OLE DB 提供者取得資料表值參數資料列集物件。</span><span class="sxs-lookup"><span data-stu-id="2648a-128">The consumer obtains a table-valued parameter rowset object from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider through the *ppRowset* output parameter.</span></span>  
  
## <a name="dynamic-scenario"></a><span data-ttu-id="2648a-129">動態案例</span><span class="sxs-lookup"><span data-stu-id="2648a-129">Dynamic Scenario</span></span>  
 <span data-ttu-id="2648a-130">當取用者沒有類型資訊時，它應該使用 IOpenRowset：： OpenRowset 來具現化資料表值參數資料列集物件。</span><span class="sxs-lookup"><span data-stu-id="2648a-130">When the consumer does not have type information, it should use IOpenRowset::OpenRowset to instantiate table-valued parameter rowset objects.</span></span> <span data-ttu-id="2648a-131">取用者只需要提供類型名稱給提供者。</span><span class="sxs-lookup"><span data-stu-id="2648a-131">All the consumer has to provide to the provider is the type name.</span></span>  
  
 <span data-ttu-id="2648a-132">在此案例中，提供者會代表取用者包含來自伺服器之資料表值參數資料列集物件的相關類型資訊。</span><span class="sxs-lookup"><span data-stu-id="2648a-132">In this scenario, the provider obtains type information about a table-valued parameter rowset object from the server on behalf of the consumer.</span></span>  
  
 <span data-ttu-id="2648a-133">*pTableID* 和 *pUnkOuter* 參數的設定應該與靜態案例相同。</span><span class="sxs-lookup"><span data-stu-id="2648a-133">The *pTableID* and *pUnkOuter* parameters should be set as in the static scenario.</span></span> <span data-ttu-id="2648a-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接著，Native Client OLE DB 提供者會從伺服器取得資料行資訊和條件) 約束 (的類型資訊，並透過*ppRowset*參數傳回資料表值參數資料列集物件。</span><span class="sxs-lookup"><span data-stu-id="2648a-134">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider then obtains the type information (column information and constraints) from the server, and return a table-valued parameter rowset object through the *ppRowset* parameter.</span></span> <span data-ttu-id="2648a-135">這項作業需要與伺服器通訊，因此其效能不比靜態案例。</span><span class="sxs-lookup"><span data-stu-id="2648a-135">This operation requires communication with the server, and therefore does not perform as well as the static scenario.</span></span> <span data-ttu-id="2648a-136">動態案例只適用於參數化程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="2648a-136">The dynamic scenario works only with parameterized procedure calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2648a-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2648a-137">See Also</span></span>  
 <span data-ttu-id="2648a-138">[資料表值參數 &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="2648a-138">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="2648a-139">使用資料表值參數 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="2648a-139">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
