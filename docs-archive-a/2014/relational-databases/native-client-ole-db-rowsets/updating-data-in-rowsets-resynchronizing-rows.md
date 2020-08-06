---
title: 重新同步處理資料列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
ms.assetid: d2d30505-a878-4aa9-b821-53d8118a45a5
author: rothja
ms.author: jroth
ms.openlocfilehash: 47c628ae583f3e635f422d5146f64508372a1114
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593374"
---
# <a name="resynchronizing-rows"></a><span data-ttu-id="c9d97-102">重新同步處理資料列</span><span class="sxs-lookup"><span data-stu-id="c9d97-102">Resynchronizing Rows</span></span>
  <span data-ttu-id="c9d97-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者只支援資料指標支援的資料列集上的**IRowsetResynch** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c9d97-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **IRowsetResynch** on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursor-supported rowsets only.</span></span> <span data-ttu-id="c9d97-104">**IRowsetResynch** 無法視需要提供。</span><span class="sxs-lookup"><span data-stu-id="c9d97-104">**IRowsetResynch** is not available on demand.</span></span> <span data-ttu-id="c9d97-105">取用者必須在開啟資料列集前要求此介面。</span><span class="sxs-lookup"><span data-stu-id="c9d97-105">The consumer must request the interface before opening the rowset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d97-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9d97-106">See Also</span></span>  
 [<span data-ttu-id="c9d97-107">更新資料列集內的資料</span><span class="sxs-lookup"><span data-stu-id="c9d97-107">Updating Data in Rowsets</span></span>](updating-data-in-rowsets.md)  
  
  
