---
title: 將追蹤結果儲存至檔案 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: ac528747-0c19-4f3d-96f5-44c762a4abed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9644751cda3689cf7b7cb00ec25310bc700ca1c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705722"
---
# <a name="save-trace-results-to-a-file-sql-server-profiler"></a><span data-ttu-id="a24cb-102">將追蹤結果儲存至檔案 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="a24cb-102">Save Trace Results to a File (SQL Server Profiler)</span></span>
  <span data-ttu-id="a24cb-103">本主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，將追蹤結果儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="a24cb-103">This topic describes how to save trace results to a file by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-save-trace-results-to-a-file"></a><span data-ttu-id="a24cb-104">若要將追蹤結果儲存至檔案</span><span class="sxs-lookup"><span data-stu-id="a24cb-104">To save trace results to a file</span></span>  
  
1.  <span data-ttu-id="a24cb-105">在 [檔案] 功能表上，按一下 [新增追蹤]，接著連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a24cb-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="a24cb-106">會出現 [追蹤屬性] **[追蹤屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a24cb-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a24cb-107">如果選取 [進行連接後立即啟動追蹤]，將不會顯示 [追蹤屬性] 對話方塊，而是開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="a24cb-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="a24cb-108">於 [工具] 功能表，按一下 [選項]，並清除 [連接後立即啟動追蹤] 核取方塊，以關閉這項設定。</span><span class="sxs-lookup"><span data-stu-id="a24cb-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="a24cb-109">在 **[追蹤名稱]** 方塊中，輸入追蹤的名稱。</span><span class="sxs-lookup"><span data-stu-id="a24cb-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="a24cb-110">選取 [儲存至檔案] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a24cb-110">Select the **Save to file** check box.</span></span>  
  
     <span data-ttu-id="a24cb-111">[另存新檔] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="a24cb-111">The **Save As**dialog box appears.</span></span>  
  
4.  <span data-ttu-id="a24cb-112">在 [另存新檔] 對話方塊中指定路徑和檔名。</span><span class="sxs-lookup"><span data-stu-id="a24cb-112">Specify a path and filename in the **Save As**dialog box.</span></span> <span data-ttu-id="a24cb-113">按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="a24cb-113">Click **Save.**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a24cb-114">請確定 SQL Server 服務具有足夠的權限，可將檔案寫入指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="a24cb-114">Ensure that the SQL Server service has sufficient permissions to write to a file in the directory specified.</span></span>  
  
5.  <span data-ttu-id="a24cb-115">在 [追蹤屬性] 對話方塊的 [設定最大檔案大小 (MB)] 文字方塊中，輸入最大檔案大小。</span><span class="sxs-lookup"><span data-stu-id="a24cb-115">In the **Trace Properties** dialog box, enter the maximum file size in the **Set maximum file size (MB)** text box.</span></span> <span data-ttu-id="a24cb-116">預設值為 5 MB。</span><span class="sxs-lookup"><span data-stu-id="a24cb-116">The default value is 5 megabytes (MB).</span></span>  
  
6.  <span data-ttu-id="a24cb-117">(選擇性) 指定下列選項：</span><span class="sxs-lookup"><span data-stu-id="a24cb-117">Optionally, specify the following options:</span></span>  
  
    -   <span data-ttu-id="a24cb-118">選取 [啟用檔案換用] 核取方塊，讓 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 一旦達到最大檔案大小時，便會建立新的追蹤資料檔案。</span><span class="sxs-lookup"><span data-stu-id="a24cb-118">Select the **Enable file rollover** check box to have [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] create new files for trace data once the maximum file size is reached.</span></span> <span data-ttu-id="a24cb-119">預設會選取此選項。</span><span class="sxs-lookup"><span data-stu-id="a24cb-119">This option is selected by default.</span></span>  
  
    -   <span data-ttu-id="a24cb-120">選取 [伺服器處理追蹤資料] 核取方塊，以確定伺服器會記錄每一個追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="a24cb-120">Select the **Server processes trace data** check box to ensure that the server records each trace event.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="a24cb-121">清除 [伺服器處理追蹤資料] 時，如果記錄事件會明顯降低效能，伺服器就不會記錄事件。</span><span class="sxs-lookup"><span data-stu-id="a24cb-121">When **Server processes trace data**is cleared, the server does not record events if recording events significantly degrades performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a24cb-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a24cb-122">See Also</span></span>  
 [<span data-ttu-id="a24cb-123">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="a24cb-123">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
