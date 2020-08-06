---
title: 更新資料列集中的資料 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, updating data
- SQL Server Native Client OLE DB provider, data updates
- data updates [SQL Server], OLE DB
ms.assetid: 37769b1c-c480-419a-8c54-5cc420bf73db
author: rothja
ms.author: jroth
ms.openlocfilehash: 993cfb67d4e6b72eec7cc0537e9b47371e94af10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702866"
---
# <a name="updating-data-in-rowsets"></a><span data-ttu-id="ada9d-102">更新資料列集中的資料</span><span class="sxs-lookup"><span data-stu-id="ada9d-102">Updating Data in Rowsets</span></span>
  <span data-ttu-id="ada9d-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 當取用者更新包含該資料的可修改資料列集時，Native Client OLE DB 提供者會更新資料。</span><span class="sxs-lookup"><span data-stu-id="ada9d-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider updates [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data when a consumer updates a modifiable rowset that contains that data.</span></span> <span data-ttu-id="ada9d-104">當取用者要求 **IRowsetChange** 或 **IRowsetUpdate** 介面的支援時，就會建立可修改的資料列集。</span><span class="sxs-lookup"><span data-stu-id="ada9d-104">A modifiable rowset is created when the consumer requests support for either the **IRowsetChange** or **IRowsetUpdate** interface.</span></span>  
  
 <span data-ttu-id="ada9d-105">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者可修改的資料列集使用資料 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指標來支援資料列集。</span><span class="sxs-lookup"><span data-stu-id="ada9d-105">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider-modifiable rowsets use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors to support the rowset.</span></span> <span data-ttu-id="ada9d-106">資料列集屬性 DBPROP_LOCKMODE 會改變資料指標中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並行控制行為，並且決定可更新資料列集中的資料列集資料列擷取以及資料完整性錯誤產生的行為。</span><span class="sxs-lookup"><span data-stu-id="ada9d-106">The rowset property DBPROP_LOCKMODE alters [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] concurrency control behavior in cursors and determines the behavior of rowset row fetching and data integrity error generation in updatable rowsets.</span></span>  
  
 <span data-ttu-id="ada9d-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者支援更新前後的資料列同步處理。</span><span class="sxs-lookup"><span data-stu-id="ada9d-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports row synchronization before or after an update.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ada9d-108">IRowChange::SetColumns 可用來設定資料列物件的一或多個具名資料行的值。</span><span class="sxs-lookup"><span data-stu-id="ada9d-108">IRowChange::SetColumns is available to set the values of one or more named columns of a row object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ada9d-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="ada9d-109">In This Section</span></span>  
  
-   [<span data-ttu-id="ada9d-110">更新 SQL Server 資料指標中的資料</span><span class="sxs-lookup"><span data-stu-id="ada9d-110">Updating Data in SQL Server Cursors</span></span>](updating-data-in-sql-server-cursors.md)  
  
-   [<span data-ttu-id="ada9d-111">重新同步處理資料列</span><span class="sxs-lookup"><span data-stu-id="ada9d-111">Resynchronizing Rows</span></span>](updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a><span data-ttu-id="ada9d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ada9d-112">See Also</span></span>  
 [<span data-ttu-id="ada9d-113">資料列集</span><span class="sxs-lookup"><span data-stu-id="ada9d-113">Rowsets</span></span>](rowsets.md)  
  
  
