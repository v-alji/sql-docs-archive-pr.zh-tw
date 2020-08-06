---
title: 將追蹤結果儲存至資料表 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: edbecf74-683b-4e43-a1ef-7a3d5f5e27f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 08acfb4e7136f8b28d1c990d508b8578f96a57b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705701"
---
# <a name="save-trace-results-to-a-table-sql-server-profiler"></a><span data-ttu-id="ade95-102">將追蹤結果儲存到資料表 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="ade95-102">Save Trace Results to a Table (SQL Server Profiler)</span></span>
  <span data-ttu-id="ade95-103">此主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]將追蹤結果儲存到資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="ade95-103">This topic describes how to save trace results to a database table by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-save-trace-results-to-a-table"></a><span data-ttu-id="ade95-104">若要將追蹤結果儲存至資料表</span><span class="sxs-lookup"><span data-stu-id="ade95-104">To save trace results to a table</span></span>  
  
1.  <span data-ttu-id="ade95-105">在 [檔案]  功能表上，按一下 [新增追蹤]  ，接著連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ade95-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="ade95-106">會出現 [追蹤屬性] **[追蹤屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ade95-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ade95-107">如果選取 [進行連接後立即啟動追蹤]  ，將不會顯示 [追蹤屬性]  對話方塊，而是開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="ade95-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="ade95-108">於 [工具]  功能表，按一下 [選項]  ，並清除 [連接後立即啟動追蹤]  核取方塊，以關閉這項設定。</span><span class="sxs-lookup"><span data-stu-id="ade95-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="ade95-109">在 [追蹤名稱]  方塊中，輸入追蹤的名稱，然後按一下 [儲存至資料表]  。</span><span class="sxs-lookup"><span data-stu-id="ade95-109">In the **Trace name** box, type a name for the trace, and then click **Save to table**.</span></span>  
  
3.  <span data-ttu-id="ade95-110">在 [連接至伺服器]  對話方塊中，連接至將包含追蹤資料表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ade95-110">In the **Connect to server** dialog box, connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that will contain the trace table.</span></span>  
  
4.  <span data-ttu-id="ade95-111">在 [目的地資料表]  對話方塊中，從 [資料庫]  清單中選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="ade95-111">In the **Destination Table** dialog box, select a database from the **Database**list.</span></span>  
  
5.  <span data-ttu-id="ade95-112">在 [擁有者]  清單中，選取追蹤的擁有者。</span><span class="sxs-lookup"><span data-stu-id="ade95-112">In the **Owner** list, select the owner for the trace.</span></span>  
  
6.  <span data-ttu-id="ade95-113">在 [資料表]  清單中，輸入或選取追蹤結果的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="ade95-113">In the **Table** list, type or select the table name for the trace results.</span></span> <span data-ttu-id="ade95-114">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="ade95-114">Click **OK.**</span></span>  
  
7.  <span data-ttu-id="ade95-115">在 [**追蹤屬性**] 對話方塊中，選取 [**設定千位) 的最大資料列 (** ] 核取方塊，以指定要儲存的最大資料列數目。</span><span class="sxs-lookup"><span data-stu-id="ade95-115">In the **Trace Properties** dialog box, select the **Set maximum rows (in thousands)** check box to specify the maximum number of rows to save.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade95-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ade95-116">See Also</span></span>  
 [<span data-ttu-id="ade95-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="ade95-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
