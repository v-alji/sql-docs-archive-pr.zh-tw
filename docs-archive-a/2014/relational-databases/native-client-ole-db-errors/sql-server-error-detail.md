---
title: SQL Server 錯誤詳細資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
ms.assetid: 51500ee3-3d78-47ec-b90f-ebfc55642e06
author: rothja
ms.author: jroth
ms.openlocfilehash: 4c03cf62dd274f9bcca213d33fb8969b26c9d980
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598840"
---
# <a name="sql-server-error-detail"></a><span data-ttu-id="58951-102">SQL Server 錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="58951-102">SQL Server Error Detail</span></span>
  <span data-ttu-id="58951-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會定義提供者特定的錯誤介面[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="58951-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the provider-specific error interface [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md).</span></span> <span data-ttu-id="58951-104">此介面會傳回有關 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤的詳細資料，在命令執行或資料列集作業失敗時非常有用。</span><span class="sxs-lookup"><span data-stu-id="58951-104">The interface returns more detail about a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error and is valuable when command execution or rowset operations fail.</span></span>  
  
 <span data-ttu-id="58951-105">取得 **ISQLServerErrorInfo** 介面存取權的方法有兩種。</span><span class="sxs-lookup"><span data-stu-id="58951-105">There are two ways to obtain access to **ISQLServerErrorInfo** interface.</span></span>  
  
 <span data-ttu-id="58951-106">取用者可以呼叫 **IErrorRecords::GetCustomerErrorObject** 來取得 **ISQLServerErrorInfo** 指標，如下列程式碼範例所示</span><span class="sxs-lookup"><span data-stu-id="58951-106">The consumer may call **IErrorRecords::GetCustomerErrorObject** to obtain an **ISQLServerErrorInfo** pointer, as shown in the following code sample.</span></span> <span data-ttu-id="58951-107">(不需要取得 **ISQLErrorInfo**)。**ISQLErrorInfo** 和 **ISQLServerErrorInfo** 這兩者都是自訂的 OLE DB 錯誤物件，其中 **ISQLServerErrorInfo** 是用來取得伺服器錯誤資訊 (包括程序名稱和行號之類的詳細資料) 的介面。</span><span class="sxs-lookup"><span data-stu-id="58951-107">(There is no need to obtain **ISQLErrorInfo.**) Both **ISQLErrorInfo** and **ISQLServerErrorInfo** are custom OLE DB error objects, with **ISQLServerErrorInfo** being the interface to use to obtain information of server errors, including such details as procedure name and line numbers.</span></span>  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 <span data-ttu-id="58951-108">另一種取得 **ISQLServerErrorInfo** 指標的方法是在已取得的 **ISQLErrorInfo** 指標上呼叫 **QueryInterface** 方法。</span><span class="sxs-lookup"><span data-stu-id="58951-108">Another way to get an **ISQLServerErrorInfo** pointer is to call the **QueryInterface** method on an already-obtained **ISQLErrorInfo** pointer.</span></span> <span data-ttu-id="58951-109">請注意，因為 **ISQLServerErrorInfo** 包含 **ISQLErrorInfo** 所提供資訊的超集，所以透過 **GetCustomerErrorObject** 直接存取 **ISQLServerErrorInfo** 很合理。</span><span class="sxs-lookup"><span data-stu-id="58951-109">Note that because **ISQLServerErrorInfo** contains a superset of the information available from **ISQLErrorInfo**, it makes sense to go directly to **ISQLServerErrorInfo** through **GetCustomerErrorObject**.</span></span>  
  
 <span data-ttu-id="58951-110">**ISQLServerErrorInfo** 介面會公開一個成員函數 [ISQLServerErrorInfo::GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="58951-110">The **ISQLServerErrorInfo** interface exposes one member function, [ISQLServerErrorInfo::GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md).</span></span> <span data-ttu-id="58951-111">該函數會傳回 SSERRORINFO 結構的指標以及字串緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="58951-111">The function returns a pointer to an SSERRORINFO structure and a pointer to a string buffer.</span></span> <span data-ttu-id="58951-112">這兩個指標都會參考取用者必須使用 **IMalloc::Free** 方法來取消配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="58951-112">Both pointers reference memory the consumer must deallocate by using the **IMalloc::Free** method.</span></span>  
  
 <span data-ttu-id="58951-113">SSERRORINFO 結構成員會依下列方式由取用者解譯。</span><span class="sxs-lookup"><span data-stu-id="58951-113">SSERRORINFO structure members are interpreted by the consumer as follows.</span></span>  
  
|<span data-ttu-id="58951-114">成員</span><span class="sxs-lookup"><span data-stu-id="58951-114">Member</span></span>|<span data-ttu-id="58951-115">描述</span><span class="sxs-lookup"><span data-stu-id="58951-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="58951-116">*pwszMessage*</span><span class="sxs-lookup"><span data-stu-id="58951-116">*pwszMessage*</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58951-117">錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="58951-117">error message.</span></span> <span data-ttu-id="58951-118">與 **IErrorInfo::GetDescription** 中傳回的字串相同。</span><span class="sxs-lookup"><span data-stu-id="58951-118">Identical to the string returned in **IErrorInfo::GetDescription**.</span></span>|  
|<span data-ttu-id="58951-119">*pwszServer*</span><span class="sxs-lookup"><span data-stu-id="58951-119">*pwszServer*</span></span>|<span data-ttu-id="58951-120">工作階段的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="58951-120">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the session.</span></span>|  
|<span data-ttu-id="58951-121">*pwszProcedure*</span><span class="sxs-lookup"><span data-stu-id="58951-121">*pwszProcedure*</span></span>|<span data-ttu-id="58951-122">如果適用，則為發生錯誤之程序的名稱，</span><span class="sxs-lookup"><span data-stu-id="58951-122">If appropriate, the name of the procedure in which the error originated.</span></span> <span data-ttu-id="58951-123">否則便為空字串。</span><span class="sxs-lookup"><span data-stu-id="58951-123">An empty string otherwise.</span></span>|  
|<span data-ttu-id="58951-124">*lNative*</span><span class="sxs-lookup"><span data-stu-id="58951-124">*lNative*</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58951-125">原生錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="58951-125">native error number.</span></span> <span data-ttu-id="58951-126">與 **ISQLErrorInfo::GetSQLInfo** 的 *plNativeError* 參數中所傳回的值相同。</span><span class="sxs-lookup"><span data-stu-id="58951-126">Identical to the value returned in the *plNativeError* parameter of **ISQLErrorInfo::GetSQLInfo**.</span></span>|  
|<span data-ttu-id="58951-127">*bState*</span><span class="sxs-lookup"><span data-stu-id="58951-127">*bState*</span></span>|<span data-ttu-id="58951-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤訊息的狀態。</span><span class="sxs-lookup"><span data-stu-id="58951-128">State of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error message.</span></span>|  
|<span data-ttu-id="58951-129">*bClass*</span><span class="sxs-lookup"><span data-stu-id="58951-129">*bClass*</span></span>|<span data-ttu-id="58951-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤訊息的嚴重性。</span><span class="sxs-lookup"><span data-stu-id="58951-130">Severity of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error message.</span></span>|  
|<span data-ttu-id="58951-131">*wLineNumber*</span><span class="sxs-lookup"><span data-stu-id="58951-131">*wLineNumber*</span></span>|<span data-ttu-id="58951-132">在適用時，這是發生錯誤之預存程序的行號。</span><span class="sxs-lookup"><span data-stu-id="58951-132">When applicable, the line number of a stored procedure on which the error occurred.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58951-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58951-133">See Also</span></span>  
 <span data-ttu-id="58951-134">[出錯](errors.md) </span><span class="sxs-lookup"><span data-stu-id="58951-134">[Errors](errors.md) </span></span>  
 [<span data-ttu-id="58951-135">RAISERROR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="58951-135">RAISERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
