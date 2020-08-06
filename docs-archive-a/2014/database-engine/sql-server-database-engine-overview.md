---
title: SQL Server 資料庫引擎 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server]
- SQL Server Database Engine
ms.assetid: 65e2f424-1386-45a6-8912-bd053f434073
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a6c243115e940f7af085c0068d2ca5c277aa5162
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585558"
---
# <a name="sql-server-database-engine"></a><span data-ttu-id="c5809-102">SQL Server Database Engine</span><span class="sxs-lookup"><span data-stu-id="c5809-102">SQL Server Database Engine</span></span>
  <span data-ttu-id="c5809-103">[!INCLUDE[ssDE](../includes/ssde-md.md)] 是用來儲存、處理和保護資料安全的核心服務。</span><span class="sxs-lookup"><span data-stu-id="c5809-103">The [!INCLUDE[ssDE](../includes/ssde-md.md)] is the core service for storing, processing, and securing data.</span></span> <span data-ttu-id="c5809-104">[!INCLUDE[ssDE](../includes/ssde-md.md)] 提供控制的存取和快速交易處理，可滿足您企業內部最嚴苛的資料取用應用程式需求。</span><span class="sxs-lookup"><span data-stu-id="c5809-104">The [!INCLUDE[ssDE](../includes/ssde-md.md)] provides controlled access and rapid transaction processing to meet the requirements of the most demanding data consuming applications within your enterprise.</span></span>

 <span data-ttu-id="c5809-105">使用 [!INCLUDE[ssDE](../includes/ssde-md.md)] 建立線上交易處理或線上分析處理資料的關聯式資料庫，</span><span class="sxs-lookup"><span data-stu-id="c5809-105">Use the [!INCLUDE[ssDE](../includes/ssde-md.md)] to create relational databases for online transaction processing or online analytical processing data.</span></span> <span data-ttu-id="c5809-106">包括建立資料表以儲存資料，以及建立索引、檢視和預存程序等資料庫物件，以檢視、管理和保護資料。</span><span class="sxs-lookup"><span data-stu-id="c5809-106">This includes creating tables for storing data, and database objects such as indexes, views, and stored procedures for viewing, managing, and securing data.</span></span> <span data-ttu-id="c5809-107">您可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 管理資料庫物件，以及使用 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 擷取伺服器事件。</span><span class="sxs-lookup"><span data-stu-id="c5809-107">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to manage the database objects, and [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to capture server events.</span></span>

 <span data-ttu-id="c5809-108">**依區域流覽內容**![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示")[新功能 (資料庫引擎) ](whats-new-in-sql-server-2016.md)</span><span class="sxs-lookup"><span data-stu-id="c5809-108">**Browse Content by Area** ![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [What's New (Database Engine)](whats-new-in-sql-server-2016.md)</span></span>

 <span data-ttu-id="c5809-109">![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示") [SQL Server 資料庫引擎回溯相容性](sql-server-database-engine-backward-compatibility.md)</span><span class="sxs-lookup"><span data-stu-id="c5809-109">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [SQL Server Database Engine Backward Compatibility](sql-server-database-engine-backward-compatibility.md)</span></span>

 <span data-ttu-id="c5809-110">![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示") [SQL Server 管理工具回溯相容性](../../2014/database-engine/sql-server-management-tools-backward-compatibility.md)</span><span class="sxs-lookup"><span data-stu-id="c5809-110">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [SQL Server Management Tools Backward Compatibility](../../2014/database-engine/sql-server-management-tools-backward-compatibility.md)</span></span>

 <span data-ttu-id="c5809-111">![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示")[資料庫功能和](../../2014/database-engine/database-engine-features-and-tasks.md)工作</span><span class="sxs-lookup"><span data-stu-id="c5809-111">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Database Features and Tasks](../../2014/database-engine/database-engine-features-and-tasks.md)</span></span>

 <span data-ttu-id="c5809-112">![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示")[技術參考](../../2014/database-engine/technical-reference-database-engine.md)</span><span class="sxs-lookup"><span data-stu-id="c5809-112">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Technical Reference](../../2014/database-engine/technical-reference-database-engine.md)</span></span>

 <span data-ttu-id="c5809-113">![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示") [transact-sql 參考](/sql/t-sql/language-reference)</span><span class="sxs-lookup"><span data-stu-id="c5809-113">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Transact-SQL Reference](/sql/t-sql/language-reference)</span></span>

 <span data-ttu-id="c5809-114">![小型檔案資料夾圖示](../../2014/integration-services/media/filefolder-small.gif "小型檔案資料夾圖示") [XQuery 參考](/sql/xquery/xquery-language-reference-sql-server)</span><span class="sxs-lookup"><span data-stu-id="c5809-114">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [XQuery Reference](/sql/xquery/xquery-language-reference-sql-server)</span></span>

## <a name="see-also"></a><span data-ttu-id="c5809-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5809-115">See Also</span></span>
 [<span data-ttu-id="c5809-116">SQL Server 資源中心</span><span class="sxs-lookup"><span data-stu-id="c5809-116">SQL Server Resource Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=219676)


