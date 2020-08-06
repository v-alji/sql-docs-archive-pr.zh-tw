---
title: SQL Server Profiler-來源資料表-Database Engine Tuning Advisor-選取工作負載資料表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.tools.sourcetable.f1
helpviewer_keywords:
- Select Workload Table dialog box
- Source Table dialog box
ms.assetid: 51185be7-7092-480a-a52c-cf7786c4a0a0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d10899c01df8e7fbc7ee45d108841a18d3248500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594668"
---
# <a name="sql-server-profiler---source-table-database-engine-tuning-advisor---select-workload-table"></a><span data-ttu-id="398c4-102">SQL Server Profiler-來源資料表-Database Engine Tuning Advisor-選取工作負載資料表</span><span class="sxs-lookup"><span data-stu-id="398c4-102">SQL Server Profiler - Source Table-Database Engine Tuning Advisor - Select Workload Table</span></span>
  <span data-ttu-id="398c4-103">Microsoft [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 和 [!INCLUDE[ssDE](../includes/ssde-md.md)] Tuning Advisor 使用此對話方塊來選取資料表。</span><span class="sxs-lookup"><span data-stu-id="398c4-103">Microsoft [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] and [!INCLUDE[ssDE](../includes/ssde-md.md)] Tuning Advisor use this dialog box to select tables.</span></span>  
  
 <span data-ttu-id="398c4-104">在 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 中，使用 [來源資料表]\*\*\*\* 對話方塊以指定追蹤資料表的來源資料表。</span><span class="sxs-lookup"><span data-stu-id="398c4-104">In [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], use the **Source Table** dialog box to specify a source table for a trace table.</span></span> <span data-ttu-id="398c4-105">此資料表是追蹤載入的來源，並且可以檢視或使用其內容來重新執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="398c4-105">This is a table from which a trace is loaded, and the contents of which are viewed or used for replaying the trace.</span></span>  
  
 <span data-ttu-id="398c4-106">在 [!INCLUDE[ssDE](../includes/ssde-md.md)] Tuning Advisor 中，使用 [選取工作負載資料表]\*\*\*\* 對話方塊，來選取包含 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 追蹤資訊的資料庫資料表用來作為微調工作負載，或在啟動微調分析之前預覽資料表內容。</span><span class="sxs-lookup"><span data-stu-id="398c4-106">In [!INCLUDE[ssDE](../includes/ssde-md.md)] Tuning Advisor, use the **Select Workload Table** dialog box to select a database table that contains [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace information to use as a tuning workload, or to preview the table contents before starting tuning analysis.</span></span>  
  
## <a name="options"></a><span data-ttu-id="398c4-107">選項</span><span class="sxs-lookup"><span data-stu-id="398c4-107">Options</span></span>  
 <span data-ttu-id="398c4-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="398c4-108">**SQL Server**</span></span>  
 <span data-ttu-id="398c4-109">指定目前連接之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="398c4-109">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] currently connected.</span></span> <span data-ttu-id="398c4-110">此欄位會自動擴展且無法更新。</span><span class="sxs-lookup"><span data-stu-id="398c4-110">This field is populated automatically and cannot be updated.</span></span>  
  
 <span data-ttu-id="398c4-111">**Database**</span><span class="sxs-lookup"><span data-stu-id="398c4-111">**Database**</span></span>  
 <span data-ttu-id="398c4-112">指定追蹤資料表所在的資料庫。</span><span class="sxs-lookup"><span data-stu-id="398c4-112">Specify the database where the trace table is located.</span></span>  
  
 <span data-ttu-id="398c4-113">**擁有者**</span><span class="sxs-lookup"><span data-stu-id="398c4-113">**Owner**</span></span>  
 <span data-ttu-id="398c4-114">指定追蹤資料表的擁有者。</span><span class="sxs-lookup"><span data-stu-id="398c4-114">Specifies the owner of the trace table.</span></span> <span data-ttu-id="398c4-115">此欄位會自動擴展為 **dbo**。</span><span class="sxs-lookup"><span data-stu-id="398c4-115">This field is populated automatically as **dbo**.</span></span>  
  
 <span data-ttu-id="398c4-116">**資料表**</span><span class="sxs-lookup"><span data-stu-id="398c4-116">**Table**</span></span>  
 <span data-ttu-id="398c4-117">指定從中讀取追蹤的追蹤資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="398c4-117">Specify the name of the trace table from which the trace should be read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="398c4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="398c4-118">See Also</span></span>  
 <span data-ttu-id="398c4-119">[將追蹤結果儲存到資料表 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="398c4-119">[Save Trace Results to a Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="398c4-120">[SQL Server Profiler 範本和權限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="398c4-120">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="398c4-121">Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="398c4-121">Database Engine Tuning Advisor</span></span>](../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
