---
title: IRowsetFastLoad::InsertRow (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IRowsetFastLoad::InsertRow (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- InsertRow method
ms.assetid: 594d3461-34d2-41e7-8ad4-bd2753601ab6
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e9ea952f27574270ee333919f778814ff3de462
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599485"
---
# <a name="irowsetfastloadinsertrow-ole-db"></a><span data-ttu-id="33b8f-102">IRowsetFastLoad::InsertRow (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="33b8f-102">IRowsetFastLoad::InsertRow (OLE DB)</span></span>
  <span data-ttu-id="33b8f-103">將資料列加入至大量複製資料列集。</span><span class="sxs-lookup"><span data-stu-id="33b8f-103">Adds a row to the bulk copy rowset.</span></span> <span data-ttu-id="33b8f-104">如需範例，請參閱[使用 IRowsetFastLoad 大量複製資料 &#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) 和[使用 IROWSETFASTLOAD 和 ISEQUENTIALSTREAM 將 BLOB 資料傳送到 SQL SERVER &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="33b8f-104">For samples, see [Bulk Copy Data Using IRowsetFastLoad &#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) and [Send BLOB Data to SQL SERVER Using IROWSETFASTLOAD and ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33b8f-105">語法</span><span class="sxs-lookup"><span data-stu-id="33b8f-105">Syntax</span></span>  
  
```  
  
HRESULT InsertRow(  
HACCESSOR  
hAccessor  
,  
void*  
pData  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="33b8f-106">引數</span><span class="sxs-lookup"><span data-stu-id="33b8f-106">Arguments</span></span>  
 <span data-ttu-id="33b8f-107">*hAccessor*[in]</span><span class="sxs-lookup"><span data-stu-id="33b8f-107">*hAccessor*[in]</span></span>  
 <span data-ttu-id="33b8f-108">針對大量複製而定義資料列資料的存取子控制代碼。</span><span class="sxs-lookup"><span data-stu-id="33b8f-108">The handle of the accessor defining the row data for bulk copy.</span></span> <span data-ttu-id="33b8f-109">所參考的存取子是資料列存取子，會繫結取用者所擁有的記憶體 (內含資料值)。</span><span class="sxs-lookup"><span data-stu-id="33b8f-109">The accessor referenced is a row accessor, binding consumer-owned memory containing data values.</span></span>  
  
 <span data-ttu-id="33b8f-110">*pData*[in]</span><span class="sxs-lookup"><span data-stu-id="33b8f-110">*pData*[in]</span></span>  
 <span data-ttu-id="33b8f-111">取用者所擁有記憶體 (內含資料值) 的指標。</span><span class="sxs-lookup"><span data-stu-id="33b8f-111">A pointer to the consumer-owned memory containing data values.</span></span> <span data-ttu-id="33b8f-112">如需詳細資訊，請參閱 [DBBINDING 結構](https://go.microsoft.com/fwlink/?LinkId=65955)。</span><span class="sxs-lookup"><span data-stu-id="33b8f-112">For more information, see [DBBINDING Structures](https://go.microsoft.com/fwlink/?LinkId=65955).</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="33b8f-113">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="33b8f-113">Return Code Values</span></span>  
 <span data-ttu-id="33b8f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="33b8f-114">S_OK</span></span>  
 <span data-ttu-id="33b8f-115">此方法已成功。</span><span class="sxs-lookup"><span data-stu-id="33b8f-115">The method succeeded.</span></span> <span data-ttu-id="33b8f-116">所有資料行的任何繫結狀態值都具有 DBSTATUS_S_OK 或 DBSTATUS_S_NULL 值。</span><span class="sxs-lookup"><span data-stu-id="33b8f-116">Any bound status values for all columns have value DBSTATUS_S_OK or DBSTATUS_S_NULL.</span></span>  
  
 <span data-ttu-id="33b8f-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="33b8f-117">E_FAIL</span></span>  
 <span data-ttu-id="33b8f-118">發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="33b8f-118">An error occurred.</span></span> <span data-ttu-id="33b8f-119">可以從資料列集的錯誤介面取得錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="33b8f-119">Error information is available from the rowset's error interfaces.</span></span>  
  
 <span data-ttu-id="33b8f-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="33b8f-120">E_INVALIDARG</span></span>  
 <span data-ttu-id="33b8f-121">*pData* 引數已設為 NULL 指標。</span><span class="sxs-lookup"><span data-stu-id="33b8f-121">The *pData* argument was set to a NULL pointer.</span></span>  
  
 <span data-ttu-id="33b8f-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="33b8f-122">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="33b8f-123">SQLNCLI11 無法配置足夠的記憶體來完成要求。</span><span class="sxs-lookup"><span data-stu-id="33b8f-123">SQLNCLI11 was unable to allocate sufficient memory to complete the request.</span></span>  
  
 <span data-ttu-id="33b8f-124">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="33b8f-124">E_UNEXPECTED</span></span>  
 <span data-ttu-id="33b8f-125">這個方法是在先前已藉由 [IRowsetFastLoad::Commit](irowsetfastload-commit-ole-db.md) 方法設為無效之大量複製資料列集上呼叫。</span><span class="sxs-lookup"><span data-stu-id="33b8f-125">The method was called on a bulk copy rowset previously invalidated by the [IRowsetFastLoad::Commit](irowsetfastload-commit-ole-db.md) method.</span></span>  
  
 <span data-ttu-id="33b8f-126">DB_E_BADACCESSORHANDLE</span><span class="sxs-lookup"><span data-stu-id="33b8f-126">DB_E_BADACCESSORHANDLE</span></span>  
 <span data-ttu-id="33b8f-127">取用者所提供的 *hAccessor* 引數無效。</span><span class="sxs-lookup"><span data-stu-id="33b8f-127">The *hAccessor* argument provided by the consumer was invalid.</span></span>  
  
 <span data-ttu-id="33b8f-128">DB_E_BADACCESSORTYPE</span><span class="sxs-lookup"><span data-stu-id="33b8f-128">DB_E_BADACCESSORTYPE</span></span>  
 <span data-ttu-id="33b8f-129">指定的存取子不是資料列存取子，或未指定取用者所擁有的記憶體。</span><span class="sxs-lookup"><span data-stu-id="33b8f-129">The specified accessor was not a row accessor or did not specify consumer-owned memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33b8f-130">備註</span><span class="sxs-lookup"><span data-stu-id="33b8f-130">Remarks</span></span>  
 <span data-ttu-id="33b8f-131">將取用者資料轉換成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料行的資料類型時發生錯誤，會導致從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者傳回 E_FAIL。</span><span class="sxs-lookup"><span data-stu-id="33b8f-131">An error converting consumer data to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for a column causes an E_FAIL return from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="33b8f-132">您可在任何 **InsertRow** 方法或僅在 **Commit** 方法上將資料傳輸至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="33b8f-132">Data can be transmitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on any **InsertRow** method or only on **Commit** method.</span></span> <span data-ttu-id="33b8f-133">取用者應用程式可能會在使用錯誤的資料呼叫 **InsertRow** 方法很多次後，才收到發生了資料類型轉換錯誤的通知。</span><span class="sxs-lookup"><span data-stu-id="33b8f-133">The consumer application can call the **InsertRow** method many times with erroneous data before it receives notice that a data type conversion error exists.</span></span> <span data-ttu-id="33b8f-134">因為 **Commit** 方法會確保所有資料都由取用者正確指定，所以取用者可依需要適當地使用 **Commit** 方法來驗證資料。</span><span class="sxs-lookup"><span data-stu-id="33b8f-134">Because the **Commit** method ensures that all data is correctly specified by the consumer, the consumer can use the **Commit** method appropriately to validate data as necessary.</span></span>  
  
 <span data-ttu-id="33b8f-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者大量複製資料列集為僅限寫入。</span><span class="sxs-lookup"><span data-stu-id="33b8f-135">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider bulk copy rowsets are write-only.</span></span> <span data-ttu-id="33b8f-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者不會公開允許取用者查詢資料列集的任何方法。</span><span class="sxs-lookup"><span data-stu-id="33b8f-136">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes no methods allowing consumer query of the rowset.</span></span> <span data-ttu-id="33b8f-137">若要終止處理，取用者可以不必呼叫 **Commit** 方法，即釋放它在 [IRowsetFastLoad](irowsetfastload-ole-db.md) 介面上的參考。</span><span class="sxs-lookup"><span data-stu-id="33b8f-137">To terminate processing, the consumer can release its reference on the [IRowsetFastLoad](irowsetfastload-ole-db.md) interface without calling the **Commit** method.</span></span> <span data-ttu-id="33b8f-138">沒有功能可用來存取資料列集中取用者插入的資料列並變更其值，或將該資料列從資料列集個別地移除。</span><span class="sxs-lookup"><span data-stu-id="33b8f-138">There are no facilities for accessing a consumer-inserted row in the rowset and changing its values, or removing it individually from the rowset.</span></span>  
  
 <span data-ttu-id="33b8f-139">大量複製的資料列會在伺服器上針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定格式。</span><span class="sxs-lookup"><span data-stu-id="33b8f-139">Bulk copied rows are formatted on the server for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="33b8f-140">資料列格式會受到已針對連接或工作階段所設定之任何選項 (例如 ANSI_PADDING) 的影響。</span><span class="sxs-lookup"><span data-stu-id="33b8f-140">The row format is affected by any options that may have been set for the connection or session such as ANSI_PADDING.</span></span> <span data-ttu-id="33b8f-141">根據預設，此選項會針對透過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者所建立的任何連接進行設定。</span><span class="sxs-lookup"><span data-stu-id="33b8f-141">This option is set on by default for any connection made through the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33b8f-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33b8f-142">See Also</span></span>  
 [<span data-ttu-id="33b8f-143">IRowsetFastLoad &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="33b8f-143">IRowsetFastLoad &#40;OLE DB&#41;</span></span>](irowsetfastload-ole-db.md)  
  
  
