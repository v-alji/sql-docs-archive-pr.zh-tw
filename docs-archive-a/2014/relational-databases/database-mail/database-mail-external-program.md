---
title: Database Mail 外部程式 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- external programs [Database Mail]
- DatabaseMail90.exe
- Database Mail [SQL Server], external programs
ms.assetid: bc124164-eb6e-4b7f-bf66-98a3113d02f7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 698fc8d97a565b4181552691a0260486c9c43bfd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709629"
---
# <a name="database-mail-external-program"></a><span data-ttu-id="04a10-102">Database Mail 外部程式</span><span class="sxs-lookup"><span data-stu-id="04a10-102">Database Mail External Program</span></span>
  <span data-ttu-id="04a10-103">Database Mail 外部可執行檔是 **DatabaseMail.exe**，位於 **安裝的** MSSQL\Binn 目錄 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="04a10-103">The Database Mail external executable is **DatabaseMail.exe**, located in the **MSSQL\Binn directory** of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="04a10-104">有電子郵件訊息需要處理時，Database Mail 會使用「Service Broker 啟用」來啟動外部程式。</span><span class="sxs-lookup"><span data-stu-id="04a10-104">Database Mail uses Service Broker activation to start the external program when there are e-mail messages to be processed.</span></span> <span data-ttu-id="04a10-105">Database Mail 會啟動一個外部程式的執行個體。</span><span class="sxs-lookup"><span data-stu-id="04a10-105">Database Mail starts one instance of the external program.</span></span> <span data-ttu-id="04a10-106">外部程式則於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]服務帳戶的安全性內容中執行。</span><span class="sxs-lookup"><span data-stu-id="04a10-106">The external program runs in the security context of the service account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="04a10-107">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="04a10-107">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="04a10-108">Database Mail 外部程式概念</span><span class="sxs-lookup"><span data-stu-id="04a10-108">Database Mail External Program Concepts</span></span>](#ComponentsAndConcepts)  
  
-   [<span data-ttu-id="04a10-109">與設定 Database Mail 外部程式相關的工作</span><span class="sxs-lookup"><span data-stu-id="04a10-109">Tasks Related to Configuring Database Mail External Program</span></span>](#RelatedTasks)  
  
##  <a name="database-mail-external-program-concepts"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="04a10-110">Database Mail 外部程式概念</span><span class="sxs-lookup"><span data-stu-id="04a10-110">Database Mail External Program Concepts</span></span>  
 <span data-ttu-id="04a10-111">外部程式啟動時，程式會使用「Windows 驗證」連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，並開始處理電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="04a10-111">When the external program starts, the program connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Windows Authentication and begins processing e-mail messages.</span></span> <span data-ttu-id="04a10-112">若在指定的逾時期限內沒有訊息需要傳送，程式就會結束。</span><span class="sxs-lookup"><span data-stu-id="04a10-112">When there have been no messages to send for the specified time-out period, the program exits.</span></span> <span data-ttu-id="04a10-113">您可以使用「Database Mail 組態精靈」或 Database Mail 預存程序，來設定程式結束前需等待的時間長度。</span><span class="sxs-lookup"><span data-stu-id="04a10-113">You can configure the amount of time that the program waits before exiting by using either Database Mail Configuration Wizard or the Database Mail stored procedures.</span></span> <span data-ttu-id="04a10-114">如需詳細資訊，請參閱 [sysmail_configure_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)服務帳戶的安全性內容中執行。</span><span class="sxs-lookup"><span data-stu-id="04a10-114">For more information, see [sysmail_configure_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql).</span></span>  
  
 <span data-ttu-id="04a10-115">外部程式會將資訊儲存在 **msdb** 資料庫的系統資料表中。</span><span class="sxs-lookup"><span data-stu-id="04a10-115">The external program stores information in system tables in the **msdb** database.</span></span> <span data-ttu-id="04a10-116">若外部程式無法與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]通訊，程式會將錯誤記錄到 Microsoft Windows 應用程式事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="04a10-116">If the external program cannot communicate with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the program logs errors to the Microsoft Windows application event log.</span></span> <span data-ttu-id="04a10-117">當您將 **[Database Mail 組態精靈]** 中 **[設定系統參數]** 對話方塊中的記錄層級設定為 **[詳細資訊]** 時，會提供額外的訊息記錄。</span><span class="sxs-lookup"><span data-stu-id="04a10-117">Additional message logging is provided when the logging level is set to **Verbose** in the **Configure System Parameters** dialog box of the **Database Mail Configuration Wizard**.</span></span>  
  
 <span data-ttu-id="04a10-118">請注意，外部程式會為了提高效率而快取帳戶與設定檔資訊，</span><span class="sxs-lookup"><span data-stu-id="04a10-118">Notice that, for efficiency, the external program caches account and profile information.</span></span> <span data-ttu-id="04a10-119">因此，對帳戶與設定檔的組態變更，可能要在幾分鐘後才會反映在外部程式中。</span><span class="sxs-lookup"><span data-stu-id="04a10-119">Therefore, configuration changes to accounts and profiles may not be reflected in the external program for a few minutes.</span></span>  
  
##  <a name="tasks-related-to-configuring-database-mail-external-program"></a><a name="RelatedTasks"></a> <span data-ttu-id="04a10-120">與設定 Database Mail 外部程式相關的工作</span><span class="sxs-lookup"><span data-stu-id="04a10-120">Tasks Related to Configuring Database Mail External Program</span></span>  
  
|<span data-ttu-id="04a10-121">組態工作</span><span class="sxs-lookup"><span data-stu-id="04a10-121">Configuration Task</span></span>|<span data-ttu-id="04a10-122">主題連結</span><span class="sxs-lookup"><span data-stu-id="04a10-122">Topic Link</span></span>|  
|------------------------|----------------|  
|<span data-ttu-id="04a10-123">指定外部程式在結束之前的時間。</span><span class="sxs-lookup"><span data-stu-id="04a10-123">Specify the time that the External Program before exiting.</span></span>|[<span data-ttu-id="04a10-124">sysmail_configure_sp &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04a10-124">sysmail_configure_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)|  
  
## <a name="see-also"></a><span data-ttu-id="04a10-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04a10-125">See Also</span></span>  
 <span data-ttu-id="04a10-126">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span><span class="sxs-lookup"><span data-stu-id="04a10-126">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span></span>  
 <span data-ttu-id="04a10-127">[Database Mail 記錄與稽核](database-mail-log-and-audits.md) </span><span class="sxs-lookup"><span data-stu-id="04a10-127">[Database Mail Log and Audits](database-mail-log-and-audits.md) </span></span>  
 [<span data-ttu-id="04a10-128">Database Mail</span><span class="sxs-lookup"><span data-stu-id="04a10-128">Database Mail</span></span>](database-mail.md)  
  
  
