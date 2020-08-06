---
title: 擷取資料列 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- IRowset interface
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 5e6dbe36-b682-464d-adfa-8e886f9bd452
author: rothja
ms.author: jroth
ms.openlocfilehash: 435e1d705091814b2544c75772f20882caddf942
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592669"
---
# <a name="fetching-rows"></a><span data-ttu-id="ed8d3-102">提取資料列</span><span class="sxs-lookup"><span data-stu-id="ed8d3-102">Fetching Rows</span></span>
  <span data-ttu-id="ed8d3-103">**IRowset** 介面是基底資料列集介面。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-103">The **IRowset** interface is the base rowset interface.</span></span> <span data-ttu-id="ed8d3-104">**IRowset** 介面提供的方法會循序擷取資料列、從這些資料列中取得資料，以及管理資料列。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-104">The **IRowset** interface provides methods for fetching rows sequentially, getting the data from those rows, and managing rows.</span></span> <span data-ttu-id="ed8d3-105">取用者會使用 **IRowset** 中的方法，進行所有基本資料列集作業。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-105">Consumers use the methods in **IRowset** for all basic rowset operations.</span></span> <span data-ttu-id="ed8d3-106">這包括提取與釋放資料列，以及取得資料行值。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-106">This includes fetching and releasing rows and getting column values.</span></span>  
  
 <span data-ttu-id="ed8d3-107">當取用者取得資料列集的介面指標時，第一個步驟通常是使用 **IRowsetInfo::GetProperties** 方法，決定資料列集的功能。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-107">When a consumer obtains an interface pointer on a rowset, the first step is ordinarily to determine the capabilities of the rowset by using the **IRowsetInfo::GetProperties** method.</span></span> <span data-ttu-id="ed8d3-108">這會傳回由資料列集公開之介面的相關資訊，同時也會傳回不當做不同介面顯示之資料列集的功能，例如，使用中資料列的數目上限，以及可以同時擁有擱置中更新之資料列的數目。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-108">This returns information about the interfaces exposed by the rowset and also capabilities of the rowset that do not show up as distinct interfaces, such as the maximum number of active rows and the number of rows that can have pending updates at the same time.</span></span>  
  
 <span data-ttu-id="ed8d3-109">取用者的下一個步驟是決定資料列集中資料行的特性或中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-109">The next step for consumers is to determine the characteristics, or metadata, of the columns in the rowset.</span></span> <span data-ttu-id="ed8d3-110">因此，他們會針對簡單的資料行資訊使用 **IColumnsInfo** 方法，或針對擴充的資料行資訊使用 **IColumnsRowset** 方法。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-110">For this they use the **IColumnsInfo** method for simple column information or the **IColumnsRowset** method for extended column information.</span></span> <span data-ttu-id="ed8d3-111">**GetColumnInfo** 方法會傳回下列資訊：</span><span class="sxs-lookup"><span data-stu-id="ed8d3-111">The **GetColumnInfo** method returns the following information:</span></span>  
  
-   <span data-ttu-id="ed8d3-112">結果集中的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-112">The number of columns in the result set.</span></span>  
  
-   <span data-ttu-id="ed8d3-113">DBCOLUMNINFO 結構的陣列，每個資料行一個。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-113">An array of DBCOLUMNINFO structures, one per column.</span></span>  
  
     <span data-ttu-id="ed8d3-114">結構的順序就是資料行出現在資料列集中的順序。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-114">The order of the structures is the order in which the columns appear in the rowset.</span></span> <span data-ttu-id="ed8d3-115">每個 DBCOLUMNINFO 結構都包含資料行中繼資料，例如，資料行名稱、資料行的序數、資料行中值的可能最大長度、資料行的資料類型、有效位數以及長度。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-115">Each DBCOLUMNINFO structure includes column metadata, such as column name, ordinal of the column, maximum possible length of a value in the column, data type of the column, precision, and length.</span></span>  
  
