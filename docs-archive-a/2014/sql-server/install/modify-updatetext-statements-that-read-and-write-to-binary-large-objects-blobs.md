---
title: 修改讀取和寫入二進位大型物件 (Blob) 的 UPDATETEXT 語句 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 061e7bad0bae5a74d103406265ad79195f79f7db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595472"
---
# <a name="modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs"></a><span data-ttu-id="1ec5c-102">修改讀取和寫入二進位大型物件 (BLOB) 的 UPDATETEXT 陳述式</span><span class="sxs-lookup"><span data-stu-id="1ec5c-102">Modify UPDATETEXT statements that read and write to binary large objects (BLOBs)</span></span>
  <span data-ttu-id="1ec5c-103">Upgrade Advisor 偵測到使用相同文字指標來讀取和寫入相同二進位大型物件區塊 (BLOB) 的 UPDATETEXT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-103">Upgrade Advisor detected UPDATETEXT statements that read and write to the same binary large objects (BLOB) by using the same text pointer.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="1ec5c-104">不支援這樣使用文字指標。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-104">does not support the use of text pointers in this manner.</span></span>  
  
## <a name="component"></a><span data-ttu-id="1ec5c-105">元件</span><span class="sxs-lookup"><span data-stu-id="1ec5c-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="1ec5c-106">更正動作</span><span class="sxs-lookup"><span data-stu-id="1ec5c-106">Corrective Action</span></span>  
 <span data-ttu-id="1ec5c-107">將 BLOB 複製至暫存資料表或資料表變數，然後將值指派回原始資料行。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-107">Copy the BLOB to a temporary table or to a table variable, and then assign the value back to the original column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec5c-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ec5c-108">See Also</span></span>  
 <span data-ttu-id="1ec5c-109">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="1ec5c-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="1ec5c-110">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="1ec5c-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
