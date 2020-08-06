---
title: SqlTriggerCoNtext 物件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlTriggerContext object
- triggers [CLR integration]
- context [CLR integration]
ms.assetid: 472a2d0b-64ae-4877-8f11-a5620aa698b7
author: rothja
ms.author: jroth
ms.openlocfilehash: f7eae3d290a70bedee0ed9badf9e6d0503caa2bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709670"
---
# <a name="sqltriggercontext-object"></a><span data-ttu-id="f833b-102">SqlTriggerContext 物件</span><span class="sxs-lookup"><span data-stu-id="f833b-102">SqlTriggerContext Object</span></span>
  <span data-ttu-id="f833b-103">`SqlTriggerContext` 類別會提供觸發程序的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="f833b-103">The `SqlTriggerContext` class provides context information about the trigger.</span></span> <span data-ttu-id="f833b-104">此內容相關資訊包括會造成引發觸發程序的動作類型 (已在 UPDATE 作業中修改其資料行)，而且若是資料定義語言 (DDL) 觸發程序，則包括描述觸發作業的 XML `EventData` 結構。</span><span class="sxs-lookup"><span data-stu-id="f833b-104">This contextual information includes the type of action that caused the trigger to fire, which columns were modified in an UPDATE operation, and, in the case of a data definition language (DDL) trigger, an XML `EventData` structure that describes the triggering operation.</span></span> <span data-ttu-id="f833b-105">如需如何使用類別的詳細資訊和範例 `SqlTriggerContext` ，請參閱[CLR 觸發](../../database-engine/dev-guide/clr-triggers.md)程式。</span><span class="sxs-lookup"><span data-stu-id="f833b-105">For more information and examples of how to use the `SqlTriggerContext` class, see [CLR Triggers](../../database-engine/dev-guide/clr-triggers.md).</span></span>  
  
 <span data-ttu-id="f833b-106">如需詳細資訊，請參閱 .NET Framework SDK 文件集中的 `Microsoft.SqlServer.Server.SqlTriggerContext` 類別參考文件集。</span><span class="sxs-lookup"><span data-stu-id="f833b-106">For more information, see the `Microsoft.SqlServer.Server.SqlTriggerContext` class reference documentation in the .NET Framework SDK documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f833b-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f833b-107">See Also</span></span>  
 <span data-ttu-id="f833b-108">[CLR 觸發程式](../../database-engine/dev-guide/clr-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="f833b-108">[CLR Triggers](../../database-engine/dev-guide/clr-triggers.md) </span></span>  
 [<span data-ttu-id="f833b-109">EVENTDATA &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f833b-109">EVENTDATA &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
