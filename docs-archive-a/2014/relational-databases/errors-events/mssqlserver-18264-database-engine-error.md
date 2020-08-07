---
title: MSSQLSERVER_18264 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3edfeb82601e254c02df87cc4a978b9ab5e653e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597146"
---
# <a name="mssqlserver_18264"></a><span data-ttu-id="048f3-102">MSSQLSERVER_18264</span><span class="sxs-lookup"><span data-stu-id="048f3-102">MSSQLSERVER_18264</span></span>
    
## <a name="details"></a><span data-ttu-id="048f3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="048f3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="048f3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="048f3-104">Product Name</span></span>|<span data-ttu-id="048f3-105">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="048f3-105">Microsoft SQL Server</span></span>|  
|<span data-ttu-id="048f3-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="048f3-106">Event ID</span></span>|<span data-ttu-id="048f3-107">18264</span><span class="sxs-lookup"><span data-stu-id="048f3-107">18264</span></span>|  
|<span data-ttu-id="048f3-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="048f3-108">Event Source</span></span>|<span data-ttu-id="048f3-109">MSSQLENGINE</span><span class="sxs-lookup"><span data-stu-id="048f3-109">MSSQLENGINE</span></span>|  
|<span data-ttu-id="048f3-110">元件</span><span class="sxs-lookup"><span data-stu-id="048f3-110">Component</span></span>|<span data-ttu-id="048f3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="048f3-111">SQLEngine</span></span>|  
|<span data-ttu-id="048f3-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="048f3-112">Symbolic Name</span></span>|<span data-ttu-id="048f3-113">STRMIO_DBDUMP</span><span class="sxs-lookup"><span data-stu-id="048f3-113">STRMIO_DBDUMP</span></span>|  
|<span data-ttu-id="048f3-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="048f3-114">Message Text</span></span>|<span data-ttu-id="048f3-115">已備份的資料庫。</span><span class="sxs-lookup"><span data-stu-id="048f3-115">Database backed up.</span></span> <span data-ttu-id="048f3-116">資料庫: %s，建立日期(時間): %s(%s)，傾印的分頁: %d，第一個 LSN: %s，最後一個 LSN: %s，傾印裝置的數量: %d，裝置資訊: (%s)。</span><span class="sxs-lookup"><span data-stu-id="048f3-116">Database: %s, creation date(time): %s(%s), pages dumped: %d, first LSN: %s, last LSN: %s, number of dump devices: %d, device information: (%s).</span></span> <span data-ttu-id="048f3-117">此為參考用訊息，</span><span class="sxs-lookup"><span data-stu-id="048f3-117">This is an informational message only.</span></span> <span data-ttu-id="048f3-118">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="048f3-118">No user action is required.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="048f3-119">說明</span><span class="sxs-lookup"><span data-stu-id="048f3-119">Explanation</span></span>  
 <span data-ttu-id="048f3-120">根據預設，每個成功的備份都會將這個參考用訊息加入至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔和系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="048f3-120">By default, every successful backup adds this informational message to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the system event log.</span></span> <span data-ttu-id="048f3-121">如果您經常備份交易記錄，這些訊息可能會快速累積，因而建立非常龐大的錯誤記錄檔，讓您難以尋找其他訊息。</span><span class="sxs-lookup"><span data-stu-id="048f3-121">If you very frequently back up the transaction log, these messages can accumulate quickly, creating very large error logs that can make finding other messages difficult.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="048f3-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="048f3-122">User Action</span></span>  
 <span data-ttu-id="048f3-123">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 追蹤旗標 **3226** 來隱藏這些記錄項目。</span><span class="sxs-lookup"><span data-stu-id="048f3-123">You can suppress these log entries by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trace flag **3226**.</span></span> <span data-ttu-id="048f3-124">如果您正執行經常記錄備份，而且沒有任何指令碼相依於這些項目，啟用此追蹤旗標就會很有用。</span><span class="sxs-lookup"><span data-stu-id="048f3-124">Enabling this trace flag is useful if you are running frequent log backups and if none of your scripts depend on those entries.</span></span>  
  
 <span data-ttu-id="048f3-125">如需有關使用追蹤旗標的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="048f3-125">For information about using trace flags, see SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="048f3-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="048f3-126">See Also</span></span>  
 [<span data-ttu-id="048f3-127">追蹤旗標 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="048f3-127">Trace Flags &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
