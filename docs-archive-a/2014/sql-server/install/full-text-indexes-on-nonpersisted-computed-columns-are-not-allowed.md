---
title: 不允許計算資料行非保存上的全文檢索索引 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: cba737f7-b187-47d0-8458-23dc18d18aca
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: de153d45e2f652bfea6e9dce68428af84be68b6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607245"
---
# <a name="full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed"></a><span data-ttu-id="93aab-102">不允許在非保存的計算資料行上使用全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="93aab-102">Full-text indexes on nonpersisted, computed columns are not allowed</span></span>
  <span data-ttu-id="93aab-103">您不可在不具決定性且不精確的計算資料行上建立全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="93aab-103">You cannot create full-text indexes on nondeterministic and imprecise computed columns.</span></span> <span data-ttu-id="93aab-104">這樣的資料行無法做為類型資料行或全文檢索索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="93aab-104">Such columns cannot be used as type columns or as full-text key columns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="93aab-105">描述</span><span class="sxs-lookup"><span data-stu-id="93aab-105">Description</span></span>  
 <span data-ttu-id="93aab-106">在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中，您可以使用不具決定性且不精確的計算資料行當做類型資料行或全文檢索索引鍵資料行，建立全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="93aab-106">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], a full-text index can be created by using a nondeterministic and imprecise computed column as the type column or the full-text key column.</span></span> <span data-ttu-id="93aab-107">但是，目前已不支援這項功能。</span><span class="sxs-lookup"><span data-stu-id="93aab-107">This functionality is not supported.</span></span> <span data-ttu-id="93aab-108">當您升級時，系統會停用較舊、不相容和不支援的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="93aab-108">When you upgrade, older, incompatible, and unsupported full-text indexes are disabled.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="93aab-109">更正動作</span><span class="sxs-lookup"><span data-stu-id="93aab-109">Corrective Action</span></span>  
 <span data-ttu-id="93aab-110">若要啟用這些全文檢索索引，請修改資料行定義，讓這些資料行具決定性且精確。</span><span class="sxs-lookup"><span data-stu-id="93aab-110">To enable these full-text indexes, modify the column definitions so that the columns are deterministic and precise.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93aab-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93aab-111">See Also</span></span>  
 [<span data-ttu-id="93aab-112">使用升級建議程式</span><span class="sxs-lookup"><span data-stu-id="93aab-112">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
