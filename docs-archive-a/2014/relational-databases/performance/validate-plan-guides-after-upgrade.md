---
title: 升級之後驗證計畫指南 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], validating after upgrade
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18cc0f93ddec46025f659bcb9489bfff3ca846ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701062"
---
# <a name="validate-plan-guides-after-upgrade"></a><span data-ttu-id="83ef9-102">升級之後驗證計畫指南</span><span class="sxs-lookup"><span data-stu-id="83ef9-102">Validate Plan Guides After Upgrade</span></span>
  <span data-ttu-id="83ef9-103">建議您將應用程式升級為新版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]時，重新評估和測試計畫指南定義。</span><span class="sxs-lookup"><span data-stu-id="83ef9-103">We recommend re-evaluating and testing plan guide definitions when you upgrade your application to a new release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="83ef9-104">效能微調需求和計畫指南符合的行為有可能會變更。</span><span class="sxs-lookup"><span data-stu-id="83ef9-104">Performance tuning requirements and plan guide matching behavior may change.</span></span> <span data-ttu-id="83ef9-105">雖然無效的計畫指南不會導致查詢失敗，但是系統將不會使用此計畫指南來編譯計畫，而且此計畫可能不是最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="83ef9-105">Although an invalid plan guide will not cause a query to fail, the plan is compiled without using the plan guide and may not be the best choice.</span></span> <span data-ttu-id="83ef9-106">將資料庫升級為 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]之後，我們建議您執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="83ef9-106">After upgrading a database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="83ef9-107">使用 [sys.fn_validate_plan_guide](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql) 函數來驗證現有的計畫指南。</span><span class="sxs-lookup"><span data-stu-id="83ef9-107">Validate existing plan guides by using the [sys.fn_validate_plan_guide](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql) function.</span></span>  
  
-   <span data-ttu-id="83ef9-108">使用擴充事件，透過 [Plan Guide Unsuccessful](../event-classes/plan-guide-unsuccessful-event-class.md) 事件，在一段時間內監視是否有誤導的計畫。</span><span class="sxs-lookup"><span data-stu-id="83ef9-108">Use extended events to monitor for misguided plans for some period of time by using the [Plan Guide Unsuccessful](../event-classes/plan-guide-unsuccessful-event-class.md) event.</span></span>  
  
  
