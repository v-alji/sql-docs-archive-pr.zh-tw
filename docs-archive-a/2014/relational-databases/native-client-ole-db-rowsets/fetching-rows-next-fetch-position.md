---
title: 下一個擷取位置 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
author: rothja
ms.author: jroth
ms.openlocfilehash: fcc771eef4acf603148bc4b4318e810b1bd72302
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687829"
---
# <a name="next-fetch-position"></a><span data-ttu-id="55a5e-102">下一個提取位置</span><span class="sxs-lookup"><span data-stu-id="55a5e-102">Next Fetch Position</span></span>
  <span data-ttu-id="55a5e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會持續追蹤下一個提取位置，讓**GetNextRows** (方法的一系列呼叫不會略過、方向變更，或**FindNextRow**、**搜尋**或**RestartPosition**方法的仲介呼叫) 讀取整個資料列集，而不會略過或重複任何資料列。</span><span class="sxs-lookup"><span data-stu-id="55a5e-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider keeps track of the next fetch position so that a sequence of calls to the **GetNextRows** method (without skips, changes of direction, or intervening calls to the **FindNextRow**, **Seek**, or **RestartPosition** methods) reads the whole rowset without skipping or repeating any row.</span></span> <span data-ttu-id="55a5e-104">下一個提取位置的變更方式為：呼叫 **IRowset::GetNextRows**、**IRowset::RestartPosition** 或 **IRowsetIndex::Seek**，或者呼叫包含 Null *pBookmark* 值的 **FindNextRow**。</span><span class="sxs-lookup"><span data-stu-id="55a5e-104">The next fetch position is changed either by calling **IRowset::GetNextRows**, **IRowset::RestartPosition**, or **IRowsetIndex::Seek**, or by calling **FindNextRow** with a null *pBookmark* value.</span></span> <span data-ttu-id="55a5e-105">呼叫包含非 Null *pBookmark* 值的 **FindNextRow** 不會影響下一個提取位置。</span><span class="sxs-lookup"><span data-stu-id="55a5e-105">Calling **FindNextRow** with a nonnull *pBookmark* value does not affect the next fetch position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55a5e-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55a5e-106">See Also</span></span>  
 [<span data-ttu-id="55a5e-107">擷取資料列</span><span class="sxs-lookup"><span data-stu-id="55a5e-107">Fetching Rows</span></span>](fetching-rows.md)  
  
  
