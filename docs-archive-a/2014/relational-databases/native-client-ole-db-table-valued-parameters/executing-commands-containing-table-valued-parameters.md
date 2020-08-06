---
title: 執行包含資料表值參數的命令 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, executing commands containing
ms.assetid: 7ecba6f6-fe7a-462a-9aa3-d5115b6d4529
author: rothja
ms.author: jroth
ms.openlocfilehash: e3f616b2b9f95ae558e444bcbdae50eae123fa4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593372"
---
# <a name="executing-commands-containing-table-valued-parameters"></a><span data-ttu-id="55097-102">執行包含資料表值參數的命令</span><span class="sxs-lookup"><span data-stu-id="55097-102">Executing Commands Containing Table-Valued Parameters</span></span>
  <span data-ttu-id="55097-103">執行包含資料表值參數的命令需要兩個階段：</span><span class="sxs-lookup"><span data-stu-id="55097-103">Executing a command that contains table-valued parameters requires two phases:</span></span>  
  
1.  <span data-ttu-id="55097-104">指定參數類型。</span><span class="sxs-lookup"><span data-stu-id="55097-104">Specify the parameter types.</span></span>  
  
2.  <span data-ttu-id="55097-105">繫結參數資料。</span><span class="sxs-lookup"><span data-stu-id="55097-105">Bind the parameter data.</span></span>  
  
## <a name="table-valued-parameter-specification"></a><span data-ttu-id="55097-106">資料表值參數規格</span><span class="sxs-lookup"><span data-stu-id="55097-106">Table-Valued Parameter Specification</span></span>  
 <span data-ttu-id="55097-107">取用者可以指定資料表值參數的類型。</span><span class="sxs-lookup"><span data-stu-id="55097-107">The consumer can specify the type of the table-valued parameter.</span></span> <span data-ttu-id="55097-108">此資訊包含資料表值參數類型名稱。</span><span class="sxs-lookup"><span data-stu-id="55097-108">This information includes the table-valued parameter type name.</span></span> <span data-ttu-id="55097-109">如果資料表值參數的使用者定義資料表類型不在用於連接的目前預設結構描述中，它也包含結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="55097-109">It also includes the schema name, if the user-defined table type for the table-valued parameter is not in the current default schema for the connection.</span></span> <span data-ttu-id="55097-110">根據伺服器支援，取用者也可以指定選擇性的中繼資料資訊，例如，資料行的順序，而且可以指定特定資料行的所有資料列都有預設值。</span><span class="sxs-lookup"><span data-stu-id="55097-110">Depending on server support, the consumer can also specify optional metadata information, such as ordering of columns, and can specify that all rows for particular columns have the default values.</span></span>  
  
 <span data-ttu-id="55097-111">若要指定資料表值參數，取用者會呼叫 ISSCommandWithParameter::SetParameterInfo，並選擇性地呼叫 ISSCommandWithParameters::SetParameterProperties。</span><span class="sxs-lookup"><span data-stu-id="55097-111">To specify a table-valued parameter, the consumer calls ISSCommandWithParameter::SetParameterInfo, and optionally calls ISSCommandWithParameters::SetParameterProperties.</span></span> <span data-ttu-id="55097-112">如果是資料表值參數，DBPARAMBINDINFO 結構中的 *pwszDataSourceType* 欄位將會有 DBTYPE_TABLE 的值。</span><span class="sxs-lookup"><span data-stu-id="55097-112">For a table-valued parameter, the *pwszDataSourceType* field in the DBPARAMBINDINFO structure has a value of DBTYPE_TABLE.</span></span> <span data-ttu-id="55097-113">*ulParamSize* 欄位會設定為 ~0，表示長度未知。</span><span class="sxs-lookup"><span data-stu-id="55097-113">The *ulParamSize* field is set to ~0 to indicate that length is unknown.</span></span> <span data-ttu-id="55097-114">資料表值參數的特定屬性 (例如結構描述名稱、類型名稱、資料行順序和預設資料行) 可以透過 ISSCommandWithParameters::SetParameterProperties 設定。</span><span class="sxs-lookup"><span data-stu-id="55097-114">Particular properties for table-valued parameters, such as schema name, type name, column order, and default columns, can be set through ISSCommandWithParameters::SetParameterProperties.</span></span>  
  
