---
title: Sp_helptrigger 輸出中的新資料行可能會影響應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0b1f5e936843ed84a5c6b88e2f3685e7a4272bc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606016"
---
# <a name="new-column-in-output-of-sp_helptrigger-may-impact-applications"></a><span data-ttu-id="d7d4f-102">sp_helptrigger 輸出中的新資料行，可能會影響應用程式</span><span class="sxs-lookup"><span data-stu-id="d7d4f-102">New column in output of sp_helptrigger may impact applications</span></span>
  <span data-ttu-id="d7d4f-103">trigger_schemaias sp_helptrigger 系統預存程式所傳回之結果集中的最後一個資料行。</span><span class="sxs-lookup"><span data-stu-id="d7d4f-103">trigger_schemaias the last column in the result set returned by the sp_helptrigger system stored procedure.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="d7d4f-104">若要取得針對特定資料表定義之觸發程序的相關資訊，請查詢 sys.triggers 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="d7d4f-104">To obtain information about triggers defined on a particular table, query the sys.triggers catalog view.</span></span>  
  
## <a name="component"></a><span data-ttu-id="d7d4f-105">元件</span><span class="sxs-lookup"><span data-stu-id="d7d4f-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="d7d4f-106">更正動作</span><span class="sxs-lookup"><span data-stu-id="d7d4f-106">Corrective Action</span></span>  
 <span data-ttu-id="d7d4f-107">請檢閱 sp_helptrigger 在應用程式中的使用方式。</span><span class="sxs-lookup"><span data-stu-id="d7d4f-107">Review the use of sp_helptrigger in applications.</span></span> <span data-ttu-id="d7d4f-108">您可能需要修改應用程式，以配合其他資料行。</span><span class="sxs-lookup"><span data-stu-id="d7d4f-108">You may need to modify your applications to accommodate the additional column.</span></span> <span data-ttu-id="d7d4f-109">或者，您也可以改用 sys.triggers 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="d7d4f-109">Alternatively, you can use the sys.triggers catalog view instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7d4f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7d4f-110">See Also</span></span>  
 <span data-ttu-id="d7d4f-111">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="d7d4f-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="d7d4f-112">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="d7d4f-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
