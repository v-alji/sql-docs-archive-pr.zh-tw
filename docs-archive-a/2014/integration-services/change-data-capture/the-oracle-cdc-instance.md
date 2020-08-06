---
title: Oracle CDC 執行個體 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ed71e8c4-e013-4bf2-8b6c-1e833ff2a41d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2228872b5a190fd416dccaa8062dd79dbc1f7a79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596233"
---
# <a name="the-oracle-cdc-instance"></a><span data-ttu-id="bfefe-102">Oracle CDC 執行個體</span><span class="sxs-lookup"><span data-stu-id="bfefe-102">The Oracle CDC Instance</span></span>
  <span data-ttu-id="bfefe-103">Oracle CDC 執行個體是由 Oracle CDC 服務建立的一種處理序，可處理從單一 Oracle 來源資料庫擷取的變更。</span><span class="sxs-lookup"><span data-stu-id="bfefe-103">The Oracle CDC Instance is a process created by the Oracle CDC Service to process changes captured from a single Oracle source database.</span></span> <span data-ttu-id="bfefe-104">Oracle CDC 執行個體會從 **cdc.xdbcdc_config** 資料表擷取其組態，並在 **cdc.xdbcdc_state** 資料表中維護其狀態。</span><span class="sxs-lookup"><span data-stu-id="bfefe-104">The Oracle CDC Instance retrieves its configuration from the **cdc.xdbcdc_config** table and maintains its state in the **cdc.xdbcdc_state** table.</span></span> <span data-ttu-id="bfefe-105">這些資料表是 CDC 資料庫的一部分 (此資料庫會定義 Oracle CDC 執行個體)。</span><span class="sxs-lookup"><span data-stu-id="bfefe-105">These tables are part of the CDC database, which defines the Oracle CDC Instance.</span></span> <span data-ttu-id="bfefe-106">如需有關 xdbcdc 資料庫和資料表的詳細資訊，請參閱＜ [The CDC Databases](the-oracle-cdc-service.md)＞。</span><span class="sxs-lookup"><span data-stu-id="bfefe-106">For more information about the xdbcdc database and tables see [The CDC Databases](the-oracle-cdc-service.md).</span></span>  
  
 <span data-ttu-id="bfefe-107">以下描述 Oracle CDC 執行個體所執行的工作：</span><span class="sxs-lookup"><span data-stu-id="bfefe-107">The following describes the tasks carried out by the Oracle CDC instance:</span></span>  
  
-   <span data-ttu-id="bfefe-108">**處理服務啟動驗證**：當啟動時，CDC 執行個體會從 **xdbcdc_config** 資料表載入其組態，並執行一系列的驗證來確保 CDC 執行個體保存的狀態一致而且可以開始處理變更。</span><span class="sxs-lookup"><span data-stu-id="bfefe-108">**Handling service startup verification**: When started, the CDC instance loads its configuration from the **xdbcdc_config** table and performs a series of status verifications that ensure that the CDC instance persisted state is consistent and that it can start processing changes.</span></span>  
  
-   <span data-ttu-id="bfefe-109">**準備變更擷取**：當順利通過驗證時，Oracle CDC 執行個體會掃描目前定義的所有擷取執行個體，並準備 Oracle LogMiner 查詢及變更擷取所需的其他支援結構。</span><span class="sxs-lookup"><span data-stu-id="bfefe-109">**Preparing for change capture**: When the verification passes successfully, the Oracle CDC Instance scans all of the capture instances currently defined and prepares the Oracle LogMiner queries and other support structures required for change capture.</span></span> <span data-ttu-id="bfefe-110">此外，Oracle 執行個體會重新載入上次執行 Oracle CDC 執行個體時所儲存的內部擷取狀態。</span><span class="sxs-lookup"><span data-stu-id="bfefe-110">In addition, the Oracle instance re-loads the internal capture state that was saved the last time the Oracle CDC Instance run.</span></span>  
  
-   <span data-ttu-id="bfefe-111">**從 Oracle 擷取變更**：Oracle CDC 執行個體會透過 Oracle LogMiner 功能來共用 Oracle 中的變更、根據交易認可加以排序，然後變更交易中的時間並將其寫入 CDC 資料庫中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 變更資料表。</span><span class="sxs-lookup"><span data-stu-id="bfefe-111">**Capturing changes from Oracle**: The Oracle CDC Instance pools changes from Oracle by means of the Oracle LogMiner facility, orders them in according to transaction commit, and then changes the time in a transaction and writes them to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] change tables in the CDC database.</span></span>  
  
