---
title: 非預期的系統失敗 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b791ba0e3f709288a4e2c5b6add4e74e15d56dee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593990"
---
# <a name="unexpected-system-failures"></a><span data-ttu-id="9471c-102">非預期的系統失敗</span><span class="sxs-lookup"><span data-stu-id="9471c-102">Unexpected System Failures</span></span>
  <span data-ttu-id="9471c-103">這個規則會檢查電腦事件記錄檔中是否有 SYSTEM 事件 6008。</span><span class="sxs-lookup"><span data-stu-id="9471c-103">This rule checks for SYSTEM Event 6008 in the computer event log.</span></span> <span data-ttu-id="9471c-104">此事件表示非預期的系統關機。</span><span class="sxs-lookup"><span data-stu-id="9471c-104">This event indicates an unexpected system shutdown.</span></span> <span data-ttu-id="9471c-105">系統可能不穩定，而且可能無法提供主控 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體所需的穩定性和完整性。</span><span class="sxs-lookup"><span data-stu-id="9471c-105">The system might be unstable and might not provide the stability and integrity that is required to host an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="9471c-106">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="9471c-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="9471c-107">立即找出非預期伺服器重新啟動的原因，或是將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體移到另一部電腦。</span><span class="sxs-lookup"><span data-stu-id="9471c-107">Immediately address the cause of the unexpected server restarts, or move the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to another computer.</span></span>  
  
  
