---
title: OLE DB 資料表值參數類型支援 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
ms.assetid: 147036a0-260e-4f81-8b3b-89209e023a32
author: rothja
ms.author: jroth
ms.openlocfilehash: 48d5fd780b2eaa2fc18e39071d3b10fde897b82c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594025"
---
# <a name="ole-db-table-valued-parameter-type-support"></a><span data-ttu-id="4f7e0-102">OLE DB 資料表值參數類型支援</span><span class="sxs-lookup"><span data-stu-id="4f7e0-102">OLE DB Table-Valued Parameter Type Support</span></span>
  <span data-ttu-id="4f7e0-103">本主題描述資料表值參數的 OLE DB 類型支援。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-103">This topic describes OLE DB type support for table-value parameters.</span></span>  
  
## <a name="table-valued-parameter-rowset-object"></a><span data-ttu-id="4f7e0-104">資料表值參數資料列集物件</span><span class="sxs-lookup"><span data-stu-id="4f7e0-104">Table-Valued Parameter Rowset Object</span></span>  
 <span data-ttu-id="4f7e0-105">您可以針對資料表值參數建立專用的資料列集物件。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-105">You can create a specialized rowset object for table-valued parameters.</span></span> <span data-ttu-id="4f7e0-106">您可以使用 ITableDefinitionWithConstraints::CreateTableWithConstraints 或 IOpenRowset::OpenRowset 來建立資料表值參數資料列集物件。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-106">You create the table-valued parameter rowset object by using ITableDefinitionWithConstraints::CreateTableWithConstraints or IOpenRowset::OpenRowset.</span></span> <span data-ttu-id="4f7e0-107">若要這樣做，請將 *pTableID* 參數的 *eKind* 成員設定為 DBKIND_GUID_NAME，並提供 CLSID_ROWSET_INMEMORY 當作 *guid* 成員。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-107">To do this, set the *eKind* member of the *pTableID* parameter to DBKIND_GUID_NAME, and provide the CLSID_ROWSET_INMEMORY as the *guid* member.</span></span> <span data-ttu-id="4f7e0-108">使用 IOpenRowset::OpenRowset 時，您必須在 *pTableID* 的 *pwszName* 成員中指定資料表值參數的伺服器類型名稱。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-108">The server type name for the table-valued parameter must be specified in the *pwszName* member of *pTableID* when using IOpenRowset::OpenRowset.</span></span> <span data-ttu-id="4f7e0-109">資料表值參數資料列集物件的行為就如同一般 SQL Server Native Client OLE DB 提供者物件。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-109">The table-valued parameter rowset object behaves like a regular SQL Server Native Client OLE DB Provider object.</span></span>  
  
```  
const GUID CLSID_ROWSET_TVP =   
{0xc7ef28d5, 0x7bee, 0x443f, {0x86, 0xda, 0xe3, 0x98, 0x4f, 0xcd, 0x4d, 0xf9}};  
  
CoType RowsetTVP  
{  
[mandatory] interface IAccessor;  
[mandatory] interface IColumnsInfo;  
[mandatory] interface IConvertType;  
[mandatory] interface IRowset;  
[mandatory] interface IRowsetInfo;  
[optional]  interface IColumnsRowset;  
[optional]  interface IRowsetChange;  
[optional]  interface ISupportErrorInfo;  
};  
```  
  
## <a name="dbtype_table"></a><span data-ttu-id="4f7e0-110">DBTYPE_TABLE</span><span class="sxs-lookup"><span data-stu-id="4f7e0-110">DBTYPE_TABLE</span></span>  
 <span data-ttu-id="4f7e0-111">新的類型 DBTYPE_TABLE 代表資料表類型。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-111">A new type, DBTYPE_TABLE, represents a table type.</span></span> <span data-ttu-id="4f7e0-112">這個類型會在需要 DBTYPE 的各種 OLE DB 介面中指定資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-112">This type specifies table-valued parameters in various OLE DB interfaces where a DBTYPE is required.</span></span>  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 <span data-ttu-id="4f7e0-113">DBTYPE_TABLE 與 DBTYPE_IUNKNOWN 具有相同的格式。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-113">DBTYPE_TABLE has the same format as DBTYPE_IUNKNOWN.</span></span> <span data-ttu-id="4f7e0-114">它是資料緩衝區中物件的指標。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-114">It is a pointer to an object in the data buffer.</span></span> <span data-ttu-id="4f7e0-115">若為繫結中的完整規格，取用者會填滿 DBOBJECT 緩衝區，並將 *iid* 設定為其中一個資料列集物件介面 (IID_IRowset)。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-115">For complete specification in the bindings, the consumer fills up the DBOBJECT buffer, with *iid* set to one of the rowset object interfaces (IID_IRowset).</span></span> <span data-ttu-id="4f7e0-116">如果繫結中沒有指定任何 DBOBJECT，系統就會採用 IID_IRowset。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-116">If no DBOBJECT is specified in the bindings, IID_IRowset will be assumed.</span></span>  
  
 <span data-ttu-id="4f7e0-117">不支援針對任何其他類型在 DBTYPE_TABLE 之間來回轉換。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-117">Conversions to and from DBTYPE_TABLE for any other types are not supported.</span></span> <span data-ttu-id="4f7e0-118">IConvertType::CanConvert 會針對任何要求的不支援轉換傳回 S_FALSE，但 DBTYPE_TABLE 與 DBTYPE_TABLE 的轉換除外。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-118">IConvertType::CanConvert will return S_FALSE for unsupported conversion for any request other than DBTYPE_TABLE to DBTYPE_TABLE conversion.</span></span> <span data-ttu-id="4f7e0-119">這會採用 Command 物件的 DBCONVERTFLAGS_PARAMETER。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-119">This assumes DBCONVERTFLAGS_PARAMETER on the Command object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4f7e0-120">方法</span><span class="sxs-lookup"><span data-stu-id="4f7e0-120">Methods</span></span>  
 <span data-ttu-id="4f7e0-121">如需有關支援資料表值參數之 OLE DB 方法的詳細資訊，請參閱 [OLE DB 資料表值參數類型支援 &#40;方法&#41;](ole-db-table-valued-parameter-type-support-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-121">For information about OLE DB methods that support table-valued parameters, see [OLE DB Table-Valued Parameter Type Support &#40;Methods&#41;](ole-db-table-valued-parameter-type-support-methods.md).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4f7e0-122">屬性</span><span class="sxs-lookup"><span data-stu-id="4f7e0-122">Properties</span></span>  
 <span data-ttu-id="4f7e0-123">如需支援資料表值參數之 OLE DB 屬性的詳細資訊，請參閱 [OLE DB 資料表值參數類型支援 &#40;屬性&#41;](ole-db-table-valued-parameter-type-support-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="4f7e0-123">For information about OLE DB properties that support table-valued parameters, see [OLE DB Table-Valued Parameter Type Support &#40;Properties&#41;](ole-db-table-valued-parameter-type-support-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f7e0-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f7e0-124">See Also</span></span>  
 <span data-ttu-id="4f7e0-125">[資料表值參數 &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="4f7e0-125">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="4f7e0-126">使用資料表值參數 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4f7e0-126">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
