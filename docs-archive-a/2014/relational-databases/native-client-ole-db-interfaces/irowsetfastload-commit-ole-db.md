---
title: IRowsetFastLoad::Commit (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IRowsetFastLoad::Commit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Commit method
ms.assetid: 19de9128-b91a-4626-847f-af721edaa24e
author: rothja
ms.author: jroth
ms.openlocfilehash: cfdf355919f65fd2cedacd09249e2aae59321390
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599489"
---
# <a name="irowsetfastloadcommit-ole-db"></a><span data-ttu-id="912ac-102">IRowsetFastLoad::Commit (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="912ac-102">IRowsetFastLoad::Commit (OLE DB)</span></span>
  <span data-ttu-id="912ac-103">標示已插入之資料列批次的結尾，並將資料列寫入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="912ac-103">Marks the end of a batch of inserted rows and writes the rows to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="912ac-104">如需範例，請參閱[使用 IRowsetFastLoad 大量複製資料 &#40;OLE DB&#41;](irowsetfastload-ole-db.md) 和[使用 IROWSETFASTLOAD 和 ISEQUENTIALSTREAM 將 BLOB 資料傳送到 SQL SERVER &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="912ac-104">For samples, see [Bulk Copy Data Using IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md) and [Send BLOB Data to SQL SERVER Using IROWSETFASTLOAD and ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="912ac-105">語法</span><span class="sxs-lookup"><span data-stu-id="912ac-105">Syntax</span></span>  
  
```  
  
HRESULT Commit(  
BOOL   
fDone  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="912ac-106">引數</span><span class="sxs-lookup"><span data-stu-id="912ac-106">Arguments</span></span>  
 <span data-ttu-id="912ac-107">*fDone*[in]</span><span class="sxs-lookup"><span data-stu-id="912ac-107">*fDone*[in]</span></span>  
 <span data-ttu-id="912ac-108">如果為 FALSE，此資料列集就會維持有效性，而且可供取用者用於其他資料列插入作業。</span><span class="sxs-lookup"><span data-stu-id="912ac-108">If FALSE, the rowset maintains validity and can be used by the consumer for additional row insertion.</span></span> <span data-ttu-id="912ac-109">如果為 TRUE，此資料列集就會喪失有效性，而且取用者無法完成其他插入作業。</span><span class="sxs-lookup"><span data-stu-id="912ac-109">If TRUE, the rowset loses validity and no further insertion can be done by the consumer.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="912ac-110">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="912ac-110">Return Code Values</span></span>  
 <span data-ttu-id="912ac-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="912ac-111">S_OK</span></span>  
 <span data-ttu-id="912ac-112">此方法已成功，而且所有插入的資料都已經寫入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中。</span><span class="sxs-lookup"><span data-stu-id="912ac-112">The method succeeded and all inserted data has been written to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="912ac-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="912ac-113">E_FAIL</span></span>  
 <span data-ttu-id="912ac-114">發生了提供者特定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="912ac-114">A provider-specific error occurred.</span></span> <span data-ttu-id="912ac-115">請從提供者中擷取特定錯誤文字的錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="912ac-115">Retrieve error information for the specific error text from the provider.</span></span>  
  
 <span data-ttu-id="912ac-116">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="912ac-116">E_UNEXPECTED</span></span>  
 <span data-ttu-id="912ac-117">這個方法是在先前已藉由 **IRowsetFastLoad::Commit** 方法設為無效之大量複製資料列集上呼叫。</span><span class="sxs-lookup"><span data-stu-id="912ac-117">The method was called on a bulk copy rowset previously invalidated by the **IRowsetFastLoad::Commit** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="912ac-118">備註</span><span class="sxs-lookup"><span data-stu-id="912ac-118">Remarks</span></span>  
 <span data-ttu-id="912ac-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者大量複製資料列集的行為是延遲更新模式資料列集。</span><span class="sxs-lookup"><span data-stu-id="912ac-119">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider bulk copy rowset behaves as a delayed-update mode rowset.</span></span> <span data-ttu-id="912ac-120">因為使用者會透過資料列集插入資料列的資料，所以插入的資料列會以相同的方式被視為支援 **IRowsetUpdate** 之資料列集上的暫止插入。</span><span class="sxs-lookup"><span data-stu-id="912ac-120">As the user inserts row data through the rowset, inserted rows are treated in the same fashion as pending inserts on a rowset supporting **IRowsetUpdate**.</span></span>  
  
 <span data-ttu-id="912ac-121">取用者必須針對大量複製資料列集呼叫 **Commit** 方法，才能將插入的資料列寫入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中，其方式就如同使用 **IRowsetUpdate::Update** 方法，將暫止資料列提交給 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="912ac-121">The consumer must call the **Commit** method on the bulk copy rowset to write inserted rows to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table in the same way as the **IRowsetUpdate::Update** method is used to submit pending rows to an instance of SQL Server.</span></span>  
  
 <span data-ttu-id="912ac-122">如果取用者釋放大量複製資料列集的參考，而沒有呼叫 **Commit** 方法，所有先前並未寫入的已插入資料列都會遺失。</span><span class="sxs-lookup"><span data-stu-id="912ac-122">If the consumer releases its reference on the bulk copy rowset without calling the **Commit** method, all inserted rows not previously written are lost.</span></span>  
  
 <span data-ttu-id="912ac-123">取用者可以呼叫 **Commit** 方法，並將 *fDone* 引數設定為 FALSE，藉以批次處理插入的資料列。</span><span class="sxs-lookup"><span data-stu-id="912ac-123">The consumer can batch inserted rows by calling the **Commit** method with the *fDone* argument set to FALSE.</span></span> <span data-ttu-id="912ac-124">當 *fDone* 設定為 TRUE 時，此資料列集就會成為無效。</span><span class="sxs-lookup"><span data-stu-id="912ac-124">When *fDone*is set to TRUE, the rowset becomes invalid.</span></span> <span data-ttu-id="912ac-125">無效的大量複製資料列集僅支援 **ISupportErrorInfo** 介面和 **IRowsetFastLoad::Release** 方法。</span><span class="sxs-lookup"><span data-stu-id="912ac-125">An invalid bulk copy rowset supports only the **ISupportErrorInfo** interface and **IRowsetFastLoad::Release** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912ac-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="912ac-126">See Also</span></span>  
 [<span data-ttu-id="912ac-127">IRowsetFastLoad &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="912ac-127">IRowsetFastLoad &#40;OLE DB&#41;</span></span>](irowsetfastload-ole-db.md)  
  
  
