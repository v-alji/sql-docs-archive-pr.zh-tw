---
title: 會話屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- SQL Server Native Client OLE DB provider, sessions
ms.assetid: 2498fbad-b3db-4bea-8fc6-fef5317d3eba
author: rothja
ms.author: jroth
ms.openlocfilehash: 99f2bc6def0f470f653446c87216c3e854b2f819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591994"
---
# <a name="session-properties"></a><span data-ttu-id="41971-102">工作階段屬性</span><span class="sxs-lookup"><span data-stu-id="41971-102">Session Properties</span></span>
  <span data-ttu-id="41971-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會解讀 OLE DB 會話屬性，如下所示。</span><span class="sxs-lookup"><span data-stu-id="41971-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider interprets OLE DB session properties as follows.</span></span>  
  
|<span data-ttu-id="41971-104">屬性識別碼</span><span class="sxs-lookup"><span data-stu-id="41971-104">Property ID</span></span>|<span data-ttu-id="41971-105">描述</span><span class="sxs-lookup"><span data-stu-id="41971-105">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="41971-106">DBPROP_SESS_AUTOCOMMITISOLEVELS</span><span class="sxs-lookup"><span data-stu-id="41971-106">DBPROP_SESS_AUTOCOMMITISOLEVELS</span></span>|<span data-ttu-id="41971-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]除了混亂層級 DBPROPVAL_TI_CHAOS 以外，Native Client OLE DB 提供者支援所有的自動認可交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="41971-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports all autocommit transaction isolation levels with the exception of the chaos level DBPROPVAL_TI_CHAOS.</span></span>|  
  
 <span data-ttu-id="41971-108">在提供者特定的屬性集 DBPROPSET_SQLSERVERSESSION 中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會定義下列額外的會話屬性。</span><span class="sxs-lookup"><span data-stu-id="41971-108">In the provider-specific property set DBPROPSET_SQLSERVERSESSION, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following additional session property.</span></span>  
  
|<span data-ttu-id="41971-109">屬性識別碼</span><span class="sxs-lookup"><span data-stu-id="41971-109">Property ID</span></span>|<span data-ttu-id="41971-110">描述</span><span class="sxs-lookup"><span data-stu-id="41971-110">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="41971-111">SSPROP_QUOTEDCATALOGNAMES</span><span class="sxs-lookup"><span data-stu-id="41971-111">SSPROP_QUOTEDCATALOGNAMES</span></span>|<span data-ttu-id="41971-112">輸入：VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="41971-112">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="41971-113">R/W︰讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="41971-113">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="41971-114">預設值：VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="41971-114">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="41971-115">描述：CATALOG 限制中允許引號識別碼。</span><span class="sxs-lookup"><span data-stu-id="41971-115">Description: Quoted identifiers allowed in CATALOG restriction.</span></span><br /><br /> <span data-ttu-id="41971-116">VARIANT_TRUE：辨識出引號識別碼有提供分散式查詢支援之結構描述資料列集的目錄限制。</span><span class="sxs-lookup"><span data-stu-id="41971-116">VARIANT_TRUE: Quoted identifiers are recognized for a catalog restriction for the schema rowsets that supply distributed query support.</span></span><br /><br /> <span data-ttu-id="41971-117">VARIANT_FALSE：未辨識出引號識別碼有提供分散式查詢支援之結構描述資料列集的目錄限制。</span><span class="sxs-lookup"><span data-stu-id="41971-117">VARIANT_FALSE: Quoted identifiers are not recognized for a catalog restriction for the schema rowsets that supply distributed query support.</span></span><br /><br /> <span data-ttu-id="41971-118">如需提供分散式查詢支援之結構描述資料列集的詳細資訊，請參閱[結構描述資料列集中的分散式查詢支援](../native-client/ole-db/schema-rowsets-distributed-query-support.md)。</span><span class="sxs-lookup"><span data-stu-id="41971-118">For more information about schema rowsets that supply distributed query support, see [Distributed Query Support in Schema Rowsets](../native-client/ole-db/schema-rowsets-distributed-query-support.md).</span></span>|  
|<span data-ttu-id="41971-119">SSPROP_ALLOWNATIVEVARIANT</span><span class="sxs-lookup"><span data-stu-id="41971-119">SSPROP_ALLOWNATIVEVARIANT</span></span>|<span data-ttu-id="41971-120">輸入：VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="41971-120">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="41971-121">R/W：讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="41971-121">R/W: Read/Write</span></span><br /><br /> <span data-ttu-id="41971-122">預設值：VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="41971-122">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="41971-123">描述：決定所提取的資料是否為 DBTYPE_VARIANT 或 DBTYPE_SQLVARIANT。</span><span class="sxs-lookup"><span data-stu-id="41971-123">Description: Determines if the data fetched in is as DBTYPE_VARIANT or DBTYPE_SQLVARIANT.</span></span><br /><br /> <span data-ttu-id="41971-124">VARIANT_TRUE：資料行類型是以 DBTYPE_SQLVARIANT 傳回，在此種情況下，緩衝區會保存 SSVARIANT 結構。</span><span class="sxs-lookup"><span data-stu-id="41971-124">VARIANT_TRUE: Column type is returned as DBTYPE_SQLVARIANT in which case the buffer will hold SSVARIANT structure.</span></span><br /><br /> <span data-ttu-id="41971-125">VARIANT_FALSE：資料行類型是以 DBTYPE_VARIANT 傳回，而且緩衝區將具有 VARIANT 結構。</span><span class="sxs-lookup"><span data-stu-id="41971-125">VARIANT_FALSE: Column type is returned as DBTYPE_VARIANT and the buffer will have VARIANT structure.</span></span>|  
|<span data-ttu-id="41971-126">SSPROP_ASYNCH_BULKCOPY</span><span class="sxs-lookup"><span data-stu-id="41971-126">SSPROP_ASYNCH_BULKCOPY</span></span>|<span data-ttu-id="41971-127">若要使用非同步模式，請在呼叫 BCPExec 方法之前將提供者特有的工作階段屬性 SSPROP_ASYNCH_BULKCOPY 設定為 VARIANT_TRUE。</span><span class="sxs-lookup"><span data-stu-id="41971-127">To use asynchronous mode, set the provider specific session property SSPROP_ASYNCH_BULKCOPY to VARIANT_TRUE before calling the BCPExec method.</span></span> <span data-ttu-id="41971-128">DBPROPSET_SQLSERVERSESSION 屬性集中有提供這個屬性。</span><span class="sxs-lookup"><span data-stu-id="41971-128">This property is available in the DBPROPSET_SQLSERVERSESSION property set.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41971-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41971-129">See Also</span></span>  
 [<span data-ttu-id="41971-130">資料來源物件 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="41971-130">Data Source Objects &#40;OLE DB&#41;</span></span>](data-source-objects-ole-db.md)  
  
  
