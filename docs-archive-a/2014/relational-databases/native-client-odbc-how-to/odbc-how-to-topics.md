---
title: ODBC 的使用說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 151f2066-1c37-410f-88f4-b27dfca66031
author: rothja
ms.author: jroth
ms.openlocfilehash: cfeb120b9fa1fedb5358b5e12dabed7835f9a6b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706446"
---
# <a name="odbc-how-to-topics"></a><span data-ttu-id="57088-102">ODBC 的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="57088-102">ODBC How-to Topics</span></span>
  <span data-ttu-id="57088-103">若要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] odbc 驅動程式，您必須能夠建立 odbc 資料來源，並確定伺服器具有正確的目錄預存程式版本。</span><span class="sxs-lookup"><span data-stu-id="57088-103">To use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver, you must be able to create ODBC data sources and ensure that the server has the correct version of the catalog stored procedures.</span></span> <span data-ttu-id="57088-104">若要撰寫使用 SQL Server 之 ODBC 應用程式的程式碼，您必須知道如何配置 ODBC 控制代碼、設定屬性、連接至 SQL Server 執行個體、執行查詢以及處理結果。</span><span class="sxs-lookup"><span data-stu-id="57088-104">To code an ODBC application that uses SQL Server, you must know how to allocate ODBC handles, set attributes, connect to an instance of SQL Server, execute queries, and process results.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57088-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="57088-105">In This Section</span></span>  
  
-   [<span data-ttu-id="57088-106">設定 SQL Server ODBC 驅動程式的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="57088-106">Configuring the SQL Server ODBC Driver How-to Topics</span></span>](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
-   [<span data-ttu-id="57088-107">配置控制碼並連接到 SQL Server &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="57088-107">Allocate Handles and Connect to SQL Server &#40;ODBC&#41;</span></span>](allocate-handles-and-connect-to-sql-server-odbc.md)  
  
-   [<span data-ttu-id="57088-108">執行查詢 &#40;ODBC&#41;的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="57088-108">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](execute-queries/executing-queries-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="57088-109">處理結果如何 &#40;ODBC&#41;的 how to 主題</span><span class="sxs-lookup"><span data-stu-id="57088-109">Processing Results How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="57088-110">使用資料指標的 how to 主題 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="57088-110">Using Cursors How-to Topics &#40;ODBC&#41;</span></span>](cursors/using-cursors-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="57088-111">使用 Microsoft 分散式交易協調器 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="57088-111">Use Microsoft Distributed Transaction Coordinator &#40;ODBC&#41;</span></span>](use-microsoft-distributed-transaction-coordinator-odbc.md)  
  
-   [<span data-ttu-id="57088-112">執行預存程式的 how to 主題 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="57088-112">Running Stored Procedures How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="57088-113">管理 text 和 image 資料行如何 &#40;ODBC&#41;的 how to 主題</span><span class="sxs-lookup"><span data-stu-id="57088-113">Managing text and image Columns How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/managing-text-and-image-columns-how-to-topics-odbc.md)  
  
-   [<span data-ttu-id="57088-114">分析 ODBC 驅動程式效能的使用說明主題 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="57088-114">Profiling ODBC Driver Performance How-to Topics &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-odbc.md)  
  
-   [<span data-ttu-id="57088-115">&#40;ODBC&#41;處理 ODBC 錯誤</span><span class="sxs-lookup"><span data-stu-id="57088-115">Process ODBC Errors &#40;ODBC&#41;</span></span>](process-odbc-errors-odbc.md)  
  
-   [<span data-ttu-id="57088-116">使用 SQL Server ODBC 驅動程式的大量複製如何 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="57088-116">Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;</span></span>](bulk-copy/bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="57088-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57088-117">See Also</span></span>  
 [<span data-ttu-id="57088-118">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="57088-118">SQL Server Native Client &#40;ODBC&#41;</span></span>](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
