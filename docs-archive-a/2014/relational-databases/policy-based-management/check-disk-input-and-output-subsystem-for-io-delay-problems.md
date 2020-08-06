---
title: 檢查磁碟輸入輸出子系統的 IO 延遲問題 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 23863340-d8e0-48d6-928b-462745885d37
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a0ae8dc0d1a93f8150ccbeab73ed8aa918d1f495
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699475"
---
# <a name="check-disk-input-and-output-subsystem-for-io-delay-problems"></a><span data-ttu-id="679ec-102">檢查磁碟輸入輸出子系統的 IO 延遲問題</span><span class="sxs-lookup"><span data-stu-id="679ec-102">Check Disk Input and Output Subsystem for IO Delay Problems</span></span>
  <span data-ttu-id="679ec-103">這個規則會檢查事件記錄檔中是否有錯誤訊息 833。</span><span class="sxs-lookup"><span data-stu-id="679ec-103">This rule checks the event log for error message 833.</span></span> <span data-ttu-id="679ec-104">此訊息表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已經從磁碟發出讀取或寫入要求，且該要求花費超過 15 秒才傳回。</span><span class="sxs-lookup"><span data-stu-id="679ec-104">This message indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has issued a read or write request from disk, and that the request has taken longer than 15 seconds to return.</span></span> <span data-ttu-id="679ec-105">此錯誤是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 回報，並且表示磁碟 I/O 子系統發生問題。</span><span class="sxs-lookup"><span data-stu-id="679ec-105">This error is reported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and indicates a problem with the disk I/O subsystem.</span></span> <span data-ttu-id="679ec-106">延遲這麼長的時間會嚴重損害 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境的效能。</span><span class="sxs-lookup"><span data-stu-id="679ec-106">Delays this long can severely damage the performance of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environment.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="679ec-107">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="679ec-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="679ec-108">查看系統事件記錄檔中是否有與硬體相關的錯誤訊息，以便對此錯誤進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="679ec-108">Troubleshoot this error by examining the system event log for hardware-related error messages.</span></span> <span data-ttu-id="679ec-109">同時，也查看硬體特定的記錄檔 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="679ec-109">Also, examine hardware-specific logs if they are available.</span></span>  
  
 <span data-ttu-id="679ec-110">使用「效能監視器」檢查下列計數器︰</span><span class="sxs-lookup"><span data-stu-id="679ec-110">Use Performance Monitor to examine the following counters:</span></span>  
  
-   <span data-ttu-id="679ec-111">Average Disk Sec/Transfer</span><span class="sxs-lookup"><span data-stu-id="679ec-111">Average Disk Sec/Transfer</span></span>  
  
-   <span data-ttu-id="679ec-112">Average Disk Queue Length</span><span class="sxs-lookup"><span data-stu-id="679ec-112">Average Disk Queue Length</span></span>  
  
-   <span data-ttu-id="679ec-113">Current Disk Queue Length</span><span class="sxs-lookup"><span data-stu-id="679ec-113">Current Disk Queue Length</span></span>  
  
 <span data-ttu-id="679ec-114">例如，在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的電腦上，Average Disk Sec/Transfer 時間通常少於 15 毫秒。</span><span class="sxs-lookup"><span data-stu-id="679ec-114">For example, the Average Disk Sec/Transfer time on a computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is typically less than 15 milliseconds.</span></span> <span data-ttu-id="679ec-115">如果 Average Disk Sec/Transfer 值增加，表示磁碟 I/O 子系統並未以最佳的方式應付 I/O 需要。</span><span class="sxs-lookup"><span data-stu-id="679ec-115">If the Average Disk Sec/Transfer value increases, this indicates that the disk I/O subsystem is not optimally keeping up with the I/O demand.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="679ec-116">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="679ec-116">For More Information</span></span>  
 [<span data-ttu-id="679ec-117">MSSQLSERVER_833</span><span class="sxs-lookup"><span data-stu-id="679ec-117">MSSQLSERVER_833</span></span>](../errors-events/mssqlserver-833-database-engine-error.md)  
  
 [<span data-ttu-id="679ec-118">Microsoft 知識庫文章 897284</span><span class="sxs-lookup"><span data-stu-id="679ec-118">Microsoft Knowledge Base article 897284</span></span>](https://go.microsoft.com/fwlink/?linkid=117743)  
  
 <span data-ttu-id="679ec-119">[SQL Server I/O 基本概念，第 2 章](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="679ec-119">[SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span></span>  
  
  