-   <span data-ttu-id="ed8d3-116">單一配置區塊內，用於儲存所有字串值的指標。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-116">The pointer to a storage for all string values within a single allocation block.</span></span>  
  
 <span data-ttu-id="ed8d3-117">取用者會從中繼資料，或根據產生資料列集的文字命令，決定所需的資料行。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-117">The consumer determines which columns it needs either from the metadata or based on the text command that generated the rowset.</span></span> <span data-ttu-id="ed8d3-118">它會從 **IColumnsInfo** 所傳回之資料行資訊的順序，或從 **IColumnsRowset** 所傳回之資料行中繼資料資料列集中的序數，決定所需資料行的序數。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-118">It determines the ordinals of the needed columns from the ordering of the column information returned by **IColumnsInfo** or from the ordinals in the column metadata rowset returned by **IColumnsRowset**.</span></span>  
  
 <span data-ttu-id="ed8d3-119">**IColumnsInfo** 和 **IColumnsRowset** 介面用於擷取資料列集中資料行的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-119">The **IColumnsInfo** and **IColumnsRowset** interfaces are used to extract information about the columns in the rowset.</span></span> <span data-ttu-id="ed8d3-120">**IColumnsInfo** 介面會傳回一組有限的資訊，而 **IColumnsRowset** 則會提供所有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-120">The **IColumnsInfo** interface returns a limited set of information, whereas **IColumnsRowset** provides all the metadata.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ed8d3-121">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 和更早版本中，**IColumnsInfo::GetColumnsInfo** 所傳回的選擇性中繼資料行 DBCOLUMN_COMPUTEMODE 會傳回 DBSTATUS_S_ISNULL (而非描述資料行是否經過計算的值)，因為無法判斷基礎資料行是否經過計算。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-121">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 and earlier, the optional metadata column DBCOLUMN_COMPUTEMODE returned by **IColumnsInfo::GetColumnsInfo** returns DBSTATUS_S_ISNULL (instead of the values describing whether the column is computed) because it cannot be determined whether the underlying column is computed.</span></span>  
  
 <span data-ttu-id="ed8d3-122">序數用於指定資料行的繫結。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-122">The ordinals are used to specify a binding to a column.</span></span> <span data-ttu-id="ed8d3-123">繫結是一種結構，可讓取用者結構的元素與資料行產生關聯。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-123">A binding is a structure that associates an element of the consumer's structure with a column.</span></span> <span data-ttu-id="ed8d3-124">繫結可以繫結資料行的資料值、長度與狀態值。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-124">The binding can bind the data value, length, and status value of the column.</span></span>  
  
 <span data-ttu-id="ed8d3-125">在存取子中，會將一組繫結收集在一起。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-125">A set of bindings is gathered together in an accessor.</span></span> <span data-ttu-id="ed8d3-126">這是使用 **IAccessor::CreateAccessor** 方法建立的。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-126">This is created by using the **IAccessor::CreateAccessor** method.</span></span> <span data-ttu-id="ed8d3-127">一個存取子可能包含多個繫結，讓多個資料行的資料可以在單一呼叫中擷取或設定。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-127">An accessor can contain multiple bindings so that the data for multiple columns can be retrieved or set in a single call.</span></span> <span data-ttu-id="ed8d3-128">取用者可以建立數個存取子來比對應用程式不同部分中的不同使用模式。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-128">The consumer can create several accessors to match different usage patterns in different parts of the application.</span></span> <span data-ttu-id="ed8d3-129">它可以建立與釋放存取子，並讓資料列集仍保持存在。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-129">It can create and release accessors while the rowset remains in existence.</span></span>  
  
 <span data-ttu-id="ed8d3-130">若要從資料庫擷取資料列，取用者會呼叫一個方法，例如 **IRowset::GetNextRows** 或 **IRowsetLocate::GetRowsAt**。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-130">To fetch rows from the database, the consumer calls a method, such as **IRowset::GetNextRows** or **IRowsetLocate::GetRowsAt**.</span></span> <span data-ttu-id="ed8d3-131">這些提取作業會將伺服器中的原始資料放入提供者的資料列緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-131">These fetch operations put row data from the server into the row buffer of the provider.</span></span> <span data-ttu-id="ed8d3-132">取用者無法直接存取提供者的資料列緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-132">The consumer does not have direct access to the row buffer of the provider.</span></span> <span data-ttu-id="ed8d3-133">取用者會使用 **IRowset::GetData**，將提供者緩衝區的資料複製到取用者緩衝區，並使用 **IRowsetChange::SetData**，將取用者緩衝區的資料變更複製到提供者緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-133">The consumer uses **IRowset::GetData** to copy data from the buffer of the provider to the consumer buffer and **IRowsetChange::SetData** to copy data changes from the consumer buffer to the provider buffer.</span></span>  
  
 <span data-ttu-id="ed8d3-134">取用者會呼叫 **GetData** 方法，並將控制代碼傳遞到資料列、將控制代碼傳遞到存取子，以及將指標傳遞到取用者配置的緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-134">The consumer calls the **GetData** method and passes the handle to a row, the handle to an accessor, and a pointer to a consumer-allocated buffer.</span></span> <span data-ttu-id="ed8d3-135">**GetData** 會轉換資料，並依照建立存取子所使用之繫結的指定，傳回資料行。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-135">**GetData** converts the data and returns the columns as specified in the bindings used to create the accessor.</span></span> <span data-ttu-id="ed8d3-136">取用者可以使用不同的存取子和緩衝區，針對資料列呼叫多次 **GetData**，讓取用者可以取得相同資料的多個複本。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-136">The consumer can call **GetData** more than one time for a row, using different accessors and buffers and therefore the consumer can obtain multiple copies of the same data.</span></span>  
  
 <span data-ttu-id="ed8d3-137">可變長度資料行的資料可以用數種方式處理。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-137">Data from variable-length columns can be treated several ways.</span></span> <span data-ttu-id="ed8d3-138">首先，此類資料行可以繫結至有限的取用者結構區段。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-138">First, such columns can be bound to a finite section of the consumer's structure.</span></span> <span data-ttu-id="ed8d3-139">這在資料長度超過緩衝區長度時，會造成截斷。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-139">This causes truncation when the length of the data exceeds the length of the buffer.</span></span> <span data-ttu-id="ed8d3-140">取用者可以檢查 DBSTATUS_S_TRUNCATED 狀態來判斷截斷已發生。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-140">The consumer can determine that truncation has occurred by checking for the status DBSTATUS_S_TRUNCATED.</span></span> <span data-ttu-id="ed8d3-141">傳回的長度永遠是真實的位元組長度，讓取用者也可以決定要截斷多少資料。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-141">The returned length is always the true length in bytes, so that the consumer also can determine how much data was truncated.</span></span>  
  
 <span data-ttu-id="ed8d3-142">當取用者完成資料列的擷取或更新時，它會以 **ReleaseRows** 方法釋放這些資料列。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-142">When the consumer has finished fetching or updating rows, it releases them with the **ReleaseRows** method.</span></span> <span data-ttu-id="ed8d3-143">這樣會從資料列集的資料列複本中釋放資源，並為新的資料列騰出空間。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-143">This releases resources from the copy of the rows in the rowset and makes room for new rows.</span></span> <span data-ttu-id="ed8d3-144">接著，取用者可以重複其提取或建立資料列，並存取其中資料的循環。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-144">The consumer can then repeat its cycle of fetching or creating rows and accessing the data in them.</span></span>  
  
 <span data-ttu-id="ed8d3-145">當取用者完成資料列集時，它會呼叫 **IAccessor::ReleaseAccessor** 方法來釋放所有存取子。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-145">When the consumer is finished with the rowset, it calls the **IAccessor::ReleaseAccessor** method to release any accessor.</span></span> <span data-ttu-id="ed8d3-146">它會針對資料列集所公開的所有介面呼叫 **IUnknown::Release** 方法，藉以釋放資料列集。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-146">It calls the **IUnknown::Release** method on all interfaces exposed by the rowset to release the rowset.</span></span> <span data-ttu-id="ed8d3-147">進行資料列集釋放時，它會強制釋放取用者可能保存的所有剩餘資料列或存取子。</span><span class="sxs-lookup"><span data-stu-id="ed8d3-147">When the rowset is released, it forces the release of any remaining rows or accessors the consumer may hold.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ed8d3-148">本節內容</span><span class="sxs-lookup"><span data-stu-id="ed8d3-148">In This Section</span></span>  
  
-   [<span data-ttu-id="ed8d3-149">下一個擷取位置</span><span class="sxs-lookup"><span data-stu-id="ed8d3-149">Next Fetch Position</span></span>](fetching-rows-next-fetch-position.md)  
  
## <a name="see-also"></a><span data-ttu-id="ed8d3-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed8d3-150">See Also</span></span>  
 [<span data-ttu-id="ed8d3-151">資料列集</span><span class="sxs-lookup"><span data-stu-id="ed8d3-151">Rowsets</span></span>](rowsets.md)  
  
  
