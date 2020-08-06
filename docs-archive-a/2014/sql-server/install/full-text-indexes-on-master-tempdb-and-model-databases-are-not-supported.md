---
title: 不支援 master、tempdb 和 model 資料庫的全文檢索索引 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fbd5e3133ed87fed9bdaf6d668df62c6471df766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607246"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a><span data-ttu-id="075f7-102">不支援 master、tempdb 和 model 資料庫的全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="075f7-102">Full-text indexes on master, tempdb and model databases are not supported</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="075f7-103">不允許在任何系統資料庫上使用全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="075f7-103">does not allow full-text indexes on any system database.</span></span>  
  
## <a name="description"></a><span data-ttu-id="075f7-104">描述</span><span class="sxs-lookup"><span data-stu-id="075f7-104">Description</span></span>  
 <span data-ttu-id="075f7-105">在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中，master、tempdb 和 model 資料庫都支援全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="075f7-105">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], full-text indexes were supported on the master, tempdb, and model databases.</span></span>  
  
 <span data-ttu-id="075f7-106">在升級期間，master、tempdb 和 model 資料庫中的任何全文檢索目錄都會移除。</span><span class="sxs-lookup"><span data-stu-id="075f7-106">Any full-text catalogs in the master, tempdb, and model databases are removed during the upgrade.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="075f7-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="075f7-107">See Also</span></span>  
 [<span data-ttu-id="075f7-108">使用升級建議程式</span><span class="sxs-lookup"><span data-stu-id="075f7-108">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