-   <span data-ttu-id="bfefe-112">**處理服務關閉**：Oracle CDC 執行個體的生命週期由 Oracle CDC 服務所管理。</span><span class="sxs-lookup"><span data-stu-id="bfefe-112">**Handling service shutdown**: The life cycle of the Oracle CDC Instance is managed by the Oracle CDC Service.</span></span> <span data-ttu-id="bfefe-113">當系統要求 Oracle CDC 執行個體關閉時，它會執行以下工作：</span><span class="sxs-lookup"><span data-stu-id="bfefe-113">When the Oracle CDC Instance is requested to shut down, it performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="bfefe-114">停止讀取 Oracle 交易記錄。</span><span class="sxs-lookup"><span data-stu-id="bfefe-114">Stops reading from the Oracle transaction log.</span></span>  
  
    -   <span data-ttu-id="bfefe-115">停止將完成的 Oracle 交易寫入 CDC 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bfefe-115">Stops writing completed Oracle transactions to the CDC database.</span></span>  
  
    -   <span data-ttu-id="bfefe-116">必要時請等候 30 秒的時間，直到目前的交易完成寫入 CDC 資料庫為止。</span><span class="sxs-lookup"><span data-stu-id="bfefe-116">Waits for up to 30 seconds (if necessary) until the current transaction finishes writing to the CDC database.</span></span> <span data-ttu-id="bfefe-117">如果過了 30 秒以上的時間，則會取消寫入並回復交易 (當重新啟動 CDC 執行個體時會重試)。</span><span class="sxs-lookup"><span data-stu-id="bfefe-117">If more than 30 seconds pass, the writing is cancelled and transaction is rolled back (to be retried when the CDC instance is restarted).</span></span>  
  
    -   <span data-ttu-id="bfefe-118">在個別執行緒中，最長可在 30 秒內盡量將許多記憶體快取的記錄寫入暫存交易資料表中 (從最舊的交易到最新的交易)，然後更新 **xdbcdc_state** 資料表並認可所有變更。</span><span class="sxs-lookup"><span data-stu-id="bfefe-118">In a separate thread, writes as many memory-cached records as possible to the staged transactions table for up to 30 seconds (from the oldest transaction to the newest), then updates the **xdbcdc_state** table and commits all the changes.</span></span>  
  
-   <span data-ttu-id="bfefe-119">**處理組態變更**：系統會通知 Oracle CDC 執行個體有關組態變更的消息 (從 CDC 服務或是藉由偵測 **cdc.xdbcdc_config** 資料表中的新版本)。</span><span class="sxs-lookup"><span data-stu-id="bfefe-119">**Handling configuration changes**: The Oracle CDC Instance is notified about configuration changes either from the CDC Service or by detecting a new version in the **cdc.xdbcdc_config** table.</span></span> <span data-ttu-id="bfefe-120">大多數的變更不需要重新啟動 Oracle CDC 執行個體 (例如，加入或移除擷取執行個體)。</span><span class="sxs-lookup"><span data-stu-id="bfefe-120">Most changes do not require the restart of the Oracle CDC Instance (for example, adding or removing capture instances).</span></span> <span data-ttu-id="bfefe-121">但是，某些變更 (例如變更 Oracle 連接字串或存取認證) 確實需要重新啟動 CDC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bfefe-121">However, some changes, such as changing the Oracle connection string or access credentials do require the restart of the CDC Instance.</span></span>  
  
-   <span data-ttu-id="bfefe-122">**處理復原**：當 Oracle CDC 執行個體啟動時，其內部狀態會從 **xdbcdc_state** 和 **xdbcdc_staged_transactions** 資料表中還原。</span><span class="sxs-lookup"><span data-stu-id="bfefe-122">**Handling recovery**: When an Oracle CDC Instance starts its internal state is restored from the **xdbcdc_state** and the **xdbcdc_staged_transactions** tables.</span></span> <span data-ttu-id="bfefe-123">還原狀態之後，CDC 執行個體會如往常一樣繼續進行。</span><span class="sxs-lookup"><span data-stu-id="bfefe-123">Once the state is restored, the CDC instance proceeds as usual.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfefe-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfefe-124">See Also</span></span>  
 [<span data-ttu-id="bfefe-125">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="bfefe-125">Error Handling</span></span>](error-handling.md)  
  
  
