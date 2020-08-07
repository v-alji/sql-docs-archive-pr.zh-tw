---
title: SERVERPROPERTY 會針對 SQL Server 2005 中的 LCID 屬性傳回正確的結果 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SERVERPROPERTY function
ms.assetid: 833a2fc9-b480-4697-aa7b-9677e78ee0b4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ebb125a86e6e30f2c3638004593da7657f02f1a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700624"
---
# <a name="serverproperty-returns-correct-result-for-lcid-property-in-sql-server-2005"></a><span data-ttu-id="d82d2-102">在 SQL Server 2005 中，SERVERPROPERTY 會傳回 LCID 屬性的正確結果</span><span class="sxs-lookup"><span data-stu-id="d82d2-102">SERVERPROPERTY returns correct result for LCID property in SQL Server 2005</span></span>
  <span data-ttu-id="d82d2-103">如果 SERVERPROPERTY('LCID') 是在二進位定序伺服器上執行，則此函數會傳回對應於伺服器定序的 Windows 地區設定識別碼 (LCID)。</span><span class="sxs-lookup"><span data-stu-id="d82d2-103">When SERVERPROPERTY('LCID') is run on binary collation servers, the function returns the Windows locale identifier (LCID) that corresponds to the collation of the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d82d2-104">對於包含 SERVERPROPERTY ('LCID') 的參考且在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之其他執行個體上執行的批次和追蹤檔案，只有在其他執行個體具有與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之目前執行個體相同的定序時，Upgrade Advisor 才會偵測此行為變更。</span><span class="sxs-lookup"><span data-stu-id="d82d2-104">For batch and trace files that contain references to SERVERPROPERTY ('LCID') and are run on other instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Upgrade Advisor will detect this behavior change only if the other instances have the same collation as the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="d82d2-105">更正動作</span><span class="sxs-lookup"><span data-stu-id="d82d2-105">Corrective Action</span></span>  
 <span data-ttu-id="d82d2-106">請修改應用程式以預期 SERVERPROPERTY('LCID') 會傳回對應至伺服器定序的 Windows LCID。</span><span class="sxs-lookup"><span data-stu-id="d82d2-106">Modify applications to expect SERVERPROPERTY('LCID') to return the Windows LCID that corresponds to the collation of the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82d2-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d82d2-107">See Also</span></span>  
 <span data-ttu-id="d82d2-108">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="d82d2-108">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="d82d2-109">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="d82d2-109">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
