---
title: 在同步處理期間執行指令碼 (複寫 Transact-SQL 程式設計) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- synchronization [SQL Server replication], scripts
- scripts [SQL Server replication], synchronization and
- sp_addscriptexec
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4bc217ad160a0238cc4247600d65eb32f156071f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585846"
---
# <a name="execute-scripts-during-synchronization-replication-transact-sql-programming"></a><span data-ttu-id="633fc-102">在同步處理期間執行指令碼 (複寫 Transact-SQL 程式設計)</span><span class="sxs-lookup"><span data-stu-id="633fc-102">Execute Scripts During Synchronization (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="633fc-103">複寫可支援視需要針對交易式與合併式發行集的訂閱者執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="633fc-103">Replication supports on demand script execution for Subscribers to transactional and merge publications.</span></span> <span data-ttu-id="633fc-104">這項功能會將指令碼複製到複寫工作目錄，然後使用 **sqlcmd** 將指令碼套用到訂閱者。</span><span class="sxs-lookup"><span data-stu-id="633fc-104">This functionality copies the script to the replication working directory and then uses **sqlcmd** to apply the script at the Subscriber.</span></span> <span data-ttu-id="633fc-105">依預設，如果針對交易式發行集的訂閱套用指令碼時發生失敗，則散發代理程式將會停止。</span><span class="sxs-lookup"><span data-stu-id="633fc-105">By default, if there is a failure when applying the script for a subscription to a transactional publication, the Distribution Agent will stop.</span></span> <span data-ttu-id="633fc-106">您可以使用複寫預存程序以程式設計的方式指定要執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="633fc-106">You can specify a [!INCLUDE[tsql](../../includes/tsql-md.md)] script to execute programmatically using replication stored procedures.</span></span>  
  
### <a name="to-specify-a-script-to-run-for-all-subscribers-to-a-snapshot-transactional-or-merge-publication"></a><span data-ttu-id="633fc-107">針對快照式、交易式或合併式發行集的所有訂閱者指定要執行的指令碼</span><span class="sxs-lookup"><span data-stu-id="633fc-107">To specify a script to run for all Subscribers to a snapshot, transactional or merge publication</span></span>  
  
1.  <span data-ttu-id="633fc-108">撰寫及測試將會視需要執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="633fc-108">Compose and test the [!INCLUDE[tsql](../../includes/tsql-md.md)] script that will be executed on demand.</span></span>  
  
2.  <span data-ttu-id="633fc-109">將指令碼檔案儲存到可由發行集之快照集代理程式存取的位置。</span><span class="sxs-lookup"><span data-stu-id="633fc-109">Save the script file to a location where it can be accessed by the Snapshot Agent for the publication.</span></span>  
  
3.  <span data-ttu-id="633fc-110">在發行集資料庫的發行者上，執行 [sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="633fc-110">At the Publisher on the publication database, execute [sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql).</span></span> <span data-ttu-id="633fc-111">針對\*\* \@ scriptfile**指定** \@ 發行**集、在步驟2中為其建立完整 UNC 路徑的指令檔名，以及** \@ skiperror\*\*的下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="633fc-111">Specify **\@publication**, the name of the script file with full UNC path created in step 2 for **\@scriptfile**, and one of the following values for **\@skiperror**:</span></span>  
  
    -   <span data-ttu-id="633fc-112">**0** - 如果遇到錯誤，代理程式將會停止執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="633fc-112">**0** - the agent will stop executing the script if an error is encountered.</span></span>  
  
    -   <span data-ttu-id="633fc-113">**1** - 如果遇到錯誤，代理程式將會記錄錯誤並繼續執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="633fc-113">**1** - the agent will log errors and continue executing the script when errors are encountered.</span></span>  
  
4.  <span data-ttu-id="633fc-114">當下一次執行代理程式來同步處理訂閱時，指定的指令碼將會在每一個訂閱者上執行。</span><span class="sxs-lookup"><span data-stu-id="633fc-114">The specified script will be executed at each Subscriber when the agent next runs to synchronize the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="633fc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="633fc-115">See Also</span></span>  
 [<span data-ttu-id="633fc-116">同步處理資料</span><span class="sxs-lookup"><span data-stu-id="633fc-116">Synchronize Data</span></span>](synchronize-data.md)  
  
  
