---
title: 回收 SQL Server Agent 錯誤記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2b30f0a2ba9a2d861d4a36a86489757cde512fea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606563"
---
# <a name="recycle-sql-server-agent-error-logs"></a><span data-ttu-id="b7bf6-102">回收 SQL Server Agent 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="b7bf6-102">Recycle SQL Server Agent Error Logs</span></span>
  <span data-ttu-id="b7bf6-103">使用此頁面來回收 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b7bf6-103">Use this page to recycle the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Error Logs.</span></span> <span data-ttu-id="b7bf6-104">回收記錄檔時會關閉目前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄檔，並在未重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務的情況下，啟動新的錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b7bf6-104">Recycling the log closes the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log and starts a new error log without restarting the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span> <span data-ttu-id="b7bf6-105">請注意， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會保留九個最新的錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b7bf6-105">Notice that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent maintains the nine most recent error logs.</span></span> <span data-ttu-id="b7bf6-106">如果已經有九個錯誤記錄檔存在，回收錯誤記錄檔會造成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 移除最舊的錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b7bf6-106">If there are already nine error logs present, recycling the error log causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to remove the oldest error log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7bf6-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7bf6-107">See Also</span></span>  
 [<span data-ttu-id="b7bf6-108">SQL Server Agent 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="b7bf6-108">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
