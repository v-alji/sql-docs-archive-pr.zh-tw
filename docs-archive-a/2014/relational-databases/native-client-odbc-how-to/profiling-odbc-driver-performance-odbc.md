---
title: 分析 ODBC 驅動程式效能的使用說明主題 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0e6d7aed-28d2-419e-be6a-f60d3729bfd0
author: rothja
ms.author: jroth
ms.openlocfilehash: d27547862138b511a4defaa3cae80f48f69fdc4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585373"
---
# <a name="profiling-odbc-driver-performance-how-to-topics-odbc"></a><span data-ttu-id="922e0-102">分析 ODBC 驅動程式效能的使用說明主題 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="922e0-102">Profiling ODBC Driver Performance How-to Topics (ODBC)</span></span>
  <span data-ttu-id="922e0-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC 驅動程式具有兩個驅動程式特有的選項，可用於分析驅動程式的效能。</span><span class="sxs-lookup"><span data-stu-id="922e0-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver has two driver-specific options for profiling the performance of the driver.</span></span>  
  
 <span data-ttu-id="922e0-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ODBC 驅動程式可以將效能統計資料記錄在檔案中。</span><span class="sxs-lookup"><span data-stu-id="922e0-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver can log performance statistics in file.</span></span> <span data-ttu-id="922e0-105">此記錄檔是以 Tab 字元分隔的檔案，可以在 Microsoft Excel 等支援以 Tab 字元分隔之檔案的任何試算表中進行分析。</span><span class="sxs-lookup"><span data-stu-id="922e0-105">The log file is a tab-delimited file that can be analyzed in any spreadsheet supporting tab-delimited files, such as Microsoft Excel.</span></span>  
  
 <span data-ttu-id="922e0-106">此驅動程式也可以記錄長時間執行的查詢 (在指定的時間長度內，沒有從伺服器取得回應的查詢)。</span><span class="sxs-lookup"><span data-stu-id="922e0-106">The driver can also log long-running queries (queries that do not get a response from the server in a specified length of time).</span></span> <span data-ttu-id="922e0-107">之後，程式設計人員和資料庫管理員就可以分析這些查詢。</span><span class="sxs-lookup"><span data-stu-id="922e0-107">These queries can later be analyzed by programmers and database administrators.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="922e0-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="922e0-108">In This Section</span></span>  
  
-   [<span data-ttu-id="922e0-109">分析 &#40;ODBC&#41;的驅動程式效能資料</span><span class="sxs-lookup"><span data-stu-id="922e0-109">Profile Driver Performance Data &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-data.md)  
  
-   [<span data-ttu-id="922e0-110">&#40;ODBC&#41;記錄長時間執行的查詢</span><span class="sxs-lookup"><span data-stu-id="922e0-110">Log Long-Running Queries &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-data-log-long-running-queries.md)  
  
## <a name="see-also"></a><span data-ttu-id="922e0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="922e0-111">See Also</span></span>  
 [<span data-ttu-id="922e0-112">ODBC 的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="922e0-112">ODBC How-to Topics</span></span>](odbc-how-to-topics.md)  
  
  
