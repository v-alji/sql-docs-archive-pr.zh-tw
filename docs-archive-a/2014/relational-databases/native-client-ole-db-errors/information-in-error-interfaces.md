---
title: 錯誤介面中的資訊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
ms.assetid: 4620f03f-1193-43e7-ba19-ad022737d300
author: rothja
ms.author: jroth
ms.openlocfilehash: e9859ccbd804ba15685d84b98cbe74d4b096d98c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598845"
---
# <a name="information-in-error-interfaces"></a><span data-ttu-id="e8e11-102">錯誤介面中的資訊</span><span class="sxs-lookup"><span data-stu-id="e8e11-102">Information in Error Interfaces</span></span>
  <span data-ttu-id="e8e11-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會在 OLE DB 定義的錯誤介面**IErrorInfo**、 **IErrorRecords**和**ISQLErrorInfo**中，報告一些錯誤和狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="e8e11-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider reports some error and status information in the OLE DB-defined error interfaces **IErrorInfo**, **IErrorRecords**, and **ISQLErrorInfo**.</span></span>  
  
 <span data-ttu-id="e8e11-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者支援**IErrorInfo**成員函式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="e8e11-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **IErrorInfo** member functions as follows.</span></span>  
  
|<span data-ttu-id="e8e11-105">成員函數</span><span class="sxs-lookup"><span data-stu-id="e8e11-105">Member function</span></span>|<span data-ttu-id="e8e11-106">描述</span><span class="sxs-lookup"><span data-stu-id="e8e11-106">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="e8e11-107">**GetDescription**</span><span class="sxs-lookup"><span data-stu-id="e8e11-107">**GetDescription**</span></span>|<span data-ttu-id="e8e11-108">描述性的錯誤訊息字串。</span><span class="sxs-lookup"><span data-stu-id="e8e11-108">Descriptive error message string.</span></span>|  
|<span data-ttu-id="e8e11-109">**GetGUID**</span><span class="sxs-lookup"><span data-stu-id="e8e11-109">**GetGUID**</span></span>|<span data-ttu-id="e8e11-110">定義錯誤之介面的 GUID。</span><span class="sxs-lookup"><span data-stu-id="e8e11-110">GUID of the interface that defined the error.</span></span>|  
|<span data-ttu-id="e8e11-111">**GetHelpContext**</span><span class="sxs-lookup"><span data-stu-id="e8e11-111">**GetHelpContext**</span></span>|<span data-ttu-id="e8e11-112">不支援。</span><span class="sxs-lookup"><span data-stu-id="e8e11-112">Not supported.</span></span> <span data-ttu-id="e8e11-113">永遠傳回零。</span><span class="sxs-lookup"><span data-stu-id="e8e11-113">Always returns zero.</span></span>|  
|<span data-ttu-id="e8e11-114">**GetHelpFile**</span><span class="sxs-lookup"><span data-stu-id="e8e11-114">**GetHelpFile**</span></span>|<span data-ttu-id="e8e11-115">不支援。</span><span class="sxs-lookup"><span data-stu-id="e8e11-115">Not supported.</span></span> <span data-ttu-id="e8e11-116">一律傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="e8e11-116">Always returns NULL.</span></span>|  
|<span data-ttu-id="e8e11-117">**GetSource**</span><span class="sxs-lookup"><span data-stu-id="e8e11-117">**GetSource**</span></span>|<span data-ttu-id="e8e11-118">字串 "Microsoft SQL Server Native Client"。</span><span class="sxs-lookup"><span data-stu-id="e8e11-118">String "Microsoft SQL Server Native Client".</span></span>|  
  
 <span data-ttu-id="e8e11-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者支援取用者可用的**IErrorRecords**成員函式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="e8e11-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports consumer-available **IErrorRecords** member functions as follows.</span></span>  
  