## <a name="table-valued-parameter-binding"></a><span data-ttu-id="55097-115">資料表值參數繫結</span><span class="sxs-lookup"><span data-stu-id="55097-115">Table-Valued Parameter Binding</span></span>  
 <span data-ttu-id="55097-116">資料表值參數可以是任何資料列集物件。</span><span class="sxs-lookup"><span data-stu-id="55097-116">A table-valued parameter can be any rowset object.</span></span> <span data-ttu-id="55097-117">提供者會在執行期間將資料表值參數傳送到伺服器的同時，從此物件讀取。</span><span class="sxs-lookup"><span data-stu-id="55097-117">The provider reads from this object while sending table-valued parameters to the server during execution.</span></span>  
  
 <span data-ttu-id="55097-118">若要繫結資料表值參數，取用者可以呼叫 IAccessor::CreateAccessor。</span><span class="sxs-lookup"><span data-stu-id="55097-118">To bind the table-valued parameter, the consumer calls IAccessor::CreateAccessor.</span></span> <span data-ttu-id="55097-119">如果是資料表值參數，DBBINDING 結構的 *wType* 欄位會設定為 DBTYPE_TABLE。</span><span class="sxs-lookup"><span data-stu-id="55097-119">The *wType* field of the DBBINDING structure for the table-valued parameter is set to DBTYPE_TABLE.</span></span> <span data-ttu-id="55097-120">DBBINDING 結構的 *pObject* 成員不是 NULL，而且 *pObject* 的 *iid* 成員會設定為 IID_IRowset 或其他任何資料表值參數資料列集物件介面。</span><span class="sxs-lookup"><span data-stu-id="55097-120">The *pObject* member of the DBBINDING structure is non-NULL, and the *pObject*'s *iid* member is set to IID_IRowset or any other table-valued parameter rowset object interfaces.</span></span> <span data-ttu-id="55097-121">DBBINDING 結構中其餘欄位的設定方式應該與針對資料流 BLOB 設定欄位的方式相同。</span><span class="sxs-lookup"><span data-stu-id="55097-121">The remaining fields in the DBBINDING structure should be set the same way they are set for streamed BLOBs.</span></span>  
  
 <span data-ttu-id="55097-122">如果是資料表值參數以及與資料表值參數相關聯之資料列集物件的繫結，則適用下列限制：</span><span class="sxs-lookup"><span data-stu-id="55097-122">In the bindings for the table-valued parameter and the rowset object associated with a table-valued parameter, the following restrictions apply:</span></span>  
  
-   <span data-ttu-id="55097-123">資料表值參數資料列集資料行資料所允許的唯一狀態值為 DBSTATUS_S_ISNULL 和 DBSTATUS_S_OK。</span><span class="sxs-lookup"><span data-stu-id="55097-123">The only status values allowed for table-valued parameter rowset column data are DBSTATUS_S_ISNULL and DBSTATUS_S_OK.</span></span> <span data-ttu-id="55097-124">DBSTATUS_S_DEFAULT 將會導致失敗，而繫結的狀態值將會設定為 DBSTATUS_E_BADSTATUS。</span><span class="sxs-lookup"><span data-stu-id="55097-124">DBSTATUS_S_DEFAULT will result in a failure, and the bound status value will be set to DBSTATUS_E_BADSTATUS.</span></span>  
  
-   <span data-ttu-id="55097-125">資料表值參數可以使用 DBSTATUS_S_DEFAULT 狀態標示。</span><span class="sxs-lookup"><span data-stu-id="55097-125">A table-valued parameter can be marked with the status DBSTATUS_S_DEFAULT.</span></span> <span data-ttu-id="55097-126">唯一的有效值為 DBSTATUS_S_DEFAULT 和 DBSTATUS_S_OK。</span><span class="sxs-lookup"><span data-stu-id="55097-126">The only valid values are DBSTATUS_S_DEFAULT and DBSTATUS_S_OK.</span></span> <span data-ttu-id="55097-127">當狀態設定為 DBSTATUS_S_DEFAULT 時，資料表值參數的值會對應到一個空資料表。</span><span class="sxs-lookup"><span data-stu-id="55097-127">When the status is set to DBSTATUS_S_DEFAULT, the value of the table-valued parameter corresponds to an empty table.</span></span>  
  
-   <span data-ttu-id="55097-128">資料表值參數中的唯讀資料行 (識別或計算資料行) 必須使用 SSPROP_PARAM_TABLE_DEFAULT_COLUMNS 屬性標示為預設值。</span><span class="sxs-lookup"><span data-stu-id="55097-128">Read-only columns in table-valued parameters (identity or computed columns) must be marked as default by using the SSPROP_PARAM_TABLE_DEFAULT_COLUMNS property.</span></span> <span data-ttu-id="55097-129">擁有預設值的資料行也必須透過 SSPROP_PARAM_TABLE_DEFAULT_COLUMNS 屬性標示為預設值，以便讓預設值用於特定資料表值參數的資料行資料值。</span><span class="sxs-lookup"><span data-stu-id="55097-129">Columns that have a default value must also be marked as default through SSPROP_PARAM_TABLE_DEFAULT_COLUMNS property to allow the default value to be used for the column's data values for a particular table-valued parameter.</span></span> <span data-ttu-id="55097-130">提供者將會忽略針對標示為預設值之資料行所繫結的資料值。</span><span class="sxs-lookup"><span data-stu-id="55097-130">The provider will ignore the data values bound for the columns marked as default.</span></span>  
  
-   <span data-ttu-id="55097-131">除非同時設定 SSPROP_PARAM_TABLE_DEFAULT，否則會將包含 DBPROP_COL_AUTOINCREMENT 或 SSPROP_COL_COMPUTED 之資料行的資料傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="55097-131">Data will be sent to the server for columns with DBPROP_COL_AUTOINCREMENT or SSPROP_COL_COMPUTED, unless SSPROP_PARAM_TABLE_DEFAULT is also set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55097-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55097-132">See Also</span></span>  
 <span data-ttu-id="55097-133">[資料表值參數 &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="55097-133">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="55097-134">使用資料表值參數 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="55097-134">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
