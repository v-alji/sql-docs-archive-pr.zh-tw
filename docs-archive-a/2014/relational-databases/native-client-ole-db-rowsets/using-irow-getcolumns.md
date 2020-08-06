---
title: 使用 IRow::GetColumns | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
author: rothja
ms.author: jroth
ms.openlocfilehash: f323dda790946565bc0dbd63c9e1f9d17ac7494b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593369"
---
# <a name="using-irowgetcolumns"></a><span data-ttu-id="439c0-102">使用 IRow::GetColumns</span><span class="sxs-lookup"><span data-stu-id="439c0-102">Using IRow::GetColumns</span></span>
  <span data-ttu-id="439c0-103">**IRow** 實作可允許以順向循序方式存取資料行。</span><span class="sxs-lookup"><span data-stu-id="439c0-103">The **IRow** implementation allows forward-only sequential access to the columns.</span></span> <span data-ttu-id="439c0-104">每次當您存取資料列中的數個資料行時，可以使用 **IRow::GetColumns** 的單一呼叫或是呼叫 **IRow::GetColumns** 多次來存取資料列中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="439c0-104">You can either access all the columns in the row with a single call to **IRow::GetColumns** or call **IRow::GetColumns** multiple times every time that you access several columns in the row.</span></span>  
  
 <span data-ttu-id="439c0-105">**IRow::GetColumns** 的多次呼叫不應該重疊。</span><span class="sxs-lookup"><span data-stu-id="439c0-105">The multiple calls to **IRow::GetColumns** should not overlap.</span></span> <span data-ttu-id="439c0-106">例如，如果初次呼叫 **IRow::GetColumns** 會擷取資料行 1、2 和 3，則第二次呼叫 **IRow::GetColumns** 就應該擷取資料行 4、5 和 6。</span><span class="sxs-lookup"><span data-stu-id="439c0-106">For example, if the first call to **IRow::GetColumns** retrieves columns 1, 2, and 3, the second call to **IRow::GetColumns** should call for columns 4, 5, and 6.</span></span> <span data-ttu-id="439c0-107">如果之後的 **IRow::GetColumns** 呼叫重疊，則狀態旗標 (DBCOLUMNACCESS 中的 dwstatus 欄位) 會設定為 DBSTATUS_E_UNAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="439c0-107">If later calls to **IRow::GetColumns** overlap, the status flag (dwstatus field in DBCOLUMNACCESS) is set to DBSTATUS_E_UNAVAILABLE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="439c0-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="439c0-108">See Also</span></span>  
 [<span data-ttu-id="439c0-109">使用 IRow 來提取單一資料列</span><span class="sxs-lookup"><span data-stu-id="439c0-109">Fetching a Single Row with IRow</span></span>](fetching-a-single-row-with-irow.md)  
  
  