|<span data-ttu-id="e8e11-120">成員函數</span><span class="sxs-lookup"><span data-stu-id="e8e11-120">Member function</span></span>|<span data-ttu-id="e8e11-121">描述</span><span class="sxs-lookup"><span data-stu-id="e8e11-121">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="e8e11-122">**GetBasicErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="e8e11-122">**GetBasicErrorInfo**</span></span>|<span data-ttu-id="e8e11-123">以有關錯誤的基本資訊填入 ERRORINFO 結構。</span><span class="sxs-lookup"><span data-stu-id="e8e11-123">Fills an ERRORINFO structure with basic information about an error.</span></span> <span data-ttu-id="e8e11-124">ERRORINFO 結構所包含的成員會識別錯誤的 HRESULT 傳回值，以及該錯誤適用的提供者和介面。</span><span class="sxs-lookup"><span data-stu-id="e8e11-124">An ERRORINFO structure contains members that identify the HRESULT return value for the error, and the provider and interface to which the error applies.</span></span>|  
|<span data-ttu-id="e8e11-125">**GetCustomErrorObject**</span><span class="sxs-lookup"><span data-stu-id="e8e11-125">**GetCustomErrorObject**</span></span>|<span data-ttu-id="e8e11-126">在 **ISQLErrorInfo** 和 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 介面上傳回參考。</span><span class="sxs-lookup"><span data-stu-id="e8e11-126">Returns a reference on interfaces **ISQLErrorInfo,** and [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md).</span></span>|  
|<span data-ttu-id="e8e11-127">**GetErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="e8e11-127">**GetErrorInfo**</span></span>|<span data-ttu-id="e8e11-128">在 **IErrorInfo** 介面上傳回參考。</span><span class="sxs-lookup"><span data-stu-id="e8e11-128">Returns a reference on an **IErrorInfo** interface.</span></span>|  
|<span data-ttu-id="e8e11-129">**GetErrorParameters**</span><span class="sxs-lookup"><span data-stu-id="e8e11-129">**GetErrorParameters**</span></span>|<span data-ttu-id="e8e11-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者不會透過**GetErrorParameters**將參數傳回給取用者。</span><span class="sxs-lookup"><span data-stu-id="e8e11-130">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not return parameters to the consumer through **GetErrorParameters**.</span></span>|  
|<span data-ttu-id="e8e11-131">**GetRecordCount**</span><span class="sxs-lookup"><span data-stu-id="e8e11-131">**GetRecordCount**</span></span>|<span data-ttu-id="e8e11-132">可用錯誤記錄的計數。</span><span class="sxs-lookup"><span data-stu-id="e8e11-132">Count of error records available.</span></span>|  
  
 <span data-ttu-id="e8e11-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者支援**ISQLErrorInfo：： GetSQLInfo**參數，如下所示。</span><span class="sxs-lookup"><span data-stu-id="e8e11-133">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **ISQLErrorInfo::GetSQLInfo** parameters as follows.</span></span>  
  
|<span data-ttu-id="e8e11-134">參數</span><span class="sxs-lookup"><span data-stu-id="e8e11-134">Parameter</span></span>|<span data-ttu-id="e8e11-135">描述</span><span class="sxs-lookup"><span data-stu-id="e8e11-135">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8e11-136">*pbstrSQLState*</span><span class="sxs-lookup"><span data-stu-id="e8e11-136">*pbstrSQLState*</span></span>|<span data-ttu-id="e8e11-137">為錯誤傳回 SQLSTATE 值。</span><span class="sxs-lookup"><span data-stu-id="e8e11-137">Returns a SQLSTATE value for the error.</span></span> <span data-ttu-id="e8e11-138">SQLSTATE 值定義於 SQL-92、ODBC 和 ISO SQL，以及 API 規格中。</span><span class="sxs-lookup"><span data-stu-id="e8e11-138">SQLSTATE values are defined in the SQL-92, ODBC and ISO SQL, and API specifications.</span></span> <span data-ttu-id="e8e11-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 都不 OLE DB 提供者定義的執行特定 SQLSTATE 值。</span><span class="sxs-lookup"><span data-stu-id="e8e11-139">Neither [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nor the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defined implementation-specific SQLSTATE values.</span></span>|  
|<span data-ttu-id="e8e11-140">*plNativeError*</span><span class="sxs-lookup"><span data-stu-id="e8e11-140">*plNativeError*</span></span>|<span data-ttu-id="e8e11-141">從 **master.dbo.sysmessages** 傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤號碼 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="e8e11-141">Returns the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error number from **master.dbo.sysmessages** when available.</span></span> <span data-ttu-id="e8e11-142">成功初始化 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者資料來源之後，就可以使用原生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e8e11-142">Native errors are available after a successful attempt to initialize a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source.</span></span> <span data-ttu-id="e8e11-143">在嘗試之前， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者一律會傳回零。</span><span class="sxs-lookup"><span data-stu-id="e8e11-143">Prior to the attempt, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider always returns zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8e11-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8e11-144">See Also</span></span>  
 [<span data-ttu-id="e8e11-145">錯誤</span><span class="sxs-lookup"><span data-stu-id="e8e11-145">Errors</span></span>](errors.md)  
  
  
