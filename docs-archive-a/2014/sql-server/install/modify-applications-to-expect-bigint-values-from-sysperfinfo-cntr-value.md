---
title: 修改應用程式，以預期來自 sysperfinfo 的 Bigint 值。 cntr_value |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 108a9b981debc95e182b16847c39a03d4b242088
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708057"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntr_value"></a><span data-ttu-id="ff835-102">修改應用程式以接受來自 sysperfinfo.cntr_value 的 bigint 值</span><span class="sxs-lookup"><span data-stu-id="ff835-102">Modify applications to expect bigint values from sysperfinfo.cntr_value</span></span>
  <span data-ttu-id="ff835-103">sysperfinfo 會傳回 `bigint` cntr_value 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="ff835-103">sysperfinfo returns a `bigint` value for the cntr_value column.</span></span>  
  
## <a name="component"></a><span data-ttu-id="ff835-104">元件</span><span class="sxs-lookup"><span data-stu-id="ff835-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="ff835-105">更正動作</span><span class="sxs-lookup"><span data-stu-id="ff835-105">Corrective Action</span></span>  
 <span data-ttu-id="ff835-106">請修改使用 sysperfinfo 的應用程式，以確保它們能夠處理 cntr_value 資料行的 `bigint` 值。</span><span class="sxs-lookup"><span data-stu-id="ff835-106">Modify applications that use sysperfinfo to ensure that they can handle the `bigint` values of the cntr_value column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ff835-107">sysperfinfo 是相容性檢視。</span><span class="sxs-lookup"><span data-stu-id="ff835-107">sysperfinfo is a compatibility view.</span></span> <span data-ttu-id="ff835-108">您應該改用 sys.dm_os_performance_counter 動態管理檢視。</span><span class="sxs-lookup"><span data-stu-id="ff835-108">You should use the sys.dm_os_performance_counter dynamic management view instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff835-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff835-109">See Also</span></span>  
 <span data-ttu-id="ff835-110">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="ff835-110">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="ff835-111">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="ff835-111">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
