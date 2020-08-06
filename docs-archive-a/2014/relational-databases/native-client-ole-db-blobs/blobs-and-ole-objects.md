---
title: BLOB 與 OLE 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 767fa2f6-9cd2-436f-add5-e760bed29a58
author: rothja
ms.author: jroth
ms.openlocfilehash: 15f8b4915ba9b05a5be19854a2e27a2e8ff3a346
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709285"
---
# <a name="blobs-and-ole-objects"></a><span data-ttu-id="1018a-102">BLOB 與 OLE 物件</span><span class="sxs-lookup"><span data-stu-id="1018a-102">BLOBs and OLE Objects</span></span>
  <span data-ttu-id="1018a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會公開**ISequentialStream**介面，以支援取用者存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Ntext**、 **text**、 **image**、 \*\*Varchar (max) \*\*、 \*\*Nvarchar (max) \*\*、 \*\*Varbinary (max) \*\*和 xml 資料類型，做為二進位大型物件 (blob) 。</span><span class="sxs-lookup"><span data-stu-id="1018a-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ISequentialStream** interface to support consumer access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**, **text**, **image**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, and xml data types as binary large objects (BLOBs).</span></span> <span data-ttu-id="1018a-104">**ISequentialStream** 上的 **Read** 方法可讓取用者在可管理的區塊中擷取更多資料。</span><span class="sxs-lookup"><span data-stu-id="1018a-104">The **Read** method on **ISequentialStream** lets the consumer retrieve much data in manageable chunks.</span></span>  
  
 <span data-ttu-id="1018a-105">如需示範此功能的範例，請參閱[設定大型資料 &#40;OLE DB&#41;](../native-client-ole-db-how-to/set-large-data-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="1018a-105">For a sample demonstrating this feature, see [Set Large Data &#40;OLE DB&#41;](../native-client-ole-db-how-to/set-large-data-ole-db.md).</span></span>  
  
 <span data-ttu-id="1018a-106">當取用者在針對資料修改所系結的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存取子中提供介面指標時，Native Client OLE DB 提供者可以使用取用者實**IStorage**介面。</span><span class="sxs-lookup"><span data-stu-id="1018a-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can use a consumer-implemented **IStorage** interface when the consumer provides the interface pointer in an accessor bound for data modification.</span></span>  
  
 <span data-ttu-id="1018a-107">對於大數值資料類型， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會在**IROWSET**和 DDL 介面中檢查類型大小假設。</span><span class="sxs-lookup"><span data-stu-id="1018a-107">For large value data types, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider checks for type size assumptions in **IRowset** and DDL interfaces.</span></span> <span data-ttu-id="1018a-108">將 max 大小設為 [無限制] 的**Varchar**、 **Nvarchar**和**Varbinary**資料類型的資料行，將會以 ISLONG 的方式，透過架構資料列集和傳回資料類型的介面來表示。</span><span class="sxs-lookup"><span data-stu-id="1018a-108">Columns with **varchar**, **nvarchar**, and **varbinary** data types with max size set to unlimited will be represented as ISLONG through the schema rowsets and interfaces returning column data types.</span></span>  
  
 <span data-ttu-id="1018a-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會分別公開\*\*Varchar (max) \*\*、 **Varbinary (max) **和**Nvarchar (**) 、DBTYPE_STR 和 DBTYPE_BYTES 的最大 DBTYPE_WSTR 類型。</span><span class="sxs-lookup"><span data-stu-id="1018a-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **varchar(max)**, **varbinary(max)** and **nvarchar(max)** types as DBTYPE_STR, DBTYPE_BYTES and DBTYPE_WSTR respectively.</span></span>  
  
 <span data-ttu-id="1018a-110">為了使用這些類型，應用程式具有下列選項：</span><span class="sxs-lookup"><span data-stu-id="1018a-110">To work with these types an application has the following options:</span></span>  
  
-   <span data-ttu-id="1018a-111">繫結為類型 (DBTYPE_BYTES、DBTYPE_STR、DBTYPE_WSTR)。</span><span class="sxs-lookup"><span data-stu-id="1018a-111">Bind as the type (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR).</span></span> <span data-ttu-id="1018a-112">如果緩衝區不夠大，就會進行截斷，這與舊版中的這些類型完全相同，只是現在使用的是較大數值。</span><span class="sxs-lookup"><span data-stu-id="1018a-112">If the buffer is not big enough truncation will occur, exactly as for these types in previous releases (although larger values are now available).</span></span>  
  
-   <span data-ttu-id="1018a-113">繫結為類型，同時指定 DBTYPE_BYREF。</span><span class="sxs-lookup"><span data-stu-id="1018a-113">Bind as the type and also specify DBTYPE_BYREF.</span></span>  
  
-   <span data-ttu-id="1018a-114">繫結為 DBTYPE_IUNKNOWN 並使用資料流。</span><span class="sxs-lookup"><span data-stu-id="1018a-114">Bind as DBTYPE_IUNKNOWN and use streaming.</span></span>  
  
 <span data-ttu-id="1018a-115">如果繫結至 DBTYPE_IUNKNOWN，就會使用 ISequentialStream 資料流功能。</span><span class="sxs-lookup"><span data-stu-id="1018a-115">If bound to DBTYPE_IUNKNOWN, ISequentialStream stream functionality is used.</span></span> <span data-ttu-id="1018a-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者支援將輸出參數系結為大數值資料類型的 DBTYPE_IUNKNOWN，以加速預存程式傳回這些資料類型做為傳回值（將公開為用戶端的 DBTYPE_IUNKNOWN）的案例。</span><span class="sxs-lookup"><span data-stu-id="1018a-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports binding output parameters as DBTYPE_IUNKNOWN for large value data types to facilitate scenarios where a stored procedure returns these data types as return values which will be exposed as DBTYPE_IUNKNOWN to the client.</span></span>  
  
## <a name="storage-object-limitations"></a><span data-ttu-id="1018a-117">儲存物件的限制</span><span class="sxs-lookup"><span data-stu-id="1018a-117">Storage Object Limitations</span></span>  
  
-   <span data-ttu-id="1018a-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者只能支援單一開啟的儲存物件。</span><span class="sxs-lookup"><span data-stu-id="1018a-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can support only a single open storage object.</span></span> <span data-ttu-id="1018a-119">開啟多個儲存物件的嘗試 (取得多個 **ISequentialStream** 介面指標的參考) 會傳回 DBSTATUS_E_CANTCREATE。</span><span class="sxs-lookup"><span data-stu-id="1018a-119">Attempts to open more than one storage object (to get a reference on more than one **ISequentialStream** interface pointer) return DBSTATUS_E_CANTCREATE.</span></span>  
  
-   <span data-ttu-id="1018a-120">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者中，DBPROP_BLOCKINGSTORAGEOBJECTS 唯讀屬性的預設值為 VARIANT_TRUE。</span><span class="sxs-lookup"><span data-stu-id="1018a-120">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the default value of the DBPROP_BLOCKINGSTORAGEOBJECTS read-only property is VARIANT_TRUE.</span></span> <span data-ttu-id="1018a-121">這表示如果儲存物件作用中，某些方法 (非儲存物件的方法) 將會吃敗，並出現 E_UNEXPECTED。</span><span class="sxs-lookup"><span data-stu-id="1018a-121">This indicates that if a storage object is active, some methods (other than those on the storage objects) will fail with E_UNEXPECTED.</span></span>  
  
-   <span data-ttu-id="1018a-122">當建立參考儲存物件的資料列存取子時，由取用者所實儲存物件所呈現的資料長度必須由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者知道。</span><span class="sxs-lookup"><span data-stu-id="1018a-122">The length of data presented by a consumer-implemented storage object must be made known to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider when the row accessor that references the storage object is created.</span></span> <span data-ttu-id="1018a-123">取用者必須在建立存取子所使用的 DBBINDING 結構中繫結長度指標。</span><span class="sxs-lookup"><span data-stu-id="1018a-123">The consumer must bind a length indicator in the DBBINDING structure used for accessor creation.</span></span>  
  
-   <span data-ttu-id="1018a-124">如果資料列包含一個以上的單一大型資料值，但未 DBPROPVAL_AO_RANDOM DBPROP_ACCESSORDER，取用者必須使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者資料指標支援的資料列集，以在抓取其他資料列值之前，先取得資料列資料或處理所有的大型資料值。</span><span class="sxs-lookup"><span data-stu-id="1018a-124">If a row contains more than a single large data value and DBPROP_ACCESSORDER is not DBPROPVAL_AO_RANDOM, the consumer must either use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider cursor-supported rowset to retrieve row data or process all large data values before retrieving other row values.</span></span> <span data-ttu-id="1018a-125">如果 DBPROP_ACCESSORDER 是 DBPROPVAL_AO_RANDOM， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會將所有 xml 資料類型快取為二進位大型物件 (blob) ，以便依任何順序存取。</span><span class="sxs-lookup"><span data-stu-id="1018a-125">If DBPROP_ACCESSORDER is DBPROPVAL_AO_RANDOM, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider caches all the xml data types as binary large objects (BLOBs) so that it can be accessed in any order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1018a-126">本節內容</span><span class="sxs-lookup"><span data-stu-id="1018a-126">In This Section</span></span>  
  
-   [<span data-ttu-id="1018a-127">取得大型資料</span><span class="sxs-lookup"><span data-stu-id="1018a-127">Getting Large Data</span></span>](getting-large-data.md)  
  
-   [<span data-ttu-id="1018a-128">設定大型資料</span><span class="sxs-lookup"><span data-stu-id="1018a-128">Setting Large Data</span></span>](setting-large-data.md)  
  
-   [<span data-ttu-id="1018a-129">BLOB 輸出參數的串流支援</span><span class="sxs-lookup"><span data-stu-id="1018a-129">Streaming Support for BLOB Output Parameters</span></span>](streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a><span data-ttu-id="1018a-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1018a-130">See Also</span></span>  
 <span data-ttu-id="1018a-131">[SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="1018a-131">[SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md) </span></span>  
 [<span data-ttu-id="1018a-132">使用大數值類型</span><span class="sxs-lookup"><span data-stu-id="1018a-132">Using Large Value Types</span></span>](../native-client/features/using-large-value-types.md)  
  
  
