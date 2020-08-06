---
title: 檢查具有可疑頁面的資料庫是否完整 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3cc1f87917c78f34ec7722fa21a1a67fda40a8c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686916"
---
# <a name="check-integrity-of-database-with-suspect-pages"></a><span data-ttu-id="b4423-102">檢查具有可疑頁面的資料庫是否完整</span><span class="sxs-lookup"><span data-stu-id="b4423-102">Check Integrity of Database with Suspect Pages</span></span>
  <span data-ttu-id="b4423-103">此規則會檢查資料庫狀態設定為有疑問的使用者資料庫。</span><span class="sxs-lookup"><span data-stu-id="b4423-103">This rule checks for user databases that have the database status set to suspect.</span></span> <span data-ttu-id="b4423-104">當 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 讀取包含 824 錯誤的資料庫頁面時，該頁面會被視為有疑問、它的頁面識別碼會記錄在 msdb 內的 suspect_pages 資料表中，而且包含此頁面的資料庫會設定為有疑問。</span><span class="sxs-lookup"><span data-stu-id="b4423-104">When the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] reads a database page that contains an 824 error, the page is considered suspect, its page ID is recorded in the suspect_pages table in msdb, and the database that contains the page is set to suspect.</span></span>  
  
 <span data-ttu-id="b4423-105">錯誤 824 表示讀取作業期間偵測到邏輯一致性錯誤。</span><span class="sxs-lookup"><span data-stu-id="b4423-105">Error 824 indicates that a logical consistency error was detected during a read operation.</span></span> <span data-ttu-id="b4423-106">這個錯誤通常表示錯誤 I/O 子系統元件所造成的資料損毀。</span><span class="sxs-lookup"><span data-stu-id="b4423-106">This error frequently indicates data corruption caused by a faulty I/O subsystem component.</span></span> <span data-ttu-id="b4423-107">這是嚴重的錯誤狀況，且可能會損及資料庫的完整性，所以必須立即更正。</span><span class="sxs-lookup"><span data-stu-id="b4423-107">This is a severe error condition that threatens database integrity and must be corrected immediately.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="b4423-108">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="b4423-108">Best Practices Recommendations</span></span>  
  
-   <span data-ttu-id="b4423-109">請檢閱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以取得這個資料庫之 824 錯誤的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b4423-109">Review the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log for the details of the 824 error for this database.</span></span>  
  
-   <span data-ttu-id="b4423-110">完成完整資料庫一致性檢查 ([DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql))。</span><span class="sxs-lookup"><span data-stu-id="b4423-110">Complete a full database consistency check ([DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)).</span></span>  
  
-   <span data-ttu-id="b4423-111">實作定義在 [MSSQLSERVER_824](https://go.microsoft.com/fwlink/?LinkId=81397)中的使用者動作。</span><span class="sxs-lookup"><span data-stu-id="b4423-111">Implement the user actions that are defined in [MSSQLSERVER_824](https://go.microsoft.com/fwlink/?LinkId=81397).</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="b4423-112">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="b4423-112">For More Information</span></span>  
 [<span data-ttu-id="b4423-113">管理 suspect_pages 資料表 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b4423-113">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
