---
title: 設定平行處理原則的最大程度選項來取得最佳效能 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3043a656cbe1ac1ec40f0d0a67b6eac057005af4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708209"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a><span data-ttu-id="9a82a-102">設定平行處理原則的最大程度選項來取得最佳效能</span><span class="sxs-lookup"><span data-stu-id="9a82a-102">Set the Max Degree of Parallelism Option for Optimal Performance</span></span>
  <span data-ttu-id="9a82a-103">此規則會判斷某個值的 max degree of parallelism (MAXDOP) 選項是否大於 8。</span><span class="sxs-lookup"><span data-stu-id="9a82a-103">This rule determines whether the max degree of parallelism (MAXDOP) option for a value greater than 8.</span></span> <span data-ttu-id="9a82a-104">將這個選項設定為較大的值通常會造成不必要的資源耗用，而且會降低效能。</span><span class="sxs-lookup"><span data-stu-id="9a82a-104">Setting this option to a larger value often causes unwanted resource consumption and performance degradation.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="9a82a-105">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="9a82a-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="9a82a-106">使用 sp_configure 將 max degree of parallelism 選項設定為 8。</span><span class="sxs-lookup"><span data-stu-id="9a82a-106">Set the max degree of parallelism option to 8 or less by using sp_configure.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="9a82a-107">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="9a82a-107">For More Information</span></span>  
 [<span data-ttu-id="9a82a-108">Microsoft 知識庫文章 329204</span><span class="sxs-lookup"><span data-stu-id="9a82a-108">Microsoft Knowledge Base article 329204</span></span>](https://go.microsoft.com/fwlink/?linkid=117786)  
  
 [<span data-ttu-id="9a82a-109">設定 max degree of parallelism 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="9a82a-109">Configure the max degree of parallelism Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [<span data-ttu-id="9a82a-110">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9a82a-110">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
